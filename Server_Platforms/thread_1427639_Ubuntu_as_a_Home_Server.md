---
title: "Ubuntu as a Home Server?"
date: 2010-03-11
forum: Server Platforms
---

### Post by frekimedia on 2010-03-11
Excuse the naivety of my post. I've been long away from the Ubuntu realm. 

I just installed Windows Home Server on an old box I had sitting around. The overall goal was to have my 500GB WD external drive acting like a NAS, which kinda worked. Another nice feature is that I can log onto my server from anywhere and access the files with a username/password, as well as remote control. The other two computers in my home are a desktop running Windows 7 Ultimate and a laptop running Windows 7 Home Premium. I also have an HD MediaBox (from Crystal Media I believe) that is connected to my TV and surround sound that I stream video and music to.

I really am kind of disappointed by the simplicity of WHS however. This got me to thinking of using Ubuntu in this capacity. Here are the things I would like to do...please help me out :).

1. Shared file storage, including my WD drive (I believe SAMBA would work?)
2. Automated or one-click backup
3. Remote access (like being able to access my files while in lecture)
4. Another cool thing that I like about WHS is the ability to access it by typing a web address into your browser ([www.example.com](www.example.com)). This would be a cool feature too, but not necessary.

What do you guys think? Any helpful minds out there? I'm pretty sure this is possible, I just don't know where to begin. THANKS!

---

### Post by Samatva on 2010-03-11
You will be happy with Ubuntu if you have the time to dedicate to learn and set it up. There is a learning curve, but Ububtu is *by far* the easiest to learn Linux version. And you've already found a great support community right here!

For your file sharing, you may want to consider Alfresco - the installation is somewhat easy and the features are great - SharePoint, Alfresco Share collaborative web space, etc.

I have this running on an old P4 Compaq at home, and mount the share at work via WebDAV - works great and is reasonably fast. I administer it all with Webmin, but you may want to start with teh Desktop version and add the server features.

See [http://jared.ottleys.net/alfresco/alfresco-community-3-2-ubuntu-package-explained](http://jared.ottleys.net/alfresco/alfresco-community-3-2-ubuntu-package-explained) for a tutorial

---

### Post by CharlesA on 2010-03-11
I use the same kind of thing. I've got a file/VM server running Samba, SSH, and DHCP.

I looked into running WHS.. but it had a bunch of garbage that I didn't want to deal with and Server 2K3/2K8 was out of my price range...

Anyway, I use SAMBA for file sharing (works great for streaming movies to my HTPC). I also use rsync for backups, running in a crontab.

So far I haven't had any problems with the setup. I do use webmin to configure Samba and DHCP, but most admin stuff is done directly over ssh.

---

### Post by zander1013 on 2010-03-11
i have set up an ubuntu server on an old ibm t60 laptop that i am using to server [http://alonzofretwell.com:1234](http://alonzofretwell.com:1234)

the url loads here but others in different locations have reported they cannot load it. can you load it?

i set it up as the default ubuntu lamp and accessed it through a browser using <servername>.localdomain for the url.

<servername>.localdomain is how you will access it with a browser right after you set it up.

thank you for reporting if you can see my server and good luck with your own.:)

---

### Post by frekimedia on 2010-03-11
> **zander1013 said:**
> i have set up an ubuntu server on an old ibm t60 laptop that i am using to server [http://alonzofretwell.com:1234](http://alonzofretwell.com:1234)

the url loads here but others in different locations have reported they cannot load it. can you load it?


 
This is the screen I get when I click your link


Thanks for the reply

---

### Post by frekimedia on 2010-03-11
> **CharlesA said:**
> I use the same kind of thing. I've got a file/VM server running Samba, SSH, and DHCP.

I looked into running WHS.. but it had a bunch of garbage that I didn't want to deal with and Server 2K3/2K8 was out of my price range...

Anyway, I use SAMBA for file sharing (works great for streaming movies to my HTPC). I also use rsync for backups, running in a crontab.

So far I haven't had any problems with the setup. I do use webmin to configure Samba and DHCP, but most admin stuff is done directly over ssh.

I've actually read a little about doing this very thing. Rsync with a cron sounds like a good idea...I read somewhere about a Windows wrapper for rsync that would let me use it on my Win7 PCs.

---

### Post by frekimedia on 2010-03-11
> **Samatva said:**
> You will be happy with Ubuntu if you have the time to dedicate to learn and set it up. There is a learning curve, but Ububtu is *by far* the easiest to learn Linux version. And you've already found a great support community right here!

For your file sharing, you may want to consider Alfresco - the installation is somewhat easy and the features are great - SharePoint, Alfresco Share collaborative web space, etc.

I have this running on an old P4 Compaq at home, and mount the share at work via WebDAV - works great and is reasonably fast. I administer it all with Webmin, but you may want to start with teh Desktop version and add the server features.

See [http://jared.ottleys.net/alfresco/alfresco-community-3-2-ubuntu-package-explained](http://jared.ottleys.net/alfresco/alfresco-community-3-2-ubuntu-package-explained) for a tutorial

You're right, Ubuntu has the best support base of any Linux I've used.

I've never heard of Alfresco...I'll check it out. Thanks for all these suggestions!

Anyone else with suggestions I'm open to them...this is a learning experience for me.

---

### Post by a.walker on 2010-03-11
You should check out[ eBox]("http://www.ebox-platform.com/"). It has a decent web interface and its installer works pretty nicely for allowing you to install only the things you want. Setup is quick and easy and it is based on Ubuntu server.

---

### Post by kaldor on 2010-03-11
Ubuntu makes a *wonderful* server OS. I didn't find it hard to set up at all. I'm not a noob to Linux, but even so I think it was pretty straightforward. It's running on a 13 year old HP pavilion desktop. Runs great.

But, some other ideas for a server include..

-Debian
-CentOS (great server OS)
-FreeBSD (not Linux, but very similar and very secure and powerful)
-Solaris (if you have a powerful enough computer and want to take the time to research it)
-Wolvix because it's lightweight and more hands-on (slackware based)


check [www.distrowatch.com](www.distrowatch.com) for more ideas. But if you just want a simple to use server, Ubuntu is pretty good.

---

### Post by CharlesA on 2010-03-11
> **frekimedia said:**
> I've actually read a little about doing this very thing. Rsync with a cron sounds like a good idea...I read somewhere about a Windows wrapper for rsync that would let me use it on my Win7 PCs.

I just have my Win7 PCs backup to a network location, and the server rsyncs it to a backup drive. It works fairly well too.

---

### Post by frekimedia on 2010-03-12
All good ideas. I think right now I'm leaning towards an Ubuntu 9.10 desktop build with some server pkgs installed (like Samba and such.

How about a remote desktop from my Win PCs? Is there a way to have an environment similar to Windows Remote Desktop onto my Ubuntu box from my Win7 computer?

---

### Post by spynappels on 2010-03-12
There is a way to have an RDP-like connection using VNC, but that would require having a GUI installed on the server, using resources that can be used for other stuff.

Using Webmin and CLI allows you to set up stuff using a GUI (Webmin) and also control stuff using SSH. It takes some more elarning but is much more rewarding. Also a SSH connection from a bad Internet connection in a remote location is much more reliable and secure.

---

### Post by frekimedia on 2010-03-12
Alright...I'm diving in. Ubuntu 9.10 Server (i386) being installed on this machine:

Foxconn P4M800 motherboard (SiS/VIA chipset I believe)
Pentium 4 520 (2.8GHz w/HT)
2GB DDR2 533 RAM
60GB SATA (filesystem)
120GB PATA (storage)
500GB WD USB (storage)

Windows Home Server flew through this, and after testing with Ubuntu 9.10 Desktop ed. today, it seems like it has even more performance. Wish me luck, lots of questions are sure to ensue.

---

### Post by Sporkman on 2010-03-12
> **kaldor said:**
> But, some other ideas for a server include..

-Debian
-CentOS (great server OS)
-FreeBSD (not Linux, but very similar and very secure and powerful)
-Solaris (if you have a powerful enough computer and want to take the time to research it)
-Wolvix because it's lightweight and more hands-on (slackware based)


FreeNAS might work for him too - it's pretty highly regarded though I've never tried it.

One other thing: You didn't mention Macs, but if you need Mac file sharing, you'll want to install "netatalk".

---

### Post by frekimedia on 2010-03-12
I've looked into FreeNAS, but I want more features than simply a NAS. Thanks for your suggestions!

---

### Post by frekimedia on 2010-03-12
Also, I'm pulling these two guides for help on this...any other resources or guides you guys suggest?

[The Perfect Server - Karmic Koala]("http://http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2")

[Installing Ubuntu 9.10 as a Home Server]("http://bendingmcp.blogspot.com/2009/12/installing-ubuntu-910-as-home-server.html")

---

### Post by dasunsrule32 on 2010-03-16
You may want to look at [this]("http://www.amahi.org/") too.

---

### Post by dudumomo on 2010-03-16
I've also done a blog with articles about it: [www.freelydifferent.com]("www.freelydifferent.com")
Just to learn how to do a basic server (Mail, Web, etc...)

---

### Post by frekimedia on 2010-03-16
> **dasunsrule32 said:**
> You may want to look at [this]("http://www.amahi.org/") too.

Thank you! This looks like exactly what I wanted. However, when I go to the "Get it!" page on the Amahi website it never gets there...page just hangs up on loading everytime. I've tried it both in IE and Chrome on 2 different computers. Anyone else getting the same thing? (amahi.org/signup is the page in question)

I just wish it was Ubuntu-based. I really have no experience with Fedora :(

---

### Post by dasunsrule32 on 2010-04-08
> **frekimedia said:**
> Thank you! This looks like exactly what I wanted. However, when I go to the "Get it!" page on the Amahi website it never gets there...page just hangs up on loading everytime. I've tried it both in IE and Chrome on 2 different computers. Anyone else getting the same thing? ([amahi.org/signup]("http://amahi.org/signup") is the page in question)

I just wish it was Ubuntu-based. I really have no experience with Fedora :(

You'll learn, you'll be fine. Besides that, it is a mostly GUI based distro, so you should be able to handle it.

---

