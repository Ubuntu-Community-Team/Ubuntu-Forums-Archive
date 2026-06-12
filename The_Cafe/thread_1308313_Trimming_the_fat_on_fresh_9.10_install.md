---
title: "Trimming the fat on fresh 9.10 install"
date: 2009-10-31
forum: The Cafe
---

### Post by Crowchild on 2009-10-31
After each upgrade/fresh install, I find that I have to spend a bit of time removing all the packages/programs that I have no use for such as evolution, ekiga, and all of the games.

I suspect a lot more of these excess packages fly under the radar of the average user. I would never have expected to find the amount of documentation packages that can be seen when scrolling through synaptic.

So in the hopes of making a list of packages that could safely be trimmed from Karmic please comment with what you would remove.

---

### Post by cariboo on 2009-10-31
To save time, why not use the minimal install using the alternate install cd, then just install the programs you want.

Personally I can't see going to the trouble of removing installed programs, as all they do is take up hard drive space, and with the size of most hard drives these days what's a couple of hundred megabytes.

---

### Post by Crowchild on 2009-10-31
Hmmm... This is why I love the forums! I never knew you could pick and choose the programs you want to install from the Alternate install CD. I will keep that in mind for 10.04

As for ' going to the trouble of removing installed programs', I guess it's just part of my OCD... I hate excess and waste, in all aspects of my life. I know that looks kind of paradoxical when it comes to wasting time deleting useless packages that only take up a minimum of space of a massive harddrive.

---

### Post by PhoHammer on 2009-10-31
> **Crowchild said:**
> I guess it's just part of my OCD... I hate excess and waste, in all aspects of my life. I know that looks kind of paradoxical when it comes to wasting time deleting useless packages that only take up a minimum of space of a massive harddrive.

Same here!

Here is a link to a minimal ubuntu iso: _[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)_

It's just 12 MB and you choose which programs to download and install when you are 
installing the OS. It also only downloads current packages, so there is no 400 MB's of
upgrades to download directly after installation.

---

### Post by adeypoop on 2009-10-31
It's interesting to find out about minimal ubuntu, I might look at that next time i upgrade. :KS 

Rather than removing apps (which I'm not too worried about personally), I'm wondering what daemons / services are running taking up resources that i may be able to disable? For example I usually disable bluetooth as I don't have hardware for that. Any others that people usually disable ?

:popcorn:

---

### Post by cariboo on 2009-10-31
Here's a list of startup applications I disable

[list]
[*] AT SPI Registry Wrapper
[*] Bluetooth Manager
[*] Evolution Alarm Notifier
[*] Remote Desktop
[*] Visual Assistance
[/list]

I could probably disable more, but I haven't looked into it yet.

---

### Post by RedSquirrel on 2009-10-31
> **PhoHammer said:**
> Same here!

Here is a link to a minimal ubuntu iso: _[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)_

It's just 12 MB and you choose which programs to download and install when you are 
installing the OS. It also only downloads current packages, so there is no 400 MB's of
upgrades to download directly after installation.

I normally recommend the Minimal CD as well. However, when I installed karmic using the Minimal CD, it pulled in **openoffice.org** (and all of its dependencies, naturally) when all I asked for was the core (command-line) system. That was about three weeks ago, but it looks like the bug still exists. See [here]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/443167").

---

### Post by kerry_s on 2009-10-31
i only remove what i replace, so far only removed transmission for deluge.

application wise, if you don't use it then it don't effect the system resource wise, only disk bloat, perfectly harmless to leave it there.

if you really are removing alot, then as the others have said, better to start from the ground up minimal install.

---

### Post by Crunchy the Headcrab on 2009-10-31
> **Crowchild said:**
> Hmmm... This is why I love the forums! I never knew you could pick and choose the programs you want to install from the Alternate install CD. I will keep that in mind for 10.04

As for ' going to the trouble of removing installed programs', I guess it's just part of my OCD... I hate excess and waste, in all aspects of my life. I know that looks kind of paradoxical when it comes to wasting time deleting useless packages that only take up a minimum of space of a massive harddrive.

You might also try fedora. Fedora 11 (the last one I used) is a lot like ubuntu, it doesn't come with a graphical user interface for installing software so you need to install one if you don't like to use the cli (I prefer it).  Anyway the install dvd let's you pick either gnome or kde and then choose which programs you want for those environments including media applications, programming, servers, games, tools, office, etc.  Basically the installer let's you almost handpick your pre-installed programs (almost) but it is still easy to set up like Ubuntu (you need to setup sudo if you want to use it).  Keep in mind that with this method you will need to download a full dvd's worth of install crappage.  A new Fedora comes out next month or something.

---

### Post by purgatori on 2009-10-31
This is a good guide for getting rid of all the junk: [http://ubuntuforums.org/showpost.php?p=2651015&postcount=1](http://ubuntuforums.org/showpost.php?p=2651015&postcount=1)

---

### Post by northwestuntu on 2009-10-31
> **Crowchild said:**
> Hmmm... This is why I love the forums! I never knew you could pick and choose the programs you want to install from the Alternate install CD

me neither :p  i agree with the 1st post a lot of stuff dont use at all.

---

