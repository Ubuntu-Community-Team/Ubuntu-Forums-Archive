---
title: "Microsoft Access Database Design Question"
date: 2008-01-02
forum: The Cafe
---

### Post by Black Mage on 2008-01-02
I'm making this database for a non-profit organizations where volunteers can clock in and out. There interface is in Java and the database is Microsoft Acces.

So what would be the best design to record hours each time they clock in and out and then be able to get hours for a week, month and yearly?

I have a few ideas in my head but they all seem to get cumbersome if a lot data is entered.

---

### Post by rax_m on 2008-01-02
Hi, You're asking a very general question for quite an involved task. 
It would be helpful if you give us some of the ideas.. or a spec ;) If you have one. 

First you need to know what the functionality of the database/application is going to be (in detail) and then take steps to design the database and/or app front-end.

Is there any reason you're not using an OSS database like MYSQL or Postgres?

Cheers
Rax

---

### Post by Black Mage on 2008-01-02
I suggested using MySQL or  PostregreSQL but the ppl who I am working with feel comfortable with Micrsoft Access *cough*Microsoft Junkies*cough*.

I've designed the GUI for the application, just the database. For the application, the user has a login name which is there initials, and when they click login it or log out, it records the time and date when the person did so.

For the staff, they are going to have option to few a volunteers hours for that week, a choosen month, a choosen year, and all total. Currently there is a table with other volunteer information such as phone, address, name, etc. I was thinking of making another table that corresponds with the primary key of the volunteer's information table, which will hold the the id, date worked, and hours worked on that day. But when I think about it, that seems to get cumbersome.

With that, I'm lost on how many tables I have for it to be efficient.

---

### Post by popch on 2008-01-02
There are just two tables needed:

Person(p#,Initials)
Work_time_slice(p#,start_date_and_time,stop_date_and_time)

With p# in Work_time_slice referring to p# in Person.

---

### Post by zipperback on 2008-01-02
> **Black Mage said:**
> I'm making this database for a non-profit organizations where volunteers can clock in and out. There interface is in Java and the database is Microsoft Acces.

So what would be the best design to record hours each time they clock in and out and then be able to get hours for a week, month and yearly?

I have a few ideas in my head but they all seem to get cumbersome if a lot data is entered.


You could easily build what you are trying to do, using php or perl and a mysql database.

If it's a matter of the application running on MS Windows, then that's not a problem either.
Mysql is available for numerous platforms, as is php and perl.

zipperback
:popcorn:

---

