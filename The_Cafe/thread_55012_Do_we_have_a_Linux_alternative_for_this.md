---
title: "Do we have a Linux alternative for this?"
date: 2005-08-07
forum: The Cafe
---

### Post by Hanj on 2005-08-07
If you've every tried to find the largest files to clean up a cluttered hard drive, you know something like [this](http://www.win.tue.nl/sequoiaview/) can save a lot of time. Really cool idea IMHO.

Now my question is, is there a linux (preferably open source) alternative for this little tool? The closest thing I can find is [this java library](http://sourceforge.net/projects/treemap/). If no one can point me to a linux program like this, I think I'll write one myself

---

### Post by SGC on 2005-08-07
If you are using kubuntu, there is [KDirStat](http://kdirstat.sourceforge.net/), it is in the universe repository:
apt-get install kdirstat

---

### Post by BWF89 on 2005-08-07
Those look pretty cool.

---

### Post by macgyver2 on 2005-08-07
SGC slipped in and posted while I was looking in Synaptic because I can never remember the name of the program even though it's come up in conversation several times in the past few weeks for me!  :)

[QUOTE=Hanj]If no one can point me to a linux program like this, I think I'll write one myself[/QUOTE]
I say got for it...unless you use KDE or you don't mind that KDirStat is going to want you to install about 8 or 10 dependencies, some of them KDE library packages. 

For a different layout idea, take a look at [this]("http://www.steffengerlach.de/freeware/"). I've seen this in action on windows and I think the circular chart looks neat. The author provides Delphi sources...but I know nothing about Delphi and Linux.

---

### Post by Kyral on 2005-08-07
I believe there is also a program called File Light in the repos that does the same thing and doesn't rely on the KDE Libs

---

### Post by macgyver2 on 2005-08-07
[QUOTE=Kyral]I believe there is also a program called File Light in the repos that does the same thing and doesn't rely on the KDE Libs[/QUOTE]
Still wants me to install pretty much the same stuff that KDirStat wants.  :neutral:  But on the plus side it does have the look I prefer!  Thanks for the heads up.

---

### Post by dcraven on 2005-08-07
There is a little program called [Baobab](http://www.gnomefiles.com/app.php?soft_id=1002) that does something similar, but focuses on directories, not the files. If you wanted to write something that does files too may I suggest contacting the Baobab author? It's a fairly new project from what I can tell and may be easily extended.

Have a look, the author might just love the help!

Cheers,
~djc

---

### Post by sooqing on 2005-08-07
erm.. read somewhere u can actually uses tools like du, find, etc.. to find the largest files?

---

### Post by Hanj on 2005-08-07
> KDirStatThat's what I'm talking about. Too bad it's KDE   :?  Same goes for Filelight. Gnome should have a program for this.

> There is a little program called Baobab that does something similarSeems to me it only creates a list over the directories and sorts them after size? Guess you could extend it with a treemap though. I'll take a look at the source code, and maybe contact the author.

> erm.. read somewhere u can actually uses tools like du, find, etc.. to find the largest files?Yeah, you could of course. But these treemaps provide a much better overview. Plus they look cool :)

---

### Post by drizek on 2005-08-07
open a folder in konqueror

view- filesize view

i think that is what you are looking for. its alredy included in kibuntu.

Edit: screenie [[IMG]http://img280.imageshack.us/img280/7426/snapshot21bk.th.png[/IMG]](http://img280.imageshack.us/my.php?image=snapshot21bk.png)

---

### Post by Hanj on 2005-08-07
Looks like there are several KDE tools for this. Haven't seen any for gnome yet though.

---

### Post by wmcbrine on 2005-08-08
There's an old generic X tool to do this, but I can't remember the name. Generally I just do:

 du | sort -n | less

---

### Post by jnoreiko on 2005-08-08
Well... this is on windows, but it's free :D (but only as in beer)

[http://www.jgoodies.com/freeware/jdiskreport/](http://www.jgoodies.com/freeware/jdiskreport/)

---

### Post by Hanj on 2005-08-08
Well, I've been talking a little to the author of Baobab, and I think I am going to write a module for his program to view directories as treemap diagrams. Baobab also has some integration into Nautilus (through a bash script), and hopfully this can be improved in the future.

If I ever finish this module, I'll post here to get some opinions on it.

---

### Post by Stormy Eyes on 2005-08-08
[QUOTE=wmcbrine]There's an old generic X tool to do this, but I can't remember the name. Generally I just do:

 du | sort -n | less[/QUOTE]

I do the same, though I throw the --si switch onto du to get my sizes in units I'm used to, so it looks like this:

```
du --si | sort -n | less
```

---

### Post by wmcbrine on 2005-08-12
[QUOTE=Stormy Eyes]I do the same, though I throw the --si switch onto du to get my sizes in units I'm used to, so it looks like this:

```
du --si | sort -n | less
```[/QUOTE]
The problem with that is, it breaks the numerical sort -- k, M and G get mixed together.

---

