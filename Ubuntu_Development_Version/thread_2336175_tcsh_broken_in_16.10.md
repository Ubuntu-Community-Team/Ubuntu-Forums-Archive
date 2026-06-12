---
title: "tcsh broken in 16.10"
date: 2016-09-05
forum: Ubuntu Development Version
---

### Post by wgarcia on 2016-09-05
tcsh is a shell (like bash, csh, and so on). Probably not too many use it, I have been using it since before linux existed. 

The point is that the version right now in yakkety is broken, if you press "tab", which you do all the time in this shell since it autocompletes the names of commands and files, tcsh crashes. This is the bug report:

[https://bugs.launchpad.net/ubuntu/+source/tcsh/+bug/1618803](https://bugs.launchpad.net/ubuntu/+source/tcsh/+bug/1618803)

It has been already fixed upstream, where the current stable version does not have it, but I don't know if it will get attention before release so that it get fixed. If anybody is using this shell, please give the above bug a "me too".

---

### Post by sudodus on 2016-09-05
I used it in unix too, long ago ;-)

I tested, and tcsh tab completion works for me in xenial (my main system), and it works in a live session running Lubuntu from the current daily yakkety-desktop-i386.iso (zsynced a couple of minutes ago).

```
lubuntu:~> apt-cache policy tcsh
tcsh:
  Installerad: 6.18.01-5
  Kandidat:    6.18.01-5
  Versionstabell:
 *** 6.18.01-5 500
        500 http://archive.ubuntu.com/ubuntu yakkety/universe i386 Packages
        100 /var/lib/dpkg/status
lubuntu:~> 
```

It is the same version as in xenial. Are you using that version?

*Edit:* I started tcsh from bash. Maybe it would be different, if the terminal window is using tcsh directly.

---

### Post by wgarcia on 2016-09-05
Strange, I have exactly the same version. I see you are in a 32bit system, maybe it's only broken in 64bit.

---

### Post by sudodus on 2016-09-05
I looked at the bug report. What does the following mean?

> InstallationDate: Installed on 2013-11-28 (1006 days ago)
InstallationMedia: Ubuntu 13.10 "Saucy Salamander" - Release amd64 

Is it an old system, do-release-upgraded several times? In that case there might be some old cruft, that is causing your problem. You can test a current daily live amd64 system, to be sure, (I thought it would behave like the i386 version, but I was wrong).

---

### Post by wgarcia on 2016-09-05
Yes, I always do upgrades over existing installations. But in any case the culprit, according to the upstream bug, is a recent change in the glibc library. It is working for me also in xenial with that same tcsh version.

And it is also crashing in another system of mine where I started with 15.10.

---

### Post by sudodus on 2016-09-05
Now I have a live session running Lubuntu from the current daily yakkety-desktop-**amd64**.iso (zsynced a couple of minutes ago, while replying and reading some threads).

And yes, I get a segfault. So the amd64 version is buggy. I will click 'affects me too'.

---

### Post by amd-64 on 2016-09-30
I didn't realize how much I use tcsh and needed all the aliases and shortcuts. 

I grabbed tcsh 6.19 from Fedora rawhide, convert to deb using alien and installed. I also got ncurses-libs_6 and extracted libtinfo.so.6 to  /lib/x86_64-linux-gnu/
Now tcsh works fine and I can tab all I want. Deferring learning more obscure shells to another day. 

Good bye zsh and friends.

---

### Post by ennob on 2016-10-16
It's not such an obscure shell... at least not for me :). Anyway, I have the same problem... Very annoying.

gdb pinpoints the problem. I can't wait until the fix gets pushed out.

> Program received signal SIGSEGV, Segmentation fault.
__GI___rewinddir (dirp=0x6aa008) at ../sysdeps/posix/rewinddir.c:34
34	../sysdeps/posix/rewinddir.c: No such file or directory.


---

