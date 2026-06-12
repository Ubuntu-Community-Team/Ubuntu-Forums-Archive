---
title: "No Multiverse for Me"
date: 2006-08-05
forum: Repositories &amp; Backports
---

### Post by Dana on 2006-08-05
I have a new Dapper installation and have been trying for about three days to access the multiverse without success. I get errors such as this:

deb [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:Sub-process](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:Sub-process) gzip returned an error code (1)

deb [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:Sub-process](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:Sub-process) gzip returned an error code (1)
(I can't these to display correctly here)

I restored a default sources.list after trying Automatix and then EasyUbuntu to get Divx capabilities. I'm not getting anywhere with the Multiverse. Current sources.list is"


## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

Thanks... Dana

---

### Post by Jagot on 2006-08-05
I don't know if this is causing the error, but you appear to have put in multiverse in the security section of your repos - I don't believe that there is a multiverse repo for security - just main, restricted and universe.  So you may have multiverse enabled, but you also have a repo which doesn't exist in your sources.list which is why its thowing up the error.  This may be causing your problem.

You may just want to copy over a properly formatted sources.list to your own:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by Dana on 2006-08-05
Thanks, that url was very helpful though I had to follow their most extreme measures to put things right again. I've spent at least 12 hours trying to figure out this problem so I'm pleased. Still fighting to get Divx working in Dapper but now I have access to more resources which should help.

Dana

---

### Post by Jagot on 2006-08-05
You may want to run through this guide with regards to getting media codecs such as DIVX to work:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Dana on 2006-08-05
Yeah, I've been through the guide and as far as I can tell I've installed everything necessary... BUT, I must have missed something. Totem-xine now plays the Divx audio portion but not the video. Same for Gxine. Thinking about taking a shot with Mplayer before I work my way back through what I have done to see if I can find a mistake. 

Dana

---

### Post by Gyrotwister on 2006-08-10
Hi, you're not the first to experience problems with downloading multiverse packages.  There is a work around.  

[http://www.ubuntuforums.org/showthread.php?t=217867](http://www.ubuntuforums.org/showthread.php?t=217867)

---

