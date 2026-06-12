---
title: "Can't get My WebApps to Work with Tomcat"
date: 2009-07-01
forum: Server Platforms
---

### Post by nikhilbhardwaj on 2009-07-01
hi

i installed tomcat with apt-get
now when i try to run my custom web app
i get a 404 error

the name of the web app is TechieBookie 
here is the list of plcaes where i have put the TechieBookie folder
/var/lib/tomcat6/webapps/
/usr/share/tomcat6/webapps/
ie in both CATALINA_HOME and CATALINA_BASE
but for some reason tomcat refuses to pick them up

i try to access the web app as
[http://localhost:8080/TechieBookie/index.jsp](http://localhost:8080/TechieBookie/index.jsp)

yes i have stopped the server and restarted it by
sudo service tomcat6 stop
sudo service tomcat6 start

i would be grateful if somebody could help me out here and tell me where to place my web apps inorder to get them working.

i had created this in windows using xampp+tomcat there i hdate top place it under CATALINA_HOME\webapps

---

### Post by nikhilbhardwaj on 2009-07-06
its been 5 days 
no reply
come on you can do better than that

---

### Post by TuckLive on 2009-07-07
To narrow down the problem, do you at least get the Tomcat page when you visit [http://localhost:8080?](http://localhost:8080?)

---

### Post by nikhilbhardwaj on 2009-07-11
yes absolutely
i get the tomcat pace on localhost:8080 
and the examples supplied with it work too

---

### Post by TuckLive on 2009-07-14
I don't have much experience with Tomcat, but the webapp I'm running is under 

usr/local/tomcat/webapps

This is the only directory I have the webapp under.

---

### Post by nikhilbhardwaj on 2009-07-15
i don't know what the problem is either
when i downloaded a tat.gz from the tomcat site
and extracted it in my ~/Public
set up the variables JAVA_HOME etc
that works without a problem

---

### Post by Tux.Ice on 2009-07-15
Have you installed Apache?

---

### Post by nikhilbhardwaj on 2009-07-16
no i havent installed apache
but i have xampp 1.7.1 in /opt/lampp

---

