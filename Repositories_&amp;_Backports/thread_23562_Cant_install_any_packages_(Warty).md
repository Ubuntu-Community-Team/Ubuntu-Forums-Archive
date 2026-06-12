---
title: "Cant install any packages (Warty)"
date: 2005-04-02
forum: Repositories &amp; Backports
---

### Post by deviant03 on 2005-04-02
Just tried upgrading to Hoary but my wireless wouldnt work so I'll wait for the official release. I reinstalled Warty but now I cant seem to get anything to install through synaptic - so far Ive tried kaffeine, mplayer, xine, vlc etc.

[IMG]http://home.nyc.rr.com/deviant03/Screenshot.png[/IMG] 

My list:

# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

#deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 

# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports main universe multiverse restricted  
# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-extras main universe multiverse restricted

---

### Post by askreet on 2005-04-02
Did you reload after changing sources.list?

-skreet

---

### Post by deviant03 on 2005-04-02
Ack, nevermind. Seem to be losing my head today :P, deleted some repositories by accident.

---

