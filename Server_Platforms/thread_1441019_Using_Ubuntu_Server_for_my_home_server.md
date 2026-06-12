---
title: "Using Ubuntu Server for my home server?"
date: 2010-03-28
forum: Server Platforms
---

### Post by MarkProvanP on 2010-03-28
Currently I use FreeNAS, which is a FreeBSD-based NAS distribution for my home server. However, I would like to move to a Linux-based home server with the ability for new software packages to be installed, which is a problem with FreeNAS. I use Lucid beta on my Dell Mini 10v, and have two Windows 7 and one Windows XP desktop(s), with all of them connected via Gigabit ethernet and Wifi N.

The home server would act as a file server (SMB and whatever the best one is for my Ubuntu netbook), a media server (UPnP, MT-DAAPD/iTunes and DLNA for my PS3), as a webserver and as a VirtualBox server just to experiment with. The server itself has a 160GB PATA drive which will be for the OS, and a 1TB SATA drive to be for the data; Gigabit ethernet; an AMD Athlon 64 2.2GHz (with AMD-V) and 1GB RAM

Are there any things you would recommend for me to install? I think that having a window manager would be nice, even if just for initial setup since I am not very experienced with command-line Linux. I'm planning on installing Webmin and a VNC/SSH server so I can configure it remotely. I don't need any firewall or VPN services as these will be provided by a pfSense box separate from this.

---

### Post by noway2 on 2010-03-28
Well, this is the Ubuntu forums, so don't be surprised to get the response of: try Ubuntu.  Both the desktop and server editions will do what your looking for.  If you want a GUI, go with the desktop edition.  It sounds like you will also want Samba for file sharing.  It is easy to set up a basic configuration but can also support some really advanced setups.  Many, including myself, will suggest you stay away from VNC and if you must use it, couple it with SSH, but make sure it is secure.  VNC is one of the most frequently used methods to compromise a system.  Alternatives exist such as just using SSH and FreeNX.

---

### Post by jfmanamtr on 2010-03-28
I would suggest using Ubuntu Server. I have been running Ubuntu Server on my server since I got tired of Windows Home Server & am very happy with the Server Version of Ubuntu. 
 
I would suggest staying away from using a GUI on a server. GUIs tend to eat CPU cycles. I wasn't very proficient with the CLI when I first started. But after doing research (read as googling it) or looking\asking on these forums, I have a pretty decent setup using CLI.  If you need a GUI-like interface, Webmin is great. I have it on there for setting up the LVM for my storage drive because LVM on command line kinda hurt my head. Between Webmin & SSH, there isn't anything you can't do on Server Edition. 
 
~John

---

### Post by MarkProvanP on 2010-03-28
Well, what I was thinking was that I could have a cut-down version of GNOME (no OpenOffice, games, etc) and only run it for the time that I need it, so it runs without it for the majority of the time.

---

### Post by dudumomo on 2010-03-28
Indeed, without GUI is the best.
But have an interface is quite convenient too, so you can indeed install a light version of gnome (gnome-core)
Or any other lighter interface (XFCE, E17, fluxbox, etc...)

What you can do, install the server edition, then install gnome-core
And at everytime you need the interface, start it with the command startx. When you're done to use GUI, simply kill the interface.

---

### Post by stickerpoint on 2010-03-28
try ebox:

[http://www.ebox-platform.com/](http://www.ebox-platform.com/)

---

### Post by drdos2006 on 2010-03-28
I tried ebox ( based on Ubuntu 8.04 ) and Ubuntu Server 9.10 with web based interface using Webmin. I much prefer Ubuntu 9.10 server and Webmin.
Here is a HOW-TO. Very thorough.

Latest versions are available at homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

regards

---

### Post by kevinthecomputerguy on 2010-03-30
Listen to drdos2006, he is wise.
:- )
-Kevin Elwood

---

### Post by slakkie on 2010-03-30
i lolled

---

### Post by UncleAelfrich on 2010-03-31
I use ubuntu server 9.10 then I installed xubuntu interface. Be sure to install SSH, unless you are going to devote the money into a keyboard, monitor, desk, chair, etc.

Ubuntu can do everything you want, and more. The only limitation I have found is my lack of desire to learn more linux than I already have. I believe life is too short to spend it going line by line through /var/log files.

Have you thought about:
backup?
file permissions?
users?

Backups and file permissions are the most annoying quirks. So long as you only have one user on your network and your hard disk never fails, it should be easy.

Have fun. The ladies really find a man sexy when he tells them how he built his linux server!

---

### Post by kevinthecomputerguy on 2010-04-08
Hey guys-

I posted a new version.   3.69
[[COLOR=#444444]http://woodel.com[/COLOR]]("http://woodel.com")  

-From a connecting client view, Ubuntu's Nautilus windows has like 10 ways of connecting to SAMBA shares, all with different results, so i pasted in a few screen shots in the how-to of how you can connect to them the best. it covers Windows, Ubuntu, and MAC clients. 

-The routing part of the how-to forgot to mention you need a static ip for a few of the configuration steps. (fixed)

Thanks again for all the kind words
-Kevin Elwood

---

### Post by kevinthecomputerguy on 2010-05-03
Hey guys-
I uploaded a new version that includes Samba groups (version 3.76)
[http://woodel.com]("http://woodel.com/")

---

