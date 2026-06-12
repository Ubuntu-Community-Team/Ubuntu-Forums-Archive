---
title: "vmware not working, want to uninstall and can't"
date: 2008-02-07
forum: Virtualisation
---

### Post by mrufino1 on 2008-02-07
Hi, I did a search but can't seem to find exactly my problem, so here goes:
I was trying to get reaper working (recording program for windows) in vmware, so I installed vmware server according to instructions I found online, then installed windows to it, and reaper worked however it wouldn't recognize my recording card. In the end, I wound up installing windows as a dual boot just so I can use my recording software without issues (and when reaper comes out for linux...bye windows). vmware now doesn't start, it attempts to start but just dies. I want to uninstall it, but can't seem to do that. Any ideas? What info do you need to help solve the problem? Thanks-Mark

---

### Post by pointone on 2008-02-08
How are you trying to uninstall it and what error message do you get / what is stopping you from uninstalling?

---

### Post by mrufino1 on 2008-02-08
Hi, I did sudo apt-get remove vmware-server and it says it is not installed so it can't remove it, then I do sudo apt-get remove vmare which says it can't find the package vmware. 
Thanks.

---

### Post by mbsullivan on 2008-02-08
Hi mrufino1,

> I installed vmware server according to instructions I found online

How did you end up installing it? Did you do it by downloading something from VMWare and decompressing it, or did you use the Ubuntu repositories?

> Hi, I did sudo apt-get remove vmware-server and it says it is not installed so it can't remove it, then I do sudo apt-get remove vmare which says it can't find the package vmware.

You could check which packages you have installed that are related to vmware... one way to do this would be to:

```
dpkg --list | grep vmware
```

And then remove these packages.

After doing this, if vmware still appears to be installed, then run:

```
sudo /usr/bin/vmware-uninstall.pl
``` 

This will uninstall vmware, but if you used the Ubuntu repositories to install it, you should try and use them to uninstall it first.

Hope this helps! 
Mike

---

### Post by mrufino1 on 2008-02-08
I used a package I got from vmare's website, so I will try the method you suggested for that. I appreciate the help, I will post again when I get a chance to do this (probably tomorrow).

---

### Post by mbsullivan on 2008-02-08
Hi,

In that case, the uninstall script should be all you need.  Good luck!

Mike

---

