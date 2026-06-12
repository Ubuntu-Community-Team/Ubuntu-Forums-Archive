---
title: "Suggestions for an Ubuntu Server to be Built from Scratch"
date: 2009-06-21
forum: Server Platforms
---

### Post by stefanadelbert on 2009-06-21
[Duplicate of post in General Help]

I need to build and configure a server that should fill the following roles:

[LIST=1]
[*]Fileserver on Windows network (Samba, 2 x 1TB HDD's in RAID Array)
[*]SVN server (http and file based)
[*]Mail server (open to suggestions here)
[*]Host to custom-built (probably Python) socket listener app
[*]Host a wiki
[/LIST]
I would definitely like to run Ubuntu on the box, but I'm looking for a few starting point suggestions and recommendations on some of the following questions and I'm sure many more that I haven't thought of yet:

[LIST]
[*] Should I just be installing the server edition or full-on desktop edition? Pros and cons?
[*] 32- or 64bit? Probably 64bit in case I decide to up the RAM beyond 3.2GB, which is likely.
[*] How best to configure Samba if security is a fairly big consideration? Multiple unix user accounts with home dirs, etc.; just Samba specific users and particular permissions on shares?
[*] Which mail server to use? Is there one that works especially well with MSOffice?
[*] Which wiki to use?
[*] Any particular hardware considerations to pay attention to (just thinking Intel Core 2 Duo, 2GB RAM, 100mbps Ethernet, onboard graphics, 2 x 1TB HDD's)?[/LIST]
I suppose I'm going to be the sysadmin (for the first time), so if anyone has any good tips for a newbie Ubuntu SA, I would really like to hear them.

These are the resources that I've found so far:
[LIST]
[*][Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html")
[*][SVN setup]("https://help.ubuntu.com/community/Subversion")
[*][Samba configuration]("https://help.ubuntu.com/community/SettingUpSamba")
[*][MediaWiki installation and setup]("https://help.ubuntu.com/8.04/serverg...mediawiki.html")
[*][MediaWiki homepage]("http://www.mediawiki.org/wiki/MediaWiki")
[*][Mail server setup]("https://help.ubuntu.com/community/MailServer")
[/LIST]
Thanks in advance for the advice.

Stef

---

