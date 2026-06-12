---
title: "update manager error"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rkrakora on 2012-03-18
Anyone seen this before?

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

I am unable to run the update manager.... running 12.04 beta.

Thanks!
R

---

### Post by Holdolin on 2012-03-18
I'm not seeing this issue.  Just ran the update manager from my beta box, no issues here.

---

### Post by MG&amp;TL on 2012-03-18
What does the command-line version:

```
sudo apt-get update
```

give?

---

### Post by jerrrys on 2012-03-18
MG&TL:  I call your update and raise an rm. :o

in terminal

[FONT=Courier New]sudo rm /var/lib/apt/lists/* -vf

followed by

[/FONT][FONT=Courier New]sudo apt-get update

may get lucky
[/FONT]

---

### Post by oldos2er on 2012-03-18
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by MG&amp;TL on 2012-03-19
> **jerrrys said:**
> MG&TL:  I call your update and raise an rm. :o

in terminal

[FONT=Courier New]sudo rm /var/lib/apt/lists/* -vf

[/FONT][FONT=Courier New]
[/FONT]

Good idea, I need to remember that one.

-v I can see, but -f? Is there some symlinks in there or something?

---

### Post by jerrrys on 2012-03-19
> **MG&TL said:**
> Good idea, I need to remember that one.

-v I can see, but -f? Is there some symlinks in there or something?

The command will work without -vf, but the -vf seems to be a standard reply.

[http://ubuntuforums.org/showthread.php?t=1940877](http://ubuntuforums.org/showthread.php?t=1940877)

---

### Post by MG&amp;TL on 2012-03-19
> **jerrrys said:**
> The command will work without -vf, but the -vf seems to be a standard reply.

[http://ubuntuforums.org/showthread.php?t=1940877](http://ubuntuforums.org/showthread.php?t=1940877)

Fine by me. :)

---

### Post by rkrakora on 2012-03-19
Thanks guys, I'm trying both commands, will update soon!

Seems to have reversed some previous installations.  I've re-run update manager and it recommended a 'partial upgrade'.  

Looks like things are good to go.  Very much appreciated!

---

### Post by jerrrys on 2012-03-20
[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

---

### Post by cariboo on 2012-03-20
> **rkrakora said:**
> Thanks guys, I'm trying both commands, will update soon!

Seems to have reversed some previous installations.  I've re-run update manager and it recommended a 'partial upgrade'.  

Looks like things are good to go.  Very much appreciated!

Do not do a partial upgrade, unless you really know what you are doing, it's better to use:

```
sudo aptitude safe-upgrade
```

in this case so as not to break your installation.

---

### Post by HereInOz on 2012-03-20
I agree with cariboo907.  I had the partial upgrade error scenario, and 

sudo aptitude update 

followed by 

sudo aptitude safe-upgrade 

fixed it on 2 different computers.

---

