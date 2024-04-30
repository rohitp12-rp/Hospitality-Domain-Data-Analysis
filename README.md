# Hospitality Domain Data Analysis

## Overview
This project focuses on analyzing data to provide valuable insights for the hospitality domain, particularly the hotel business. By utilizing Industry identical data and various DAX (Data Analysis Expressions) formulas, the aim is to uncover patterns, trends, and performance metrics to assist hotel management in making informed decisions and optimizing their operations.

![Final Dashboard Image](Final%20DashBoard.png)

## DAX Formulas Used
- **Revenue**: `SUM(fact_bookings[revenue_realized])`
  
- **Total Bookings**: `COUNT(fact_bookings[booking_id])`
  
- **Total Capacity**: `SUM(fact_aggregated_bookings[capacity])`
  
- **Total Successful Bookings**: `SUM(fact_aggregated_bookings[successful_bookings])`
  
- **Occupancy %**: `DIVIDE([Total Successful Bookings],[Total Capacity],0)`
  
- **Average Rating**: `AVERAGE(fact_bookings[ratings_given])`
  
- **No of Days**: `DATEDIFF(MIN(dim_date[date]),MAX(dim_date[date]),DAY) +1`
  
- **Total Cancelled Bookings**: `CALCULATE([Total Bookings],fact_bookings[booking_status]="Cancelled")`
  
- **Cancellation %**: `DIVIDE([Total Cancelled Bookings],[Total Bookings])`
  
- **Total Checked Out**: `CALCULATE([Total Bookings],fact_bookings[booking_status]="Checked Out")`
  
- **Total No Show Bookings**: `CALCULATE([Total Bookings],fact_bookings[booking_status]="No Show")`
  
- **No Show Rate %**: `DIVIDE([Total No Show Bookings],[Total Bookings])`
  
- **Booking % by Platform**: `DIVIDE([Total Bookings], CALCULATE([Total Bookings], ALL(fact_bookings[booking_platform])))*100`
  
- **Booking % by Room class**: `DIVIDE([Total Bookings], CALCULATE([Total Bookings], ALL(dim_rooms[room_class])))*100`
  
- **ADR (Average Daily Rate)**: `DIVIDE([Revenue], [Total Bookings],0)`
  
- **Realisation %**: `1- ([Cancellation %]+[No Show Rate %])`
  
- **RevPAR (Revenue Per Available Room)**: `DIVIDE([Revenue],[Total Capacity])`
  
- **DBRN (Daily Booked Room Nights)**: `DIVIDE([Total Bookings], [No of Days])`
  
- **DSRN (Daily Sellable Room Nights)**: `DIVIDE([Total Capacity], [No of Days])`
  
- **DURN (Daily Utilized Room Nights)**: `DIVIDE([Total Checked Out],[No of Days])`
  
- **Revenue WoW Change %**: `(revcw / revpw) - 1` (Where revcw is revenue for the current week and revpw is revenue for the previous week)
  
- **Occupancy WoW Change %**: `(revcw / revpw) - 1` (Where revcw is occupancy for the current week and revpw is occupancy for the previous week)
  
- **ADR WoW Change %**: `(revcw / revpw) - 1` (Where revcw is ADR for the current week and revpw is ADR for the previous week)


- **RevPAR WoW Change %**: `(revcw / revpw) - 1` (Where revcw is RevPAR for the current week and revpw is RevPAR for the previous week)
  
- **Realisation WoW Change %**: `(revcw / revpw) - 1` (Where revcw is realisation for the current week and revpw is realisation for the previous week)
  
- **DSRN WoW Change %**: `(revcw / revpw) - 1` (Where revcw is DSRN for the current week and revpw is DSRN for the previous week)

  [!NOTE]
  A more detailed view on these DAX can be found in the Metrics/metrics list.xlsx file
