---
title: "VMWare crashes on OS install"
date: 2007-12-15
forum: Virtualisation
---

### Post by Squizz on 2007-12-15
I've just installed the latest version of VMWare, but the system freezes and Ubuntu crashes during install.

I got the majority of the way through the XP install before it just hangs and crashes, the mouse still moves but I can't press anything within VMWare or in Ubuntu.

I also tried to install Windows 98 with an iso and that didn't even start the installation before it crashed.

Any ideas?

---

### Post by Shazaam on 2007-12-15
How much actual physical ram do you have and how much of it do you have allocated to the virtual machines?

---

### Post by Squizz on 2007-12-15
I have 1 gig DDR, and I allocated the default to the install, which was 192MB.

---

### Post by Shazaam on 2007-12-15
I think I see part of your problem. I have had a vm crash and thought I had an unresponsive pc. BUT, the real problem is that since vmware has focus (the mouse cursor is inside the vm) when it crashes you can't get back to the host. One way to solve this when that happens is to hold down Control+Alt+SysRq and type in REISUB at the same time. This will gracefully reboot your pc.

[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

After that I learned to quickly hit Control+Alt as the vm was booting to release focus so if it did crash I still had mouse control. As far as why the vm's are crashing maybe someone will come along with more help.

---

### Post by Squizz on 2007-12-15
That's useful nonetheless :) .  Do you think maybe trying an install with more RAM would yield better results?

---

### Post by Squizz on 2007-12-15
Well I just tried an install with 400MB of RAM this time, and had pretty much the same results.

The last time I checked the screen there was about 15 mins of the install remaining - and then system freeze.

The music I was listening to cut out abruptly, I still had control of the mouse, but couldn't click anything or use any keyboard shortcuts.   I've been able to install using virtualbox before now, but the ability to use VMWare properly would help me significantly at work, so I'd really like to get it to work properly.


EDIT:

I decided to go all out and try ANOTHER install.  This time I tried pressing F2, just to make sure there wasn't anything obvious in the bios I was overlooking - but alas it froze up on me instantly, and I wasn't even able to choose anything from the first menu.

So basically I've managed to crash Ubuntu several times this evening - all is not boding well.

---

