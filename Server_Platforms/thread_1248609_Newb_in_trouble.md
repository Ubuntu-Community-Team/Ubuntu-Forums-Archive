---
title: "Newb in trouble"
date: 2009-08-24
forum: Server Platforms
---

### Post by HolyFlirkingShnit on 2009-08-24
Hi Everyone,
 
I am relatively new to Ubuntu, and to Ubuntu Server. I am working with an install of 8.10, and trying to get an application to deploy in Tomcat 6, but without any luck so far.
 
I have managed to set the permissions for the various directories (/var/lib/tomcat6 and so on) to the Tomcat group, but my application still fails to start. The application is Mondrian from Pentaho.
 
I know the application itself works because it has been run and deployed on other machines with Tomcat 6, but these were all windows machines. So in short, I trust the war file to work becausse it is the same one.
 
In the log for the virtualhost (localhost) there is an error (SEVERE) listed for the application, caused by java.security.AccesControlException: access denied ... and then lists something from the app I am trying to deploy.
 
Does anyone have an idea what might be the problem. I cant seem to figure a way through this, and it doesnt appear to be a file permissions setting issue from what I can tell.
 
Any help would be greatly appreciated.
 
HFS :)

---

### Post by windependence on 2009-08-24
We could get a better idea if you would post the log files. Also am curious what you are doing with this application and why you are deploying on Tomcat.

-Tim

---

### Post by HermanAB on 2009-08-24
Yah, good luck with Tomcat.  Once you have that going, you will be a certified Linux Guru and can grow the requisite beard...

Here is some (old) Tomcat info, it may help:
[http://aeronetworks.ca/tomcat-howto.html](http://aeronetworks.ca/tomcat-howto.html)

---

### Post by HolyFlirkingShnit on 2009-08-25
Thankyou for your replies, I appreciate the help
 
I am trying to set up a 'Proof of Concept' box as the basis of a BI implementation. Mondrian works quite well as an XMLA / ROLAP provider, and allows me to model and demonstrate to others the concepts involved.
 
I am not necessarily fixed on using Tomcat, however it is 'supposed' to be the reference implementation for this type thing. Basically I have this working on a WinXP laptop (my dev environment) and am trying to shift it to a box on our network so that others in the office can toy with it too. I need their feedback to move this forward.
 
Anyway, I chose Ubuntu sever because I like the philosophy of the OS, and the fact that it is natively headless (in my opinion it is the way a server should be). I am also a fan of Postgres and Ubuntu server has this as a 'native' install as well. If I manage to move the proof-of-concept to production, then there is also the option of commercial support which will make my IT dept very happy indeed. In short I thought it was a great platform for this project - and I hope it continues to be.
 
The log file is attached to this post.
 
Surely it is not such an impossibility to create a Tomcat install that functions? The install was simple enough for the main app, as well as the admin components. It just doesnt seem to want to let me deploy a war file and have it run... Seems strange. I am sure it is just a permissions thing lurking in the background somewhere.
 
I really appreciate your help.
 
HFS

---

### Post by HermanAB on 2009-08-25
You have to go to the Tomcat project web site for information.  Most information you will find with Google is outdated or wrong or worse.
[http://tomcat.apache.org/](http://tomcat.apache.org/)

---

