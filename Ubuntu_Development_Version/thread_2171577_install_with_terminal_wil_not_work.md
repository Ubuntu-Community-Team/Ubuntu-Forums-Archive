---
title: "install with terminal wil not work"
date: 2013-08-31
forum: Ubuntu Development Version
---

### Post by kaj_rumpff on 2013-08-31
hello,
i've been started wirh jusing ubuntu,
i have update it to 13.10 but...
if i try to install (as exaple: ) wine with this code:[PHP]sudo apt-get install wine1.4[/PHP] and i type my password it say's: [PHP]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/PHP]

so i stuck,:confused:
so, can you help me?

---

### Post by nerdtron on 2013-08-31
Have you tried to restart?
Try
```
 [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**rm**[/COLOR] [COLOR=#000000]**/**[/COLOR]var[COLOR=#000000]**/**[/COLOR]lib[COLOR=#000000]**/**[/COLOR]apt[COLOR=#000000]**/**[/COLOR]lists[COLOR=#000000]**/**[/COLOR]lock 
```

---

### Post by kaj_rumpff on 2013-09-01
> Have you tried to restart?
Try
     Code:
      [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**rm**[/COLOR] [COLOR=#000000]**/**[/COLOR]var[COLOR=#000000]**/**[/COLOR]lib[COLOR=#000000]**/**[/COLOR]apt[COLOR=#000000]**/**[/COLOR]lists[COLOR=#000000]**/**[/COLOR]lock 
i've try it out now but now he say's:E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

so i entered that and he say's a lot: Setting up sandboxgamemaker (2.7.1+dfsg-2build1) ...
Cleaned old data
--2013-09-01 11:54:51--  [http://sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip](http://sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip)
Resolving sandboxgamemaker.com (sandboxgamemaker.com)... 173.236.241.215
Connecting to sandboxgamemaker.com (sandboxgamemaker.com)|173.236.241.215|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip](http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip) [following]
--2013-09-01 11:54:52--  [http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip](http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip)
Resolving [www.sandboxgamemaker.com]("http://www.sandboxgamemaker.com") ([www.sandboxgamemaker.com]("http://www.sandboxgamemaker.com"))... 173.236.241.215
Reusing existing connection to sandboxgamemaker.com:80.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

replace PlatinumArtsSandbox2.7.1/bin/jpeg.dll? [y]es, [n]o, [A]ll, [N]one, [r]ename: 

but what should i awnser???

---

### Post by newb85 on 2013-09-01
Something else was already installing or updating.  The system is designed to prevent your trying to run two instances of dpkg at once (a very bad idea), hence the /var/lib/dpkg/lock mechanism.  When you deleted that file, you interrupted the dpkg that was already in progress.

Did you have Software Center, Synaptic, Software Updater, or another instance of apt-get or dpkg running when you tried to install wine?


As a side note, being such a beginner, you probably should be using a stable release, not a beta release.

---

### Post by Rob Sayer on 2013-09-01
> **newb85 said:**
> ... As a side note, being such a beginner, you probably should be using a stable release, not a beta release.

That's what I was thinking as well.  In fact I'd only install wine (or anything else) from beta tested ubuntu repositories if I were you.  Ie. the standard settings in software centre.  

Actually I's also recommend installing synaptic package manager and learning how to use it.  It's the best way to install programs I've found.  It'll use the same fefault software sources as ubuntu software centre, since they're both just graphical interfaces for apt anyway.

---

### Post by Frogs Hair on 2013-09-01
***Moved to Ubuntu +1***

---

