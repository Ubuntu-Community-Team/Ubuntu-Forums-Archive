---
title: "Ventrilo 3.0 in WinXP client as Virtualbox 3.0 session in Ubuntu 9.04"
date: 2009-08-11
forum: Virtualisation
---

### Post by couzin2000 on 2009-08-11
I'm an avid gamer, and I have been trying to get Ventrilo to work correctly in Wine for the past year. However, all my efforts are in vain, since most servers encountered always use the MSGSM voice codec - this is what gives all of us the most problems with Vent in Ubuntu.

So, I've decided to build a Windows XP image specifically for Ventrilo. Keep the .vdi small enough (5Gb) and shutting down all the services from Windows except for those needed to function properly... essentially running a Windows on minimal life support.

I am, however, at a loss when it comes to true compatibility as far as **audio** between host (Ubuntu 9.04) and client (Win XP SP3). So far, my best attempts at making all audio functional have only been semi-successful -- I've gotten audio output working, or audio input working -- never both simultaneously. I'm assuming I'll have to use a different audio driver than the one used by Wine, so maybe running PulseAudio and Alsa simultaneously, both routed to the sound card (a SB Audigy).

I'm looking for any advice Ubuntu users would have as far as making this work flawlessly - and I mean without one single hitch. No crapping out after a few hours of gameplay. This install would have to be solid and stable.

That means:
[LIST]
[*]running a game with Wine
[*]running a session of Windows XP SP3 in Virtualbox at the same time
[*]running Ventrilo in the vbox session
[*]being able to use the PTT (push-to-talk) keypress function WHILE I'm in the wine-run game
[/LIST]

If all this stuff works without a hitch, then I'm happy.

I will keep this thread updated with my progress, and will list any and all problems encountered. This may be a great workaround for any gamers using Ubuntu... hope this all helps!

---

### Post by dardack on 2009-08-11
I'm confused you put up a HOWTO for vent in wine on ubuntu.  Also, I encounter no problems on multiple vent servers and have even run my own with that codec and had no problem.

---

### Post by gega on 2009-08-28
look and this page [http://kevinfitzgerald.net/trac/wiki/VboxVentControl](http://kevinfitzgerald.net/trac/wiki/VboxVentControl) 
i try it but no results .... if u can edit it to make it better

---

### Post by kfitzgerald on 2010-06-02
> **gega said:**
> look and this page [http://kevinfitzgerald.net/trac/wiki/VboxVentControl](http://kevinfitzgerald.net/trac/wiki/VboxVentControl) 
i try it but no results .... if u can edit it to make it better

I just noticed this post now (though 10 months old) but I wrote the VBoxVentControl app mentioned above. If you (or anyone for that matter) has any questions on the program, feel free to post back or let me know :)

-Kevin

---

