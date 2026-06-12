---
title: "Home Server HowTo"
date: 2008-04-30
forum: Server Platforms
---

### Post by mbt12 on 2008-04-30
Hi, I am pretty new to this but I am going to try to make a home server.  I don't know if this is possible, but I want to be able to store music, movies etc. on it and be able to use them on my normal computer.  Is this possible and how hard would it be?

---

### Post by Dr Small on 2008-04-30
It would not be that difficult.
First you will need a dedicated box that will be the server. Once you have that, you can install Ubuntu Server Edition or Ubuntu CLI Edition (basically a CLI install) and then install things as you need to from there.

For a Filestorage, here are the basics you will need:

OpenSSH-Server -- This will be what you use to administer the box. You must know the command line.

Apache -- This will host your files and make them accessible via a browser over your network. You can install Apache from the repositories, or my personal choice of Xampp.

FTP -- Although insecure, if you simply plan to use it on your network and not have it accessible from the outside, you should be fine. ProFTPd works great in my opinion.

Of course, others will also tell you that you could simply install a desktop and make it into a server, but that is the long way around things, yet easier if you are not familiar with the command line.

Good Luck,
If you have any more questions, feel free to ask.

Dr Small

---

### Post by _sAm_ on 2008-05-01
mbt12: whats OS is on your "normal pc". Do gonna use the share from the server on only your LAN, or also via Interntt?

---

### Post by Jeztastic on 2008-05-01
I have set up a home server following this guide:

[Build Your Own Server 1]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1")

and 

[Build Your Own Server 2]("http://www.bit-tech.net/bits/2007/07/24/build_your_own_better_server/1")

I would read through it all before you start, as the second part of the tutorial has some things it would be easier to do first time round. For example, ignore the ftp install instructions and install Webmin instead.

Likewise, I would not recommend installing Xubuntu desktop edition - rather install the Ubuntu Server edition, then add the XFCE (Xubuntu) desktop after. There's instructions on how to do all that here: 

[psychocats]("http://www.psychocats.net/ubuntu/")

---

### Post by R.Bucky on 2008-05-01
I started my server on the 15th of April using minimal hardware. I am hosting my site on 2.3GHz AMD Athlon 4400+. It does just fine. However, I will admit that a dedicated server would be best (and in the works), hosting your webpages from a desktop would be perfectly adequate for a small load (~0-7 users at a time). RAM seems to be the limiting factor as well as type of content (e.g. pictures and resolution, streaming media, etc...).

---

### Post by njparton on 2008-05-01
Check out FreeNAS and Openfiler before deciding to go with a full blown distro.
 
I have a home made headless NAS based on ubuntu that's a sever for our 2 windows PCs. At the time freenas had bad samba performance and openfiler was difficult to setup. Both are more mature and a few versions on now.
 
Install ubuntu, configure the inbuilt VNC server, then install and configure samba and that will give you a basic setup that you can develop over time. I'd also consider installing openssh so you can putty into it to administer it without having to open up a remote desktop connection.
 
Good luck!

---

### Post by eldragon on 2008-05-01
i would setup ubuntu (regular).

install open-sshd to manage it from the desktop. and allow X forwarding (works quite well from the lan)

i would not install ftp, instead use scp (or psftp from the putty package) for wan transfers. 

setup samba for LAN file xfers.

and maybe install unison to sync files between server and desktop. allowing you to work either on the server or the desktop without the need to move files yourself.

on the server i would add an external usb drive for backups and setup rsnapshot to do the dirty work every night.

use dovecot to handle your mail and setup an imap server

thats what ive done. so far so good.

:)

---

### Post by njparton on 2008-05-01
rsync flies for synching or backing up.

---

### Post by mbt12 on 2008-05-01
I have vista on my everyday computer and currently have hardy running on my older one.  I do not need to access anything remotely

Also, thanks everyone for the suggestions

---

### Post by mbt12 on 2008-05-01
Also, I am pretty new to all this stuff and don't really know what a lot of those things even mean

---

### Post by neill on 2008-05-01
hi

it's all very doable from scratch on ubuntu, and webmin makes a lot of this stuff much easier

however ...

if it's your first time and you have the time to experiment you could try one of the 'out of the box' server distros you can find out there

go to distrowatch. com and check out clark connect and sme server. i've dabbled with both (although i now do it all myself with ubuntu server, SSH and webmin)and they have the advantage of (largely) working straight off and all the config stuff is there as a web interface

much easier for the novice 

good luck

/neill

---

### Post by njparton on 2008-05-02
I suggest you read through the online ubuntu _server_ guide before you start.  It gives good advice on how to configure the services you'll need.  The desktop guide has a slightly different focus.

---

