---
title: "Question about os-uninstaller and something else"
date: 2015-03-31
forum: Windows
---

### Post by knguye22 on 2015-03-31
So i have ubuntu installed on pc along with windows = dual boot. I want to remove ubuntu so i boot ubuntu live disk and type in a bunch of code to get os-uninstaller. Now I selected ubuntu and uninstall that. When I boot back in windows i notice there's a partition of where ubuntu used to be and it's currently in in use so i format that and merge it to my primary partition that contains windows. However i notice that it's missing some space like maybe 300-500mb not a big deal but that just irks me. Can anyone explain this phenomenon? Sorry this is another issue but my friend who mess around with his master boot record(doing this tutorial: [https://www.youtube.com/watch?v=JEbHPyHPNnU](https://www.youtube.com/watch?v=JEbHPyHPNnU)) is losing 200gb of space on his hard drive but when he boot ubuntu live cd he sees /dev/loop0 how can he remove that and restore his hard-drive original capacity?

---

### Post by oldfred on 2015-03-31
Is this two different Windows issues?
We are an Ubuntu forum.

If you want you can post this from the Ubuntu live installer's terminal.
sudo parted -l
sudo fdisk -lu

/dev/loop0 is the live installer, not your hard drive.

If just Windows these forums may be better?
 [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by Mark Phelps on 2015-03-31
> However i notice that it's missing some space like maybe 300-500mbThis could simply be a matter of partition alignment along cylinder boundaries.  IF you want detailed advice on this, then run Disk Management and check with one of the two forums that Oldfred suggested.

As to your second issue, again, this is a Linux forum, not a Windows forum.  You should check with one of those two forums.

---

### Post by knguye22 on 2015-04-01
Yes I know this is a "ubuntu" forum. But that's the problem is it not? I want to unisntall it so I use "ubuntu" live disc to uninstall it using the os-uninstaller. And yes this is 2 questions because both lumps is about uninstalling "UBUNTU". So after using the OS-uninstaller and merging windows with the recently uninstalled partition of ubuntu I see that the total space of my hdd is missing 300-500 mb. If you want I can draw it out for u of what I see and what i did. That was the first bit.
The second bit was my friend who did not use os-uninstaller and basically formated his hdd hoping to remove ubnutu. It worked I guess but instead of missing just only 300-500mb he was missing 200gb. So for this issue my question is how to fix this or if a fix is even possible? I told him get a new hard-drive.

---

### Post by oldfred on 2015-04-01
He certainly should not need a new hard drive.

But you have to post details not just general info if you want help. See post #2.

---

### Post by howefield on 2015-04-01
Thread moved to the "*Windows*" forum.

---

