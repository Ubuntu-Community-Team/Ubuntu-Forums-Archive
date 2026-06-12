---
title: "Backport Synaptic Update Errors."
date: 2005-06-17
forum: Ubuntu Backports
---

### Post by dmccarney on 2005-06-17
I followed the instructions to add backports to my repo list
but I get the following when starting Synaptic.

```
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
``` 

I added the following two lines to /etc/apt/sources.list...

```
## Main and Universe Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe
``` 

If anyone knows how to fix this I'm all ears.

---

### Post by Seth on 2005-06-17
[QUOTE=dmccarney]I followed the instructions to add backports to my repo list
but I get the following when starting Synaptic.

```
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
``` 

I added the following two lines to /etc/apt/sources.list...

```
## Main and Universe Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe
``` 

If anyone knows how to fix this I'm all ears.[/QUOTE]
 Did you hit Reload?

---

### Post by dmccarney on 2005-06-17
Ahhhh. I'm an idiot. Don't mind me :P I saw an error and figured reloading wouldn't help.

---

### Post by jonatin on 2005-06-18
> I added the following two lines to /etc/apt/sources.list...

```
## Main and Universe Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe
``` 

If anyone knows how to fix this I'm all ears.

Try taking the trailing slashes off the http:// address...

```
deb http://ubuntu-backports.mirrormax.net hoary-backports ..
```

---

