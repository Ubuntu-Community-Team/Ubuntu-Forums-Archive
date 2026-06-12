---
title: "Bootable anti-virus CD?"
date: 2009-08-02
forum: The Cafe
---

### Post by billdotson on 2009-08-02
I have heard of the Ultimate Boot cd for Windows and how it basically creates a mini-XP with anti-virus, malware and spyware utilities to clean up nasty viruses that can't be cleaned when the OS is running. However, in this thread: [http://www.wilderssecurity.com/archive/index.php/t-128914.html]("http://www.wilderssecurity.com/archive/index.php/t-128914.html") user vlk says that there are multiple things that need to be done in order to correctly remove a virus with a boot cd.

Is what he says in that thread accurate? If so, is Ultimate Boot CD for Windows accurate? What about some of the others like avast boot cd or bitdefender? About the closest I ever get to spyware is tracking cookies and I haven't had a resident virus in years but after getting upset about a false positive I thought it might be a good idea to have a boot cd to check for them every now and then.

Any help is appreciated.

---

### Post by stwschool on 2009-08-02
Any CD antivirus has one basic problem. It's non-updatable (short of regularly burning new CDs). That means that your scan will miss any new stuff, so unless you're manually removing the virus, forget it.

Also, frankly if a Windows machine is compromised, you're gonna have a hell of a mess to clear up. Better to backup important data using a linux live cd and reinstall from there.

---

### Post by billdotson on 2009-08-02
Unless I am mistaken I believe some of this boot CDs boot with network operability and the programs actualyl do update their definitions. Could be wrong though. Thing is with a Windows virus or trojan or anything else is that some of them have defenses. If you use a boot CD you can scan and find viruses, etc. that are sneaky and hide when the OS is running. Also, if you cant scan for them while the OS is running you can bet you can't remove them. If they aren't woken up they can't do crap so you simply have them removed. 

This is all what I have read but I have never done this myself. My main question was if ultimate boot cd or if any of the others allowed the kind of tweaks that that user in that forum said was necessary (and if they do, do they do it for you or do you have to learn an arduous method to do it manually). 

Normally a reinstall is a great idea, but if I have a bunch of programs installed with lots of settings there is no way I can write down or backup (or don't know how) then a fix would be ideal. Also, if I ever help my family or a friend out with this they probably aren't going to want to have to reinstall everything.

---

### Post by jmszr on 2009-08-02
billdotson,

You might want to check this out: [http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12) . Wikipedia has this: [http://en.wikipedia.org/wiki/Trinity_Rescue_Kit](http://en.wikipedia.org/wiki/Trinity_Rescue_Kit) .
TRK will update virus definitions and drivers if burned to a CD-RW.

---

### Post by stwschool on 2009-08-02
You're right that viruses do indeed do sneaky things and hide themselves in obscure places, which is why I recommend the reinstall. Regarding network functionality and updating, it's certainly possible to use an ubuntu live-cd in that way (ie run the live cd, install clamav and update it) but the problem you run into is that eventually you're dealing with very large downloads.

Trust me, whether you like it or not, there's really no way around it. If there's a virus, you reinstall. If you don't, you'll either leave security holes in there (very likely) or annoyances such as windows crashing because it can't find the bit of virus you removed that it is now dependent on for something. It's a ball-ache to remember what programs and settings, but to be honest, welcome to the world of Windows. This is what linux has over it, we can quickly auto-catalog our installs, backup the home directory and thus recreate an install on any computer.

The alt-plan? Linux as primary OS, windows in virtualbox, suitably sandboxed. Install the apps you want and keep a copy of the hard drive image somewhere. Save all your personal files to a shared folder (virtualbox will let you share a folder between the two) and that way you can get access in both and you don't have to update the hard drive image.

---

### Post by Post Monkeh on 2009-08-02
i've come across countless viirii on my friend's pcs, and my own years ago before i got a bit better at avoiding them, and i think i've only ever had to reinstall once, and that was only because the laptop i was working on was rubbish and taking too long to do everything, so i decided it would be quicker to just wipe it.

i asked a similar question [here]("http://ubuntuforums.org/showthread.php?t=1228800") . it'd be interesting to know if the discussions in the thread you posted about the difficulties in removing a virus from a system that isn't booted was still relevant today - that thread was from 3 years ago

---

### Post by ssam on 2009-08-02
try the [clam AV live cd]("http://www.volatileminds.net/projects/clamav/"). i can connect to the network to get the latest definitions.

it is probably a pain if your network is encrypted wireless, but if you have wired with DHCP (if you don't know what DHCP is then you probably have it :-) ) then it should be automatic. there is a tutorial on the site.

---

### Post by koenn on 2009-08-02
> **Post Monkeh said:**
> i've come across countless viirii 
there's no such thing as viirii, or virii, for that matter

---

### Post by koenn on 2009-08-02
> **billdotson said:**
> user vlk says that there are multiple things that need to be done in order to correctly remove a virus with a boot cd.

Is what he says in that thread accurate? 
He's correct that if you do an offline scan (from a live cd or so), all you do is scan the filesystem for infected files and malicious executables. You can possibly also delete those files. That would render your system virus-free because their executables are gone. 

You would probably end up with a load of registry settings and some associated files that weren't detected, but they are now harmless because the virus executable isn't there to call them. Usually you can clean them out by running an AV from within Windows afterwards. 

The risk of ending up with an unbootable system is real, but minor -  that would only happen if a virus made such changes (purposely or as a side effect of its own install mechanism) that the boot process or the core elements of the OS depend on the virus being present and running. 
not very likely, but not completely impossible. Boot sector viruses used to do this, but they've become obsolete when people stopped using floppies to boot operating systems

---

### Post by firen on 2009-08-02
Trinity Rescue Kit [http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12) also uses Clamav, and it is a superb distro for rescuing systems.

---

### Post by Post Monkeh on 2009-08-02
> **koenn said:**
> there's no such thing as viirii, or virii, for that matter

there is, however, such a thing as knobish pedantry. :-\"

---

### Post by koenn on 2009-08-02
> **Post Monkeh said:**
> there is, however, such a thing as knobish pedantry. :-\"
... and verbal snobbery

---

### Post by Post Monkeh on 2009-08-02
> **koenn said:**
> ... and verbal snobbery

you're the one correcting people's choice of words :biggrin:

---

### Post by koenn on 2009-08-02
> **Post Monkeh said:**
> you're the one correcting people's **mistakes**
see, i did it again.

Apparently this means a lot to you, so go ahead saying 'virii' (or ('viirii') if it makes you feel better.
I'm done with this.

---

### Post by Post Monkeh on 2009-08-02
> **koenn said:**
> see, i did it again.

Apparently this means a lot to you, so go ahead saying 'virii' (or ('viirii') if it makes you feel better.
I'm done with this.

once again chum, you're the only one who made a big deal out of my choice of the word.

tell you what, i'm a reasonable guy, if it annoys you that much i promise i won't use it here again.

---

### Post by billdotson on 2009-08-08
Thanks, I will look into it. Maybe if I have some time I'll clone my clean XP install back and try to find an annoying (but relatively safe, as in it won't wreck the boot sector or anything) virus and test out clamAV or some other AV program from a boot cd/dvd. It will be interesting to see how the whole registry thing will work... I guess that is what the Ultimate Boot CD for XP might be for, but I don't have my XP install CD anymore so I can't use it.

---

