---
title: "Server: Load gnome from CD?"
date: 2007-06-10
forum: Server Platforms
---

### Post by vbmds on 2007-06-10
I've installed server and now want to install gnome. Simple ah - well here's the catch, the server is currently offline - no internet connection/access.

I do have a desktop cd for ubuntu; same version, so I was wondering if I could source gnome from the CD instead of the usual internet method? 

If this can be done, how would it be done from the server commandline?

---

### Post by craigp84 on 2007-06-10
Hi vbmds,

> source gnome from the CD instead of the usual internet method?

Of course. Pop the CD in the drive, then type the below at the console:

```
sudo apt-cdrom add
```

Hit return when prompted to.

Then you can:

> sudo apt-get update
sudo apt-get install ubuntu-desktop

Or whatever else you wish to install.

-c

---

### Post by vbmds on 2007-06-10
Gave this a try, even reinstalled server with network cable unplugged, but alas apt is only looking for internet sources even through the cdrom has been added. All I get basically is E: unable to get to online repositories... thats paraphrased not actual error text ;)

Its almost as if I need to somehow rebuild the repository list with only the cdrom repository(s) in it.

Any other suggestions?

---

### Post by craigp84 on 2007-06-11
You will see errors because your /etc/apt/sources.list still refers to network repos - we have done nothing to disable those.

You can go disable them just now (just comment them out, when you open the file all will become obvious), or you can just leave them - the errors are reported but you'll still be able to add software from the cdrom.

-c

---

### Post by az on 2007-06-11
> **craigp84 said:**
> Hi vbmds,



Of course. Pop the CD in the drive, then type the below at the console:

```
sudo apt-cdrom add
```

Hit return when prompted to.

Then you can:



Or whatever else you wish to install.

-c

No.  You can do this with the alternate cd, since it is a repository-on-a-disk.  But the Desktop cd is a live cd filesystem, with only a small seperate repo with some tools on it.

You would need to use the alternate cd.

---

