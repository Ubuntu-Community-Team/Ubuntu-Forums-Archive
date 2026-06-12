---
title: "Beginner Questions"
date: 2008-05-24
forum: Server Platforms
---

### Post by TJCIB on 2008-05-24
I am part of a small international school in Brazil.  We don't really have the budget for a lot of things, like web hosting.  I said I would look into it.

If someone could please point me in the right direction.  Here is what we would like to do, nothing big:

Host our own website
Have our own email system
File sharing within our 15 computer network

We can get a static IP from our ISP.

I'm a total noob at this, I appreciate any help.

---

### Post by freebeer on 2008-05-25
Don't worry about being a noob.  We like noobs here. :D

All of what you listed is certainly pssible with Ubuntu.  If you're completely new to Linux, and are more comfortable with graphical interfaces, you'll want a version that has one installed.  You can get the server version, then install a graphical desktop, or you can get the standard version, and install the other apps that you require.  Either way is good and will get you to where you want to go, I think.

Once you've installed it, post back with any questions.

oh... while a static IP can be helpful, you can host a website with a dynamic IP.  I use dyndns.org's free service for this and it works well.

---

### Post by hyper_ch on 2008-05-25
TJCIB have a look at:

[http://www.howtoforge.com/perfect_setup_debian_etch](http://www.howtoforge.com/perfect_setup_debian_etch)  --> and afterwards installing ISPConfig

or

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) --> if you want to use Ubuntu (I prefer debian as server)

The static IP is required as you want to also operate an email server.

And filesharing should be rather simple... what OS are the other boxes running?

---

### Post by cviniciusm on 2008-05-25
Hello,

I'm just concluding a server using Ubuntu Server 8.04 LTS.

It's has:
- DHCP Server;
- DNS Server;
- SMTP, POP3 and IMAP Server (Postfix + Dovecot);
- Web Server (Apache2);
- Webmail (Squirrelmail);
- Collaboration (eGroupWare);
- LDAP Server;
- MySQL Server;
- PostgreSQL Server.

All this was possible using the 8.04 LTS Server Guide and the Ubuntu Help, at least.


Cheers,
cviniciusm.

---

### Post by TJCIB on 2008-05-25
That information was exactly what I needed to get started.  Thanks for all your help!

We are already running Ubuntu on all our computers, but not Thin Client or anything.  I am familiar with file sharing and such using NIS and NFS, thats what we're using now.

Thanks for the great responses.

---

### Post by CptSnork on 2009-05-07
Absolute NOOB here! 

I have another question: Is there a way to have egroupware display 2 languages within the email portion of it?

The specific PROBLEM is when receiving a German email and the sender has a special character it doesn't display the name of the sender at all. Since the parent company is in Germany, this poses a rather annoying problem! And you also see a bunch of a blue diamonds with a ? inside of it sprinkled liberally within the email (place holders for special characters). 

I've tried the global categories with both languages... and it's the same problem :'( 

Also I can't save the email notification feature, it always resets although I apply or save or both :''''(

Does anyone have an idea on how to tackle all this?  Oh, and we're running ver 1.6.001

Thanks for your time!

---

### Post by CptSnork on 2009-05-07
OOPS, this should be in "eGroupware anyone?" This was a mistake... just to show you the day I've been having :'''''''(

I would still like some pointers since I can't post in the eGroupware thread... says I'm blocked!

---

