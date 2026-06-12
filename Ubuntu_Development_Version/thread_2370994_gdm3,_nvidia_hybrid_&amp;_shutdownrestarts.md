---
title: "gdm3, nvidia hybrid &amp; shutdown/restarts"
date: 2017-09-09
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-09-09
As seen here when using nvidia drivers on a hybrid machine, shutdowns & restarts can 'hang' many times at black screen/blinking cursor.
Happens normally at 'random', 100% of the time if doing a log out/in any time prior to shutdown/restart attempt.

workaround here is to hit ctrl+F7 at black screen, then it immediately  proceeds as normal..

---

### Post by BenginM on 2017-09-11
Hiya mc4man , When did this start to occur, since the installtion, or after updating nvidia driver or the kernel! which kernel base in use Now? try reinstallin' the kernel and see it that fix it. Do you experience the same behavior with a previous kernel ! the cause might not be a code in the kernel, could be a service, app , or a zombie process, So you may want to remove quiet splash from the default kernel boot line and reboot/shutdown to catch logs on the screen. 

Does it also hang if you reboot/shutdown in terminal !

Also, try switchin' to a different & lighter display manager , slim,xdm, lightdm . to see if the cause is gdm or not!

---

### Post by mc4man on 2017-09-11
I haven't checked in several days if still going on, (though my bug report is still open
It's from gdm, with lightdm this never happens.
Currently there are  a number of gdm only bugs, some of high importance.
Edit - removed bug link, it was systemd, not gdm

---

### Post by joshi2 on 2017-09-14
I too suffer from this issue. It's incredibly annoying. Ctrl+F7 does nothing.

---

### Post by mc4man on 2017-09-14
> **joshi2 said:**
> I too suffer from this issue. It's incredibly annoying. Ctrl+F7 does nothing.
I may have meant ctrl+alt+F7 give that a try...
I just installed nvidia on a fresh install & this wasn't occurring but I just updated gdm3, so maybe get current...

But I also hadn't enabled KMS for Prime Sync yet, once I did that the bug reappeared, just not as often..
So also see if the upcoming gdm3 update helps... or helps somewhat mitigate..

Are you using KMS for nvidia?

current bug on this
[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1715746](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1715746)

related bug on prime profiles (also gdm3
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1704781](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1704781)

---

### Post by joshi2 on 2017-09-15
> **mc4man said:**
> I may have meant ctrl+alt+F7 give that a try...
I just installed nvidia on a fresh install & this wasn't occurring but I just updated gdm3, so maybe get current...

But I also hadn't enabled KMS for Prime Sync yet, once I did that the bug reappeared, just not as often..
So also see if the upcoming gdm3 update helps... or helps somewhat mitigate..

Are you using KMS for nvidia?

current bug on this
[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1715746](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1715746)

related bug on prime profiles (also gdm3
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1704781](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1704781)

Thanks, I'll try ctrl+alt+f7 to see if that helps. Otherwise I'll stick to Ubuntu 16.04 LTS. That one works just fine, never hangs. I think the culprit is somehow related to systemd.

---

### Post by mc4man on 2017-09-15
> **joshi2 said:**
> Thanks, I'll try ctrl+alt+f7 to see if that helps. Otherwise I'll stick to Ubuntu 16.04 LTS. That one works just fine, never hangs. I think the culprit is somehow related to systemd.
It doesn't happen with lightdm though certainly systemd & gdm3 both seem to provide poor behaviors for users on irregular basis's
(- here sticking with 16.04.x as between gnome-shell & Wayland it's too restrictive & repetitive an environment for me..

---

### Post by joshi2 on 2017-09-16
> **mc4man said:**
> It doesn't happen with lightdm though certainly systemd & gdm3 both seem to provide poor behaviors for users on irregular basis's
(- here sticking with 16.04.x as between gnome-shell & Wayland it's too restrictive & repetitive an environment for me..

You were right. It was gdm3. Installed lightdm on Ubuntu 17.10. Zero hangs since. :)

---

### Post by mc4man on 2017-09-16
> **joshi2 said:**
> You were right. It was gdm3. Installed lightdm on Ubuntu 17.10. Zero hangs since. :)
If you're using a hybrid nividia (seems likely..) then if you didn't already you might consider doing this, should work ok with lightdm as it's working fine in 16.04.3

[https://ubuntuforums.org/showthread.php?t=2365449](https://ubuntuforums.org/showthread.php?t=2365449)

---

### Post by joshi2 on 2017-09-16
> **mc4man said:**
> If you're using a hybrid nividia (seems likely..) then if you didn't already you might consider doing this, should work ok with lightdm as it's working fine in 16.04.3

[https://ubuntuforums.org/showthread.php?t=2365449](https://ubuntuforums.org/showthread.php?t=2365449)

I'm using nvidia 340.102 drivers with GeForce GTX 275.

---

### Post by mc4man on 2017-09-16
> **joshi2 said:**
> I'm using nvidia 340.102 drivers with GeForce GTX 275.
Oh, so not applicable ..
So you were seeing this on a Desktop GPU?

---

### Post by joshi2 on 2017-09-16
> **mc4man said:**
> Oh, so not applicable ..
So you were seeing this on a Desktop GPU?

Yes. On my 8-year-old desktop pc.

---

### Post by mc4man on 2017-09-16
> **joshi2 said:**
> Yes. On my 8-year-old desktop pc.
Ok, so the bug I linked above, repeating here, it's pretty much what you get? Are you using xorg or wayland session?

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1715746](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1715746)

---

### Post by joshi2 on 2017-09-16
> **mc4man said:**
> Ok, so the bug I linked above, repeating here, it's pretty much what you get? Are you using xorg or wayland session?

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1715746](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1715746)

Yep, that bug is precisely what I get. Xorg, Wayland is not supported on old nvidia drivers.

---

### Post by mc4man on 2017-09-16
> **joshi2 said:**
> Yep, that bug is precisely what I get. Xorg, Wayland is not supported on old nvidia drivers.
Alright, I'll add to report. 
nvidia hybrid (optimus) users also can't use wayland if they wish to use nvidia drivers so atm Ubuntu's default session excludes  large class(es) of machines..

---

