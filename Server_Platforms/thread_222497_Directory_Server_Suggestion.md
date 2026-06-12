---
title: "Directory Server Suggestion"
date: 2006-07-25
forum: Server Platforms
---

### Post by Socratez on 2006-07-25
Thought I would start a thread to get some suggestions from you guys. The community seems to be my best resource so here goes. I am trying to get the most out of my environment and simplfiy life on my network. I have been looking at running some sort of directory server to acomplish this. I am looking at opensource / free software. Redhat Directory server, Open LDAP, or any others if you have suggestions. I am looking for a good management suite to maintain things either command line or webGUI. There will be aprox 2000 entries maximum.

Anyways I'm gonna let you guys help me make my decision so don't be shy. 

Thanks ....


Soc

---

### Post by jnegro1176 on 2006-07-27
We have found a few ways to accomplish this.  There is a howto posted related to LTSP on Ubuntu which basically gives the steps for building an LDAP/SMB server on top of ubuntu with administrative tools.  We've tried it and it tends to be a bit tedious.

[http://wiki.ltsp.org/twiki/bin/view/Ltsp/LDAP](http://wiki.ltsp.org/twiki/bin/view/Ltsp/LDAP)

Alternatively, someone has made scripts to automate this process, although still somewhat buggy being that only the bleeding edge SVN version works with ubuntu:

[www.majen.net/smbldap](www.majen.net/smbldap)

We have been working on our own script for both client and server that is a bit cleaner than those offered above, but they are not complete yet.

Recently we stumbled upon the best option we've seen yet.  It is offered as an ISO for a full install on a single machine, or instructions to add it to an existing OS.

[www.ebox-platform.com](www.ebox-platform.com)

It appears to be similar to SME server, but a bit more flexible.  I honestly don't know what the current status of the project is, or whether its just suffering from lack of interest.  I hope it catches on and hopefully becomes a stable part of Ubuntu server.  It would be the answer to authentication services for ubuntu.  As for the client config, I will post the script we are working on when it is finished.  It configures an ubuntu or kubuntu client automatically.

Hope this help!

---

### Post by kabronkline on 2006-07-27
The EBOX solution seems perfect for this major Ubuntu Server dilema. Not only does it provide a wonderful web-gui for administration, all the functionality of a typically directory server are included. Further, EBOX apparently uses Debian, and thus I am assuming that if the software available on EBOX wouldn't be difficult to migrate to Ubuntu. Since EBOX is GPL, could it be possible to build a package that could be installed via APT?

I'm going to download this and give it a shot, see if I like. I want something besides Windows Server + AD.... I'm sick of M$ junk and I don't want to admin it anymore, to many headaches.

Here is the development site for EBOX:
[https://projects.warp.es/projects/ebox-platform/]("https://projects.warp.es/projects/ebox-platform/")

---

### Post by Socratez on 2006-07-27
Thanks this seems to be a great little tool for directory serving .... I will try to get this running under Ubuntu myself but chances are I'll fail horribly ... Either way it is not a huge task I am going to be managing anyway ... just want to make sure I have home office configured properly for ease of admin while on the road.

---

### Post by kabronkline on 2006-07-28
> **Socratez said:**
> Thanks this seems to be a great little tool for directory serving .... I will try to get this running under Ubuntu myself but chances are I'll fail horribly ... Either way it is not a huge task I am going to be managing anyway ... just want to make sure I have home office configured properly for ease of admin while on the road.

Definitely keep this thread updated with your findings.

---

### Post by screeb on 2006-07-30
Socratez: I don't know ebox, but it seems very intersting. If you try it, could you give your impression. Some users are now trying to get a good solution to manage an ubuntu server ( [http://www.ubuntuforums.org/showthread.php?t=191858]("http://www.ubuntuforums.org/showthread.php?t=191858")) and your experience could help us.
Even if I don't now ebox, I know quite well OpenLDAP, an maybe I can help you :)

---

### Post by Jabran Asghar on 2006-08-04
Hi,

I installed eBox on fresh Dapper server, but could not get it working. I Used Installation Guide at the ebox website. While installing packages, it kept asking for some password again and again (ofcourse I was already installing it through sudo). No password worked even I tried root password, which I enabled before starting), and I ended having a messed up system, which will not let me do anything correctly, On each reboot, there was same password question for starting apache, bind, and perhaps every other service that ebox installed. I did it on a VMWare based Ubuntu installation so was lucky to drop the machine and to use the fresh copy of the Ubuntu installation (which I made before starting installation of ebox) for another experiment.

Has anyone else installed eBox on ubuntu successfully? The eBox interface seems really good, and user friendly, and I really want to have it running.

Any feedback?

Jabran

---

### Post by Tortanick on 2006-08-04
ebox won't work as a directory server, it uses LDAP but only internally, its strictly a open source server for Microsft clients. Unless you hack it that is but it dosn't look like any hacks will survive an update.

You could try useing GOsa from the universe and openLDAP, no idea how, if you figure it out please post a guide.

---

### Post by Nachico on 2006-08-10
> **jnegro1176 said:**
> Recently we stumbled upon the best option we've seen yet.  It is offered as an ISO for a full install on a single machine, or instructions to add it to an existing OS.

[www.ebox-platform.com](www.ebox-platform.com)

It appears to be similar to SME server, but a bit more flexible.  I honestly don't know what the current status of the project is, or whether its just suffering from lack of interest.  I hope it catches on and hopefully becomes a stable part of Ubuntu server.  It would be the answer to authentication services for ubuntu.  As for the client config, I will post the script we are working on when it is finished.  It configures an ubuntu or kubuntu client automatically.

Hope this help!

Wow! Thanks for the positive feedback. It is very encouraging to hear this kind of impressions :)

We have never lost interest in our project but we have had a period of low-activity while searching for fundings to help us continue with the development. Recently we received the funding we needed and in the following weeks we will start a high-activity period. Stay tuned!

By the way, eBox was working under Ubuntu breezy but we do not have enough resources to keep eBox compatible with two different distributions, specially taking into account Ubuntu's release pace. Any help will be welcome!

---

### Post by fnjordy on 2006-08-10
An alternative :KS  [miru directory server](http://developer.novell.com/wiki/index.php/%E3%81%BF%E3%82%8B_directory_server), its basically FreeBSD + Samba 4 Active Directory.  About 12MB download for an entire setup.

---

