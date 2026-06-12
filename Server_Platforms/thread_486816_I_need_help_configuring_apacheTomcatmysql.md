---
title: "I need help configuring apache/Tomcat/mysql"
date: 2007-06-28
forum: Server Platforms
---

### Post by glennyboiwpg on 2007-06-28
I need help with a complex setup.  I have limited experence with all this stuff but I'm wanting to learn.

I don't need the blow by blow by blow expanation but just the general steps required to get this to work, so then I can research those steps and figure it out from there.  Here is the setup


I have a ubuntu (fiesty fawn) desktop machine set up as a apache, tomcat, mysql ubuntu server.
I am not using the server edition of ubuntu because it couldn't reconize my wireless card, but the desktop version can, and does.  apache, tomcat and mysql are ALL installed, but need to be configured.

I will be building 2 java spring mvc applications (4 apps in total as I want a development version and a production version for both apps)

And I want a general html/css website that I will use to showcase or explain the applications.

I have registered a domain, for converstatonal purposes lets call it xyz.ca

I need apache to serve:

[www.xyz.ca](www.xyz.ca) (this will be a regular website)
[www.webstore.xyz.ca](www.webstore.xyz.ca) (this will be a java spring MVC web app)
[www.dashboard.xyz.ca](www.dashboard.xyz.ca) (this will be an inventory/reporting java mvc web app)
test.webstore.xyz.ca (This will be the development, or test version of the webstore app)
test.dashboard.xyz.ca (This will be the development, or test version of the dashboard app)

[www.webstore.xyz.ca](www.webstore.xyz.ca) and [www.dashboard.xyz.ca](www.dashboard.xyz.ca) will go to one instance of tomcat (2 seperate webapps within once instance of tomcat)

test.webstore.xyz.ca and test.dashboard.xyz.ca will go to another instance of tomcat.

Both instances of tomcat will connect to the one mysql server which will have two databases (test/prod)

I want mysql to be able to be accessed from another box.  Meaning mysql is on the server, I want to be able to go on my client, (mac osx) open a sql editor and run sql against the server.

Ok so thats what I need done... 

What are the general steps required to complete this?  

And for interest sake, this is a project that i'm doing for educational/career development purposes.

---

