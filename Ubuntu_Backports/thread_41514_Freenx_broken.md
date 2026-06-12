---
title: "Freenx broken ?"
date: 2005-06-13
forum: Ubuntu Backports
---

### Post by Leif on 2005-06-13
I realize this has been mentioned elsewhere, but I thought it could use its own header. After today's upgrade my freenx server seems to have stopped working. All's well with making the connection and establishing X, but once the window is opened gnome never loads.

---

### Post by mird on 2005-06-13
Yeah, there's definitely something bung.

I noticed there was a FreeNX package that moved out of staging recently, which I assume is the package that everyone will have upgraded to.  

I noted a thread mentioning a new version in staging and that people were having problems with it, but that was some time ago... which makes me wonder whether it should've actually been promoted (perhaps it was done accidentally?).

---

### Post by btdown on 2005-06-14
yeah mine is hosed up, too. Ever since the upgrade that just happened within the past few days, mine just hangs..... 
 
Now when I log in, I get the nomachine logo for a few seconds and then the screen just goes black and hangs. Can't even close the viewer app.
 
 
 
Anyone know whats up with it?

---

### Post by jdong on 2005-06-14
strange... That version of FreeNX was working fine for me, especially since it is the version that Knoppix and Kanotix uses now.

Did you guys dist-upgrade to it?

---

### Post by Leif on 2005-06-14
Yes, I think I did it thru synaptic and "smart upgrade". I've also checked the versions of stuff installed, they're all from the backports. A couple are marked alpha, but I guess that's as intended.

---

### Post by jdong on 2005-06-14
I have a fresh Hoary virtual machine. Let me see if I can reproduce your bug on it.

---

### Post by jdong on 2005-06-14
no, it works fine from here. Can you do a full uninstall and reinstall?

1) Run **nxsetup --uninstall --purge**
2) open up synaptic, search up nx, remove all nx/freenx related packages (with purge)
3) Mark 'freenx' for installation
4) Run **nxsetup --uninstall --purge**
5) run **nxsetup --install --setup-nomachine-key**

---

### Post by Leif on 2005-06-14
I'm afraid that doesn't fix it. I also tried connecting to it from a windows client in case I'd screwed up smt with my home machine, but still the same black screen.

---

### Post by jdong on 2005-06-14
Are you sure you set up a UNIX GNOME Session properly, with 'Encrypt all data with SSH'?

---

### Post by Leif on 2005-06-14
Yes, I haven't changed my home nx client recently.

---

### Post by btdown on 2005-06-14
Nope...Tried all the above and I still get the same result...hanging black screen after nomachine logo...

---

### Post by btdown on 2005-06-14
Oh BTW, Jdong, could I please request the 'locales' package be backported?
\\:D/

---

### Post by jdong on 2005-06-14
Can you upgrade your NX clients to the latest version available?

---

### Post by Leif on 2005-06-14
Tried it on an XP box. Still the same.

---

### Post by jdong on 2005-06-14
ok, does anyone here (other than me) have WORKING FreeNX?

I find it strange that I can't reproduce the black screen.

If you let it sit for a minute or two, does anything ever happen?

---

### Post by btdown on 2005-06-14
I'm already at the latest client... 1.4.0-92. I've let the client sit there with the black screen for 10+ minutes and no activity--not only that. I cant close the client. I have to manually kill the process. Im uninstalling the client and reinstalling, but I dont expect it to change the result.
 
THanks!
BT
 
Edit: Nope...no joy...

---

### Post by deshda on 2005-06-14
I've got the same problem with freenx.  I've done a couple of prior installations of freenx without any problem.  I went to install freenx on a new server with a fresh installation of Ubuntu and on my clients I get the black screen.  I've tried it from multiple linux clients and an XP client with the same results.

---

### Post by jdong on 2005-06-14
very well, I'll roll back FreeNX to the old version.

---

### Post by rcunha on 2005-06-16
[QUOTE=jdong]ok, does anyone here (other than me) have WORKING FreeNX?

I find it strange that I can't reproduce the black screen.

If you let it sit for a minute or two, does anything ever happen?[/QUOTE]
 Well, i still have the "broken" version on my server and, yesterday i went home and tried to connect to my server from my desktop there, where i had first installed nx client (windows box) and, for my suprise, gnome-session worked. It was in the same lan, then i tried my laptop at work and didn't work also another computer at work, didn't work, and that's over dsl.
My computer at home was the only one that had connected to my freenx server before the upgrade to the broken version and, it keep working... any other computer didn't.

---

### Post by jdong on 2005-06-16
Ok, freeNX has been rolled back. Uninstall and reinstall.

---

### Post by Leif on 2005-06-21
Thanks a lot, it works now !

Well, except for one unrelated thing for me : my nxclient on one of my hoary machines is acting odd; it logs in, but doesn't always click, or clicks somewhere other than where it should, so it's basically unusable. It's not the server, which works with clients on other computers. I've tried removing and reinstalling everything but it persists. Has anyone come across this ?

---

### Post by jdong on 2005-06-21
well, I'll stick a newer upstream nxclient from Kanotix into staging.

---

### Post by luluguegue on 2005-07-01
hi, just installed freenx form extras repositiory, but got client problem :
NXPROXY - Version 1.4.0

Copyright (C) 2001, 2004 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '11425'.
Info: Connecting to remote host '10.10.3.215:5002'.
Warning: Couldn't invoke 'nxclient'. Error is 2 'No such file or directory'.
Warning: Trying with path '/usr/NX/bin:/opt/NX/bin:/usr/local/NX/bin:/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games'.
Warning: Couldn't invoke 'nxclient'. Error is 2 'No such file or directory'.
Warning: Trying with path '/usr/NX/bin:/opt/NX/bin:/usr/local/NX/bin:/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games'.
Info: Aborting procedure due to signal '15'.

trying with installation from kanotix and download propietary version has same error  too.

any solution? what should i do?

thnx alot.

---

