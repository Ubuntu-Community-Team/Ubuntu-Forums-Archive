---
title: "apache tomcat"
date: 2013-02-19
forum: Server Platforms
---

### Post by sachin0091 on 2013-02-19
I'm new to apache tomcat

Can anybody tell me how to install tomcat server and write program in tomcat.

I'm not getting what to do after I install apache 2 on my ubuntu running machine.

---

### Post by slickymaster on 2013-02-19
To install Tomcat in Ubuntu Server 12.04, just run the following command at a terminal window:
```
sudo apt-get install tomcat7
```

You don't *"write program in tomcat"*, what you do is to develop web applications that will run/deployed in Tomcat.
So first of all you have to ask yourself in what programming language are you planning on developing?

The best place for you to start is here: [Apache Tomcat]("http://tomcat.apache.org/")

---

### Post by sachin0091 on 2013-02-20
i need to do it using java mean to say i wann develop jsp page

i have a code right with me how can i do it..

in microsoft we have gui's

but i dint find anything of like that in ubuntu 

wat shall i do

---

### Post by slickymaster on 2013-02-20
I'm confused. Do you already have your web application done and need assistance on the deployment into Tomcat or do you need assistance on the java server pages and servlets development to make a web application?

---

### Post by sachin0091 on 2013-02-20
no..
actually have to code a jsp page jus ik a login page
an run it in tomcat(local host)..

consider a scenario lik
 'm posting using curl
on the server side i need my jsp page to catch it..

how can i do it

i knw to code in jsp and curl but not getting where to dump them in order to make a communication between them;);););););)

---

### Post by slickymaster on 2013-02-20
Take a look at [Tomcat's Manager App HOW-TO -> Deploy A New Application from a Local Path]("http://tomcat.apache.org/tomcat-7.0-doc/manager-howto.html#Deploy_A_New_Application_from_a_Local_Path")

---

