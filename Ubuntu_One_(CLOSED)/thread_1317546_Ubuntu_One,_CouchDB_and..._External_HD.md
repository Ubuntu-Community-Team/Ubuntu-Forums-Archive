---
title: "Ubuntu One, CouchDB and... External HD"
date: 2009-11-06
forum: Ubuntu One (CLOSED)
---

### Post by peterson_espacoporto on 2009-11-06
I heard somewhere somehow that CouchDB is powerful and flexible so people could set him up to sync files and other stuff between their own personal servers and even.. devices...

I was thinking: I have an external HD which I use for backup. when I change something in the files from my computer, I take notes of these changes with Tomboy so when I have time I connect the external drive and "syncronize" the whole thing up - basically what U1 does with the cloud; copies the files over, downloads newer ones, if a common file has been deleted here is hence deleted there, etc.

So I thought I could simplify the whole process I do by somehow syncing the files between the external HD and my PC using CouchDB. Would it be possible? Will it be possible, if it isn't now? Is there a way to do it with relative ease now? (I'm not worried about using the terminal at all, I rather like it a lot =] by 'ease' I mean not tons of technical reading and complex config files..)

---

### Post by joshuahoover on 2009-11-09
> **peterson_espacoporto said:**
> I heard somewhere somehow that CouchDB is powerful and flexible so people could set him up to sync files and other stuff between their own personal servers and even.. devices...

I was thinking: I have an external HD which I use for backup. when I change something in the files from my computer, I take notes of these changes with Tomboy so when I have time I connect the external drive and "syncronize" the whole thing up - basically what U1 does with the cloud; copies the files over, downloads newer ones, if a common file has been deleted here is hence deleted there, etc.

So I thought I could simplify the whole process I do by somehow syncing the files between the external HD and my PC using CouchDB. Would it be possible? Will it be possible, if it isn't now? Is there a way to do it with relative ease now? (I'm not worried about using the terminal at all, I rather like it a lot =] by 'ease' I mean not tons of technical reading and complex config files..)

The way CouchDB works in Ubuntu 9.10 in terms of syncing is that it can sync with a CouchDB server running on the Ubuntu One cloud (if you have the Ubuntu One client setup and are using CouchDB) and/or you sync two CouchDB instances (say one on your computer and another CouchDB running on a separate computer) on the same network. I will try to get a quick tutorial up on how to do this second option soon. Look for it at: [http://wiki.ubuntu.com/UbuntuOne/Tutorials](http://wiki.ubuntu.com/UbuntuOne/Tutorials)

Thank you,

Joshua

---

### Post by peterson_espacoporto on 2009-11-09
Thanks! That might be very useful =) I'll keep an eye on it..

---

