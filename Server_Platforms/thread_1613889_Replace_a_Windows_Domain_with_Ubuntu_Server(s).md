---
title: "Replace a Windows Domain with Ubuntu Server(s)"
date: 2010-11-05
forum: Server Platforms
---

### Post by nightmare0 on 2010-11-05
Okay, I know this has got to be eating at many of thoughts here on the forums..
 
How in the world would one go about converting a simple Windows Domain to being a purely linux, and in this case, Ubuntu environment? It would need a solution for a GPO equivalent to manage user permissions..computer settings..etc.. Also either integration with an Exchange server (2003+) -or- a linux based equivalent (which would then need to include an alternative for GALs and Calendars - shared and the like..) 
 
I have no doubt the answer is here in the forums..held in someone's mind and scattered in pieces in posts.. lets gather it here. I'd really like to actually do this, I have a small 10 user domain that I'd love to try this with, I just need a plan before I get the thumbs up. Any comments are appreciated! Thanks!

---

### Post by s1nch4n on 2010-11-05
> **nightmare0 said:**
> Okay, I know this has got to be eating at many of thoughts here on the forums..
 
How in the world would one go about converting a simple Windows Domain to being a purely linux, and in this case, Ubuntu environment? It would need a solution for a GPO equivalent to manage user permissions..computer settings..etc.. Also either integration with an Exchange server (2003+) -or- a linux based equivalent (which would then need to include an alternative for GALs and Calendars - shared and the like..) 
 
I have no doubt the answer is here in the forums..held in someone's mind and scattered in pieces in posts.. lets gather it here. I'd really like to actually do this, I have a small 10 user domain that I'd love to try this with, I just need a plan before I get the thumbs up. Any comments are appreciated! Thanks!
with GPO?

you can use samba 4, do not install samba 4 from ubuntu or debian repo... it's broken..

you need to compile from source...

[http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

download the latest source....


i've never try integration exchange server's with samba 4... maybe you can try by yourself...

---

### Post by nightmare0 on 2010-11-05
I was under the impression that Samba only handled file shares(?) perhaps not? How would you use Samba for a GPO-esque effect? I essentially want to be able to take this domain and still be able to change network-wide configuration settings and such.. How can I do this with Samba? (I was thinking more along the lines of LDAP too..) 
 
(btw I'm thinking out-loud here, I may be wrong, correct me if I am) :)

---

### Post by nightmare0 on 2010-11-05
Searching around has left me even more puzzled. I'm not certain that Samba can provide what I need, I'm talking a Ubuntu-GPO-thing, something like System Policies (I think they're called..) so a distribution and implementation system..? And for exchange, either a Ubuntu Outlook app or a Linux Exchange server alternative..(with client of course ;) )

---

### Post by HermanAB on 2010-11-05
Howdy,

I have come to the conclusion that it is not worth the hassle really.  

The main problems with Windows 2003  server are difficulty with installing due to a lack of hardware support and difficulty with backing it up.  Both of those problems can be solved by turning it into a virtual machine.  On VMware, Win2003 works without any issues and backing it up is as simple as making a tar ball of the whole VM.  Finally, if you then need another one, you just untar your VM and few minutes later, yet another DC is running and once the ball of wax melts down and goes all wonky, you just untar it again from backup.

Because virtualization is such an effective cure for the MS Blues, I don't see the point in making a Samba clone of that ball of wax.

---

### Post by nightmare0 on 2010-11-05
> **HermanAB said:**
> Howdy,
 
I have come to the conclusion that it is not worth the hassle really. 
 ... 
Because virtualization is such an effective cure for the MS Blues, I don't see the point in making a Samba clone of that ball of wax.
 
I want to rid my network of MS completely if possible.. I have a physical Server2003 with MSExchange and such on there, but I would prefer to dump that junk (and its EULA's + other licensing..). I've been longing for a purely linux based Domain complete with mail server, policies, and nfs.. Maybe it'll only be just a nice dream. Is it possible though Herman?

---

### Post by jbrown96 on 2010-11-05
There isn't anything competitive with AD on Linux. Samba4 is nowhere near ready for production use, and still wouldn't support nearly as much as AD does. Plus there's no decent user interface.

Really one of the most successful IDM tools for Linux environments is Centrify, which uses AD as the backend.

---

### Post by s1nch4n on 2010-11-05
> **nightmare0 said:**
> I was under the impression that Samba only handled file shares(?) perhaps not? How would you use Samba for a GPO-esque effect? I essentially want to be able to take this domain and still be able to change network-wide configuration settings and such.. How can I do this with Samba? (I was thinking more along the lines of LDAP too..) 
 
(btw I'm thinking out-loud here, I may be wrong, correct me if I am) :)

> **nightmare0 said:**
> Searching around has left me even more puzzled. I'm not certain that Samba can provide what I need, I'm talking a Ubuntu-GPO-thing, something like System Policies (I think they're called..) so a distribution and implementation system..? And for exchange, either a Ubuntu Outlook app or a Linux Exchange server alternative..(with client of course ;) )here's screenshot from samba 4 with windows as a client...
 
[IMG]http://i56.tinypic.com/2u60k2g.jpg[/IMG]
[IMG]http://i51.tinypic.com/25rikcj.jpg[/IMG]
[IMG]http://i56.tinypic.com/akyauv.jpg[/IMG]

GPO? i already try with samba 4... and it's works with windows client...

and don't expect GPO will work on linux... :)

---

### Post by HermanAB on 2010-11-05
Howdy,

I can feel your pain with Windows ADS - it works fine until one day when it screws up and then it is a bloody nightmare.  However, Samba is not without issues either.

So I use the virtualization route win Win2003 and turn automatic updates and the like off, in order to keep the thing static and before I make any change to it, I first shut it down and make a tar ball of the VM.  Win2003 is the greatest nightmare ever foisted upon ITkind, but it is OK once put in a VM straight jacket.

If however, if you can forego the Windoze registry management crap of ADS, then you would probably be better off with NIS+ on the server and Windows Services for UNIX on each client machine.

There is also a pre-configured LDAP Virtual Machine with great wizards available for free from Mandriva.
[http://www2.mandriva.com/linux/server/directory/](http://www2.mandriva.com/linux/server/directory/)

Oh, and if you want a no hassle mail server system that can handle terabytes of mail, use Citadel.  The Easy Install script takes about 20 minutes, or you can download a pre-installed VM from my web site in a few hours.  There are also various Citadel howtos on my site.

---

### Post by nightmare0 on 2010-11-05
@Herman: NIS+ is a distribution system is it not? So then I'd distribute whatever conf files I edit to essentially create a policy?

I think that what I am looking for is kind of what Centrify provides, Policies for Ubuntu (I could care less about having policies for a windows client as they're getting junked.) Is it possible then to distribute System Policies to multiple computers via NIS+?

I'll take a look at that mail server..storage is no object ;)

Edit: I'll be using Citadel, thanks for that one! One problem down!

---

### Post by alienprdkt on 2010-11-05
Since no one is giving you any real guidance, figure I will give it a shot. Though I have not done this yet either but am in the process of learning and building the same.

Heres what I am doing in ubuntu:

Ldap 

[https://help.ubuntu.com/community/OpenLDAPServer]("https://help.ubuntu.com/community/OpenLDAPServer")

[http://www.debuntu.org/ldap-server-and-linux-ldap-clients]("http://www.debuntu.org/ldap-server-and-linux-ldap-clients")

and an ebook [http://digitalfreaks.org/~lavalamp/OReilly_-_LDAP_System_Administration.pdf]("http://digitalfreaks.org/~lavalamp/OReilly_-_LDAP_System_Administration.pdf")

mail

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04")

Calendars

[http://www.spicebird.com/category/image-galleries/spicebird-screenshots/spicebird-08-screenshots]("http://www.spicebird.com/category/image-galleries/spicebird-screenshots/spicebird-08-screenshots")

GPO's your closest bet prolly not what your looking for though...

[http://en.wikipedia.org/wiki/Network_Information_Service]("http://en.wikipedia.org/wiki/Network_Information_Service")

[https://help.ubuntu.com/community/SettingUpNISHowTo]("https://help.ubuntu.com/community/SettingUpNISHowTo")

note -  You can configure Samba to act as a primary domain controller. The functionality you get from that is centralized logins, logon scripts, logoff scripts.

but the best I have found would be this [http://www.centrify.com/directcontrol/grouppolicy.asp]("http://www.centrify.com/directcontrol/grouppolicy.asp")

I would Map directories to NFS and use NIS or OpenLDAP for authentication purpose. NFS act as a file server and user can login to any workstation using centalized OpenLDAP / NIS user account. When user logs in his / her home dir mapped from NFS file server. And you can use puppet along with NFS+NIS combo. It is a system for automating system administration tasks. It only works with UNIX / Linux and no need to use AD server. 

[http://docs.puppetlabs.com/guides/introduction.html]("http://docs.puppetlabs.com/guides/introduction.html")
 
or if you are just looking for User Management check out [https://help.ubuntu.com/8.04/serverguide/C/user-management.html]("https://help.ubuntu.com/8.04/serverguide/C/user-management.html")

As you can see it is alot of work to get rid of Windows, but I am in the process of doing it as well.

Glad if I could be of any help...

---

### Post by nightmare0 on 2010-11-05
> **alienprdkt said:**
> ]

As you can see it is alot of work to get rid of Windows, but I am in the process of doing it as well.

Glad if I could be of any help...

Thank you so very much alienprdkt! Seems like you and I are on the same wavelength.. Now I have somewhere to actually begin. I'll let you know if I come up with anything else pertaining to what was said here..honestly, thanks a bunch.

---

