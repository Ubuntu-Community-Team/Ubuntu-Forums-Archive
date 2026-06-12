---
title: "How to setup server"
date: 2009-01-22
forum: Server Platforms
---

### Post by johnroyworld on 2009-01-22
hi all, i'm newbie w/ ubuntu please help me of my concern on what i'm going to do or configure. Heres what i've planned to do. I have an simple account management system that runs w/ ruby on rails and i've planned to put it in a local server here in my office so that other computer can access it in a local network. So my problem now on how i can do this, and whats my first thing to do or install? is there any tutorials that you can provide? please help me! I'm now currently have a ubuntu 8.10 here installed yesterday.

---

### Post by linux_tech on 2009-01-22
[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

---

### Post by johnroyworld on 2009-01-22
Hi Linux_tech,

Thanks for your quick response. well, i'm following this guide now that you gave me and i've found out that its a quick overview of Ubuntu 8.10 Server Edition but what im using now is Ubuntu 8.10 (intrepid) is this they same or should i install the Ubuntu 8.10 Server Edition? forgive me im very new to ubuntu. 

Thanks...

---

### Post by djchaly on 2009-01-22
> **johnroyworld said:**
> Hi Linux_tech,

Thanks for your quick response. well, i'm following this guide now that you gave me and i've found out that its a quick overview of Ubuntu 8.10 Server Edition but what im using now is Ubuntu 8.10 (intrepid) is this they same or should i install the Ubuntu 8.10 Server Edition? forgive me im very new to ubuntu. 

Thanks...
You mean you are using Ubuntu 8.10 Desktop version? That's probably same...
You can build a server from Ubuntu Desktop version....

The big different of both is, Ubuntu Desktop in the GUI mode...and application auto installed by Ubuntu desktop such as games, office, internet, multimedia, etc no need to be installing to the server...

---

### Post by sahabcse on 2009-01-22
For setup server following setup is important

1) First Choose powerful machine like IBM x series, Dell power edge, Hp etc

2) Hardware RAID -- For data secure, access speed. RAID 0, RAID 1, RAID 5, RAID 10 etc, Each have different futures.

3)Operating system -- Linux, Unix, Windows etc (Based on your requirements)

4)Partition - Depends upon the size and server configuration eg)Database server or web server

5)packages - Based on your application. If web server means apache,tomcat , mysql or postgres etc

6)Storage - If you need additional storage means configure SAN, NAS

7)Backup - For backup use tape drive, TSM etc

---

### Post by happyhacker on 2009-01-22
Is this account program accessed via a browser (i.e. OS independant)? You could grab an old computer reinstall windows to clean the environment or install the Ubuntu desktop (assuming of course this Ruby thing is compatible with Linux).

---

