#install.packages('shinydashboard')
library(shinydashboard)
library(DT)
library(shiny)
library(shinydashboard)

#input data
data = read.csv('data/DASH. 1000.csv')
data3 = read.csv('data/Book2.csv')
labels <- c("a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k")

#ui
ui <- dashboardPage(
  dashboardHeader(title = "TUGAS ADE"),
  dashboardSidebar(
    sidebarMenu(
      menuItem("DATA TABEL", tabName = "TABEL", icon = icon("chart-bar")),
      menuItem("HISTOGRAM", tabName = "ADE", icon = icon("table")),
      menuItem("TENTANG SAYA", tabName = "1", icon = icon("users"))
    )
  ),
  dashboardBody(
    tabItems(
      tabItem(tabName = "ADE",
     
    # tab konten pertama
      sliderInput(inputId = "n_breaks",
                  label = "Banyak Kelas",
                  min = 0,
                  max = 50,
                  value = 5),
      
      plotOutput(outputId = "main_plot", height = "500px", width ="500px"),
      conditionalPanel(condition = "input.density == true",
                       sliderInput(inputId = "bw_adjust",
                                   label = "Bandwidth adjustment:",
                                   min = 0.2, max = 2, value = 1, step = 0.2))
    ),
      
    #tab konten kedua
    tabItem(tabName = "ADE",
            caption =  "1000 data yang di bangkitkan dari 10.000 data. di pisahkan berdasarkan interval"),
            
      tabItem(tabName = "TABEL",
              datatable(data3,
                        caption =  "1000 data yang di bangkitkan dari 10.000 data. di pisahkan berdasarkan interval",
                        rownames = TRUE,
                        filter = "top",
                        options = list(pageLenght = 50))),
   
     tabItem(tabName = "1",
             tabPanel(id= "tim","Tentang Tim",
                      includeHTML("www/about.html")))
      )))

#server
server <- function(input, output) {
  output$main_plot <- renderPlot({
    
    hist(data$DATA,
         breaks = as.numeric(input$n_breaks),
         xlab = "Data",
         ylim = c(0,150),
         col = "lightblue",
         border = "white",
         main ="HISTOGRAM")
  
   output$tabel <- renderDataTable({
    data3
   }) 
    })
}

shinyApp(ui, server)
