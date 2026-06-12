---
title: "Server GUI with no internet"
date: 2008-03-07
forum: Server Platforms
---

### Post by Imashinu on 2008-03-07
I have recently installed Ubuntu server edition at my workplace and have been using the CLI with no problems. Recently my boss has requested that I install the GUI so he could use it easier. 

The problem is, the proxy isn't configured properly and apt-get refuses to work so I can't download the right respiratories. 

I do have the desktop addition on a CD. Is it possible to mount the disk and use the files off of it?

---

### Post by Dr Small on 2008-03-07
You can not use the Desktop CD for that. You would need the *Alternate* CD, which can be used as a repository. 

But why not configure the network and use apt-get?

---

### Post by lespaul_rentals on 2008-03-07
I don't know if the desktop CD will work.  I think the packages may be configured for the desktop kernel instead of the server kernel.  Then again, I could be completely wrong.

You might try using the alternate CD?  I know that has a lot of packages on it.  It might not have desktop packages, however.

Haha, the start of your post made me shake my head.  How come the guy who requires the GUI outranks the guy who manages a server with CLI -- the way it's meant to be?  Oh, and just a tip, install a lightweight window manager, such as Fluxbox, to use instead of the bloated desktop enviroment.

---

### Post by Imashinu on 2008-03-07
We can't get the network to configure properly and I'm not sure why. The machine is getting internet and the cables are good. It might have something to do with our networks proxy.

---

### Post by renzokuken on 2008-03-07
[color=red]just saw above posts, didnt know you couldnt desktop cd, but instructions below should be valid for alternate too[/color]

you can easily use the CD as a repo source

on the server run

```
sudo nano /etc/apt/sources.list
``` 

and uncomment (remove the #) the lines starting with **deb cd-rom**

make sure the cd is in the drive and run

```
sudo apt-get update
```

**make sure you are using the same desktop version (dapper/edgy/feisty/gutsy etc) as the server version you have installed**

to install a **gnome desktop**
```
sudo apt-get install ubuntu-desktop
```
to install a **KDE desktop**
```
sudo apt-get install kubuntu-desktop
```
to install a **Xubuntu desktop**
```
sudo apt-get install xubuntu-desktop
```

---

### Post by Dr Small on 2008-03-07
Go with Xorg and IceWM, Fluxbox or Openbox if you want a lightweight GUI forthe server.

By the way, what on earth is this server being used for if it doesn't have network / internet ?

---

### Post by Imashinu on 2008-03-07
Alright I appreciate the help. I will try downloading the alternate CD and see if that fixes the issues. I'll report back.

---

### Post by jonabyte on 2008-03-07
> **Imashinu said:**
> I have recently installed Ubuntu server edition at my workplace and have been using the CLI with no problems. Recently my boss has requested that I install the GUI so he could use it easier. 


No offense and I know you didn't ask for it, but that should be a warning not to install it. If your boss cannot use the command line, then he has no place on a Linux server. Unless this is a test box or something not critical.
I am speaking from experience....

---

### Post by igknighted on 2008-03-07
If he wants a GUI, give him a web based one like Webmin (or install canonical's landscape and use the trial).  He won't be any better able to admin the box from a GUI because there are no xorg-based tools really.  He would still need to pull up a terminal and use the CLI, and in that case you might as well just SSH into it.

---

### Post by Imashinu on 2008-03-07
> **igknighted said:**
> If he wants a GUI, give him a web based one like Webmin (or install canonical's landscape and use the trial).  He won't be any better able to admin the box from a GUI because there are no xorg-based tools really.  He would still need to pull up a terminal and use the CLI, and in that case you might as well just SSH into it.

Thats what I said to do. See we can SSH in but we can't access internet resources from the server itself which makes no sense. My boss isn't very smart and I don't think he will listen to reason :(

---

### Post by Imashinu on 2008-03-13
Ok I finally got it to work using Apt-cdrom. I am still having the internet issue though. Everything seems configured properly and the machine is getting a connection. 

I have set up all of the possible settings and am still recieveing issues when trying to update in Synaptic.

```

http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/Release.gpg: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/main/i18n/Translation-en_US.bz2: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/universe/i18n/Translation-en_US.bz2: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/restricted/i18n/Translation-en_US.bz2: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/multiverse/i18n/Translation-en_US.bz2: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/main/binary-i386/Packages.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/universe/binary-i386/Packages.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/restricted/binary-i386/Packages.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/multiverse/binary-i386/Packages.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/main/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/universe/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/restricted/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://mirrors.ccs.neu.edu/archive.ubuntu.com/dists/gutsy/multiverse/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz: Could not connect to illidan:808 (192.168.4.32). - connect (113 No route to host)

```

One solution I did try was installing NTLMaps but it says that I dont have python installed which is.

If anyone has any ideas why this is happening please let me know.

Thanks.

---

