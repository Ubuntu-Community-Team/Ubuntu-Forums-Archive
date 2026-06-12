---
title: "[SOLVED] First Server, Need help"
date: 2008-05-15
forum: Server Platforms
---

### Post by SurrealWraith on 2008-05-15
Hello.  I am currently wanting to make a server similar to that used by police to look up information on drivers using the drivers license number.  Specifically, I would like to construct a server that would be accessible to staff members at my school so they could look up information on students using the student's school ID number or a bar-code on the ID card.  Information about a student would include his or her dean, counselor, schedule, and IEP (learning accommodations) if applicable.  Just being able to display such information is the basic need for my server, though I may come back for more help later.  So, what I need to know is whether this is possible to do using Ubuntu (as my school uses Windows), and how I would go about doing it.  Thank you in advanced for all your help.

---

### Post by nhandler on 2008-05-17
I would look into creating a database. There are many database tools out there (both for ubuntu and windows). You should pick one that you like. Then, you will store all of the info on the students in this database. Once you have all of the info in the database, you can create a website or application (using nearly any programming language) that will access the database and display the requested information. If you don't want to crate a site/application, you can manually connect to the server using a terminal, and use sql commands to search for the information.

---

### Post by Thirtysixway on 2008-05-18
I would setup a lamp server, and use mysql to hold all the information.  Then create a secure way for staff to login and look things up via a webpage.

---

### Post by prshah on 2008-05-18
> **SurrealWraith said:**
> Specifically, I would like to construct a server that would be accessible to staff members at my school so they could look up information on students using the student's school ID number or a bar-code on the ID card.  

So, what I need to know is whether this is possible to do using Ubuntu (as my school uses Windows), and how I would go about doing it

Yes, you can do this using Ubuntu (Server edition would be better).

About how to do it; that's the kicker. I would suggest getting professional help to setup a whole distributed database system.

Ubuntu includes database utilities, and you can use any of a number of front ends. But from the tenor of your post, I don't really think that you can get such a system up and running in a reasonable length of time.

The short answer: Yes.

---

### Post by Dr Small on 2008-05-18
Yes, very possible. It would be simple with SQL and Php. Of course, you would have to write the entire framework for it.

---

