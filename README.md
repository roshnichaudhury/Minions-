# Group 2 MIST4610 Group Project 1

## Team Name:
21484 Group A2

## Team Members: 
1. Roshni Chaudhury - Group Leader
2. Malia Bender - Conceptual Modeler
3. Alexander Davidow - Database Designer
4. Justin Rather - Data Wrangler
5. Samira Gulyamov - SQL Writer

## Problem Description:
The task at hand is to model and build a relational database for the Wilderness Exploration Society (WES) at Peachtree State University. The purpose of the database is to visualize the general workings of an outdoor recreation and equipment rental company. The database centers around customers, rental agreements, trips, staff, and equipment inventory, which all play a key role in the company's day-to-day operations. Customers can rent equipment and register for scheduled trips, while the staff oversees rentals, maintenence tasks, trip operation, and routine inspections. Our goal is to ultimaly model these relationships, generate sample data, and populate the entities and attributes so that the database can support meaningful business insight and decision-making.

Our proposed extension to the case was to introduce a system for maintenance tracking for equipment items and to provide a service history of the equipment. Through the addition of maintenence records, implementing inspections done by staff and adding inspection records, and finally damage reports, the database can capture operational details beyond the basic rental and registration process. This allows for a more realistic representation of the company's overall operations and supports analysis related to safety issues and all issues related to equipment damage. 

## Data Model:
Our data model is based on the structure of the Wilderness Exploration Society (WES), an organization that manages outdoor trips and equipment rentals for university members and guests. The Customer entity represents all individuals who interact with the WES, including all students, faculty, alumni, and guests. Because guests must be sponsored by a university member, we included a recursive relationship within Customers, where one customer can sponsor many others, but one guest only has one sponsor. 

Customers interact with both trips and rentals. For trips, we use the Trip entity to define our general trip information like trip name, difficulty level, and trip length, and fees. Each trip can occur multiple times, so we created a one-to-many relationship between Trip and Scheduled_Trip. Scheduled_Trip includes specific dates and assigned staff leaders (the lead and the assistant). Staff members are stored in the Staff entity, and they are connected to Scheduled_Trip.

To track registration and participation in trips, we created the Trip_reg associative entity between Customers and Scheduled_Trip. This represents a many-to-many relationship since customers can register for many trips and each scheduled trip can have many people registered for them. The Trip_reg table includes attributes such as waiver status and registration status. 

We also included a recursive many-to-many relationship with the Trip entity for when a trip has prerequisites, where one trip may require completion of another before participation in that trip.

On top of managing outdoor trips, WES also does equipment rentals. The Equipment_type entity represents the type of equipment being rented and includes pricing tiers. Each equipment type can have many individual items, which is why we created a one-to-many relationship with the entity Equipment_Item. Each Equipment_Item has its own unique ID, condition rating, and availability status.

The equipment rental process itself is handled through the Rental_agreement entity, which represents a single rental transaction for a customer and is managed by a staff member. Because a rental agreement can have multiple items, we created the Rental_item associative entity between Rental_agreement and Equipment_Item to track details like expected return date and actual return date.

As an extension to the case, we added the Maintenance, Inspection, and Damage_Report entities that are all connected to Equipment_Item. This reflects our creation of a system that will track all things maintenance, from damages from inspections to breaks in equipment reported by customers. The Maintenance entity tracks repairs, costs, maintenance type, and next due dates. This has a one-to-many relationship with Equipment_item. The Inspection entity records routine checks, including results and future inspection dates. The Damage_Report entity captures damage incidents, severity, repair needs, and associated charges. Each of these entities is also linked to the Staff entity, representing which staff member performed the maintenance, inspection, or report.

<img width="500" height="455" alt="FINAL_MODEL" src="https://github.com/user-attachments/assets/6254ab20-ddcf-4f0e-8fa2-4e1900a8c9a8" />

## Data Dictonary:

## Queries:

## Database Information: 
Name of database: mb_A2
