---
title: "Don't you love operator error?"
date: 2009-08-30
forum: The Cafe
---

### Post by BslBryan on 2009-08-30
I was very bored, and decided to revamp my Hardy desktop.  

I like eye-candy, but only when tastefully done, so I decided to use Compiz to create a widget layer to make room for newly implemented Screenlets.  I've used it before, but only for Now Playing.  This really was my foray into Screenlets.  Anyway, so I set everything up, but the FolderView Screenlet isn't compatible with Hardy.  

This annoyed me slightly, so I tried to get it to work.  I trusted a forum post that stated that some person had gotten it to work by installing a missing package and its dependencies from Ibex.  It didn't install correctly, however.  

I shrugged my shoulders and continued for about an hour to customize my desktop before returning to the problem.  I would simply reinstall the Hardy package.  

Well, summed up, it didn't work.  Nothing did.  I broke apt, GDEBI refused to install anything (for good reason, but I was going to install the package that would stop it from complaining.  Not that it matters much.)  I compromised my entire GUI, and the way that several programs worked.

So, after a heavy sigh, I ran ```
sudo apt-get install -f
```, which completely uninstalled everything but a core system and my personal files.  Bad timing dictated that I wasn't allowed to move anything to my (for some reason undetected) USB stick.  Since I broke apt, I couldn't reinstall what I needed.

After about an hour of cursing, facepalming, and listing pros and cons, I decided that I'd have to reinstall Ubuntu, as it would take a heck of a lot less work than rebuilding and fixing the system.  Plus, I'm at school, so devoting that much time to my computer when no actual work is being completed just isn't feasible. 

I look through my install cds.  "Fedora 9?  Hmm.  Nope.  Windows 7?  No.  Fedora 10?  Fedora 11?  Why do I have so many Fedora install discs?  Ubuntu 9.04.  Finally!"  So, I pop it in, glad to have a GUI back, and install.  66%....67%....68%....68%....68%....ERROR.  


"Damn."

So, I try again, with the same results.  

Because of this, I now have Fedora 11 installed on my computer, as my only (therefore primary) OS.  All of the artwork, unsubmitted code, projects I was leading for SpreadUbuntu, other miscellaneous personal treasures (pictures, music) are all gone.  Not to mention that I have System76's Ubuntu stickers on my machine.  All of this happened because I am a curious programmer who made a very stupid mistake.  

Fedora 11 is cool, and I really like it, but I miss Ubuntu, and doing work for Ubuntu is going to be strange without being on an Ubuntu machine.  Gnome menu paths are different, yum is a stranger to me, but I suppose I'll have to live with it, at least for a little while.

Anyone have similar experiences?

---

### Post by CJ Master on 2009-08-30
Ouch. Why didn't you boot to live-cd to recover your files? Dropbox or something.

---

### Post by Ocxic on 2009-08-30
This is why backups are important. :(

---

### Post by BslBryan on 2009-08-30
> **CJ Master said:**
> Ouch. Why didn't you boot to live-cd to recover your files? Dropbox or something.
Tbh, I skipped over that option completely.  I was very sloppy in my thinking because I had homework to do.
> **Ocxic said:**
> This is why backups are important. :(
Big +1.

---

### Post by Namtabmai on 2009-08-30
> **BslBryan said:**
> So, after a heavy sigh, I ran ```
sudo apt-get install -f
```, which completely uninstalled everything but a core system and my personal files.

I'm sorry to doubt you, but how? It's possible that apt might have uninstalled everything but a base system but how exactly did it uninstall your personal files?

---

### Post by Skripka on 2009-08-30
> **Ocxic said:**
> This is why backups are important. :(

He who laughs last usually has at least 3 good backups.

---

### Post by BslBryan on 2009-08-30
> **Namtabmai said:**
> I'm sorry to doubt you, but how? It's possible that apt might have uninstalled everything but a base system but how exactly did it uninstall your personal files?

It didn't. :P You misread it.  Here,
[QUOTE=me]which completely uninstalled everything **[except] a core system and my personal files.**[/QUOTE]

---

### Post by Chronon on 2009-08-30
So, you did salvage your personal files then?

---

### Post by Namtabmai on 2009-08-30
> **BslBryan said:**
> It didn't. :P You misread it.  Here,

Ah, apologies. Too much time programming seems to have made me automatically apply operator precedence to the English language.
:(

---

### Post by TuckLive on 2009-08-30
#-o Forgot the LiveCD.

---

### Post by BslBryan on 2009-08-30
> **Chronon said:**
> So, you did salvage your personal files then?
No.  I overthought about solutions, completely ignoring obvious options.  One of the dumbest things I've done this year.
> **Namtabmai said:**
> Ah, apologies. Too much time programming seems to have made me automatically apply operator precedence to the English language.
:(
No worries. :-)

> **TuckLive said:**
> #-o Forgot the LiveCD.
Such a simple solution, a simple object.  If I had one thought about it, I'd have all of the files I need right now. :-(

---

### Post by The Real Dave on 2009-08-31
I had a similar experience today, different error, but same frustration :D Came home from holidays, where I had no computer or Internet connection (for the past month :(). So glad to be back, so booted up, my main PC, and went to boot the server. I come back to the main PC to be greeted by a Grub Error 17 :(

A frantic grab disc, boot live, check gparted cycle ensued, where I found that my Ubuntu was well and truly gone :( And of course, I hadn't gotten around to backing up the OS to the server yet. So there's nothing to be done, other then re-install Ubuntu :(

Luckily, my home partition and all major Data are seperate, and backed up :D So its just a painful matter of downloading updates, programs, and configuring everything the way I liked it

---

