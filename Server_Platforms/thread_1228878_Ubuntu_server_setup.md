---
title: "Ubuntu server setup"
date: 2009-08-01
forum: Server Platforms
---

### Post by roshanjose on 2009-08-01
I am planning to set up a server for 60 client systems...I think DNS and LDAP are best according to my specification...but I am unsure...i will specify the requirements that the server has to provide:

1. Enable/Disable access to internet for each client

2. Monitor the settings for the entire network and for each client

3. Monitor every client activities

4. Enable/Disable access to certain websites

5. Package updations from server to clients

6. File transfers (sort of ssh....but if GUI is available then its an    advantage for naive users)


7. Ability to access certain files on server which are made public by the server. For example a java program on server can be downloaded from the server by clients. (I suppose this can be done by installing apache2 and placing the files in /var/www)

8. If possible secure every user files and enable personalized login of each user from any system...(this is a feature of LDAP..and its just optional)


I have taken this task to install the server at college. We have 8.04 running in the systems...We need to install a server. My team in doing this to start FSF (Free Software Foundation) activities and also some projects in linux. The sole purpose is to create a strong Linux group in our college. As a student I have motivated certain students to take up these activities....The first activity is with this server setup...


Later on additional activity on server will start by installing an additional mail client... For example ibm has for eg. [email]abc@ibm.com....so[/email] we may have that at later stages....

and also a mailing list....so that students can discuss about their projects....

I hope i can get good suggestions

---

### Post by HermanAB on 2009-08-01
What are the 60 clients?  If they run Windows, then mozy on over to the Samba web site and set up domain server.  If they don't run Windows, then mozy on over to the Samba web site and set up a domain server...
;)

---

### Post by roshanjose on 2009-08-01
All those systems are with Hardy Heron....The lab is dedicated to Linux...and we installed Hardy Heron

---

### Post by roshanjose on 2009-08-01
and what is with this Samba. As far as i know its used for file sharing... and there's no windows system in the lab

---

### Post by oliv2915 on 2009-08-01
Samba can be used by all systems. It is better to have it setup for Windows then not to have it all. I am still in the learning stages of Samba my self.

---

### Post by jamesrfla on 2009-08-01
4. Squid proxy server
6. WinSCP 
7. If the file doesn't have to exit your LAN you can just host a Samba file server
For a mailing list you can use MailMan with a mail server.
Hope this helps.

---

### Post by roshanjose on 2009-08-02
I remember now..i have heard of squid......

but for each requirement requires a separate server???

Is there no single server that exhibits atleast the 1st six requirements

And by the way, Package updations here mean...updating ubuntu packages, bugs, fixes etc....

---

### Post by jamesrfla on 2009-08-02
Yeah you can run all of your serer services on one server. I run a apache2 web server, samba file server, mysql, terminal server, mail server, and SSH server all one computer.

---

### Post by roshanjose on 2009-08-02
Ohh yes i know that it can be run on a single system....I just wanted a single type of server that performs all these functionalities...

---

### Post by roshanjose on 2009-08-02
so solutions to my requirements are:

1. Squid

4. Squid

6. SSH

7. Samba

Well if there are more suggestions and corrections to my above list do remind me

---

