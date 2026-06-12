---
title: "NFS and Automount direct map"
date: 2007-09-20
forum: Server Platforms
---

### Post by AThomsen on 2007-09-20
Hi!

I have a debian server with some directories exported though NFS.

On my Ubuntu desktop I would like to mount a directory from the server to a folder in my home dir. Putting it in fstab works as expected except that it often doesn't mount on boot. I have to do a "mount -a" later to mount the drives. I figured that automount/autofs is the way to go. And sine I would like one directory on the server to be mapped to a directory in my home dir, I reckon direct maps should be used. I cannot get this to work however. Anyone knows how to pull this off?

---

### Post by James79 on 2007-09-22
> **AThomsen said:**
> Putting it in fstab works as expected except that it often doesn't mount on boot. 

"Often" - as in sometimes it works and sometimes no?

What does your fstab line look like?

I take it the debian server is always up and running?

Just thinking out loud... :)

---

### Post by AThomsen on 2007-09-22
Hi, 

I haven't really checked if it EVER works on boot-up. I just usually do an mount -a just to be shure :)  The desktop connect though wireless network so that might be the reason.

The debian server is always on.

This is a line from my fstab:
```

192.168.1.10:/srv/musik /home/anders/musik   nfs user,rw,soft  0 0

```

---

### Post by James79 on 2007-09-22
Ahhh you're wireless. The plot thickens :)

Are you using networkmanager by any chance? Seems to me when I used to use it, it would only be loaded once the desktop was started up. Which meant that fstab was already processed and would have failed even before the network was up.

I eventually switched to putting my wireless settings directly into /etc/network/interfaces and disabling networkmanager altogether, which I found to be less flexible (as it's hard coded) but also far more reliable. 

That might solve you problem assuming my assumptions are correct ;)

---

