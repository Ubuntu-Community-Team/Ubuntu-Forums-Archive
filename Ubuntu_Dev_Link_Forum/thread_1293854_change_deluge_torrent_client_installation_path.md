---
title: "change deluge torrent client installation path"
date: 2009-10-17
forum: Ubuntu Dev Link Forum
---

### Post by TheOne...more on 2009-10-17
hi,

i would like to know how to change the installation path of bittorrent client deluge. i'm installing 1.1.9 from source as my ubuntu is an old release. i have an earlier version already installed in my system, but i wanted to try the new one and i wanted to leave my current version intact at the same time.

thanx

---

### Post by s3a on 2009-10-17
I don't know how to use it unfortunately :( but **stow** allows you to compile programs that you install from non-binary files and allows the programs to be easily removed by storing them in it's own folder, you can even remove it using a certain command and stuff like that. I wish I knew how to use it though. Fortunately I can make .debs :)

---

### Post by TheOne...more on 2009-10-18
hi,

thanx for your response s3a, i red the manual for stow, and i tried it. but it seems that stow is some form of a primitive package manager. it doesn't perform compile or configure on it's own, but rather you instruct the program you want to compile to locate it's directory tree under the stow directory, then invoke stow to create symlinks to this program directory [http://www.gnu.org/software/stow/manual.html#SEC7](http://www.gnu.org/software/stow/manual.html#SEC7).

deluge is different in that it doesn't use neither a configure script and consequently nor a make script. it has a python script called install.py that does the job. i tried to locate any line inside any file through all the deluge source tree that explicitly points to the installation location but no use.

i changed directory to the source root, then issued the command

```
grep -rie usr/lib -e usr/bin *
```
and the output wasn't what i wanted to read.

it seems that the installation location is implicitly instructed inside the install.py script or inside another script but i don't know for sure, so i would appreciate any help or any suggestions.

thanx

---

