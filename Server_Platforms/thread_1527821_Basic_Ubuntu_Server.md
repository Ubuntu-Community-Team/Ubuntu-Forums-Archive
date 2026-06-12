---
title: "Basic Ubuntu Server?"
date: 2010-07-09
forum: Server Platforms
---

### Post by Robotuner on 2010-07-09
Hi:

I need to Install MySql Server somewhere that I can access.  Instead on installing it in a Windows box like I have for years, I'm thinking of putting it on a Ubuntu Server box (or virtual machine) instead.  Should I do it on a Ubuntu Server or a Ubunto desktop box?  I have never installed Ubuntu as a server, is it more or less the same as installing the desktop version?  Lastly, is there multiple versions of Ubuntu where one might be more appropriate than another?  

All I want is a machine that I can access MySql via an IP address.  Don't need DHCP, dns, Mail server or anything else.

Thanks

---

### Post by samjbobb on 2010-07-09
Ubuntu Server doesn't have a GUI, you configure it only with the command line. Ubuntu Desktop has a GUI, you can still install all the server software (like mysql) that you might want on the desktop version.

You save resources using the server edition by not running the desktop environment. So if you're comfortable administering entirely from the command line, go with the server edition. If you have memory and cpu to spare and think you might want a GUI for somethings, go with the desktop. 

The installations are very similar. If you've done one you can do the other.

You can also change a ubuntu installation from desktop to server after install by installing and removing the correct packages. I don't remember exactly what they are, maybe: ubuntu-desktop and ubuntu-server ?

Hope that helps. And I'd suggest going for it, having a little ubuntu server around is a really handy thing.

---

### Post by bodhi.zazen on 2010-07-09
> **Robotuner said:**
> Hi:

I need to Install MySql Server somewhere that I can access.  Instead on installing it in a Windows box like I have for years, I'm thinking of putting it on a Ubuntu Server box (or virtual machine) instead.  Should I do it on a Ubuntu Server or a Ubunto desktop box?  I have never installed Ubuntu as a server, is it more or less the same as installing the desktop version?  Lastly, is there multiple versions of Ubuntu where one might be more appropriate than another?  

All I want is a machine that I can access MySql via an IP address.  Don't need DHCP, dns, Mail server or anything else.

Thanks

The Desktop edition adds very little as the majority of server administration is either editing text files or running commands in a terminal.

If you want a graphical interface, take a look at webmin or phpmyadmin.

---

### Post by Robotuner on 2010-07-10
Thanks for your quick replies.  I'll go with the desktop.  I haven't used a command line interface for years, so the server might be a mistake.

BTW, I have mysql on my network server and machine for testing, but eventually I'm going to want it on a fast pipe for access via the internet, probably from a web service.  As I see it my options are:
1.  expose one of my machines on the outside of the firewall for direct access to the internet.  The problem is that I have a dsl so the upload and download speeds are limited.
2.  go with a mysql hosting service.
3.  put it on the cloud, where I could throw up my own virtual machine with Ubuntu hosting mysql.

It seems to me that option 2 is the cheaper (~$5/month) than option 3, but option 3 gives me root access so I can replicate the DB somewhere, say my outward facing machine, . . . just a thought.  I would throw a Ubuntu machine on the cloud and another ubuntu machine as my outwade facing machine and let them provide the replication service.

---

### Post by abaden on 2010-07-10
As far as your home server goes, bodhi.zazen said it perfectly - go with the server edition and phpmyadmin. You really don't need to do too much securing if the machine is internal, and all mysql packages can be installed via aptitude (as can phpmyadmin). 

If you want to make this public, I'd go with a shared host. That way you don't have to worry about your ISP, your home boxes getting hacked, or keeping things online. I don't know much about Amazon EC2, but I'd look at that as a possibility if you want to stick with Ubuntu.


Alex

---

