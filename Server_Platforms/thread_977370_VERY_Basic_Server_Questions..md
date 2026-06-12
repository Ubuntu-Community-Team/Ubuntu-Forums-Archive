---
title: "VERY Basic Server Questions."
date: 2008-11-10
forum: Server Platforms
---

### Post by ShakeyJake on 2008-11-10
Ok, so I'm now at the point where I have 4 machines, Ive had two desktops and a laptop for a while but Ive just been given a not-so-old desktop as my brother upgraded to a new Vista machine. So I think that the new one will become a server. All of the machine will run Ubuntu.

I know its possible to set it up to backup files and act as a torrent client etc. But I was wondering about something else. Whenever I log on to a uni pc (theyre a mix of thin/fat clients), all of my the documents and favourites and files are all there, on 'my' desktop, not mapped on to some server drive somewhere. 

So, is it possible to set up my server so that no matter which of the three clients I log on to (using the same user/password) all of my files in the right place? eg. I would like my music to appear in places->music and have my library in rhythmbox on all of the clients. 

So, all data stored on a server but appearing to the end user to be on their machine, just like an office or uni. Possible?

I know this probably dumb, but Ive never made a server before.


Cheers, 
Jack

---

### Post by HermanAB on 2008-11-10
I think what you want is to network mount the home directory.  This can be done using NFS, but it causes problems if the systems are not highly reliable and on an UPS.  So in a home setting I would advise against that.  It will be more trouble than it is worth.

---

### Post by CrucifiedEgo on 2008-11-10
I think HermanAB has it right.  Windows does this using a domain controller and RUP(Roaming User Profiles).  In Linux, the only way I know to do it is to mount the home directory (/home) over the network using NFS.  I'd say that if the server is on a UPS(and configured to shutdown before the UPS runs out of juice), you're probably okay.

As an aside, the only thing my UPS is used for is to facilitate a graceful shutdown.  If 60 seconds goes by with no AC, i shut my server down.  No point in taunting the happy fun ball, as it were.

---

### Post by Coreigh on 2008-11-10
Well ...
It is true that doing this "full-on" as a roaming profile or desktop would be a lot of work and not really worth it, it would be easy to do a NFS share to store the "big-stuff" music, photo collection documents etc.

Create a share on the server with NFS.
Configure each machine with a local profile (like you already have)
Create a network mount from each computer to the share and store your bulky things on the server.

This will reduce duplication, avoid version problems with documents, and provided you set up a back-up system protect you from lost data due to computer loss or failure.

If you need to access the share from a Windows computer you will need to use samba, but NFS is better faster between Linux machines. 

There are several easy tutorials about NFS sharing on the web. I would google for Ubuntu NFS share.

---

### Post by rustutzman on 2008-11-10
Sounds like a media server setup would do the trick for you. Look into mediatomb (mediatomb.cc) I can access my music, photos, and video from any one of my various machines without using up local storage space.

Russ

---

### Post by ShakeyJake on 2008-11-16
Thanks guys, by the looks of it, mounting /home to the server is exactly what I want to do!

Much appreciated!
Jack.

---

