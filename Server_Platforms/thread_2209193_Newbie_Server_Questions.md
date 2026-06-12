---
title: "Newbie Server Questions"
date: 2014-03-04
forum: Server Platforms
---

### Post by darksideforge on 2014-03-04
I've installed 12.04 Server on a previously-unused machine I had in storage. I installed LAMP, Mail, DNS, NFS, and SAMBA packages during the initial install.  The server is not currently connected to the internet (with no real plans for that to happen either). I did not install a/the GUI (desktop) during the install and do not plan to. Several years ago I became somewhat proficient working with CLI and I'd like to pick back up on that basic education now. The server is NOT headless, however; I have an old keyboard/monitor/mouse attached to the box and I'm not planning on SSH-ing into the server on the local network for a while yet. I *do*, however, wish to create a new home network (no internet connection) for file sharing and media (pictures, music, documents) storage...no RAID Array or anything fancy and no Cron jobs for creating .bak's either. In order to set manipulate my ancient Netopia Cayman 3346 router, I'd like to be able to use Webmin. I have downloaded the latest iteration of Webmin to my laptop (which *does* connect to the net via my cell phone), and now I've got several questions:

1) If I copy the webmin.deb file to a flash drive, what is the command to install webmin on my server?

2) Was x installed during the basic server installation from CD (v12.04) and if it wasn't, is it on the installation CD that came from the Ubuntu mirror <or> is there somewhere that I can download whatever I need to make webmin work on my server?

3) What else will I need to install to the basic server package in order to get webmin to work? I *do not* want to install xfce/desktop etc etc....is there a choice? 

4) Am I going to have to install Firefox as well or is there a native program that will run the webmin?

5) Assuming I have to download Firefox.deb (or whatever it's called), will it have its own dependencies included in that download or will they already be on the system? 

**Remember, the server isn't connected to the internet so anything that has to be downloaded will have to come to my netbook first and then transfer to the server via flash drive. The server has a DVD but the netbook does not**

***If I had an available wireless AP or if my router were wireless and not so ancient, I'd just disconnect from my cellular network and connect to the server network (which I'd have to manually set to DHCP) and xfer it over that way...which may end up happening in the near future anyway.***

Basically, I want enough "extra" to run Webmin so that I can configure my planned home network visually but that is ALL i want. I don't want a GUI with a bunch of extra nonsense. And yes, most of you purists are going to tell me to suck it up, buckle down, and get better in the terminal so that I don't NEED webmin. And you'd be right. And I promise I'll get there....but I'm not there yet. Ugh.

6) One last question, and this is pretty far O/T and a moderator may tell me to move this to another post, but I remember seeing an ubuntu wiki several years ago that gave good instructions for how to create your own repository and put it on a DVD that you could insert at-will and then execute a wget pointed at your -cdrom .... anybody got any idea on where that thing went? I think i was playing around with 9.04 when I read about that....that's the last version of Ubuntu I've messed with and I didn't mess with the server version of it much.

Thanks in advance....try not to laugh so hard you spill your coffee now that you've read all of this nonsense.  ~dsf

---

### Post by coldraven on 2014-03-04
I'm as clueles you but in this blog he says "while I control the torrents using its WebUI.".
How that works I don't know, just sharing :)

[http://blog.kagesenshi.org/2007/06/running-x-applications-headless-using.html](http://blog.kagesenshi.org/2007/06/running-x-applications-headless-using.html)

---

### Post by darksideforge on 2014-03-04
Thanks for the link, Coldraven. His situation is slightly different but it may have answered one of my questions for me. What he's saying is that he wants to run a web-based user interface to control a torrent program rather than using the torrent program itself (which is CLI-based)...and that's pretty much exactly what I want to do with Webmin: manipulate my network using a graphical interface rather than using $: ifconfig on the command line (CLI). In order for him to do that, he's saying you have to: yum install xorg-x11-server-Xvfb (where yum is the fedora version of apt). 

xvfb sounds like a neat process and I'll have to look into it more. I'm not sure there's any real reason for me to have it since (according to him, I think) I have to have xorg and x11 running anyway. I've never thought about the need to have a virtual frame buffer for X before, but if you wanted to run a program that normally required a GUI and you didn't have a GUI, it would be perfect. At least, it *sounds like* it would be perfect...

Thanks again.

---

### Post by darksideforge on 2014-03-04
*bump*

---

### Post by DJ_Max on 2014-03-06
> **darksideforge said:**
> I've installed 12.04 Server on a previously-unused machine I had in storage. I installed LAMP, Mail, DNS, NFS, and SAMBA packages during the initial install.  The server is not currently connected to the internet (with no real plans for that to happen either). I did not install a/the GUI (desktop) during the install and do not plan to. Several years ago I became somewhat proficient working with CLI and I'd like to pick back up on that basic education now. The server is NOT headless, however; I have an old keyboard/monitor/mouse attached to the box and I'm not planning on SSH-ing into the server on the local network for a while yet. I *do*, however, wish to create a new home network (no internet connection) for file sharing and media (pictures, music, documents) storage...no RAID Array or anything fancy and no Cron jobs for creating .bak's either. In order to set manipulate my ancient Netopia Cayman 3346 router, I'd like to be able to use Webmin. I have downloaded the latest iteration of Webmin to my laptop (which *does* connect to the net via my cell phone), and now I've got several questions:

1) If I copy the webmin.deb file to a flash drive, what is the command to install webmin on my server?

2) Was x installed during the basic server installation from CD (v12.04) and if it wasn't, is it on the installation CD that came from the Ubuntu mirror <or> is there somewhere that I can download whatever I need to make webmin work on my server?

3) What else will I need to install to the basic server package in order to get webmin to work? I *do not* want to install xfce/desktop etc etc....is there a choice? 

4) Am I going to have to install Firefox as well or is there a native program that will run the webmin?

5) Assuming I have to download Firefox.deb (or whatever it's called), will it have its own dependencies included in that download or will they already be on the system? 

**Remember, the server isn't connected to the internet so anything that has to be downloaded will have to come to my netbook first and then transfer to the server via flash drive. The server has a DVD but the netbook does not**

***If I had an available wireless AP or if my router were wireless and not so ancient, I'd just disconnect from my cellular network and connect to the server network (which I'd have to manually set to DHCP) and xfer it over that way...which may end up happening in the near future anyway.***

Basically, I want enough "extra" to run Webmin so that I can configure my planned home network visually but that is ALL i want. I don't want a GUI with a bunch of extra nonsense. And yes, most of you purists are going to tell me to suck it up, buckle down, and get better in the terminal so that I don't NEED webmin. And you'd be right. And I promise I'll get there....but I'm not there yet. Ugh.

6) One last question, and this is pretty far O/T and a moderator may tell me to move this to another post, but I remember seeing an ubuntu wiki several years ago that gave good instructions for how to create your own repository and put it on a DVD that you could insert at-will and then execute a wget pointed at your -cdrom .... anybody got any idea on where that thing went? I think i was playing around with 9.04 when I read about that....that's the last version of Ubuntu I've messed with and I didn't mess with the server version of it much.

Thanks in advance....try not to laugh so hard you spill your coffee now that you've read all of this nonsense.  ~dsf
Assuming you have all the dependencies installed.

1) dpkg -i <package>.deb

2.) It shouldn't have been, but you should be able to check for it.

3.) Webmin is a server admin software you access via a web browser. There is no need for any GUI on the server. You need perl and what ever other libraries is required, it's been some time since I've used Webmin (perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions python)

4.) It's irrelevant

5.) [http://packages.ubuntu.com/precise/firefox](http://packages.ubuntu.com/precise/firefox)

6) [http://askubuntu.com/questions/147654/how-to-setup-local-repository-for-ubuntu-12-04](http://askubuntu.com/questions/147654/how-to-setup-local-repository-for-ubuntu-12-04)

---

