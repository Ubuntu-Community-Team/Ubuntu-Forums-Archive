---
title: "Problems installing EVE Online"
date: 2009-06-09
forum: Wine
---

### Post by ninja_numbnuts on 2009-06-09
Lol, this is my third post here in an hour! xD

Anyway, I'm geting the issue thats in the attached screenshot.

How do I find where the installer downloaded the files too, so I can install manually?

Thanks!

---

### Post by NightMKoder on 2009-06-09
What exactly is the problem with clicking download files manually?

---

### Post by ninja_numbnuts on 2009-06-09
> **NightMKoder said:**
> What exactly is the problem with clicking download files manually?

It doesn't do anything, and I don't really want to have to download another 2GB of files that it already has stored somewhere on my HDD. I just need to know where those files are so I can install them manually!

---

### Post by ninja_numbnuts on 2009-06-10
Meep.

---

### Post by ninja_numbnuts on 2009-06-17
Double meep.

---

### Post by Vers on 2009-12-01
I, too, have a problem installing EVE-Online. However my problem is that the install CD is locked, and so wine will not open the installation applications (no rhyme intended). Here is some terminal entries for you:

> 
john@Euclid:/media/cdrom0/windows$ wine setup_pc.exe
wine: could not load L"D:\\windows\\setup_pc.exe": Module not found
john@Euclid:/media/cdrom0/windows$ err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r> john@Euclid:/media/cdrom0/windows/fscommand$ dir
eve_premium_setup_74306.exe
john@Euclid:/media/cdrom0/windows/fscommand$ wine eve_premium_setup_74306.exe
wine: could not load L"D:\\windows\\fscommand\\eve_premium_setup_74306.exe": Module not found
john@Euclid:/media/cdrom0/windows/fscommand$ err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -rI was thinking I should try the Auto-run .inf file using:
> wine start autorun.inf Would this work?

I'm relatively new to Linux (a week) and I am running under the latest version of Kubuntu. Wine version "wine-1.0.1" 

Any tips or things I am doing wrong?

Thanks for any help you can give :)

---

