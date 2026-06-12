---
title: "apache tomcat 6 - deploying war files"
date: 2009-06-03
forum: Server Platforms
---

### Post by chf on 2009-06-03
hello,

my tomcat server is running fine and i can see all documentation and examples, which came with it. the server is running under localhost: portnumber.

i have a problem when trying to deploy war files. every time i try to run the war files i get an error message like this: **HTTP Status 404 - /myapplication/**.

i am generating my war files this way: jar file.war mywarfolder.

is there any possibility to just copy the war folder into my directory /var/lib/tomcat6/webapps

does anyone now a solution to the problem?

best regards

chf

---

### Post by keesp on 2010-12-21
Just one possible solution that probably a lot of Ubuntu newbies will make:
look at the permissions of the war file you copy in the webapps folder. If you copy a war with limited permissiinos (readonly) then tomcat cannot extract the war, and will give an error (var/log/tomcatxxx) that will give a clue what went wrong.

---

