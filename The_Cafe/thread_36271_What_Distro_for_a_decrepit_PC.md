---
title: "What Distro for a decrepit PC?"
date: 2005-05-22
forum: The Cafe
---

### Post by thorN on 2005-05-22
Alright gang,

I'd like to hear your recommendations for a Distro or alternative Window manager for Ubuntu for a crummy old PC.

This is the sorta thing I'd normally like to investigate myself, but I'm strapped for time.

What I got:
300 MHz Intel
64MB RAM
2GB

What I need:
OpenOffice.org (or something which can interoperate with microsoft office)
Very good ease of use.

- Would installing Ubuntu, then apt-get'ing FVWM or XFCE work? - or would this bodge up the ubuntu default OpenOffice.org install?

---

### Post by &#12465;&#12452;&#12488; on 2005-05-22
I installed [Damn Small Linux](http://www.damnsmalllinux.org/) on my laptop yesterday. It is a livecd based on KNOPPIX, but you can do a HDD-install. Since my computer also has only 64MB RAM, few other distros would run properly. DSL uses Fluxbox, and is very light. The best part; it's only a 50MB download.

It has it's own package-system, and you can easily add support for apt-get, so installing OpenOffice.org afterwards is easy! It probably has some office applications installed already, but I have not used them yet.

---

### Post by thorN on 2005-05-22
Thanks, that distro does seem to stand out.

Is there a chance Ubuntu could be modded to work with this old PC?
I'm thinking this because I've got more experience with Ubuntu that anything else (if that matters at all).

---

### Post by the_clown on 2005-05-22
HOWTO: XFCE4 with no Gnome
[http://www.ubuntuforums.org/showthread.php?t=30896](http://www.ubuntuforums.org/showthread.php?t=30896)

---

### Post by &#12465;&#12452;&#12488; on 2005-05-22
I think it would be easier to use a distro intended for slow computers, but Ubuntu should also be possible to run on an older computer.

I don't know how about you, but DSL isn't that hard to use. Like Ubuntu, it is also based on Debian. Try to run the LiveCD, and find out what it's like. It's pretty much the same thing.

---

### Post by thorN on 2005-05-22
Excellent, I didn't realise it was Debian based.


> It has it's own package-system, and you can easily add support for apt-get, 

Perhaps i should pay more attention :)

I'm gonna get DSL, thanks for your help.

Thanks for that link, the_clown, I hadn't found that before. I'll keep that path open if DSL doesn't work out.

---

### Post by poofyhairguy on 2005-05-22
[QUOTE=thorN]
300 MHz Intel
64MB RAM
2GB
[/QUOTE]


I have a computer about that slow that I run ubuntu on like champ. The trick is to spend a little upgrading the RAM, it goes a LONG way.

---

### Post by thorN on 2005-05-22
Good idea, I hadn't thought of that.
RAM is freakishly cost effective for upgrading.

However, it seems the lighter distro will be best suited to my budget atm.

---

### Post by GOwin on 2005-05-22
Lighweight distros I've tried before

[http://featherlinux.berlios.de](http://featherlinux.berlios.de) - My distro of choice, if I have to use an old computer.
Vector Linux
Slax

---

### Post by Ozitraveller on 2005-05-22
I running Ubuntu on a PII/400 with 64mb Video, 389mb ram, 2 X 8gb harddisks. It works fine. 

I've also tried the XFCE4 howto for Ubuntu, and  Debian with XFCE4 on PII/300, as well as DSL. All are good.

---

### Post by davidgypsy on 2005-05-23
I'm using Ubuntu on an old AMD K2 with 64mb RAM for the kids to play games on, and it runs ok! It doesn't even start to run XP or 98, or Mandrake or Suse. But it is usable with Ubuntu. I'm a happy customer! :)

---

### Post by thorN on 2005-05-23
Wow, is that running Gnome 2.10 david?

I'm happy with Ubuntu too, but I don't think we class as customers because it's free and Free.

---

### Post by jdodson on 2005-05-23
damn small or ubuntu with xfce, icewm or fluxbox would work well for you.

---

### Post by Jussi Kukkonen on 2005-05-24
With that amount of RAM, I don't think you should even dream about launching OO.org... Otherwise there is nothing wrong with those specs.

Just bite it and upgrade your memory ;)

---

### Post by UbuWu on 2005-05-24
You are probably better off using abiword and gnumeric instead of openoffice.

---

### Post by ubuntu_demon on 2005-05-24
ubuntu with XFCE or beatrix :

[http://www.watsky.net](http://www.watsky.net)

---

### Post by thorN on 2005-05-24
I've tried DamnSmall Linux today (it's the 4th Distro I've tried so far) and I didn't much like it - it's not as simple and elegant as I'd need. It's not a problem for me, but a Swap file monitor is of no use to most other people using the PC.
However, it was very very small and very very fast. I'd probably use it as a LiveCD because of this.

Would it be best to install XCFE on Ubuntu by doing the "server" install first, then whacking XCFE on from the repositories?

edit: From the screenshots of Beatrix, it doesn't look much lighter than Ubuntu, what with Gnome and everything - think it would run on <128MB of RAM?

---

### Post by ubuntu_demon on 2005-05-24
[QUOTE=thorN]I've tried DamnSmall Linux today (it's the 4th Distro I've tried so far) and I didn't much like it - it's not as simple and elegant as I'd need. It's not a problem for me, but a Swap file monitor is of no use to most other people using the PC.
However, it was very very small and very very fast. I'd probably use it as a LiveCD because of this.

Would it be best to install XCFE on Ubuntu by doing the "server" install first, then whacking XCFE on from the repositories?

edit: From the screenshots of Beatrix, it doesn't look much lighter than Ubuntu, what with Gnome and everything - think it would run on <128MB of RAM?[/QUOTE]

**editted :**

XFCE with Ubuntu rocks but it is harder to install than beatrix (you will have to do a server install and install the necessary packages with apt-get)

yes beatrix will run ... it is very light-weight (read their website). I haven't tried it myself. But I have heard nice things about it. 

there's a lot of talk about beatrix on the forums :

[http://www.ubuntuforums.org/search.php?searchid=806424](http://www.ubuntuforums.org/search.php?searchid=806424)

the user called "oskarku" is the main developer of beatrix. This is one of his posts :

[http://www.ubuntuforums.org/member.php?u=2524](http://www.ubuntuforums.org/member.php?u=2524)

---

### Post by thorN on 2005-05-24
Ah great, I'll do that then (install XFCE from "server" install). It shouldn't be harder, I've found apt-get'ing stuff from the server install to be fairly elegant and simple.

---

### Post by weekend warrior on 2005-05-24
If that doesn't work for you for some reason thorN, you may want to have a look at [ Morphix 0.5-pre4 LightGUI](http://www.morphix.org/index.php?option=com_content&task=view&id=26&Itemid=59) 

Contains:

    * Xfce 4.2
    * Linux 2.6.9 kernel
    * Abiword
    * Mozilla firefox
    * Mozilla thunderbird
    * the Gimp

I'm not as quick to point it now though because the last couple of people I've recommended it to ran into problems. It worked for me when I tried it on a celeron 500 and it's a LiveCD, only about 260 MB so nothing to lose trying it out.

HTH

---

### Post by davidgypsy on 2005-05-24
[QUOTE=thorN]Wow, is that running Gnome 2.10 david?
[/QUOTE]

Yep! This thing would only run Win95 before, so I am very impressed!

---

