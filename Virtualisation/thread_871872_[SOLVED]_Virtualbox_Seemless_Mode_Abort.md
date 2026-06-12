---
title: "[SOLVED] Virtualbox Seemless Mode Abort"
date: 2008-07-27
forum: Virtualisation
---

### Post by VaRanger1 on 2008-07-27
Installed virtualbox on ubuntu 8.04 with windows XP guest and it originally worked flawlessly.  Now, when attempting to expand windows xp to full screen mode or to put into seemless mode it aborts the virtualbox.

That is, when pressing the <ctrl-L> or <ctrl-F) keys the virtualbox aborts the windows xp session.

Any thoughts on the cause or a fix?

---

### Post by sonicb00m on 2008-07-27
have you made sure the latest version of the guest additions is installed. It's usually updated and non compatible every time a new release comes out.

Install it again just incase.

---

### Post by VaRanger1 on 2008-07-27
Reinstalled, but the problem still exists.  It is also intermittent - happens most, but not all, of the time.  It is also aborts when using the window size buttons.

---

### Post by sonicb00m on 2008-07-28
I don't know then. There is a log file. I'd head over to the support forums at the virtualbox site, they are quite helpful there.

---

### Post by VaRanger1 on 2008-07-28
This may be of help to others running Virtualbox.  The problem I had with Windows XP aborting whenever sizing a window or trying to go to seamless mode has been resolved.

The problem was with a HP printer driver installed into the Windows XP guest OS.  I had installed a HP L7590 printer into the guest OS using the regular install disk.  This is a network based printer.  The printer worked just fine.  But as it turned out, it hosed the video.

Removing the printer driver resolved the windows abort problems.

Lesson learned:  Careful what software is installed into the guest OS.  If you have problems, start with the guest OS (aka windows) prior to trying to debug Virtualbox.

Other comment:  The seamless mode is incredible.  Runs Quicken perfectly.

---

### Post by genothomas on 2010-07-21
I Installed latest Virtualbox PUEL edition on Linux Mint 9 and also on  Ubuntu 10.04 LTS with Windows XP SP2 guest and the first day itself the  problem starts. That is when attempting to expand windows xp to full  screen mode it aborts the virtualbox.

That is, when pressing the  <ctrl-F> key the virtualbox aborts my windows xp session.

Any  thoughts on the cause or a fix? [IMG]http://forums.virtualbox.org/images/smilies/icon_cry.gif[/IMG] 

My virtual box ver is  3.2.6 (latest)

I attached my log file below [IMG]http://forums.virtualbox.org/images/smilies/icon_exclaim.gif[/IMG]

---

