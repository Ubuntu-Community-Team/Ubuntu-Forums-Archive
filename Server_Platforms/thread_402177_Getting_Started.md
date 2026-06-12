---
title: "Getting Started"
date: 2007-04-05
forum: Server Platforms
---

### Post by Copland Audio on 2007-04-05
Hello.  I'm a newbie with an ambitious plan.  I have come into a posession of a Pentium 4 computer I'd like to trick out and run as a server on my network.  I would like this box to serve as the network's firewall, Host a couple websites, be a shared print server, an FTP resource, and run Myth TV for home use.
I have set up servers before (a while ago, NDS, WinNT 4), and now am looking to dive in with Linux.  I have xubuntu on a laptop I toy with.
Having not started this project, and armed with decent, yet rusty skills, my questions are: how would you prepare to embark on this?  Are there specific distros I could focus on to minimize my startup pain?  Is there a sequence of installs that will better insure my success rate?
My first step in my mind is to get the hardware together (update RAM, new HD, Get the Hauppage cards for Myth, etc), but am I asking for trouble with all this?

---

### Post by newlinux on 2007-04-05
> **Copland Audio said:**
> Hello.  I'm a newbie with an ambitious plan.  I have come into a posession of a Pentium 4 computer I'd like to trick out and run as a server on my network.  I would like this box to serve as the network's firewall, Host a couple websites, be a shared print server, an FTP resource, and run Myth TV for home use.
I have set up servers before (a while ago, NDS, WinNT 4), and now am looking to dive in with Linux.  I have xubuntu on a laptop I toy with.
Having not started this project, and armed with decent, yet rusty skills, my questions are: how would you prepare to embark on this?  Are there specific distros I could focus on to minimize my startup pain?  Is there a sequence of installs that will better insure my success rate?
My first step in my mind is to get the hardware together (update RAM, new HD, Get the Hauppage cards for Myth, etc), but am I asking for trouble with all this?

I'd read a few guides, figure out what you want and what you hardware will support and dive on in. Many people here can help. What kind of hardware do you currently have (graphics card, RAM, CPU specs, tuner cards). If you just want to record and display NTSC then hardware requirements are pretty minimal, provided you have a hardware encoding tuner card (such as the Hauppage cards) Hauppage cards are pretty easy to setup in myth and ubuntu. If you like ubuntu I recommend looking over:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by newlinux on 2007-04-05
Sorry, I ignored you other uses for the box. Those should all be fairly easy to setup with ubuntu (or any linux distro). Hardware needs will depend greatly on how often the web site and other servers will be used. If they are mainly for personal use, any P4 will probably be fine...

---

### Post by Copland Audio on 2007-04-05
This will be for home business use - probably not a hog, but I'd like to host soundclips and a flash site.  
Sounds like you're saying 'jump in'  Which I respect, and will probably do - it's the only way to learn.  I suppose there's no way to anticipate all the problems, but I'd be interested to hear any stories from other users who have a similar server setup.  To recap:  would like this box to serve as the network's firewall (although maybe I should consider having my linksys router as the firewall), Host a couple websites, be a shared print server, an FTP resource, and run Myth TV for home use.

---

### Post by newlinux on 2007-04-05
> **Copland Audio said:**
> This will be for home business use - probably not a hog, but I'd like to host soundclips and a flash site.  
Sounds like you're saying 'jump in'  Which I respect, and will probably do - it's the only way to learn.  I suppose there's no way to anticipate all the problems, but I'd be interested to hear any stories from other users who have a similar server setup.  To recap:  would like this box to serve as the network's firewall (although maybe I should consider having my linksys router as the firewall), Host a couple websites, be a shared print server, an FTP resource, and run Myth TV for home use.

I do have a similar setup. I have a P4 2.6HT that is my print server for three printers, runs a web site (apache2), and I do use it as an FTP server, although I do it through ssh (sftp) (no configuration other than sudo aptitude install openssh-server, but for certain FTP applications its not appropriate--such as anonymous ftps). It is also a mythbox. Everything was easy except the Myth part. And how hard that part will be depends on a number of hardware variables and which distro you go with. My web site doesn't get much traffic (it's really only for a few people and password protected), but in all honesty, my uploading bandwidth is the biggest bottleneck. I use my linksys router flashed with dd-wrt  firmware as my firewall (but hey that's linux too :) ) Mine also is a fileserver. Samba (for fileserver) took a little time to get right as well. Apache took a little time to learn how to password protect it. But really there was very little configuration involved in any of these compared to mythtv.

As far as order goes, I don't think it will make much difference. I'd probably setup the firewall last so you know it's not messing things up. Maybe start with the print server, move on the ftp, then, if you are going to use mythweb I'd setup myth next since mythweb installs a web server, and then setup the other two web sites... That's off the top of my head, there are probably other considerations that others may give you.

---

### Post by pppetter on 2007-04-05
Jump in and be ready to spend some time with learning how the system works, and the different servers you intend to use. I did exactly that, and though I still feel like a novice, I now spend quite some time every day here in the forum helping others.

Some quick tips then... I would recommend using Ubuntu 6.06.1, since it's supported with security updates to 2011, the other server releases are just supported for 3 years from release.
I would recommend using your existing router as firewall and all that, of course you may if you want, have a firewall in your server too. But setting up your server as firewall for the entire network is just unnecessary (and takes quite a lot of extra time).

---

