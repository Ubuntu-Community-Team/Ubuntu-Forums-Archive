---
title: "Questions about setting up a home fileserver running Ubuntu."
date: 2006-07-21
forum: Server Platforms
---

### Post by KillrBuckeye on 2006-07-21
Hi, I have some basic knowledge of Ubuntu, and I have managed to successfully enable Samba and gain access to my Ubuntu machines from my Windows machines (and vice versa).  However, I am wanting to take this to the next level and convert one of my old machines into a full-blown home fileserver which will run 24/7.  However, I still relatively new to Linux and I have some questions as follows.

1) I realize that any file system that the server OS can read/write will work okay in terms of being accessible from other computers on the network, but my fear is this: What if something happens to the OS (Ubuntu) on my server and it becomes unbootable? I am primarily a Windows user (slowly learning about Linux), so if I need immediate access to files on my server's HDD, what are my options? I can't just install the HDD in a Windows machine and expect to be able to read an ext3 or other Linux filesystem, right? I have heard about drivers that allow Windows to read ext3, but is this really easy for a n00b to set up?

2) I have absolutely no experience with remote administration of computers, outside some very limited experience with Windows Remote Desktop. I have been told that Linux boxes can be administered remotely using a certain protocol, but what if the other computers on the network are all Windows machines? Is it possible to control a Linux box from a Windows machine? If so, can it be done without purchasing some expensive software? I'd very much prefer remote admistration of the server so that I don't have to have a keyboard, mouse, and monitor for the server. 

Any help you could provide would be appreciated!

---

### Post by Paerez on 2006-07-21
1) If you set up one partition as ext3 for linux's install, then a large storage partition as FAT32, you can share the fat32 across the network, and also be able to pop the HD into a windows comp to grab the files.

2) If you install VNC on your linux comp and run a VNC server, any computer with a vnc client can view and use the desktop remotely (windows or linux or mac or unix, anything with a vnc client).

Good luck!

---

### Post by it.henrik on 2006-07-21
agree with Paerez but here are some alternatives that I personally prefere.

1) Use ext3 if you want. If you mess up your linux installation and it wont boot, just pop in the live ubuntu cd and mount your hardrives. Voila! .. there are your files.

2)SSH is an encrypted protocol that gives you total control of your machine. There are great ssh clients for windows, putty is one of them.

---

### Post by Paerez on 2006-07-21
SSH vs VNC:

SSH is faster
VNC gives you a full GUI

so if your connection supports it (like LAN or fast cable/DSL) go for VNC. If you have Dialup or Cable/DSL with a slow up speed, go for SSH. With SSH you only get a terminal, so its harder to use, but much faster.

I have a server on a cable modem, so I only get 40kBps up, which makes VNC pretty slow.

---

### Post by KillrBuckeye on 2006-07-21
Thanks for the responses guys.  

> **Paerez said:**
> 1) If you set up one partition as ext3 for linux's install, then a large storage partition as FAT32, you can share the fat32 across the network, and also be able to pop the HD into a windows comp to grab the files.I thought of using FAT32, but I plan to store a lot of data on this server and I don't like the idea of making lots of different partitions.  FAT32 only supports smallish partitions, right?

[QUOTE=it.henrik]1) Use ext3 if you want. If you mess up your linux installation and it wont boot, just pop in the live ubuntu cd and mount your hardrives. Voila! .. there are your files.[/QUOTE]Forgive me for being a n00b, but does this allow me access the files from the Windows machines?  Is it possible to set up Samba during a LiveCD session so that the server functionality is temporarily restored?

Regarding SSH and VNC, I need some clarification.  Are either of these protocols a substitute for Samba, or are they purely for remote administration?  Is there a steep learning curve for setting up a working SSH or VNC connection?  Are there free Windows clients for both SSH and VNC?

---

### Post by Paerez on 2006-07-21
> FAT32 only supports smallish partitions, right?[FAT32]("http://en.wikipedia.org/wiki/FAT32") supports single files up to 4gigs and volumes (drives) up to 2 TiB. So no, it supports big ones too. But the data can become easily corrupted. I had some trouble when I lost power.

> Forgive me for being a n00b, but does this allow me access the files from the Windows machines? Is it possible to set up Samba during a LiveCD session so that the server functionality is temporarily restored?
I think you can set up samba on a livecd. But also like you said, you could mount the ext3 in windows.

SSH and VNC are purely for remote admin.

SSH is a piece of cake to set up. You install it on the server using synaptic, then you just go to another computer, type in the server's ip or hostname, and it asks you for username/pw and you're in.

VNC is a little trickier because once you install it you have to run the server. It's hard to set up but easier to use once its set up.

There are free windows clients for both SSH and VNC. I recommend Putty and TightVNC.

---

### Post by KillrBuckeye on 2006-07-21
Thank you!  I'm thinking that I'll give SSH a try first, since it sounds much easier to get started with.  I don't necessarily need a GUI.

---

### Post by jinx099 on 2006-07-21
> **Paerez said:**
> 
VNC is a little trickier because once you install it you have to run the server. It's hard to set up but easier to use once its set up.

There are free windows clients for both SSH and VNC. I recommend Putty and TightVNC.
Well technically you have to run the SSH server too, but that usually is started on boot.  My VNC server starts on boot too, and I didnt have to do anyhting special to set it up that way.

Check out this guide for setting up VNC with resumable sessions, it has worked great for me: [http://www.ubuntuforums.org/showthread.php?t=191564](http://www.ubuntuforums.org/showthread.php?t=191564)

---

