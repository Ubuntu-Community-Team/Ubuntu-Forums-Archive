---
title: "Proper xubuntu LAMP and file server setup"
date: 2007-11-24
forum: Server Platforms
---

### Post by vsiege on 2007-11-24
Hi,

After looking at all the other distros out there I'm deciding to go with xubuntu for my first lInux deployment. I am interested in setting up a LAMP and file server to be used for my personal projects with minimal outside usuage. I have found random articles disussing either file or LAMP setup, but have not found one that includes both together. I will be setting up the entire OS from scratch (new build without an OS and that will not have any other OS) and want to set it up properlly. I will be administering this box from a mac as well as from windows. Can anyone direct me to an article that discusses installing xubuntu with:
the newest LAMP services
file serving (and how to administer that from M and W)
SSH
security
I just do not want to start off on the wrong foot.

Thanks for all your help.

---

### Post by prodezigner on 2007-11-24
How about a mini-howto...

Download and burn the Server 7.10 ISO to CD.

Install as you normally would... when it asks for what packages you want (near the end), select LAMP, SSH and SAMBA.

When you get to the command line type:

sudo apt-get install xubuntu-desktop

TADA... simple AND easy :D

NOTE: Default ports = 22 for SSH, 80 for Apache2 and as for administering your server and security... it just really depends on HOW secure you want it honestly...

---

### Post by HermanAB on 2007-11-24
Well, you should do things in a certain order.  First get the basics installed, Ubuntu or Xubuntu, both are good.  Then get Synaptic to work properly and install OpenSSL.  Test out ssh and ensure that it works.  Install Firestarter and ensure that ssh still works.

Now install the rest in order of difficulty: First proftpd, followed by Apache and finally Samba.  

By then, you'll know more about Linux than you ever thought you would need to know...

Cheers,

Herman

---

### Post by vsiege on 2007-11-24
Both ways sound do-able!

I have never installed any of this stuff. I really dont mind getting my hadns wet, but at the same time I dont want to get stuck in the middle with a question on which option to choose.

**prodezigner**: mini-is good! The server ISO sounds easy, and probably includes alot (some of which I may not need), I thought they only made ubuntu as a server edition? Will this be a bulky OS? As far as security I find that everytime I ask questions regarding server OS people are very quick to remind me of security - to what degree I cant say - how about more than someone doing it for the first time would think of?!

** HermanAB** I only choose xubuntu for its smaller size, thats the only reason I didnt choose its bigger brother. This really acts as no more than a server for me, hence I figured that ubuntu had more than I needed. v. I'm really not sure how to configure Synaptic, OpenSSL, ssh, Firestarter and so on. Does this invite the possibility for disaster?

---

### Post by HermanAB on 2007-11-24
Xubuntu is just a different desktop system.  Xfce is blazingly fast compared to Ubuntu with Gnome.  Other than that, there is no difference.

Stay away from the 'server' edition.  It is meant for use in data centres where the machines have no attached screens or keyboards and are managed remotely via SSH from another machine, that does have a screen and keyboard and X running.   So unless you are working at a server farm, then you don't want the server version.

So in general, if you got to ask, then the 'server' version is *not* for you.

'Hope that helps!

Cheers,

Herman

---

### Post by vsiege on 2007-11-24
Thanks. I was familiar about the desktop environments but did not know that about the server edition (but that makes sense). I still think that x is right for me. I guess I will do this in steps like you had suggested. I am still building the machine at the moment (waiting on the rest of the parts). Is Synaptic a package of x (I seem to recall it being)? or are all the apps you named before part of the distro? One of my concern is having the most up-to-date LAMP services.

---

### Post by prodezigner on 2007-11-24
I hate to say this, but HermAB is WRONG.

Server Edition is just a CLI version of Ubuntu with the default server packages installed.

If you sudo apt-get install xubuntu-desktop after the initial install you'll get the full blow Xubuntu distro on TOP of the LAMP, SSH and SAMBA servers when you done the initial setup.

You CAN use Server Ed. for a headless server, but I run Xubuntu just fine on my Server Ed. with a monitor.

ALSO... after you install the Xubuntu Desktop you can install TightVNCServer and use a VNC to see your desktop from anywhere you have a VNC Client.

---

### Post by vsiege on 2007-11-24
If thats the case, why go the other way (to learn how!)? My server will eventually be headless- but i would definitely want the X desktop. I will need to know how to admin X from a Mac OS 10.4 - almost like a remote desktop. Any suggestions?

---

### Post by prodezigner on 2007-11-24
VNC it is...

[http://sourceforge.net/projects/cotvnc/](http://sourceforge.net/projects/cotvnc/)

You'll need that on OS X for connecting to the server...

And as for setting up the Xubuntu desktop for remote management... check out this article.

[http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html)


Hope this helps!

And on a closing note: If your going to do a lot of home network sharing, I'd recommend a dedicated NIC card for it assigned in SAMBA. If you download files and share files through the same NIC... it's gonna put a hurtin' on bandwidth and transfer speeds. VNC alone could use a dedicated NIC (cause of the constant transfer of data). But you should be fine with two NICs.

---

### Post by HermanAB on 2007-11-24
Hmm, Linux is Linux is Linux...  any perceived differences are purely cosmetic.

The server edition is the same as the desktop edition, minus the desktop.  So yes, you can take the server edition then add the desktop back in, or you can take the desktop edition and take the desktop out again.  Your choice.

---

### Post by vsiege on 2007-11-28
Should I check off this option on the DL page?
>  Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.

---

### Post by prodezigner on 2007-11-28
Alternate installer is for a text based installer. It's intended for computers with no so plentiful resources. Such as an older machine.

The server installer doesn't have an alternate I don't believe.

---

### Post by vsiege on 2007-11-28
I DLed it both ways - the file size was exactly the same. Once I get it installed, I'll give you a holler - thanx for all the info so far!

READ BELOW

---

### Post by vsiege on 2007-12-01
i got xbuntu desktop to run and installed the server edition with these packages:

LAMP server
OpenSSH Server
PostgreSQL database
Print Server
Samaba File Server

What shouls I set up next???

---

