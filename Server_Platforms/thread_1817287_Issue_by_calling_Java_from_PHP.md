---
title: "Issue by calling Java from PHP"
date: 2011-08-03
forum: Server Platforms
---

### Post by Romu on 2011-08-03
I develop my company's web site which is based on Ubuntu Server 10.04 LTS/Apache2/PHP/MySQL/WordPress.

Our internal development server is called **webdev** and its main user is also called **webdev**.

For some specific goals, we are calling from PHP (by using the **system** or **shell_exec** PHP commands) a Java program we developed. This Java program, takes some files in input and creates some output files as well.

The issue is our Java program perfectly works when we are connected to the **webdev** user account. But if we call it from the web site (and PHP), we can see from the Java verbose output that the program is actually loaded by produces...nothing.

I've recently found that the user which runs Apache is **www-data**, so I added this user to the **webdev** group (good idea or not?), but no change.

And here we are, we try some tricks in Java to get more traces and output but if someone has the genius idea to make it work, he will be my god :D

Thanks.

---

### Post by Romu on 2011-08-03
Found the problem which comes from the user accounts (storage and used by Apache). Now, I need to fix it, not really simple.

---

