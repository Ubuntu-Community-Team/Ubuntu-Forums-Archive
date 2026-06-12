---
title: "Ktorrent 2.0 is out."
date: 2006-08-09
forum: The Cafe
---

### Post by GarethMB on 2006-08-09
I'm trying to build the source now. I'll post a .deb if i'm successful.
The Release Client was great, so i'm guessing the final will also be spankingly good.

---

### Post by GarethMB on 2006-08-09
I've made a .deb. No promises, this is the first time i've shared anything i've built from source. [http://rapidshare.de/files/28757308/ktorrent-2.0i386.deb.html](http://rapidshare.de/files/28757308/ktorrent-2.0i386.deb.html)

I couldn't install using sudo spkg -i ktorrent2.02i386.deb as i needed to overwrite some file :S so i used 

```
sudo dpkg -i --force-all ktorrent-2.0i386.deb
```

If anyone does install it. Let me know how it is.:idea:

---

### Post by irober02 on 2006-08-12
I've just installed your package and it seems to have worked. Thanks. :-)

I was a bit scared  of the force install option but I did it anyway and it seems to be OK.

I had tried compiling my own ktorrent2 but its configure script failed:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

Did you have that problem? How did you fix it? (I thought I'd installed all the dev packages I need -perhaps I've missed something)

bye

ian

---

### Post by flaak_monkey on 2006-08-13
how would you guys compare this to Azereus? I have always used it and found none better. But i would like an opion on Ktorrent.

---

### Post by NeoChaosX on 2006-08-13
Gareth: The reason your package needs a force install is because it doesn't replace the default ktorrent package in Ubuntu; rather it installs as ktorrent-2.0, completely seperate from the Ubuntu package. Could you try repackaging the deb so it replaces, and not conflicts with, the current KTorrent package?

---

### Post by GarethMB on 2006-08-13
> **irober02 said:**
> I've just installed your package and it seems to have worked. Thanks. :-)

I was a bit scared  of the force install option but I did it anyway and it seems to be OK.

I had tried compiling my own ktorrent2 but its configure script failed:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

Did you have that problem? How did you fix it? (I thought I'd installed all the dev packages I need -perhaps I've missed something)

bye

ianI have had this problem before, you need something like xlibs-dev or libx-dev
> **flaak_monkey said:**
> how would you guys compare this to Azereus? I have always used it and found none better. But i would like an opion on Ktorrent.Azureus never works well on Ubuntu for me. I always have problems with sticky popups etc. Ktorrent is pretty fully featured as of 2.0 and in my opinion the best compromise of features and usuability at present.
> **NeoChaosX said:**
> Gareth: The reason your package needs a force install is because it doesn't replace the default ktorrent package in Ubuntu; rather it installs as ktorrent-2.0, completely seperate from the Ubuntu package. Could you try repackaging the deb so it replaces, and not conflicts with, the current KTorrent package?
I can try. Do you know how to do it?

---

### Post by CronoDekar on 2006-08-13
> **NeoChaosX said:**
> Gareth: The reason your package needs a force install is because it doesn't replace the default ktorrent package in Ubuntu; rather it installs as ktorrent-2.0, completely seperate from the Ubuntu package. Could you try repackaging the deb so it replaces, and not conflicts with, the current KTorrent package?

I was thinking that too, but I compiled from source and named the package ktorrent, and it still needed a --force-overwrite to work.

Gareth: Supposing you make the deb with checkinstall, one of the options will be something like "Package Name" and will default to ktorrent-2.0.  Hit the appropriate number and make it ktorrent.

---

### Post by stoeptegel on 2006-08-13
You might come away with replacing the "x-bittorrent.desktop" file with the one out of kdelibs. Not sure though.

---

### Post by atrus123 on 2006-08-13
> **flaak_monkey said:**
> how would you guys compare this to Azereus? I have always used it and found none better. But i would like an opion on Ktorrent.

Ktorrent is the best torrent manager, period (and I don't even like KDE).  Azereus provides about the same level of control, but it's slower and clunkier, and it seems to argue with Ubuntu from time to time.

However, I usually just use bittorrent.

---

### Post by ivasic on 2006-08-21
Fresh 2.0.1 release introduces several bugfixes for 2.0 series as well as some performance improvements.

Grab the sources&packages at [www.ktorrent.org](www.ktorrent.org)

---

### Post by jdong on 2006-08-21
ktorrent 2.0 is in Edgy. Package backports cleanly to Dapper, so please build it that way. The packages posted on ktorrent's website also look fairly safe, though they are generated with checkinstall.

---

### Post by stoeptegel on 2006-08-29
Hey guys, i just noticed that KTorrent 2.0.2 is out.

---

### Post by jdong on 2006-08-29
[https://launchpad.net/distros/ubuntu/+source/ktorrent/+bug/58139](https://launchpad.net/distros/ubuntu/+source/ktorrent/+bug/58139)

Noticed it, already filed a request to get it into Edgy and ready to backport.

---

### Post by closet geek on 2006-08-30
2.0.2 is a necessity *waits*

cg

---

### Post by GarethMB on 2006-08-30
If anyone can't wait, I've built it. I've called it ktorrent, so in theory it should replace the version in the repos, but if it doesn't you will need to use sudo dpkg -i --force-overwrite. It shouldn't do any harm.

[http://www.yousendit.com/transfer.php?action=download&ufid=7A0AD50871D6929E](http://www.yousendit.com/transfer.php?action=download&ufid=7A0AD50871D6929E)

---

### Post by closet geek on 2006-08-30
Thanks, it installed fine but the bug is still present for me. Downloads of seemingly any torrent just keeps flicking between 3-6Kb/s and 0Kb/s. It can never seem to keep a consistent speed/connection. All my port forwarding is working fine, other clients work fine.

Grrrr.

cg

---

### Post by GarethMB on 2006-08-30
What ports are you using?

---

### Post by closet geek on 2006-08-30
Why do you ask?

cg

---

### Post by Christmas on 2006-08-30
KTorrent 2.0.1 and 2.0.2 both give me some error at the "make" command, even though I compiled and installed GMP.

---

### Post by GarethMB on 2006-08-30
> **closet geek said:**
> Why do you ask?

cgI thought perhaps you might be using a port know for file sharing and 
my be suffering from ISP bandwith shaping. Or perhaps antoher program is using the port. If you don't want to tell me it doesn't matter.

---

### Post by closet geek on 2006-08-30
> **GarethMB said:**
> I thought perhaps you might be using a port know for file sharing and 
my be suffering from ISP bandwith shaping. Or perhaps antoher program is using the port. If you don't want to tell me it doesn't matter.

No harshness intended I was just curious as to why you were asking. As I say, BT is running fine for me with other clients, even uTorrent via wine. It seems there is still a bug in even this latest kTorrent release. I will look into filing a but report.

cg

---

### Post by ivasic on 2006-10-11
Third bugfix release to 2.0 series.

Dapper packages & sources are available on [www.ktorrent.org](www.ktorrent.org) 
Official dapper/edgy packages will be available on repositories soon.

---

