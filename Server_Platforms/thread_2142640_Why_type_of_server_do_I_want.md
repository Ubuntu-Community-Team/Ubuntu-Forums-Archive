---
title: "Why type of server do I want?"
date: 2013-05-06
forum: Server Platforms
---

### Post by DaimyoKirby on 2013-05-06
This is incredibly nooby of me, but I need to ask this since I have no idea what I'm doing at all. I'm looking to create a server, and I'm not sure what components I need to install using the Ubuntu 13.04 server installer.

How the server should work (modelling it after the current school server) is a student boots the computer, puts in their login info, and the computer connects to the server, syncs their network folder (where all their files and such are stored), and then the computer loads the desktop.

It would also be great to be able to manage updates, settings and everything on the computers from the server, although I don't know if that's possible (I suppose kinda like Landscape does, just for free)

If that's not enough info, please ask me questions and I'll do my best to provide more.

---

### Post by matt_symes on 2013-05-06
Thread moved to **Server Platforms**.

---

### Post by Zukaro on 2013-05-06
The only thing I can think of that lets you load a desktop from a server is running a PXE server.  I haven't run one myself as of yet however, but in order to get it to work you need to run your own DHCP server (one that you can customize (from what I've read anyways)).  Generally PXE servers aren't persistent however but you can set them to be persistent.  You also wont need a hard drive in the computers booting via the PXE server (you will need to enable network booting in the BIOS though).

Sorry I can't give you more info; I haven't run one myself yet so I don't know much about them.  I'm also not sure if this would do what you want.

---

### Post by volkswagner on 2013-05-06
Have a read of the [LTSP and Edubuntu]("http://www.edubuntu.org").

---

### Post by koenn on 2013-05-07
> **Zukaro said:**
> The only thing I can think of that lets you load a desktop from a server is running a PXE server. ...
Correct, but the OP could simply be describing y'r average ms windows environment where a user logs on, get's a windows file share as home directory (probably mapped to a drive letter) and/or some other network share,  and loads a user profile from a server (either a real download into local profile folders, or again, from network shares (socalled "redirected" profile folders)

Doing that off a linux server (and assuming windows clients) would involve samba and a bit of tweaking with logon scripts and such, assuming the clients are windows systems. 

"manage updates, settings and everything on the computers from the server" sounds like the OP is looking to mimic WSUS and AD GPOs, for which there are, to my knowledge, no linux solutions  -- it's very much MS server technology aimend ad manageing MS Windows clients --  although there are probably ways to mimic it to some extend. 

Frankly, I don't think it's worth the effort. If you're going to run a Windows environment, use the Windows tools that were designed to that purpose. They mostly work, and will most likely work better than any linux workarounds, especially if the sysadmin in question has '"no idea what [he]'s doing at all".

---

### Post by lykwydchykyn on 2013-05-07
> **koenn said:**
> 
"manage updates, settings and everything on the computers from the server" sounds like the OP is looking to mimic WSUS and AD GPOs, for which there are, to my knowledge, no linux solutions  -- it's very much MS server technology aimend ad manageing MS Windows clients --  although there are probably ways to mimic it to some extend. 



Introducing... [Puppet](https://puppetlabs.com/).

---

### Post by DaimyoKirby on 2013-05-07
Yes, koenn got it right - I'm not looking for PXE (trust me, I've already looked into that, and that isn't a viable option).

Also, although I don't know much about what I'm doing, (I am moderately comfortable with the cli, though) that's kinda the point - this is part of an independent project I'm doing at school (for my own education, not for a grade, so don't start thinking I'm "cheating" or anything) and I don't even know what type of server I would want to set up, which makes it incredibly difficult to even google anything for a starting point.

And it isn't a Windows environment - right now I'm working purely with Ubuntu, since I'm trying to mimic (or upstage, if possible) our school's current Mac server in terms of reliability, efficiency, etc. using only linux (Ubuntu). However, I recognize that this may be difficult (or impossible), depending on the availability of free (as in free beer) linux-based tools, so I'm also open to alternative solutions to what I'm currently trying to set up.

Thanks lykwydchykyn for pointing that out, I'll keep that bookmarked for later.

---

### Post by Cheesemill on 2013-05-08
This is usually done by having all the users home directories on an NFS share on the server, and then all of the client machines have this location mounted at /home. You then need some sort of directory service such as OpenLDAP to store all of the user credentials and provide authentication for all of the clients.

[https://help.ubuntu.com/12.04/serverguide/network-file-system.html](https://help.ubuntu.com/12.04/serverguide/network-file-system.html)
[https://help.ubuntu.com/12.04/serverguide/openldap-server.html](https://help.ubuntu.com/12.04/serverguide/openldap-server.html)

---

