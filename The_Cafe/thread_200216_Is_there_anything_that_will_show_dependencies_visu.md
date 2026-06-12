---
title: "Is there anything that will show dependencies visually, like a tree?"
date: 2006-06-19
forum: The Cafe
---

### Post by K.Mandla on 2006-06-19
This might be stupid, but I'd like to be able to see what dependencies a package has, and its subdependencies and so forth. Preferably like a tree, with the subdependencies branching off. 

It probably sounds bizarre. I thought perhaps someone had drawn up something like that already, but I'm at a loss to find anything. Packages.ubuntu.com is useful, but not very helpful for this, and neither is *aptitude show*.

Any tips? Has it been done?

---

### Post by aysiu on 2006-06-20
I've never heard of such a thing. I know you can right-click a package in Synaptic and see its dependencies before you install it, but it won't then show you the dependencies of those dependencies.

Can I ask what this is for?

---

### Post by nalmeth on 2006-06-20
Just for kicks I'd imagine. I think it would be cool to see.

Something like this, but interactive, and individualized?

[http://www.linux-dt.com/](http://www.linux-dt.com/)

---

### Post by RAV TUX on 2006-06-20
[quote=aysiu]I've never heard of such a thing. I know you can right-click a package in Synaptic and see its dependencies before you install it, but it won't then show you the dependencies of those dependencies.

Can I ask what this is for?[/quote]

I may be mistaken, but I remember running across a package that had this description, recently.

---

### Post by aysiu on 2006-06-20
[QUOTE=yozef]I may be mistaken, but I remember running across a package that had this description, recently.[/QUOTE]
By all means, if you find it again, post it. I'd really be interested in seeing this.

---

### Post by RAV TUX on 2006-06-20
[quote=aysiu]By all means, if you find it again, post it. I'd really be interested in seeing this.[/quote]

I will if I ever run across it again, it was probably on a night much like tonight 2:39am EST.

---

### Post by K.Mandla on 2006-06-20
[QUOTE=aysiu]Can I ask what this is for?[/QUOTE]
I was running into the same old problem, trying to help someone without an Internet connection to install a package on their computer. This package depended on this one, which again depended two others, and those depended on eight others, and so forth.

It's possible to track all the dependencies through packages.ubuntu.com then download them one by one, but it's long and tedious. I was thinking that some sort of dependency tree would at least give you a visual idea what you were looking for, and what linked to what.

Anyways, I'm not a developer and I don't know word one about how all this stuff works, so perhaps something like this isn't feasible. If nothing else it would be neat to see. And instructive, which is always good. :cool: 

[quote=nalmeth]Something like this, but interactive, and individualized?

[http://www.linux-dt.com/](http://www.linux-dt.com/)[/quote]
That's the idea. If I could get that for any package it would be perfect ... and smaller, I imagine, but that would depend on the package.

---

### Post by Kvark on 2006-06-20
[QUOTE=K.Mandla]I was running into the same old problem, trying to help someone without an Internet connection to install a package on their computer. This package depended on this one, which again depended two others, and those depended on eight others, and so forth.[/QUOTE]
If your friend uses a live CD and a usb memory to get the packages then do:
```
sudo **-d** apt-get install package
```
The -d isn't neccessary but saves time by only downloading and not installing the packages on the live session.

Then copy all the downloaded debs in /var/cache/apt/archives/ to the usb memory.

That'll get all needed packages that the live CD doesn't have and hopefully your friend's system has everything the live CD has.

But if your friend uses a Windows system to get the debs then I don't know how to solve it. Going through a tree display downloading the debs one by one as you want to would be tiresome. Perhaps the packges.ubuntu.com website could add a javascript that starts downloads of all needed packages so you only have to click yes on a lot of pop up questions.


The best solution would be a DVD or two with all debs from main, universe and multiverse. Then your friend could install anything they want without needing another system.

---

### Post by jasay on 2006-06-20
apt-rdepends maybe (it's in the universe repo)?

```
$ apt-rdepends -p grep
Reading package lists... Done
Building dependency tree... Done
grep
  PreDepends: libc6 (>= 2.3.4-1) [Installed]
libc6
  Depends: locales (>= 2.3.11) [Installed]
locales
  Depends: belocs-locales-bin (>= 2.3.5-5ubuntu1) [Installed]
belocs-locales-bin
  Depends: libc6 (>= 2.3.4-1) [Installed]
  Depends: locales [Installed]

```

---

### Post by Kvark on 2006-06-21
[QUOTE=jasay]apt-rdepends maybe (it's in the universe repo)?[/QUOTE]
That is awesome!

Do this to get a graphical tree (it looks more like a web though) of the dependancies:
```
apt-rdepends -d package | springgraph > file.png
```
The attached image shows Firefox's dependancies as an example.

This is interesting and cool.  :grin:
*Tries to decide what packages' dependancies to take a look at first*

---

### Post by andrecasteliano on 2006-06-21
cool.

---

### Post by K.Mandla on 2006-06-21
Very cool. That's exactly what I wanted. Thanks, gang.

:wink:

---

