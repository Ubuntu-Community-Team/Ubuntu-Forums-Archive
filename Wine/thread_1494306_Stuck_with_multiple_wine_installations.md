---
title: "Stuck with multiple wine installations"
date: 2010-05-26
forum: Wine
---

### Post by kinsago on 2010-05-26
Hi.

I'm having a bit of trouble managing multiple wine installations. Here is what I'm trying to achieve.
-> Office 2007 (Specifically Publisher) runs perfectly on wine 1.1.16
-> GTA SA (my choice of stress release) and Photoshop runs perfectly under wine 1.1.42

However, neither one will run on the other... if you get my drift.
I've tried installing both, installing the older version as a second install so that update manager doesn't complain all the time but I'm not actually getting anywhere. This is very frustrating and I don't really want to run one or the other options through a virtual machine. I know it works under wine, I just can't get two installations to work... HELP!?!?!?!?!

Cheers

---

### Post by cogadh on 2010-05-26
[PlayOnLinux]("http://www.playonlinux.com") offers the option to install multiple versions of Wine and will help you manage them.

---

### Post by beastrace91 on 2010-05-26
If you want to set up multiple Wine installs manually check the link in my sig for a HOWTO

~Jeff

---

### Post by kinsago on 2010-05-27
> **beastrace91 said:**
> If you want to set up multiple Wine installs manually check the link in my sig for a HOWTO

~Jeff

Hi.

Ok, tried it your way and so far it installed but I'm not sure how to install office using this 'older' version. Everytime I run the office installer from terminal using the older version, setup crashes! Ach! I've tried POL but although publisher runs it will only open a file, not let me actually use publisher. If I try to create a new file having opened one then it crashes. If I try to cancel the open file dialog box then the program just closes.

It could be that I just need to read up on how to use wine through terminal properly, but any assistance would be greatly appreciated.

Cheers

---

### Post by beastrace91 on 2010-05-27
If you followed my guide to the letter then you should be able to type **wine-1.1.16 something.exe** to run your something.exe under Wine 1.1.16 version.

Regards,
~Jeff

---

### Post by cogadh on 2010-05-27
Your problems with Publisher are probably related to the fact that it does not work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=663](http://appdb.winehq.org/objectManager.php?sClass=application&iId=663)

---

### Post by kinsago on 2010-05-27
> **cogadh said:**
> Your problems with Publisher are probably related to the fact that it does not work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=663](http://appdb.winehq.org/objectManager.php?sClass=application&iId=663)

I'll try the installing under 1.1.16 process again - maybe I just need to reboot. I'll also read up some more on wine. 

I know that WineHQ reports that publisher doesn't work but I have had it working under 1.1.16. If I can perfect this process then perhaps it will help other people who are in a similar situation. :)


Anyway, I'll try again and report back. All help so far is MUCH appreciated!

---

### Post by kinsago on 2010-05-27
Ok, I've done everything suggested so far. My installation of 1.1.16 (as a second wine installation) seems to be ok as I can run the office setup. It crashes part-way through the installation however.

I've un-installed wine (the newest version) and installed 1.1.16 from a deb file from the winehq website. Office - particularly publisher - runs very well under this, however I want to be able to have 1.1.16 installed permanently (until they solve the office problem) and the newest version for all my other wine-based goodies. It also keeps the update manager happy :)

Any more thoughts? I can post the terminal output if requested?

Thanks for all your help guys - together we can make this work...

---

### Post by kinsago on 2010-06-01
DONE IT (I think) !!!!!!!

Ok, I'm not posting this as done and solved until I'm sure - but I have an up-to-date version of wine and a working copy of publisher (+ the rest of office).

When I'm confident it works I'll post my methods, if anyone wants any more info for now then message me.

:)

---

### Post by javafiend on 2010-06-02
I just followed beastrace91's instructions for setting up a new wine version last night and everything ran perfectly.  The only suggestion I would make is to add wineboot to the winecfg and regedit setup section.

---

### Post by kinsago on 2010-06-02
Ok... update time.

Extra version of wine is now working perfectly (so far...) so, in effect, problem solved.

However, publisher will not save a file without crashing. Everything else works so far.

ACK! So close...

---

