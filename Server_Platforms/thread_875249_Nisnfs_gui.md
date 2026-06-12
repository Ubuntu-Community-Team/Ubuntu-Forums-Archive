---
title: "Nis/nfs gui"
date: 2008-07-30
forum: Server Platforms
---

### Post by wilbbe01 on 2008-07-30
I've installed NIS and NFS.  I was told there was an easy graphical way of configuring it.  I see mention of a "Shared Folders" on this forum, but I see nothing of it on my machine.  Does anyone know of a easy to use gui for NIS and NFS?  Or could someone tell me where it is located in Ubuntu's menus.

Thanks.

---

### Post by RealPSL on 2008-08-16
It is not clear what edition of Ubuntu you are running but assuming you are running Desktop you can get there with **System > Administration > Shared Folders**.

This will allow you to share folders using the NFS or SMB (think Windows) protocols. As far as I know there is no graphical user interface for configuring NIS. NIS is old technology and there is not a lot of development taking place with it but there might be one that I just do not know of.

---

### Post by Archaios on 2008-08-18
> **RealPSL said:**
> It is not clear what edition of Ubuntu you are running but assuming you are running Desktop you can get there with **System > Administration > Shared Folders**.


I'm having trouble finding an easy way to share via NFS as well.  There doesn't seem to be a Shared Folders option under System -> Admin...?  Is there another package I should install?

---

### Post by RealPSL on 2008-08-18
What release of Ubuntu are you running?  I am running 7.10 so it might be a little different.

---

### Post by Guilden_NL on 2008-09-14
It's gone in Hardy.  They moved it to Nautilus! (Why???) I decided to nuke Samba since I only have one client with Windows and it runs Linux 98% of the time.  So I pulled Samba and set up NFS with a lot of grumbling under my breath - just very short on time and setting it up via terminal takes me much longer than GUI.

I want to add a suggestion to put it back in, makes no sense to blow it away when it can happily live in Admin where all noobies are going to be exploring anyway.

---

### Post by HermanAB on 2008-09-15
Gee, NFS requires only TWO lines of configuration - one line on the server and one line on the client.  That is why there aren't any wizards for it, since wizards just make it more difficult...

---

### Post by cariboo on 2008-09-15
Have a look at this howto:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

it explains what is needed.

Jim

---

### Post by fadumpt on 2008-11-16
> **HermanAB said:**
> Gee, NFS requires only TWO lines of configuration - one line on the server and one line on the client.  That is why there aren't any wizards for it, since wizards just make it more difficult...

not sure if this the right way to respond to someone's problem, although I see where you are coming from.

I disagree that should not be a GUI because usability should be the first consideration and anything that can help a user to do something easier is always a good thing.  Imagine having to explain to a windows user that is trying to switch that for something as simple as sharing a folder they have to open up a command line and start editing files.  

I'd rather have the ability to do it either way.  Considering the fact that NFS is a much nicer way to share files amongst linux computers, it should be available to any user.

--My two cents

---

### Post by Philio on 2008-11-16
For NFS server you need 1 line in /etc/exports for every directory you want to share, suggest you look at man exports this will explain the options. You will want something like this:

/shared/folder/ NETWORK_ADDRESS/SUBNET(OPTIONS)

In it's most simple form you could probably even scrub the network stuff and option and just specify a share path.

For NFS clients, easiest way is probably to use fstab to mount at boot with something like:

NFS_SERVER_IP:/shared/folder /mount/folder nfs rw 0 0

It really is that simple! There are so many guides for this on Google, just have a look.

---

