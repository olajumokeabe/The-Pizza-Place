# The-Pizza-Place Analysis

Pizza is a dish of Italian origin consisting of a usually round, flat base of leavened wheat-based dough topped with tomatoes, cheese, and often various toppings.
The pizza place store has been doing fairly well since its inception this year, however the owner of the pizza place store would like to get more insights on whatnots of his business. He has given me the past year's data and after carefully accessing the data, I came up with the following questions.

        Here are some questions that we'd like to be able to answer:
What are our best and worst selling pizzas?

What days and times do we tend to be busiest?

Are there any peak hours?

Do we have any bestsellers?

How much money did we make this year?

Can we indentify any seasonality in the sales?

Are there any pizzas we should take of the menu, or any promotions we could leverage?

#  Data Collection
        Tool Used:
Microsoft Excel was used for this analysis.

        About the dataset
        
This dataset contains 4 tables in CSV format

The Orders table contains the date & time that all table orders were placed

The Order Details table contains the different pizzas served with each order in the Orders table, and their quantities

The Pizzas table contains the size and price for each distinct pizza in the Order Details table, as well as its broader pizza type

The Pizza Types table contains details on the pizza types in the Pizzas table, including their name as it appears on the menu, the category it falls under, and its list of ingredients

# Data Cleaning and Transformation

I joined the respective tables together using the VLOOKUP function, an example of that is written below. The function was used as I did not intend to join all the columns in some tables.

             =VLOOKUP([@[Order_Details_Id]],Order_details!$1:$1048576,3,FALSE)
 
VLOOKUP stands for 'Vertical Lookup'. It is a function that makes Excel search for a certain value in a column (the so called 'table array'), in order to return a value from a different column in the same row. 
vlookup syntaxAfter joining the respective tables together, I created another column - a conditional column, to indicate the period of the day using the order_time column.

![image](https://github.com/olajumokeabe/The-Pizza-Place/assets/125363157/3d490eef-f361-4363-b49a-c0a7e4a9b41c)

The code can be seen below:

          =IF(TIME(HOUR(K2), MINUTE(K2), SECOND(K2)) < TIME(12, 0, 0), "Morning",
           IF(TIME(HOUR(K2), MINUTE(K2), SECOND(K2)) < TIME(15, 0, 0), "Mid-day",
           IF(TIME(HOUR(K2), MINUTE(K2), SECOND(K2)) <= TIME(19, 0, 0), "Evening",
          "Night")))

Another column was also created using the TEXT function, to extra the days of the week as we would use that to know which day of the week is usually the busiest.

             =TEXT(J:J,"dddd")

![image](https://github.com/olajumokeabe/The-Pizza-Place/assets/125363157/0f250bc5-2a5d-4c45-8a86-c46f182960af)

Other transformations that were done includes; changing the price data type to currency and using the $ dollar to denote which currency type
The size columns were also changed from L,M,S,XL,XXL to Large, Medium, Small, Xtra large and Extra-extra-large for better understanding.

# EDA and Insights

The total revenue from pizza sales is $801,944.70 calculated using the SUM function, with July being the best-performing month. Using the SUMIF function, revenue generated on each sizes were also calculated.

![image](https://github.com/olajumokeabe/The-Pizza-Place/assets/125363157/dfa8df83-a80c-4424-b6ec-6baee5151f93)

                =SUMIF(C:C,C2,D:D) for small sized pizza

![Screenshot (275)](https://github.com/olajumokeabe/The-Pizza-Place/assets/125363157/0f565dc3-1ad7-49dc-a602-ff1d85fa8e5a)

Sales show an up and down trend, with some months experiencing high sales and others experiencing drops, but overall remaining within a similar price range. However, October had the lowest drop in sales.


The top ten best-selling pizza types with the highest order quantities are:

![image](https://github.com/olajumokeabe/The-Pizza-Place/assets/125363157/e63443ba-c2ff-4d71-8611-c4fcf465b952)

· The Big Meat Pizza - Small

· The Thai Chicken Pizza - Large

· The Five Cheese Pizza - Large

· The Four Cheese Pizza - Large

· The Classic Deluxe Pizza - Medium

· The Spicy Italian Pizza - Large

· The Hawaiian Pizza - Small

· The Southwest Chicken Pizza - Large

· The Barbecue Chicken Pizza - Large

· The Barbecue Chicken Pizza - Medium

Friday is considered the best days for sales as the store experiences high influx of orders on this day, while the day with the least customers is Sunday and this could be attributed to the fact that its usually a day in for most people. 

![Screenshot (276)](https://github.com/olajumokeabe/The-Pizza-Place/assets/125363157/c2bcf38d-2829-419f-bf45-793a78246461)


The highest sold pizza by category is the classic pizza which has sales of 29.99% followed by supreme at 24.22%, and overall the preferred size is the large size.
Peak hours for pizza orders are from mid-day to evening, specifically between 12 pm and 7 pm, with major focus on 12 pm - 3 pm.

The least ordered pizzas, with low quantity, are:

· The Greek Pizza - extra-extra-large

· The Green Garden Pizza - Large

· The Chicken Alfredo Pizza - Small

· The Calabrese Pizza - Small

· The Mexicana Pizza - Small


# Visualization
The interactive dashboard involves the use of slicers to get better knowledge insights into each month and pizza sizes

![Pizza3](https://github.com/olajumokeabe/The-Pizza-Place/assets/125363157/2bcd9a55-30f9-408a-bdcb-2d3278531614)


# Recommendations
The worst selling pizzas should be removed from the menu to save cost on them and more attention should be given to the best sellers.

The Ingredients of the Pepperoni pizza should always be made readily available and in large quantities especially on Fridays as it is most ordered pizza on the day.

Since more orders are received on Fridays, a discount policy should be introduced every last Friday of the month or incentives given where customers gets an extra pizza when they buy more than one.

More staffs should also be assigned to work on this day in order to make order delivery prompt

Offer discounted price for the most ordered pizza type and sizes in order to encourage more consumers to consider their favourite pizza

To boost orders and potentially increase sales, discounts could also be offered on the following five pizzas:
· The Chicken Alfredo Pizza - Large

· The Italian Veggie - Large

· The Italian Supreme Pizza - Small

· The Greek Pizza - Large

· The Spinach Supreme Pizza - Medium

Link to interactive dashboard on excel;
[Pizza Sales Report.xlsx](https%3A%2F%2F1drv.ms%2Fx%2Fs!Amhisb_pS3WhgXnP14CCWaa8s4kf)


Connect with me 🔔:
https://linktr.ee/olajumoke_ajala
