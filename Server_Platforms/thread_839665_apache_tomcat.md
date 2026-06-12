---
title: "apache tomcat???"
date: 2008-06-24
forum: Server Platforms
---

### Post by hockey97 on 2008-06-24
Hey  I talked to some people saying apache tomcat is great.

I never heard of it until my friends told me some about it.

They said it's a java application server.

I was woundering what database does it use??

mysql??

does it have it intergraded into the software??

how does it store data?

I am currently using apache with mysql and was woundering about what people use for datastorage with this.

---

### Post by lazy74 on 2008-06-30
Hello,
Tomcat will just run Java web applications (Servlet and JSP).
It does not handle any data storage or database access by default.
You have to do a bunch of JAva programming to access a database.
If you don't have to use Java for a specific reason, using apache + PHP + mysql is probably a better idea.

---

