---
title: "System crash after apt-get upgrade"
date: 2004-12-01
forum: Repositories &amp; Backports
---

### Post by dishbert on 2004-12-01
I let my dial-up run all last night after a fresh Ubuntu install (my fourth, don't even ask).  This morning the modem was still connected, 90% of the upgrades had downloaded and there was a message "unable to continue at this time" (or some such).  I hit apt-get upgrade again, and it seemed to fire back up where it had left off.   I came back a half hour later, and the system was locked up:  no screen, no keystrokes.  

I rebooted, and now it seems I'm back to square one:  a new apt-get upgrade says I need all 100 Mg.

Has anyone else seen this?  Is there any way I can recover the downloaded data?

---

### Post by adbak on 2004-12-01
I can't say that I've seen it, but there's a good chance that all the files that you've successfully downloaded have been stored on your comp, somewhere in /var/cache/apt/archives, I believe.  So while it may say you need to download 100megs, you may only need to download a fraction of that.

---

### Post by dishbert on 2004-12-01
Thanks for giving me hope adbak, I'll have a look when I get home.  

I had noticed that "resume" behavior before, when apt-get upgrade died in the middle, and starting again meant starting where it had left off, but this time it sure looked like it had started back at the beginning.

I thought that the difference was the hard boot after the interuption, let's hope not.

---

### Post by dishbert on 2004-12-02
You were exactly correct adbak, the files were right where you said they'd be, and starting apt-get upgrade again started where it had left off.

Thanks.

---

### Post by Marauder1 on 2004-12-05
Until you do the command  : apt-get clean
Everything stays in this directory.

---

