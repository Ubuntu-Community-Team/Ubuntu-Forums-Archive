---
title: "naim 0.11.8-1"
date: 2006-02-22
forum: Requests
---

### Post by jchau on 2006-02-22
I am requesting that naim 0.11.8-1 be backported for Breezy.  

The current version (0.11.8-1) is available for Dapper.  [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=naim](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=naim)

```
apt-get build-dep naim
``` works and gets gawk for me.  
```
sudo apt-get source -b naim
``` spits out > dpkg-deb: building package `naim' in `../naim_0.11.7.3.1-1_i386.deb'. but this command builds the wrong version for me. I am not sure how to force it to get (0.11.8-1).  

This package does not start with "lib" and I have no reason to believe a good build will ruin the system.  

As far as I can tell, it did not make any changes to my interpreters.  

The version of naim currently available seems to be unable to connect to aim (see [http://www.ubuntuforums.org/showthread.php?t=134889](http://www.ubuntuforums.org/showthread.php?t=134889) ).  The new version seems to have a fix:> 2005-10-02  &#8226;  naim 0.11.8 released
 
AOL discontinued the TOC 1 service that naim versions 0.10.0 through 0.11.7.3.1 used. Joshua Wise has modernized naim's TOC protocol driver to operate with the newer TOC 2 service, and this release incorporates his changes. from [http://naim.n.ml.org/download](http://naim.n.ml.org/download) .  

Thank you!

---

### Post by jchau on 2006-02-24
From: [http://ubuntuforums.org/showthread.php?t=123241](http://ubuntuforums.org/showthread.php?t=123241)
[QUOTE=Mez]I'm hopefully going to be having a meeting at some point with one of the launchpad developers.... until then - please mail requests to [email]ubuntu-backports@lists.ubuntu.com[/email] with a subject line starting with [REQUEST] (if you're not signed up a it'll nd dont use this tag in the subject, it'll get put on hold till I get round to accepting the email)
__________________
Regards,
Mez
Backports Lead & MOTU [/QUOTE]

I'm not on [email]ubuntu-backports@lists.ubuntu.com[/email] . Can someone on the list help me by emailing my request? Thanks. 

Note: if you do decide to email my request, please post a reply here so other users do not submit multiple identical requests on my behalf.

---

### Post by Hezekiah on 2006-02-25
Just so you know, you need to add a Dapper deb-src line to your /etc/apt/sources.list file in order to backport a deb as you described above.  If you do so, and repeat the steps you followed to build 0.11.7 it should work properly for you.  I've done the same thing to make personal backports of Vim and f-spot.

Good luck!

---

### Post by jchau on 2006-02-25
Thanks. It works.  

I added to /etc/apt/sources.list
```
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
```

then I ran:
```
sudo apt-get build-dep naim
sudo apt-get source -b naim
sudo dpkg -i naim_0.11.8-1_i386.deb
```

naim can connect now! Yay! It seems to work so far! (a little slow on startup though. but it works.)

If I want to be able to uninstall my package to use the one from backports later, can I safely delete my naim_0.11.8-1_i386.deb? Or do I need it in the future to do stuff with the package?

---

### Post by Hezekiah on 2006-02-25
As far as I know, once/if this ends up in Backports you can just delete your locally created .deb file.  There shouldn't be any need for it, unless the backports version doesn't work for you.

---

