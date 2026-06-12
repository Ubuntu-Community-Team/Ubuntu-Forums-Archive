---
title: "What is MySQL?"
date: 2006-01-31
forum: Server Platforms
---

### Post by Stealth on 2006-01-31
Hey, I recently gotten a website from a friend who works in webhosting. Its for a comic I have, and so I wanted to try some stuff with a little server I'm using for my backups and stuff.

Like, I wanted to see if I (or one of my other friends who actually knows how) could create a PHP script that could submit an image, with some HTML coding, reading a list of images from another directory to have it link to the recently posted comc strip, and have it all archive properly and stuff. Anyway, I'm pretty sure that's where MySQL comes in, as my webhosting gives me one database. But when I checked it out it was really confusing. then I tried installing the mysql-server phpmyadmin apache stuff and got it working and noticed that databases are not as simple I thought they were! I thought they were more like...advanced spreadsheets, or kind of like 2D "lists" in Python, but a little more advanced. But apparently there's a lot more than "rows" and "columns" but things like tables and such. Should I not bother even figuring this tuff out and get someone more experienced on it, or can someone here be able to explain it to me a little better so I can atleast start messing with it a bit?

---

### Post by mvaniersel on 2006-01-31
> 
I thought they were more like...advanced spreadsheets

In a way, yes. Tables are like a spreadsheets with a fixed number of columns, and each column can only take one type of data. It's really not very hard, and if you spend some time reading up about this, I'm sure you can figure it out.

If you have phpmyadmin up and running it should be pretty easy to try stuff out. Google for "phpmyadmin tutorial".

---

### Post by KLineD on 2006-01-31
With a database, you use a specific language (SQL) to retrieve the data you want using queries. The specific sintax varies from vendor to vendor and some database servers add their own extensions to SQL but for the basics it's pretty much the same for any server you use.

Start fooling around with mysql. In their page there's a tutorial to get you started using the mysql console. If you want to learn SQL the [W3Schools tutorial]("http://www.w3schools.com/sql/default.asp") is very handy.

---

