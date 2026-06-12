---
title: "Ubuntu server for file downloading and serving"
date: 2010-12-02
forum: Server Platforms
---

### Post by mmad on 2010-12-02
Hi guys, I would like to run a small file server at home which I could connect to both remotely and within my own network. I was thinking of using something similar to a cheap dell optiplex machine (Pentium 3 or 4 2GHz?, with 256mb ram and a 40GB hard drive[will do something about the lack of space later]).

The file server part of this should be straightforward but I wanted advice on how I could manage downloads on the machine. On my laptop I currently use both firefox's built in download manager and JDownloader. Sometimes Jdownloader isn't the ideal solution for all downloads, e.g. sometimes a single connection through firefox gets a faster download speed. I also occcasionally download torrents through Miro.

If anyone has setup something like what I'm suggesting, could you please give me a general idea of how best to go about this? Thank you.

---

### Post by KB1JWQ on 2010-12-02
What I generally do when I want to have things show up to my "download server" is to ssh in, and fire up a screen session.

Within that screen session, I'll get the file I care about via wget, rsync, or whatever other tool best fits the use case in question.

Later, I'll connect to my download server, and rsync that file over to my laptop for use.  

This keeps me from having to maintain a persistent connection.  It may or may not be what you wanted; let me know if I can clarify any of this.

---

### Post by drdos2006 on 2010-12-02
Check out this thread.....
Server software on one machine, client software on the other. 
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

Addendum:	On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin. If Webmin not an option then use terminal on the Server machine: 
sudo addgroup MyGroupName	
Added sharedfiles on server with :	
sudo mkdir  /media/sdb1/sdb1-shared
Needed to change group permissions for /media/sdb1/sdb1-shared:	
sudo chgrp -R  MyGroupName  /media/sdb1/sdb1-shared
//**
On the Client machine: 
Created a directory of sharedfiles with : sudo mkdir /media/sharedfiles
mounted /media/sharedfiles from terminal with : 
sudo mount  <serverIPaddress>:/media/sdb1/sdb1-shared      /media/sharedfiles 
Can also be added to /etc/fstab for automatic mounting.
Copied files as test and it worked.

---

### Post by KB1JWQ on 2010-12-02
This gets extremely hairy if you lack a persistent NFS connection, such as with a laptop.

---

### Post by mmad on 2010-12-02
Thanks for the responses people.

> **KB1JWQ said:**
> What I generally do when I want to have things show up to my "download server" is to ssh in, and fire up a screen session.

Within that screen session, I'll get the file I care about via wget, rsync, or whatever other tool best fits the use case in question.

Later, I'll connect to my download server, and rsync that file over to my laptop for use.  

This keeps me from having to maintain a persistent connection.  It may or may not be what you wanted; let me know if I can clarify any of this.

This seems like what I'm after. Opening just a single instance of a browser or a download manager and then just letting it download my files... that sounds good. I'm installing Ubuntu Server 10.10 into a virtual machine right now. I just don't understand if I can do this without installing a window manager like LXDE or whatever first.

---

### Post by mmad on 2010-12-03
I'm having some issues with working out my internal ip address of the server. I've tried running ifconfig and ifconfig -a, but both do not give me an address I can work with. The only recognisable ip like address is 10.0.0.25 - which I cannot connect through with my browser.

---

