---
title: "Can I upgrade without a CD?"
date: 2006-09-08
forum: Server Platforms
---

### Post by linuxpenguin on 2006-09-08
I installed my server a while ago with Ubuntu 5.05.  Now I've set up an SSH connection and want to try an upgrade.
Can I upgrade all the way up to the latest version, even though I have 5.05 installed?  (ie, is there any way to bring it from 5.05 packages up to the 6.06 packages?)  What would be the command to do this?

---

### Post by infoburner on 2006-09-08
it is possible, ive done it on a server remotly myself. however, the prefered method would be with a cd i think, because the last time i did it i ran into some strange dependency problems. i got it working, it was just a bit of a pain. i have done it with no problems as well.

anywho, the first thing to do is edit your /etc/apt/sources.list and change all the "breezy"s to "dapper"s. the easiest way to do that, i think, is to bring up my fav editor: vim
```

sudo vim /etc/apt/sources.list

```
and type 
```

:%s/brezzy/dapper/
:w

```
that should replace all the breezys with dapper, and the :w will save the file. then do this:
```

sudo apt-get update ; sudo apt-get upgrade ; sudo apt-get dist-upgrade

```
and that should do it. note that i typed that all on one line, spereated by ':'. the reason is that its going to take a long time (there are a lot of packages that need to be downloaded), this way you can just type that in and go to lunch or whatever instead of sitting around and typing one line after another as they get done.
post back here if you have any problems.

---

### Post by rastilin on 2006-09-08
I'll have to remember that. But shouldn't you be running "sudo apt-get dist-upgrade" before running "sudo apt-get upgrade". I believe dist-upgrade handles dependencies differently and it is built specifically for upgrading between versions of a distribution?

---

### Post by infoburner on 2006-09-08
> **rastilin said:**
> I'll have to remember that. But shouldn't you be running "sudo apt-get dist-upgrade" before running "sudo apt-get upgrade". I believe dist-upgrade handles dependencies differently and it is built specifically for upgrading between versions of a distribution?

you know, im not really sure which is the right way to do it. thats the way ive done it and has both worked and not worked. :D maybe if i do dist-upgrade first next time i wont run into my dependency problem

---

