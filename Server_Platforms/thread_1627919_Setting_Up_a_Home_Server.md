---
title: "Setting Up a Home Server"
date: 2010-11-22
forum: Server Platforms
---

### Post by GuitarRocker2562 on 2010-11-22
I recently install Windows Home Server on an extra PC I have laying around and I really enjoy having a server in my home, but there are many things I don't love about Windows Home Server, so I'm moving to Ubuntu.

So before I begin working on my first Ubuntu server, I have a few questions. Basically, want I want to accomplish is a home server that I can use as a bittorrent server, media server, and to make daily backups of the three machines in my house. Do any of you know good mediaserver programs, I just want DLNA support to stream media to my PS3. In addition, I need the server to make daily backups of my three machines, any good software to automatically back up my PCs? 

Lastly, the GUI question. I can get around a terminal and run a computer sans gui if necessary. However, GUIs can be very helpful. Since I want to run a headless system, is there a way I can log into the server using a pc on the local network and control it via GUI? What are my best options?

Thanks in advance!

---

### Post by potat on 2010-11-22
As for using a GUI remotely, I think VNC is the way to go. Try installing tightvncserver - it creates an X display that you can remote in to without actually outputting to any monitor.

Then get a VNC client (I think Ubuntu comes with Vinagre, and you can get TightVNC Viewer for Windows) and connect!

Since the server generally runs on display :1, you need to specify to the viewer to connect to

(server's local IP address):5901

Hope this helps.
=============================
EDIT: Additionally, if you are SSH'ing into your server from a Linux machine, you can try the -X option for ssh. This enables X11 forwarding over the connection, so that when you run a graphical program from the command line, it will open on your own display. This should be faster than VNC in general because it is only sending window information and I/O over the connection rather than video.

+++++++++++++++++++++++++++++
You may want to check this out as well.
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by drdos2006 on 2010-11-22
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by HermanAB on 2010-11-22
Howdy,

Ubuntu Server has SSH installed by default - it is better than VNC.  VNC is mainly a Windows thing and should be avoided on Linux.

If you want wizards with a GUI, install Webmin and access it with a web browser.

---

### Post by clay7 on 2010-11-22
If you go with webmin, after you install it you should change its default port from 10000 to some other port for security purposes by going to Webmin, Webmin Configuration, Ports and Addresses, and near the top change the 10000 port to something else.

If you're behind a router at home, be sure to forward the port on the router to your new server (probably located at 192.168.1.3 or something similiar).

---

### Post by GuitarRocker2562 on 2010-11-22
Alright, so a lot of you are suggesting to use webmin, which looks really good to me. However, in the Ubuntu official wiki it says webmin is unsupported, is this going to cause issues for me? Any idea why it isn't supported?

---

### Post by clay7 on 2010-11-22
My guess is that "unsupported" means that Ubuntu developers don't contribute to Webmin code...but that's just my guess. Webmin has been around for a while and has been used with Ubuntu for at least several years. It's never caused me problems.

---

### Post by GuitarRocker2562 on 2010-11-23
Installed Ubuntu server and immediately ran into my first issue. I want to create a RAID 0 between my computer's internal 200 GB HDD and an external USB one that is 500 GB. I set this up and now grub won't boot, something about a disk not existing. I think the problem is that GRUB can not see the external disk so it thinks the system is messed up. I think that if I create a separate /boot partition on the internal drive before I create the RAID (which would be both discs minus the /boot partition), GRUB will work fine. Does this sound correct, is there a better way to solve this problem?

---

### Post by HermanAB on 2010-11-23
Howdy,

Doing RAID with a removable disk as one of the parts is not a good idea.

---

### Post by Drenriza on 2010-11-23
> **GuitarRocker2562 said:**
> RAID 0 between my computer's internal 200 GB HDD and an external USB one that is 500 GB.

Delete what you have on your hard drives again, and start from the beginning. Since your already on your way to smash your system.

With all raid systems you should use hard drives with equal size in GB/TB.
To have one on 200GB and other on 500GB is asking for ALOT of trouble and loosing data.

My strong advice.
Do equal size HDD and same sata connection type or dont do raid. And on a server do raid 1 (mirror) instead of raid 0 (strip) that is also asking for trouble. Since when one dies you have 100% lost all your data.

---

### Post by James78 on 2010-11-23
> **GuitarRocker2562 said:**
> Alright, so a lot of you are suggesting to use webmin, which looks really good to me. However, in the Ubuntu official wiki it says webmin is unsupported, is this going to cause issues for me? Any idea why it isn't supported?
Installing Webmin/Virtualmin is supported (by the Webmin developers) on the LTS releases.. E.g. 10.04.1, 8.04 .. Installing it on 10.10 will give you errors.

As for your question regarding why it isn't supported, it isn't supported because the Ubuntu team has no control over the code, so they can't verify it's validity or if it works. That's the same with every other third party software you get (with multiverse and universe software I believe)

You can get it running quickly by loosely following this guide. There's probably many more you can find by doing a Google search.
[http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)

---

### Post by GuitarRocker2562 on 2010-11-23
I installed it using an LVM with the two drives with a separate /boot partition. I know that having two drives in such a set up isn't quite so good for my data but none of the data is sensitive and I need the extra space.

---

### Post by wreed on 2010-11-28
[http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html](http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html)
 
That link worked better for me on Ubuntu 10.10

---

### Post by SeijiSensei on 2010-11-29
No one answered the DLNA server question it appears.  By all accounts, [ps3mediaserver]("http://code.google.com/p/ps3mediaserver/") is the best choice.

---

### Post by CharlesA on 2010-11-29
> **SeijiSensei said:**
> No one answered the DLNA server question it appears.  By all accounts, [ps3mediaserver]("http://code.google.com/p/ps3mediaserver/") is the best choice.

+1 to that.

I've used it before with little problems.

---

### Post by matt_symes on 2010-11-29
Hi

I have also used mediatomb and that has not given me any issues and has a simple web interface.

I have never used ps3mediaserver so i cant really comment on it.

Kind regards

---

### Post by Kluttz on 2010-11-29
My current home server consists of the following installed:

transmission for my torrents
miniDLNA for local media streaming
WEBMIN for local administrative stuff
phpsysinfo to display system resources

As for backups, I do have anything that will backup my PC's.
I have all the PC's in the house use network drives to store data on the server.

Good luck

If anything has any other cool apps they have on there ubuntu server please share.  Always looking for cool things

Also, if you interested in a all in one solutions, check out [www.amahi.org](www.amahi.org)

I will take a look at it once its updated.  Its currently only works with fedora 12 but they are working on fedora 14

---

