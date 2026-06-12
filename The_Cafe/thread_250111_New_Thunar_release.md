---
title: "New Thunar release"
date: 2006-09-03
forum: The Cafe
---

### Post by weekend warrior on 2006-09-03
Thunar 0.4.0 RC1 released today - has a nice GUI installer for the compile process too - good stuff, it's been running well on my system so far. 

Have a look over [here]("http://thunar.xfce.org/news.html") or go straight for the download [here]("http://thunar.xfce.org/download.html#0.4.0").


 :)

---

### Post by Turgon on 2006-09-03
Nice! Finaly a trash in xubuntu!

---

### Post by maniacmusician on 2006-09-03
looks great. is this part of edgy knot2? because i just downloaded that and will probably set up as a virtual machine soon.

---

### Post by maniacmusician on 2006-09-03
to answer my own question, it is part of edgy knot2. i'm on the live cd, and i see a trash icon. this is awesome! xubuntu rocks.

---

### Post by Super King on 2006-09-04
Awesome, that's one of the things I missed in Thunar.

---

### Post by shunthemask on 2006-09-04
yeah, trash is something that I missed, too.  Too bad that it doesn't work...

---

### Post by Jason-X on 2006-09-04
Can I install this on my existing Xubuntu installation or do I have to remove  the Thunar that came with Xubuntu first?

---

### Post by weekend warrior on 2006-09-04
> **shunthemask said:**
> yeah, trash is something that I missed, too.  Too bad that it doesn't work...
Hmm.. trash is ok here - right-click 'delete', drag & drop, cut & pasting files into trash:/// and the restore function are all working for me.

> **Jason-X said:**
> Can I install this on my existing Xubuntu installation or do I have to remove  the Thunar that came with Xubuntu first?
I uninstalled first but it was a fairly old build that needed replacing. There's also a GUI uninstaller in this RC that's dead easy to use if you want/need to go back to a previous version.

---

### Post by Miguel on 2006-09-04
Maybe you guys are interested to know that Xfce 4.4 RC1 has been released. I've checked the edgy packages and they are still at beta2 (through packages.ubuntu.com, I don't have edgy installed).

This release goes with Thunar 0.4.0.

---

### Post by Jason-X on 2006-09-04
Thanks Weekend Warrior:) It works a treat. Also my trash works fine too.

---

### Post by weekend warrior on 2006-09-04
> **Miguel said:**
> Maybe you guys are interested to know that Xfce 4.4 RC1 has been released. I've checked the edgy packages and they are still at beta2 (through packages.ubuntu.com, I don't have edgy installed).

This release goes with Thunar 0.4.0.
Yeah, saw that too yesterday - even downloaded the installer, but thought it wiser to wait a couple days at least to see if any major bugs come up - a lot more can potentially go wrong with a desktop environment compared to a file manager ;)

---

### Post by songo on 2006-09-04
> **Jason-X said:**
> Thanks Weekend Warrior:) It works a treat. Also my trash works fine too.
what did you do? did you installed over or removed it before?

---

### Post by Jason-X on 2006-09-04
> what did you do? did you installed over or removed it before?

I removed the Thunar that came with Xubuntu with Synaptic and then installed the new Thuner with the installer. It installed very smoothly.

---

### Post by kripkenstein on 2006-09-04
This is great news. Possibly the main thing stopping me from using XFce was the lack of a trashcan.

Looks like I have a big decision to make when Edgy comes out - GNOME or XFce...

---

### Post by lapsey on 2006-09-04
I know for sure that I'm dumping Gnome. Or rather, nautilus. 
I have a pretty fast amchine but I'm tired of the instability and un-necessary footprint.

The lastest environment is a must have for Xubuntu Edgy.

---

### Post by zugu on 2006-09-05
Is it possible for me to replace Nautilus with Thunar without installing Xubuntu?

---

### Post by fuscia on 2006-09-05
> **zugu said:**
> Is it possible for me to replace Nautilus with Thunar without installing Xubuntu?

yes.

---

### Post by zugu on 2006-09-06
And would you be kind enough to tell me how? Is it as simple as apt-get remove nautilus / apt-get install thunar ?

---

### Post by gurgle on 2006-09-07
im running gnome - i tried to install thunar but i got this error:

evan@linux:~/Downloads$ ./Thunar-0.4.0rc1-installer.run
Verifying file integrity... OK.
Extracting the installer... OK.
Checking for usable C compiler... gcc
Checking for usable C++ compiler... g++
Checking for GNU make... make
Checking for package config tool... pkg-config
Checking for GLib (GModule) >= 2.6.0... not found, see /home/evan/.Thunar.installer-log for details
Cleaning up... OK.

---

### Post by fuscia on 2006-09-07
> **zugu said:**
> And would you be kind enough to tell me how? Is it as simple as apt-get remove nautilus / apt-get install thunar ?

yup. i think you have to have dapper repositories for getting thunar. i don't recall it being in the breezy repositories.

---

### Post by maniacmusician on 2006-09-07
also you probably wouldn't do apt-get install thunar (if you want the brand spankin new version), you'd probably download the installer and install it that way

---

### Post by zugu on 2006-09-08
Do I need to remove Nautilus? And if not, how do I make folders open with thunar by default?

Sorry for the nagging questions, but it's really important to me.

---

### Post by maniacmusician on 2006-09-08
umm i wouldnt know, don't like gnome. but fuscia said that apt-get remove nautilus would be fine.

---

### Post by jkroto on 2006-10-03
> **gurgle said:**
> im running gnome - i tried to install thunar but i got this error:

evan@linux:~/Downloads$ ./Thunar-0.4.0rc1-installer.run
Verifying file integrity... OK.
Extracting the installer... OK.
Checking for usable C compiler... gcc
Checking for usable C++ compiler... g++
Checking for GNU make... make
Checking for package config tool... pkg-config
Checking for GLib (GModule) >= 2.6.0... not found, see /home/evan/.Thunar.installer-log for details
Cleaning up... OK.

I got the same thing.  If I find anything I'll pass it along, please do the same.

---

### Post by jkroto on 2006-10-03
> **gurgle said:**
> im running gnome - i tried to install thunar but i got this error:

evan@linux:~/Downloads$ ./Thunar-0.4.0rc1-installer.run
Verifying file integrity... OK.
Extracting the installer... OK.
Checking for usable C compiler... gcc
Checking for usable C++ compiler... g++
Checking for GNU make... make
Checking for package config tool... pkg-config
Checking for GLib (GModule) >= 2.6.0... not found, see /home/evan/.Thunar.installer-log for details
Cleaning up... OK.

I had do this
"You may have to run sudo apt-get build-dep thunar beforehand."
Found here [http://http://xubuntu.wordpress.com/2006/09/03/new-thunar-release/]("http://http://xubuntu.wordpress.com/2006/09/03/new-thunar-release/")
It is now installing.

---

