---
title: "Home Server/simple file server"
date: 2008-05-14
forum: Server Platforms
---

### Post by PendragonUK on 2008-05-14
I have been using ubuntu on my laptop for a couple of years.

I have an old PC that I would like to use as a home server. At first just as a file server but I'm sure other projects will come to light as time passes. The server would be running without a screen, tucked out of the way.

System Spec:
Intel P4 1.5Ghz
RAM 1Gb
4 IDE hard drives 80Gb, 60Gb, 2x30Gb
NIC 10/100 (there is room for others and I have spares if it would help)
simple graphics card.

To install the OS, one of the hard drives will have to be dropped but once ubuntu server is installed the CD ROM will be removed.

As this has been built from 4 old/dead PC's it's not great but it was free :)

Could anyone please point me in the right direction for some nice howto's to walk me through some projects. file server first but as I said earlier there will be other uses I'm sure.

---

### Post by Thirtysixway on 2008-05-14
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)
has some good walkthroughs for setting up these services.

I would recommend setting up Samba to share folders with your network.  You could also setup apache - web server, access your files via the web browser, proftp - ftp access to your files.

There are many options you can use for file sharing in your small network.  Samba is probably the best way to go, as you can get mount the folders on linux and windows as network drives.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by cdtech on 2008-05-15
Here's the latest Hardy guide for [[COLOR="DarkRed"]The Perfect Server[/COLOR]]("http://howtoforge.com/perfect-server-ubuntu8.04-lts").

Samba is as simple as sudo apt-get, once you have your server setup.

Good luck...

---

### Post by hyper_ch on 2008-05-15
what are the other clients in the network?
Must data be protected?
The howtoforge guide aims at setting up a webserver with associated services... I don't think you are asking for that (yet)

---

### Post by PendragonUK on 2008-05-15
Thanks for the answers guys, as for the questions. there are three PC's in the network. Two Win-Boxs and a Laptop running Hardy. All behind a router, the router is also wireless so the laptop has access. Encryption is not important and I'm not expecting much in the way of speed as the network is slow and so is the hardware. Might be nice to use it as a print server too. At a later date I will think about it for bittorrent. Also ftp if I can sort out the IP redirect for the dynamic IP from my ISP.

---

### Post by Mr_Whippy on 2008-05-15
Thanks pendragon i will add that when i am up and running.

---

