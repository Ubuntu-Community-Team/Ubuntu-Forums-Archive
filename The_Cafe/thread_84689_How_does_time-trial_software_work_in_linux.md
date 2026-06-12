---
title: "How does time-trial software work in linux?"
date: 2005-10-31
forum: The Cafe
---

### Post by mfyahya on 2005-10-31
One of the main reasons I moved to ubuntu was that I could install some software, check it out, and remove it later for whatever reason and be assured that it did not leave nasty cruft behind. There is no central registry that gets polluted over time, and there's no need for regular system reformats.

However I've come accross time-limited linux software (e.g. crossover office). Since there's no registry to hide installation history, how do these work?

---

### Post by xequence on 2005-10-31
I am guessing there is something hidden in a configuration file somewhere, but I dont know :P

---

### Post by jasay on 2005-10-31
I could be way off, but I thought crossover office allowed you to download the software and any updates that are made during the subscription period.  After that expired you simply can't download anything new, but the software stays fully functional on your computer.  In this case it would be trivial to keep track of your subscription date and cut you off from further downloads after 6 months or whatever the subscription period is.

---

### Post by mfyahya on 2005-10-31
I'm talking about the free trial version. I downloaded it yesterday and it has nag screens and such asking me to register. I haven't tested this but if I uninstall the software and then download and install a new copy, shouldn't it somehow know it's been installed before? If so, what's to prevent people from simply reinstalling programs after they expire?

I'm pretty new to Linux and haven't yet come across trial software/shareware that would need to leave something behind after uninstallation, and I'm just curious how this is done in linux. Or is it that there are no shareware/trialware programs?

In any case I really like crossover office very much and  will most likely buy it soon, as it lets me run Internet Explorer quickly which is essential for me at work.

---

### Post by Kvark on 2005-10-31
A registry isn't needed to hide stuff. There are tons of directories and files in your filesystem. More then enough of a mess to hide a "trace" file anywhere in it.

Guess you can trust synaptic/apt-get and dpkg to not hide any trace files. But if the time-trial software comes with it's own custom installer and you run that installer as root then it can do anything it wants. Also if you ever run the program itself as root then it can do anything it wants. "anything it wants" includes placing a trace file in some obscure directory in a part of the filesystem that you never look at.

If you never run a custom installer as root or the program itself as root then it can't hide anything outside of your home directory. But most users wouldn't notice if it placed some randomly gnomishly named file in for example /home/user/.gnome2/

---

### Post by wmcbrine on 2005-10-31
[QUOTE=mfyahya]I'm pretty new to Linux and haven't yet come across trial software/shareware that would need to leave something behind after uninstallation, and I'm just curious how this is done in linux. Or is it that there are no shareware/trialware programs?[/QUOTE]
Generally, there aren't; far, far fewer than in Windows, certainly. Most anything you could want is available open source.

In a few cases, I've seen software that was time-limited in its Windows version, with the Linux version operating on the honor system -- e.g., it says you should run it only for thirty days, but there's nothing to enforce that.

The one effective piece of expiring software that I have on my Linux system is CDRecord-ProDVD, and that works by expiring for everyone at the same time, every six months -- whereupon you can get a new key for free. So it's pointless, and a hassle. But I digress...

---

### Post by BoyOfDestiny on 2005-10-31
Ah time trials... Remember when they were poorly coded? i.e. change the the system date to the "future", install, and then set your date back to normal... I hope that still doesn't work...

---

