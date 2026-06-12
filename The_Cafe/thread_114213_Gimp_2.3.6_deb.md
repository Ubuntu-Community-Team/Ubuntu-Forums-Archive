---
title: "Gimp 2.3.6 deb"
date: 2006-01-08
forum: The Cafe
---

### Post by kakashi on 2006-01-08
hi all.  i have recently started making deb files the source programs i compile. no i am not very good at it but i am not too bad either. i made this deb for myself (to get the experrince of compiling gimp in deb form and to update my own gimp).

well here is a torrent for it. 
[http://static.thepiratebay.org/downloadtorrent/3429118.torrent/gimp_2.3.6-1_i386.deb.3429118.TPB.torrent](http://static.thepiratebay.org/downloadtorrent/3429118.torrent/gimp_2.3.6-1_i386.deb.3429118.TPB.torrent)


[http://thepiratebay.org/details.php?id=3429118](http://thepiratebay.org/details.php?id=3429118)


please use this the tell me if this works. one problem you might have is that this single deb replaces all the gimp packages installed like a libgimp and others. sorry i have yet to figure out how to make multi-binaries.
PLEASE USE AT YOUR OWN RISK:KS 
. (had to add this since most other guides  and stuff have this :rolleyes: ) 

if this works and is good enough for use then i shall make debs for the cvs version.
edit.
rubinstein confirmed that it does work but you'll hve to rmove 
gimp, gimp-data and libgimp
use this 
```
 apt-get remove --purge gimp gimp-data libgimp2.0
```

---

### Post by kakashi on 2006-01-08
i noticed that the torrent was not working so i uploaded the deb to rapidshar . 
[http://rapidshare.de/files/10635040/gimp_2.3.6-1_i386.deb.html](http://rapidshare.de/files/10635040/gimp_2.3.6-1_i386.deb.html)

---

### Post by rubinstein on 2006-01-08
Had to remove the old gimp, gimp-data and libgimp*, works for me under Dapper Drake.

---

### Post by rwabel on 2006-01-10
works fine, thanks!

---

### Post by kakashi on 2006-01-10
yay my first big package works. wohoo.

---

### Post by TheGrudge on 2006-01-17
Hi,

how did you compile TheGimp! ???
The only message I get is the following:
```
checking for GTK+ - version >= 2.6.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: Test for GTK+ failed. See the file 'INSTALL' for help.
```

I dried to install some developement packages for GTK but it doesn't seem to work. Which packages should I install to get the configure working??

Did you use **checkinstall** or **dh_make** ??

---

### Post by TheGrudge on 2006-01-17
ok ich found all the packages I need, checkinstall is up and running...
this could take a while now...

---

### Post by kakashi on 2006-02-17
[QUOTE=TheGrudge]Hi,

how did you compile TheGimp! ???
The only message I get is the following:
```
checking for GTK+ - version >= 2.6.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: Test for GTK+ failed. See the file 'INSTALL' for help.
```

I dried to install some developement packages for GTK but it doesn't seem to work. Which packages should I install to get the configure working??

Did you use **checkinstall** or **dh_make** ??[/QUOTE]
dh_make. 
i did it the true deibian way. 
guided by the new maintaier's guide.

---

