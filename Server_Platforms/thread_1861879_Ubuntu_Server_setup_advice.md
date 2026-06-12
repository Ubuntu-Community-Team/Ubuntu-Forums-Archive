---
title: "Ubuntu Server setup advice"
date: 2011-10-16
forum: Server Platforms
---

### Post by mindfilter on 2011-10-16
Greetings!

As a linux n00b currently at the steep end of the learning curve, I'm in desperate need of guidance right now.

I want to set up an Ubuntu Server (11.10 amd64) with the following features:

[LIST=1]
[*]Domain Controller with centralized user authentication
[*]Roaming profiles and disk quotas for all users
[*]Capable of serving both Ubuntu Desktop and Windows workstations
[*]Ability to remotely control the server from outside the local network (internet)
[/LIST]
So, Samba4? OpenLDAP? Trying to make sense of it all gave me a headache..

Simple step-by-step instructions would be greatly appreciated! :)

Thanks,
mindfilter

---

### Post by HermanAB on 2011-10-16
It is very easy actually, since you mentioned Windows workstations.  Go and buy Windows Server and install that with Active Directory. You need to use the right tool for the job.

---

### Post by mindfilter on 2011-10-16
> **HermanAB said:**
> It is very easy actually, since you mentioned Windows workstations.  Go and buy Windows Server and install that with Active Directory. You need to use the right tool for the job.

I appreciate your honesty, and I have already considered the option. However, I also mentioned Ubuntu desktops, which will have to be connected to Windows Server should I go for that solution. Do you happen to know how to accomplish that?


So Ubuntu Server just can't cut the mustard in a mixed Linux/Windows environment? Is that it?


Regards,
mindfilter

---

### Post by newbie-user on 2011-10-19
A properly configured samba server will act as a domain controller.  You can use Ubuntu server for that.  For roaming profiles, I would recommend using NFS, but I'm not sure how roaming profiles would work on both Ubuntu and Windows.  For remotely controlling the server, Ubuntu is better equipped out of the box to control both Windows and Ubuntu servers.

---

### Post by haqking on 2011-10-19
here is the guide for Ubuntu Server 

[https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html)

This covers pretty much every useful server service.

for remote control, most Linux server remote admin is done with ssh.

---

### Post by senor_smile on 2011-11-16
> **mindfilter said:**
> Greetings!

As a linux n00b currently at the steep end of the learning curve, I'm in desperate need of guidance right now.

I want to set up an Ubuntu Server (11.10 amd64) with the following features:

[LIST=1]
[*]Domain Controller with centralized user authentication
[*]Roaming profiles and disk quotas for all users
[*]Capable of serving both Ubuntu Desktop and Windows workstations
[*]Ability to remotely control the server from outside the local network (internet)
[/LIST]
So, Samba4? OpenLDAP? Trying to make sense of it all gave me a headache..

Simple step-by-step instructions would be greatly appreciated! :)

Thanks,
mindfilter

1. Centralized user authentication: 
[INDENT]Samba3 and samba4 can both fulfill this basic requirement.  Since samba4 is still in alpha, as previously mentioned, I would recommend to hold off.  I am excited about some of the success stories I have heard recently, but for production it might not be ready.  

With samba3 you can make an NT 4 compatible directory for authenticating windows users.  I don't have any links right now, but I know that it is very possible to authenticate a Linux client through a samba3 domain controller as well.[/INDENT]

2. Roaming profiles:
[INDENT]With samba3, roaming profiles are also fully supported.  I have used this feature in the past, although between Windows XP and my users filling up their user folders, I decided against roaming profiles. [/INDENT]

3. Ubuntu and Windows client compability: 
[INDENT]As mentioned, Windows will work natively with a samba3 domain, and some set up should get you to the point of joining an Ubuntu client to a samba3 domain.  [/INDENT]

4. Remotely control the server from the internet: 
[INDENT]As previously mentioned, SSH is usually used for this.  If you want a gui environment, check out freenx on the server side, with nomachine nx as a client connecting to the server. [/INDENT]

If I find links to tutorials on any of this stuff, I will post.

---

### Post by senor_smile on 2011-11-16
> **senor_smile said:**
> 1. Centralized user authentication: 
[INDENT]Samba3 and samba4 can both fulfill this basic requirement.  Since samba4 is still in alpha, as previously mentioned, I would recommend to hold off.  I am excited about some of the success stories I have heard recently, but for production it might not be ready.  

With samba3 you can make an NT 4 compatible directory for authenticating windows users.  I don't have any links right now, but I know that it is very possible to authenticate a Linux client through a samba3 domain controller as well.[/INDENT]

2. Roaming profiles:
[INDENT]With samba3, roaming profiles are also fully supported.  I have used this feature in the past, although between Windows XP and my users filling up their user folders, I decided against roaming profiles. [/INDENT]

3. Ubuntu and Windows client compability: 
[INDENT]As mentioned, Windows will work natively with a samba3 domain, and some set up should get you to the point of joining an Ubuntu client to a samba3 domain.  [/INDENT]

4. Remotely control the server from the internet: 
[INDENT]As previously mentioned, SSH is usually used for this.  If you want a gui environment, check out freenx on the server side, with nomachine nx as a client connecting to the server. [/INDENT]

If I find links to tutorials on any of this stuff, I will post.

I had nearly forgotten about zentyal (formerly known as ebox).  It automates many things, including making an NT 4 style domain controller for Windows machines to authenticate to, it provides the sharing services, replication to multiple zentyal based servers, and supports roaming profiles.  They also have an Ubuntu based client module to allow Ubuntu desktops to join the domain for authentication and integration. 


[http://www.zentyal.org/]("http://www.zentyal.org/")
[http://trac.zentyal.org/wiki/Documentation/Community/ZentyalDesktop/Ubuntu]("http://trac.zentyal.org/wiki/Documentation/Community/ZentyalDesktop/Ubuntu")

---

