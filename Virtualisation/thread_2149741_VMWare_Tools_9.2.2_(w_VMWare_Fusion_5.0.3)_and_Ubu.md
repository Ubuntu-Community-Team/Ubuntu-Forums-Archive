---
title: "VMWare Tools 9.2.2 (w/ VMWare Fusion 5.0.3) and Ubuntu 13.04 - FIXED"
date: 2013-05-29
forum: Virtualisation
---

### Post by nacholito on 2013-05-29
Here is a patch to get VMWare Tools 9.2.2 (which comes with VMWare  Fusion 5.0.3) working with Ubuntu 13.04 (x64).

This information is based on a few other threads etc. Links at bottom of post.

First download the following files (make sure you save them with the names given):[INDENT]vmwaretools-fix.sh: [http://pastebin.com/k35PzXYU](http://pastebin.com/k35PzXYU)
[/INDENT]
[INDENT]vmtools.inode.c.patch: [http://pastebin.com/2ewxWAun](http://pastebin.com/2ewxWAun)
vmtools.linux-driver.c.patch: [http://pastebin.com/73rJ3316](http://pastebin.com/73rJ3316)[/INDENT]

Create a new directory. Copy into it your "VMwareTools-9.x.x.xxxxx.tar.gz" file, and all of the files above you just downloaded

If needed, do a chmod +x vmwaretools-fix.sh

Then run: ./vmwaretools-fix.sh

This patched vmware tools 9.2.2 successfully for me, and there were no compile errors at all during installation.

Based on  [http://ubuntuforums.org/showthread.php?t=2136277&page=3&p=12630786#post12630786](http://ubuntuforums.org/showthread.php?t=2136277&page=3&p=12630786#post12630786)  and  [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2050666](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2050666)

---

### Post by caligarisdad on 2013-07-10
Just wanted to say thanks for compiling this - it fixed my vmware tools install on Fusion 5.03 with Mint 15 x64.

I did have to run it through dos2unix before I ran it though, cos I got encoding errors:

```
curl [http://pastebin.com/raw.php?i=k35PzXYU](http://pastebin.com/raw.php?i=k35PzXYU) | dos2unix > vmwaretools-fix.sh
```

---

