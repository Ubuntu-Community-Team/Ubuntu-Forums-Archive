---
title: "What is the difference between application server and web server?"
date: 2010-01-05
forum: Server Platforms
---

### Post by andrewan on 2010-01-05
I want to know more specific about this.
 1.Which of the server  support business logic and business logic is written using which programming language?
2.In J2EE,which is application server and which is web server?
3.what are the roles of both the application and web server?
4.Programming language and concept used in application server and web server?

---

### Post by kiranmurari on 2010-01-05
[SIZE=2]The following links throw some insight on differences between Web Servers and Application Servers.
[http://www.sap-img.com/java/difference-between-web-and-application-server.htm](http://www.sap-img.com/java/difference-between-web-and-application-server.htm)
[http://www.javaworld.com/javaqa/2002-08/01-qa-0823-appvswebserver.html](http://www.javaworld.com/javaqa/2002-08/01-qa-0823-appvswebserver.html)[/SIZE]  
       
[SIZE=2]**1. Which of the server support business logic and business logic is written using which programming language?**
Web server exclusively handles HTTP requests, whereas an application server serves business logic to application programs through any number of protocols.[/SIZE]
       [SIZE=2]There are many options for server-side scripting languages. Each language has advantages and disadvantages, but any language sufficiently handles most of the needs. Some of the most popular server-side scripting languages include PHP, JSP, Ruby on Rails, Adobe Cold Fusion, Microsoft ASP.NET[/SIZE]
       
[SIZE=2]**2. In J2EE,which is application server and which is web server?**
J2EE or Java EE 5 application servers include Apache Tomcat, Tcat Server, tc Server, WebSphere, Sybase Enterprise Application Server, WebLogic Server, JBoss, JRun, Apache Geronimo, Oracle OC4J, Sun GlassFish Enterprise Server, SAP Netweaver AS, Glassfish Application Server, WebObjects[/SIZE]
       [SIZE=2]Sun Java System Web Server is a web server designed for medium and large business
applications. It is based on the earlier Sun ONE Web Server, iPlanet Web Server and Netscape Enterprise Server products. This is available on all major operating systems, supports JSP and Java Servlet technologies, PHP, NSAPI, CGI, and ColdFusion
[/SIZE] 
[SIZE=2][http://wikis.sun.com/display/wsFOSS/Open+Web+Server](http://wikis.sun.com/display/wsFOSS/Open+Web+Server)[/SIZE]
       
[SIZE=2]**3.what are the roles of both the application and web server?**
Essentially Web Servers host and serve static web pages and their associated files like images, CSS, js and flash movies.[/SIZE]
       [SIZE=2]Role of the application server is to serve as a platform for the web application (which in the case of J2EE applications would be a collection of servlets, JSP. HTML pages etc) App Servers also typically provide services like authentication, authorization, access control, connection pooling etc[/SIZE]
       
[SIZE=2]**4.Programming language and concept used in application server and web server?**
Hope answer to question 1 also answers this.[/SIZE]
       [SIZE=2]
[/SIZE]
[SIZE=2]Regards,
Kiran[/SIZE]

---

