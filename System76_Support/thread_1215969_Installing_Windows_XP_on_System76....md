---
title: "Installing Windows XP on System76..."
date: 2009-07-17
forum: System76 Support
---

### Post by Cadeyrn on 2009-07-17
Seems to be a stupid idea. I tried it, and it didn't work.

It installed just fine, but now whenever I start it up I get that popular corrupt hal.dll message and can't start up. I know it's simple to fix this, but not for me--I've tried everything. I've tried both methods of replacing it from the disk in the recovery console, I've tried replacing it through Ubuntu, I've tried rebuilding, deleting, and replace boot.ini, and I've tried a download of hal.dll, but it all doesn't work. I think the computer automatically corrupts hal.dll whenever it starts up.

And this is pretty important because the Windows installation told me it rendered my main Ubuntu installation inactive, and the only way do undo this is to go into Device Manager. I can't access Device Manager until this problem is fixed, and the whole inactive thing was not fixed by using GParted to move the boot flag back. When I try to boot into my main Ubuntu installation, it says "Operating system could not start" and hangs there.

---

### Post by MorphWVUtuba on 2009-07-17
Did you install Windows after installing Ubuntu?

---

### Post by Cadeyrn on 2009-07-18
Yes.

Actually, nevermind. After a day and a half of trying to get Linux working I eventually succeeded.

To any of you who have this same problem, deleting the Windows partition should leave your Linux grub with error 22. To fix this, boot into an Ubuntu LiveCD and reinstall grub--Googling "Grub error 22" should find numerous grub reinstallation guides. The reason why I took a day and a half is because Windows changed the position of my Linux partition from /dev/sda2 to /dev/sda3, and grub wasn't notified of this. I couldn't find out how to change which partition (hd0,2) refers to, and simply telling grub by editing menu.lst didn't do it, so eventually I managed to use GParted to create a partition to the right of sda2, aptly named sda3, copied my sda2 into sda3, and deleted sda2, and it works now.

---

