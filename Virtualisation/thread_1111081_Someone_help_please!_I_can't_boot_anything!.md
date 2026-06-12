---
title: "Someone help please! I can't boot anything!"
date: 2009-03-30
forum: Virtualisation
---

### Post by enabulator on 2009-03-30
SOMEONE HELP PLEASE! I CAN'T BOOT ANYTHING!

(I'm writing this from my mom's pc)

First, apologies if this has already been covered.

I was trying to boot an existing winodws xp pro from a separate partition inside virtualbox.

I got virtualbox booting into my partition, but with a bsod.

Booting in safe mode in virtual box, it stalled before the bsod at hpdskflt.sys.

What I have done: (moved files from windows/system32/drivers to desktop):
mup.sys
hpdskflt.sys
agp440.sys
intelppm.sys

It then stalled on mup.sys - which I moved out of the drivers folder. (like I said above)

I somehow got into hp recovery (I don't remember how, but it wasn't with a cd). I let recovery boot up, hit browse, and hit cancel - I didn't OK to anything. It then reboot. But when I try to boot, there is no grub (I put the suse grub on ubuntu if that makes any difference). Also, when I try to boot from windows (since I can't boot ubuntu), it still crashes!

If someone could help me boot into something, that would be nice. If they could then tell me what to do to get it working in virtualbox, that would be great.

I hope that all that happened to ubuntu is grub got bumped of the boot priority or something. . . I'm no expert - I don't know what happened.

I don't even know how to fix windows if I could boot into ubuntu because I haven't been able to mount my windows partition after an unsuccessful boot.

BYW: When I could boot into them both I tried both PCI3 and PCI4, or whatever they are. I had primary ide channel and two other things under the ide controllers (I saw someone on this forum with kind of the same setup). I also had a separate hardware profile.

thanks

EDIT: If I can move mup.sys from my windows desktop to windows/system32/drivers, I should at least be able to boot windows. . . I cant boot into windows to do even that, though. . .

EDIT: I remembered I have a live ubuntu USB - I'm still not sure how to fix my system, though. . .

---

### Post by enabulator on 2009-03-30
I was able to boot ubuntu from a live usb and get grub working following instructions here::)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I was then able to move the file hpdskflt.sys (mup.sys was already in the drivers folder. . . must have copied instead of cut or something. . .)(for some reason I wasn't getting the usual permissions mounting error when trying to access my windows partition after an uncessessful boot):) from the desktop to the drivers folder. It now boots, but still kind of seems to stall at hpdskflt.sys before successfully booting from safe mode. I don't know if this is normall (It will boot normally also)

I still don't have virtualbox working, but for the main purpose of the thread, I'm good.

thanks to all who looked.

I don't know how to mark as solved. . .

---

