---
title: "Compiz Themer install problem"
date: 2007-04-18
forum: Repositories &amp; Backports
---

### Post by deep-z on 2007-04-18
After some time working with Beryl I decided to try out Compiz. Compiz and all neccessary packages downloaded and installed like a breeze, but then I felt into this:

> 
sudo apt-get install gcompizthemer gcompizthemer-themes compiz-quinn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gcompizthemer is a virtual package provided by:
  emerald 0.2.0~0beryl1
You should explicitly select one to install.
E: Package gcompizthemer has no installation candidate

Same things happen when I try to install cgwd package.
I don't get why it wants to install Beryl Emerald decorator...

Maybe I have selected wrong repository? Any ideas would be highly welcome!

---

### Post by mattymattysidebyeach on 2007-04-20
simply put: the package gwindowdecorator is an alias for the package emerald

it is natural for one to associate emerald with beryl, and not to do so with compiz, since they are distributed as unique software packages, nevertheless... 


[COLOR="RoyalBlue"]**c**ompiz **g**nome **w**indow **d**ecorator[/COLOR] (its old name cgwd) **became** [COLOR="YellowGreen"]emerald[/COLOR], the first window decorator release  for beryl.

here's the rub: 

*fwiw and fyi*
beryl = was new name for "compiz-quinn", soon to be called compiz-extra 
compiz-quinn = fork of compiz aka "compiz-vanilla", soon compiz-core 

compiz and beryl are re-uniting: [http://forum.compiz.org/viewtopic.php?t=761&sid=cfd23e38a805d30e8c75c88f6a5b5e8e](http://forum.compiz.org/viewtopic.php?t=761&sid=cfd23e38a805d30e8c75c88f6a5b5e8e)

emerald is ported back over to compiz:
[http://forum.compiz.org/viewtopic.php?t=700&highlight=emerald](http://forum.compiz.org/viewtopic.php?t=700&highlight=emerald)
----------------------------------------------------------------------------------------------------------------------------------

[SIZE="3"]know that its ok to allow emerald to install, because it IS cgwd, unless you want to use a different decorator, in which case,

know that there are plenty of resources available to you since compiz is a highly active project..[/SIZE]

assuming that you won't miss all the bells and whistles of beryl.you could install the "desktop-effects" package:

*check this thread on compiz/beryl & desktop-effects:[http://ubuntuforums.org/archive/index.php/t-300350.html](http://ubuntuforums.org/archive/index.php/t-300350.html)*

----------------------------------------------------------------------------------------------------------------------------------

---

### Post by deep-z on 2007-04-20
Thank's for such complete reference, man! :)
I allready sorted out the problem and yeah, now compiz is working fine. I configured it with gconf-editor and just upgraded my whole system to Feisty Fawn.

There was the problem with old compiz (compiz crashed with segfaults) plugins right after the upgrade, but I managed to run (as root) gconf-editor and remove all plugins from apps/compiz/options/allscreens plugin branch.

Also removed compiz-extra package at all.

Now it's working just fine, except some of the FX are not working, but as this ir development version issue, I think it's OK to wait for update.

Cheerz! ;)

---

