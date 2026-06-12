---
title: "Server Setup Suggestions"
date: 2009-01-29
forum: Server Platforms
---

### Post by Moobsy on 2009-01-29
Hi everyone, I have been reading around the forums here and it looks like this Ubuntu server will suit my needs, but I am a noob to unix and servers in general.

Before you flame me to death, lol, I should explain that I do have a pretty good knowledge of computers, but definately from an end user perspective.  I am old enough that command line doesn't scare me to death, but I honestly haven't used command line since like the mid 90's in Windows 3.11...

Anyway, here is what I am trying to accomplish:

**Host websites**, nothing major, just a place where my friends and I can post our own personal web pages.

**Share files**, I would like to be able to allow users to login from any machine that can access the internet and either stream or download pictures, music, video, etc. via FTP or similar method.

**Allow users to save files to the server** from any machine with web access.

That is it!  I know there is extra overhead involved in running a GUI, but the box I will be using to power the server is an old gaming rig that is way more powerful than neccessary.  I would like the simplest to manage and setup interface even at the expense of performance.

**What version of Ubuntu is right for me?**

**What are the neccessary apps I need** to install to do the tasks I am trying to accomplish?

**What is the maximum number of users** an Ubuntu server can support?

Thanks for your help!

---

### Post by redroad55 on 2009-01-29
Hi, 8.04 desktop is your best bet it is the same kernel for the most part as the server version with the gui .. 
 [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
By downloading the desktop you can familiarize yourself with things like repositories ( to download the apps you want), Terminal for command line ..work with this awhile .. Try out these How TO's
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
[http://ubuntuforums.org/showthread.php?t=809695]("http://ubuntuforums.org/showthread.php?t=809695") 
here is a helpful link for command line
[http://linuxcommand.org/]("http://linuxcommand.org/")
A basic understanding of the following links are critical before going forward with installing your server environment..Think hard about how you want to format and partition your hard drive or drives before you begin with server..
[https://help.ubuntu.com/8.04/serverguide/C/index.html]("https://help.ubuntu.com/8.04/serverguide/C/index.html")
[http://tldp.org/LDP/sag/html/index.html]("http://tldp.org/LDP/sag/html/index.html")
best to you .. Post back with any further questions

---

### Post by cariboo on 2009-01-29
There a couple of better ways to manage you server other than installing a desktop. Check out [Webmin]("http://www.webmin.com/") and [eBox]("http://ebox-platform.com/"). eBox is available in the repositories and Webmin debs are available from the web site.

Jim

---

### Post by Moobsy on 2009-01-29
Thanks! I will definately read up on these.

This project is a hobby and the PC I am installing on is literally a paperweight right now.  I am willing to have a few failed attempts ;)

My remaining questions are uber-noob...

1) Do I understand corretly that my hardware arangement should have 2 network cards, 1 to the router and one to the interweb?  Other computers will then access the server through the router which will then access the net through the server?

2)  Are there drivers on the Ubuntu install to support common hardware or will I have to find Linux drivers for these parts and install them?  My setup is a Northwood Mobo running a P4 2.8ghz on 1.5 gigs of RAMBUS 1066 (lol @ RAMBUS) spinning 2 80gig HDD's.  I have 1 onboard network adapter and a Netgear (I think) 10/100 PCI Network adapter.

3)  will I still be able to access the web on my other PC's while I tinker with installing server software?

Be gentle! lol.

---

### Post by redroad55 on 2009-01-29
As to number 1) a little better description of your LAN (local area network) would help .. A network switch would solve the initial learning curve .. keeping your server back from the internet until your ready to turn it loose but still being able to connect to the internet with your other machines as you learn how to serve your LAN first ...
  as to number 2) download the Ubuntu Image you choose from the link I gave you above and put it on a cd ..You can use it as a live cd .. if it loads there are no hardware issues if not we will go from there ..If you have success with the live cd there is also the choice to install .. You won't break anything or create a situation that can,t be resolved ..
this is a pretty good choice for a switch [http://www.newegg.com/Product/Product.aspx?Item=N82E16833127082]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833127082")
you will connect all your Lan PC's to it including your server prospect and one of the ports on the switch to whatever you go to the internet with ..Hope this helps .. Best to you ..Post back with any questions

---

### Post by Moobsy on 2009-01-29
My "LAN" consists of 1 desktop computer hard-wired to a router which is connected to a cable modem.  There is 1 Netbook connecting to the router wirelessly.

I think I understand what you are saying. I should put another router on the experimental server and leave the one I am using for the internet the way it is for now.

---

### Post by redroad55 on 2009-01-29
Depending on the router flavor and number of ports you could directly go into the router with server prospect . name and mdl of router ? Is it a DHCP capable ?  Best to you .. Post back

---

### Post by FerociousTwig on 2009-01-29
I have essentially the exact same desires for my server. I however am in college where I cannot have a server behind the firewall. So what I am doing is using my old computer which is at home lying dormant in the basement as setting up an SSH server on it. If you don't know SSH is basically just a remote access client that happens to be quite secure. Once I go home and set up the SSH client, I can pretty much administer everything else from school so I havent really thought them out in too much detail but my plan is roughly as follows:

1) Install Ubuntu Server Edition (8.04 or 8.10) 
2) Install open-SSH
3) Write down external IP address of my home 
4) Set up a static local IP for my basement computer

------- end of steps that need to be done at home ------

5) Install apache webserver
6) Install php
7) Install some sort of FTP client. . . perhaps filezilla

That is a rough sketch of what I am doing and it sounds like you are trying to do the same. As for network cards you should only need one. Just a btw though, for a server, 160GB doesn't really sounds like a whole lot of storage. Might wanna think about adding more to that if you're using it for file storage as FTP would indicate. Maybe someone more experienced could give us some suggestions that would help. Good luck mate

---

### Post by redroad55 on 2009-01-29
here is a great link ..It was written for Gutsy Gibbon but most of it transfers to 8.04 ..
[http://users.bigpond.net.au/hermanzone/p11.htm#DHCP]("http://users.bigpond.net.au/hermanzone/p11.htm#DHCP")
openssh client is already part of the 8.04 desktop pkg.

---

### Post by Moobsy on 2009-01-29
lol yeah 160gig for HDD space is inadequate.  We will be replacing those with 2 1 TB's as soon as I can set up a working server :)

---

