---
title: "Simple Membership Manager/Database"
date: 2017-01-05
forum: The Cafe
---

### Post by elliotbeken on 2017-01-05
Hi All,

Hope this is in the correct section of the forum!

I am a membership secretary for a small club. Members have to pay on a annual bases.

I am looking for a solution to manage the members. Ideally i am after an online CMS package that i can use to store the members information. (I want this to be installed on my web hosting)

Looking to store the following information:

Names
Address
Email Address
Membership Purchase/Expiry
ETC

Obviously i need the information to be secure so i will need to login to add and view the information.  

Ideally something like an MS-access database.

Does anyone know of such a thing?

---

### Post by ian-weisser on 2017-01-06
CMS seems rather overkill for such a paltry amount of flat (single table, non-relational) data.
What about a simple LibreOffice spreadsheet or database?
Or a simple Google spreadsheet?
There are also online solutions like Wild Apricot, often free for 50-or-fewer members.

Any hosting, online or offline, of Personally Identifiable Information should be encrypted with a strong key, lest stolen data lead to identity theft and subsequent lawsuits.
Any stored payment information (like bank accounts and credit cards) has even more stringent requirements. Avoid whenever possible.

One imagines that your club Treasurer has some kind of bookkeeping and audit trail. That workflow may be adaptable to your needs, too.
If anyone in your club is handy with Python or another easy language, customizing a solution to exactly meet your needs may be fairly rapid.

---

### Post by mastablasta on 2017-01-06
depends how many members you have. i run 52 in a simple excel spreadsheet. i later moved it to GoogleApps which we use, so that members of executive board have Access to this informaiton. 

otherwise you need to be careful with securing information if you publish it online. and ofcourse there should be a statement that they agree for you to process personal informaiton etc. etc.

---

### Post by elliotbeken on 2017-01-06
Thanks for the replys. 

I currently use a spreadsheet and with 600-700 members this is not ideal, i also want it to be hosted to stop any issues with data loss and its also nice being able to access the info from any device via a web page.

To add no payment details are stored at all, all payments are made via PayPal all i want to store is the following:

Name 
Address
Dates of membership expiry
Membership number

I have looked at just using MYSQL and phpmyadmin to store the information (provided with my hosting) but not sure how and not had time to have a proper play/test.

---

### Post by ian-weisser on 2017-01-06
You can play with a SQL-type database with the 'sqlite' package. It's small and has few dependencies, and will give you a safe sandbox to play with the database and SQL language. The SQL language in sqlite should be near-identical to your online provider's SQL.

I use Python to manage a somewhat similar list of about 500 of my ongoing customers. We use our (off-network) bookkeeping database to store our data, and Python scripts to send the billing emails, prepare reports for the bookkeeper, and even record most of the payments with one keystroke. It's fast, light, and easy for me to debug and maintain.

---

