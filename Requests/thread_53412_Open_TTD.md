---
title: "Open TTD"
date: 2005-07-31
forum: Requests
---

### Post by christooss on 2005-07-31
If there is a posibility for porting this fabolus game in to backports. 

It has deb package on surceforge.org but when dpkg -i I get this error

```
Unpacking openttd (from openttd_0.4.0.1-2_i386.deb) ...
dpkg: dependency problems prevent configuration of openttd:
 openttd depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing openttd (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openttd
``` 

You can only solve dependecie problems (hint hint hint)
[Link to sourceforge](https://sourceforge.net/project/showfiles.php?group_id=103924&package_id=111717)

Thanks

---

### Post by Burgundavia on 2005-08-01
The libc bug is due to Openttd being compiled on Sarge, which is binary compatibility with Hoary. 

The problem with OpenTTD is lack of free media files. There was an attempt to get it into Debian (and thus Ubuntu), but that fell over.

Corey

---

### Post by christooss on 2005-08-01
So there is no chance to wver play Openttd on Ubuntu

---

### Post by Burgundavia on 2005-08-01
That is not true. The best way to get it into Ubuntu is to help them get free media files. There is an effort already underway at their forums:

[www.tt-forums.net](www.tt-forums.net)

Corey

---

### Post by christooss on 2005-08-01
[QUOTE=Burgundavia]That is not true. The best way to get it into Ubuntu is to help them get free media files. There is an effort already underway at their forums:

[www.tt-forums.net](www.tt-forums.net)

Corey[/QUOTE]
 Ok I managed to start game with one of tar.gz package on source forge. Thanks anyway.

I still don't get'it what the problem is with files. Is that now they aren't free. I had to ad some of my tranyport tycoon files in data dir. Is this the problem? I will read through the forums and find out more about this problem.

Thanks again

---

### Post by charlieg on 2005-08-01
OpenTTD currently uses the old TT graphics.  So it requires files from a commercial game.  That is why Debian won't absorb it.

---

### Post by Badcel on 2005-08-04
But there could be an universe / multiverse package for ottd, even if it needs files from the original game?

---

### Post by christooss on 2005-08-04
[QUOTE=Badcel]But there could be an universe / multiverse package for ottd, even if it needs files from the original game?[/QUOTE]
 Yes it would help but for now tar.gz version siuts me. No compiling no nothing.

It can be in extras-staging

---

