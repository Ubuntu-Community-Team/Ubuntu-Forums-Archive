---
title: "ldap and dsn on ubuntu"
date: 2012-12-04
forum: Server Platforms
---

### Post by Rakeshvijayan on 2012-12-04
Hi friends 

I got a new requirement in my firm .That it is ,they ask me to all user in my firm have user name and password in server .all user must login to the server and store their data s to the server  like ACTIVE DIRECTORY  in windows ..Directors ask me to do it on windows os my question is , is it possible on OUR  ubuntu system ...I search on google about this, i got information about ldap but I don't know how it works and configure on ubuntu 

FRIENDS THIS IS AN  URGENT REQUIREMENT ,if it don't possible  the pressure   from higher authorities make me to use windows os .I leave that os on past 2 years 

 THANKS

---

### Post by dapperdanny77 on 2012-12-04
hi,

the main question is what services do you have to provide for your users - fileservices, webservices, databases, whatever?

you can do all these things on linux and windows systems, but ...
what are your experiences with LDAP, Samba, Apache, ... on Linux? you have to have a more or less deep knowlege about these pieces of software - if not, this whole project can become very frustrating for all participants.

decide carefully - be pragmatic

---

### Post by Neill_R on 2012-12-04
I am running a Ubuntu -Windows AD domain. The Ubuntu machine is the gateway to the Internet and I use centrifydc to connect it to my windows domain. It all seems to work well but I am no expert in server administration either Windows or Linux. However I am running postfix mail-server, apache web server printer server. I also have Ubuntu-desktop installed users can log in to the domain on the Ubuntu server as they can with Windows and are validated against the domain.

[email]firstname.lastname@i-surname.co.uk[/email] or i-surname\firstname.lastname.


check it out at 
[http://www.centrify.com/express/free.asp ]("http://www.centrify.com/express/free.asp")

FYI I am using Windows 2000 Advanced server SP4 and Centrify is new I believe

---

### Post by Rakeshvijayan on 2012-12-06
> **Neill_R said:**
> also have Ubuntu-desktop installed users can log in to the domain on the Ubuntu server as they can with Windows and are validated against the domain.


Site give me Idea for integrating ubuntu system to windows active directory am I correct ?

I need an individual setup for ubuntu systems  and windows systems  in my ubuntu server 
like windows server os .My requirement is that all users in my firm must can  login all system with their user id and password , They need GUI and store their date in their own shared directory and can access any where in lan systems 

IS IT POSSIBLE ON OUR UBUNTU   , I DONT KNOW WHICH SERVICE AND PACKAGES ARE NEED FOR THIS 


Thanks

---

### Post by Rakeshvijayan on 2012-12-06
> **dapperdanny77 said:**
> hi,

the main question is what services do you have to provide for your users - fileservices, webservices, databases, whatever?

you can do all these things on linux and windows systems, but ...
what are your experiences with LDAP, Samba, Apache, ... on Linux? you have to have a more or less deep knowlege about these pieces of software - if not, this whole project can become very frustrating for all participants.

decide carefully - be pragmatic


 I need to give them samba , webbrowsing , enough but my requirement is windows system must act as client of ubuntu server .Is it possible ?

---

### Post by foxuser on 2012-12-06
Hi,

You can try Zentyal

[http://www.zentyal.org/](http://www.zentyal.org/)

---

### Post by Rakeshvijayan on 2012-12-12
Final question for all my friend Is any body configured ldap on ubuntu if so please 

make tutorial about this topic else it may disadvantage of ubuntu

---

### Post by miguelpires on 2012-12-12
> **Rakeshvijayan said:**
> Final question for all my friend Is any body configured ldap on ubuntu if so please 

make tutorial about this topic else it may disadvantage of ubuntu

Hi,
I've an office running with 7 machines (not to big I know), using Zentyal as a Server and Ubuntu 12.04 as workstations. We have Ldap authentication (AD).

Is not easy to setup the "Zentyal" whay, and we, right now, only have share folders and gatway configured. 

If you want i can share the how to.

Regard's
Miguel

---

### Post by miguelpires on 2012-12-12
Sorry i don't read correctly your post:
The How to of Ldap (Zentyal whay) link:

[http://dl.dropbox.com/u/33841668/server%20conf.odt](http://dl.dropbox.com/u/33841668/server%20conf.odt)

regard's
Miguel

---

