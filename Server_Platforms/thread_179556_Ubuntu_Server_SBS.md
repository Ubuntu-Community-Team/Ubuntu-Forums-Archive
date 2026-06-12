---
title: "Ubuntu Server SBS"
date: 2006-05-20
forum: Server Platforms
---

### Post by Khaine on 2006-05-20
I want to setup a Ubuntu server to do the following things:

Access to/from the outside/internet
      Firewall
      VPN/IPSec
      Web Proxy and content filter

Authentication
      Central user and group management (for Unix clients and Win clients)
      LDAP/Kerberos

File Storage
      "Roaming profiles", central home directories
      Storage for Unix based clients (NFS, AFS)
      Storage for Win clients (SMB)
      WebDAV

Groupware
      Mail sending/receiving
      Spam/Virus detection and filtering
      Mail storage
      Shared Calendar
      Shared Address books

All of these tasks are listed in the wiki here
[https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/SmallBusinessServer?highlight=%28SmallBusinessServer%29](https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/SmallBusinessServer?highlight=%28SmallBusinessServer%29)
as a work in progress to make an Ubuntu Small Business Server, Now I know that I can setup most of this stuff already; but some of it, is very difficult to integrate.  

I was wondering if anybody new of the progress of the Ubuntu-SBS (as if its nearly ready I may as well wait) or whether an open-xchange package will be made soon, or of any really good guides for setting up stuff

Thanks

---

### Post by RocketMan66 on 2006-05-21
I just stumbled onto this thread . . .

I was thinking of installed ubuntu as a server and then implement it as a SOHO server using many of the packages listed above.

**So therefore I am very interested in the UbuntiuSBS.**

I am currently using ClarkConnect which does the job but is not well documented.

Rocket

---

### Post by nkr1ptd on 2006-05-23
I also would like to see the SBS progress.  I have found this [http://hannibal.solstice.nl/](http://hannibal.solstice.nl/) which is a good start.  However, it is not an easy to admin system.  We have to realize that the folks managing the SBS server many times dont really understand the underlining technology but need to do basic maintenance like add/remove users, backups, clean mail queue, setup file and print shares, etc.  I did find this pretty cool tool for easy administration, but have not gotten it to fully work. [https://gosa.gonicus.de/](https://gosa.gonicus.de/)

I like the idea of Hannibal in the fact that while it is setup like an SBS server, it can scale.  You can pull off individual pieces parts and put them on their own server.  Personally for email I have used eGroupWare.org quite a bit just because it is easy to setup and configure and the administration is easy to do for just about anyone.  It also integrates well with cyrus to create users and such. I have never had luck with the contact management using LDAP.  For those that have to use clients it seems like the contact stuff just never maps correctly.  I have also not had the cycles to put to getting it working like I need.

Hopefully this helps someone get the SBS project jump started.

BTW I base my email servers on this document: [http://www200.pair.com/mecham/spam/](http://www200.pair.com/mecham/spam/)

Although I am interested in potentially utilizing DSPAM instead.

-Brandon

---

### Post by Koybe on 2006-05-24
I don't have much to say at the moment. But i marked this post.
I tried to do something like this on debian... but the key is to make the whole working together.

The main question at the moments remains on the groupware to use. I tested several ones but I wasn't conviced by any of them. Zimbra looks great but it's only found as a binary and install itself... Open-Xchange looks great but as still some bugs in my mind. So i came and wonder about using a simplier php-based groupware. It could be ok. But most of the clients are using windows and need an outlook connector... So the key : good web-based groupware + good outlook connector.

I did not worked with Kerberos and set no firewall/vpn/proxy solution, but i would be interested. I'll try to help on this one :)

Good idea ;)

---

