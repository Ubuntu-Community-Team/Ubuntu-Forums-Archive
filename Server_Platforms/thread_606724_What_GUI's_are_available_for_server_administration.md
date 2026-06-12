---
title: "What GUI's are available for server administration?"
date: 2007-11-08
forum: Server Platforms
---

### Post by simonduz on 2007-11-08
Hello all.  Brand new Linux user here.  I am setting up a PDC for my small home network.  I was going to use Windows but decided to take the plunge and try Linux.    My specific criteria for this server are:
[LIST]
[*]Logical Volume Management + GUI
[*]SAMBA as a PDC + GUI
[*]Print server  + GUI
[*]Groupware + GUI
[*]Media Streaming
[/LIST]

After reviewing much of the server docs available here at Ubuntu I have come to realize that they all list commands to setup and edit these services.   My question is, does Ubuntu offer **ANY GUI options **for server management, specifically for the server services I have listed above.  I don't feel quite that comfortable in setting up a Linux server as a first time user without the GUI option.
Thanks....

---

### Post by stalker145 on 2007-11-08
> **simonduz said:**
> Hello all.  Brand new Linux user here.  I am setting up a PDC for my small home network.  I was going to use Windows but decided to take the plunge and try Linux.    My specific criteria for this server are:
[LIST]
[*]Logical Volume Management + GUI
[*]SAMBA as a PDC + GUI
[*]Print server  + GUI
[*]Groupware + GUI
[*]Media Streaming
[/LIST]

After reviewing much of the server docs available here at Ubuntu I have come to realize that they all list commands to setup and edit these services.   My question is, does Ubuntu offer **ANY GUI options **for server management, specifically for the server services I have listed above.  I don't feel quite that comfortable in setting up a Linux server as a first time user without the GUI option.
Thanks....

You have a couple of choices here. First, you can actually set up a full-fledged GUI OS and add the desired server packages. This will give you, I believe, most of the control you are looking for.

Another option is to look into something like [WebMin]("http://www.webmin.com") for remotely controlling your server. I know that there are control interfaces for LVM, SAMBA, and printing, but I do not know about groupware and I'm pretty sure it has nothing in the way of media streaming. I use WebMin because it is easy to set up and you get a simple web browser interface that can be accessed from anywhere in the world. WebMin also allows you full control over your computer (package management, running processes, file management, etc).

For media *streaming* I use GNUMP3D. That is an install, a relatively simple config file change, and you now have a magical web browser interface to all your media (audio and video).

---

### Post by timcredible on 2007-11-08
stalker145 said it best - there's guis for most apps, and if not, webmin.

---

### Post by HermanAB on 2007-11-08
In general, if you want to use GUI wizards to configure your system, then Ubuntu is the wrong solution.  You would be better off moving to Mandriva Linux.  Even the Redhat wizards (which are quite dreadful) are better than Ubuntu wizards.

If you want to stick it out with Ubuntu, then Webmin is pretty much your only option, but it takes a long time to configure it properly so that it works right.

Web browser interface:
Webmin
Virtualmin

3rd Party web browser interface:
Plesk
Cpanel

Mandriva Linux SSH X interface:
MCC, the famous drake wizards

RedHat Linux SSH X interface:
system-config wizards

Cheers,

H.

---

### Post by simonduz on 2007-11-08
Thanks to all for your honest replys!
I have also looked at:
linuxgfx.co.uk/karoshi/mambo/dev/  **Karoshi** and
clarkconnect.com/  **ClarkConnect**

I have been told by others this may be overkill for what I need.  Opinions?

---

### Post by AgentZ86 on 2007-11-11
> **simonduz said:**
> Thanks to all for your honest replys!
I have also looked at:
linuxgfx.co.uk/karoshi/mambo/dev/  **Karoshi** and
clarkconnect.com/  **ClarkConnect**

I have been told by others this may be overkill for what I need.  Opinions?

I'm considering Ubuntu server with webmin for my website etc. and hostings for a few people.

I'm currently using SME Linux server  from [www.smeserver.org](www.smeserver.org)

And SME works well has it's own remote admin interface, webmail and IMAP mail via Horde. Can host virtual domains etc. and Horde is a fulll Groupware/email/address/task/calendar/ etc.

Works pretty nice out of the box.

I'm not sure exactly why I'm considering Ubuntu server I guess cause I'm using Ubuntu desktop and it works so well with everything I'm doing. But I don't know enough about the Ubuntu server or if it's going to be a big hassle.

I basically just want my own email server, and also want to host a few sites for my freinds, and also listing my images for ebay stuff.

So I'm considering installing a Ubunu server on a differerent machine to play with until I get familiar. 

Does anyone know what Ubuntu server has out of the box. any email server stuff, or webmail. Or ability to host webpages  with little configuration or is this something I really need to know more about linux command line konsole use etc. ???

Please advise
Thanks

---

