---
title: "Win question: a terminal emulator that doesn't suck?"
date: 2006-01-09
forum: The Cafe
---

### Post by Liam on 2006-01-09
Yo.

I've got a nice little collection of GNU tools that have been ported to Windows sitting on my thumb drive. Mostly for sysadmin tasks, and using vi, etc.

Only problem is, I've got to use cmd.exe or command.com. After being spoiled by everything from basic xterms to GNOME Terminal, it's really, really painful.

Are there any free/Free terminals for Windows that a) don't need Cygwin, and b) have tabs? Preferably something that doesn't require installation or touching the registry, because I don't necessarily have admin access to the machines, and I'd like to be able to run it off my flash drive.

I'd like to maybe crib the setup from [unixkit]("http://twu.net/code/unixkit.php") and wrap it in the emulator; I dunno.

Any thoughts?

Thanks.

---

### Post by Stormy Eyes on 2006-01-09
If you've got the patience, try setting up a [SSH (Secure Shell)](http://sshwindows.sourceforge.net/) daemon on Windows and then use [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) to connect to localhost.

---

### Post by briancurtin on 2006-01-09
i am a fan of putty myself. used every day over the summer at my internship to do work with my web application

---

### Post by Mr. Electric Wizard on 2006-01-09
Between Putty and WinSCP you've got it made...:p

---

### Post by Liam on 2006-01-09
[QUOTE=Stormy Eyes]If you've got the patience, try setting up a [SSH (Secure Shell)](http://sshwindows.sourceforge.net/) daemon on Windows and then use [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) to connect to localhost.[/QUOTE]

Heh. I'm actually doing that on a couple of my own Windows machines, but I'm pretty sure it requires admin rights to register and run the service.

---

### Post by Liam on 2006-01-09
Sorry, I guess I wasn't clear. I'd like to use a *local* shell, ala Cygwin, without Cygwin's overhead or installation requirements.

If you check out the link to Unixkit that posted above, it just wraps cmd.exe around bash or ksh (IIRC), and includes a bunch of GNU apps that have been ported to win32.

I'd like to get rid of cmd.exe and use something that doesn't suck, preferably with tabs and decent clipboard support, like GNOME Terminal, mrxvt, or konsole.

Now I *could* use GNOME Terminal or whatever, but then I'd need to install X, and therefore Cygwin, etc. That's fine for a machine that I run, but not for a thumb drive.

Thanks for the suggestions, though.

---

### Post by Stormy Eyes on 2006-01-09
Cygwin also comes with rxvt.exe. I don't think it requires a X server.

---

### Post by stoffe on 2006-01-09
[http://www.mingw.org/msys.shtml](http://www.mingw.org/msys.shtml)

Don't remember how good/bad it is, but that's the only non-cygwin "complete" shell I recall.

---

