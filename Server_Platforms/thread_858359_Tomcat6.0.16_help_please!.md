---
title: "Tomcat6.0.16 help please!"
date: 2008-07-13
forum: Server Platforms
---

### Post by babyboss on 2008-07-13
I am having problem with enabling admin and manager access with newly installed tomcat 6.0.16.

I followed documentation on Manager Access Configuration by editing tomcat_folder/conf/tomcat-users.xml file, following is my tomcat-users.xml file after editing:
<?xml version='1.0' encoding='utf-8'?> 
<tomcat-users> 
<role rolename="manager"/> 
<role rolename="standard"/> 
<user username="craigmcc" password="secret" roles="standard,manager" /> 
</tomcat-users> 

Normally, after editing the file, when I go to [http://localhost:8080](http://localhost:8080), and click on Status and Tomcat Manager link on the left side bar, I should be asked to promot username and password. However, I immediately received a "http error 401"

Can someone please help me on this? Thank you very much!

---

