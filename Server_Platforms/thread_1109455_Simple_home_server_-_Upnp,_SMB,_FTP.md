---
title: "Simple home server - Upnp, SMB, FTP"
date: 2009-03-28
forum: Server Platforms
---

### Post by oxymoron on 2009-03-28
Hi,

I'm looking resurrect some old hardware in the loft to create a linux home server.

I think its an Asus K8N-E, can anyone recall if its gonna be problematic?

Anyway, I have been playing about with FreeNAS today on a spare Dell optiplex. It is truely an awesome piece of software. I got Upnp, smb and ftp setup in little over 20 mins :)

My only issue is usenet, I did get sabnzbd 0.4.3 working, but couldn't gtet it upgraded to 0.4.8 despite my best efforts :p

Is there anything else to try? or should I be happy with FreeNAS and an outdated Sabnzbd?

My only concern is that this K8N-E motherboard isn't compatible with BSD so I need to look at linux solutions as well.

I'm not scared of the command line, I need something I can setup once then forget about it, i.e I can't be spending countless hours bug fixing.

---

### Post by falconed7 on 2009-03-28
If you like FreeNAS then also checkout ClarkConnect, it has more features than FreeNAS and also has a nice WebGUI for admin purposes.

I myself use FreeNAS and have also used Ubuntu Server Edition 8.04.2 and found both to be great. I'm enjoying FreeNAS more because for what I need (basic file sharing) it's a lot less time to setup.

Your motherboard should be fine. Hope this helps.

---

### Post by andrew.46 on 2009-04-17
Hi oxymoron,

> **oxymoron said:**
> 
My only issue is usenet, I did get sabnzbd 0.4.3 working, but couldn't gtet it upgraded to 0.4.8 despite my best efforts

The best lightweight proxy nntp server is leafnode 2, if you are after a caching server that can distribute news for up to 2 dozen or so people? If this is what you are after you are in luck as I have written a much neglected guide to installing and configuring leafnode 2 on ubuntu:

[http://ubuntuforums.org/showthread.php?t=676837](http://ubuntuforums.org/showthread.php?t=676837)

Just ignore the whole slrn thing :-).

All the best,

Andrew

---

