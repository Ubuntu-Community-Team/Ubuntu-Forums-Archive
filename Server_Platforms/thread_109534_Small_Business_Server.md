---
title: "Small Business Server"
date: 2005-12-28
forum: Server Platforms
---

### Post by kejar31 on 2005-12-28
would like to discuss the possibility of creating an easy to install script. A script that would, with a very limited number of questions, setup and install a true SBS server on Ubuntu. Recently I setup an Ubuntu server using Kolab and Samba backed up to the same ldap directory. It works but I see more promise in my current project that that includes Open-Xchange ( comes with a very nice  web interface for users ). I have taken a German script built for RHEL and scientific Linux ( I use scientific )
 [http://www.haufschild.de/groupware/install.html](http://www.haufschild.de/groupware/install.html). I started to modify it for my own needs such as removing software modifying samba and the such. What I end up with is a ready to go server in about 1.5 hours ( including the install of scientific - minimal install) with only the need to answer about 5~10 site specific questions. The server includes Open-Xchange, Samba as a PDC and both backed up to the same ldap directory.  Also included is its own dns server using Bind webmin ( with all need modules ready to go ) and  phpldapadmin. I am working on including a couple extras such as LAM and OXAdm. Oh yea of course the whole thing is in Engish now as well. Well what I am trying to get is that I and I am sure many others would like something very similar for Ubuntu (maybe even something easer). I'm sure it can be done. I'm willing to devote some time to it but i know i would need help as i dont have that much free time. If anyone is interested pm me or reply to this thread. I am also more then willing to share the script i have as well as all need rpms and the install procedures for scientific.

PS sorry for my bad grammar I wrote this in a hurry. 

Justin Rogers
Network Engineer

---

### Post by kejar31 on 2005-12-28
I'll go ahead and through the script out here for anyone interested.

PS: remember this was originally German so some wording my not be the best.


It does work though (on scientific) I have installed it multiple time for testing.


here ya go--------------------------------------------------

---

### Post by alfred on 2006-01-13
I am interested in this and will look over the zip file.
I will try and install the openexchange.
Kolab has been a tough install and I do not like or yet know how to keep it from replacing my Ubuntu installs of apache etc.
Anyways I will write more later.
Thanks
Al

---

### Post by JazzCrazed on 2006-01-27
Any word on this Alfred?

Looking forward to trying this myself.

---

### Post by kejar31 on 2006-02-06
Ok people this idea has come along way since my last talk. The project is now called AVA-SBS. It is an installer and admin tool for a samba PDC with Open-Xchange both using the same ldap server. As of now it is only for rpm based distros but that can change with a little effort and some help. I wish I could port it myself but I just don't have the time. 

As of now AVA-SBS includes everything you need to build the server

included and configured with only 10 questions
bind
samba / PDS with LDAP
Open-Xchange
Webmin
and AVA-ADM

AVA-ADM is my new web based admin tool for system administration. With it you can create review and modify your samba and open-xchange email accounts. AVA-ADM is still under heavy development.

In this post I am hoping to get some help porting the system to ubuntu. We would need some people with good bash scripting skills for the installer and I could always use some help with AVA-ADM which is PHP.

I have just recently picked up the domain AVASBS.com and submitted for a sourceforge project. I hope to get a wiki soon as well. 

As of right now AVA-SBS is a one man show ( ME ;) ) but other are starting to get involved. I have also started working with Peter H. the original writer of the script for LX-office and we have just begun to collaborate. 

in the next few posts I will post some screen-shoots of the installer and AVA-ADM

For those interested you can email me at justin dot a dot rogers at gmail dot com

here is the link for the current download 

[http://oxmirror.nethinks.com/mirror/AVA/](http://oxmirror.nethinks.com/mirror/AVA/)

---

### Post by kejar31 on 2006-02-06
You can also download the how-to for the installer.

[http://oxmirror.nethinks.com/mirror/AVA/AVA-INSTALL-HOWTO.pdf](http://oxmirror.nethinks.com/mirror/AVA/AVA-INSTALL-HOWTO.pdf)

Note: 
it is outdated now as some things have changed but for the most part it is correct.

Also even though I show the installer within gnome is not needed. The installer will work just as well from command line only with a minimal install.

---

### Post by kejar31 on 2006-02-06
here are some screenshots of AVA-ADM

---

### Post by insomni on 2006-02-07
I've been watching this thread for a while and I think this is way cool

Just started new job, so not much time to help out - would be great if this could be ported to a Ubuntu Server install, but maybe I got it wrong, but the installguide linked to above seems to require X?? Would be great if X was not needed

---

### Post by kejar31 on 2006-02-07
AVA-SBS just got approved for a sourceforge project

[http://sourceforge.net/projects/ava-sbs/](http://sourceforge.net/projects/ava-sbs/)

If any one wants to join in email me justin dot a dot rogers at gmail dot com

---

### Post by kejar31 on 2006-02-07
[QUOTE=insomni]I've been watching this thread for a while and I think this is way cool

Just started new job, so not much time to help out - would be great if this could be ported to a Ubuntu Server install, but maybe I got it wrong, but the installguide linked to above seems to require X?? Would be great if X was not needed[/QUOTE]

no X is not needed. 

I need to make another howto showing the install without X

believe it or not it is just as easy. :D 

again check out my last post I have a new sourceforge project started ;)

---

### Post by kejar31 on 2006-02-09
hey everyone I have an update to AVA-SBS

this is a bug fix and is not the whole download just the update. So you only need to download around 2 meg

get it at [http://sourceforge.net/projects/ava-sbs/](http://sourceforge.net/projects/ava-sbs/)

Also I will be keeping an eye on the forms at the sourceforge project page so you can post problems / success there if you like as well.

---

