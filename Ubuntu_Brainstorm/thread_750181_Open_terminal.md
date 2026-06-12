---
title: "Open terminal"
date: 2008-04-09
forum: Ubuntu Brainstorm
---

### Post by Danijel Snajder on 2008-04-09
I cant find anywhere and, so i will post it as new thread.

Cant believe that no-one mention **nautilus-open-terminal**, this thing is so small and has to be included in ubuntu, this is first thing i ever install after ubuntu and drivers. And use it everyday, minimum 50-times a day. And it can save lot of time. You work something and if you need terminal just right click and it open terminal in this place.

You dont need to open terminal and type cd 100x times to go to some place:
(cd, ls, cd xx, ls, cd xy, ls, cd yy, ls, cd zz,
or cd /xx/xy/yy/zz/ if you know exactly where you need to go)
and this can be especialy useful for newbies.

---

### Post by smartboyathome on 2008-04-09
Actually, it is included in hardy as far as I know (came with my install).

---

### Post by xelapond on 2008-04-09
How big is it?  They could same a few bytes if they used a simple bash script in the nautilus scripts area.

---

### Post by CarpKing on 2008-04-10
> **xelapond said:**
> How big is it?  They could same a few bytes if they used a simple bash script in the nautilus scripts area.

I think that's what it is, except it gets globally installed.

---

### Post by Danijel Snajder on 2008-04-10
> **smartboyathome said:**
> Actually, it is included in hardy as far as I know (came with my install).

Wuhu =D>

---

### Post by nhandler on 2008-04-10
I have it installed on gutsy, but I rarely use it. I normally have a terminal open at all times. Since most of my scripts/files are in my home directory (or 1 folder down from there), I don't need to cd much. For the few times that I do need to change directories, I just use cd and tab autocompletion. That enables me to switch much faster than having to open the directory with nautilus, right click, and then select the open in terminal option. Finally, I can always get to a terminal by hitting Ctrl+Alt+F1-6.

---

### Post by 3rdalbum on 2008-04-11
I use the Open In Terminal extension ALL the time!

Also, the Open As Administrator can be useful (nautilus-gksu).

As far as I know, they are not preinstalled on Hardy - I installed the beta for a friend and I know the extensions weren't present. I guess that shows how ubiquitous they are, that people install them without even remembering :-)

---

### Post by myle on 2008-04-11
```
#!/usr/bin/perl -w
#
# Open terminal here
#
# Nautilus script that opens a gnome-terminal at the current location, if it's
# a valid one. This could be done in shell script, but I love Perl!.
#
# 20020930 -- Javier Donaire <jyuyu@fraguel.org>
# http://www.fraguel.org/~jyuyu/
# Licensed under the GPL v2+
#
# Modified by: Dexter Ang [thepoch@mydestiny.net]
# 2003-12-08: Modified for Gnome 2.4
#		- Added checking if executed on Desktop "x-nautilus-desktop:///"
#		  so that it opens in /home/{user}/Desktop

use strict;

$_ = $ENV{'NAUTILUS_SCRIPT_CURRENT_URI'};
if ($_ and m#^file:///#) {
  s/%([0-9A-Fa-f]{2})/chr(hex($1))/eg;
  s#^file://##;
  exec "gnome-terminal --working-directory='$_'";
}

# Added 2003-12-08 Dexter Ang
if ($_ == "x-nautilus-desktop:///") {
  $_ = $ENV{'HOME'};
  $_ = $_.'/Desktop';
  exec "gnome-terminal --working-directory='$_'";
}


```

---

