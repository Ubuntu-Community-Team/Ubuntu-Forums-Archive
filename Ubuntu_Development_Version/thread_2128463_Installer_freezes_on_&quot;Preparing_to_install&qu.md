---
title: "Installer freezes on &quot;Preparing to install&quot;"
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by The Cog on 2013-03-23
Has anyone else seen this? Anyone know a fix?

I'm trying to install the Xubuntu Raring beta. I get as far as the first page of the installer with checkboxes for whether to install 3rd-party software, and whether to download updates while installing, click Next and nothing happens except I get the spinny wait-for-it mouse cursor. I've watched it for over 20 minutes before giving up. This happens on both 32-bit and 64-bit installers (dd the iso image to a flash stick), and whether or not I choose nomodeset. 

If I choose to install 3rd party drivers I can see that it fetches nvidia310 in the background, so at least part of the installer is alive. Other than that, choosing to install 3rd party or not, choosing to download updates or not makes no difference, and neither does unplugging the network cable completely.

The same 32-bit installer worked perfectly on my netbook, so the install stick is OK and it's not all machines that have this trouble.

---

### Post by kansasnoob on 2013-03-23
Maybe this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

---

### Post by monkeybrain2012 on 2013-03-23
[http://ubuntuforums.org/showthread.php?t=2089533](http://ubuntuforums.org/showthread.php?t=2089533)

Work around in post #6 worked for me.

---

### Post by The Cog on 2013-03-23
Thanks for the replies.
There's an interesting note in kansasnoob's link that suggests mounting all the partitions before starting the installer. I tried that (simply by launching gparted, which then mounts everything it can find) and that seems to have domne the trick. After a few seconds, the installer says there are mounted partitions and would I like to unmount them. I said yes, and carried on. 

The partitioner has another bug though - I chose "something else" and opted to install on sda7, not resizing it, just reformatting and using as /. I got a popup warning that the resize could take some time. I clicked Cancel to return to the partition editing screen, and then carried on normally. Typing this as the installer copies the files across.

@monkeybrain2012
I tried a live upgrade earlier without success. Thanks for the suggestion though.

---

### Post by buzzingrobot on 2013-03-23
> **The Cog said:**
> 
The partitioner has another bug though - I chose "something else" and opted to install on sda7, not resizing it, just reformatting and using as /. I got a popup warning that the resize could take some time. I clicked Cancel to return to the partition editing screen, and then carried on normally. Typing this as the installer copies the files across.



I've seen that several times in earlier releases. If you don't cancel, it will go ahead and "resize" the partition.

---

### Post by The Cog on 2013-03-23
Posting from a shiny new Xubuntu 13.04. Maybe imagination, but it feels faster.
The fix for me was to launch gparted (which mounts all the partitions it can find) before launching the installer.

Thanks again for the help, folks.

---

### Post by The Cog on 2013-03-23
I take it all back. Although I managed to install 32-bit, the 64-bit install has the same problem even with all the partitions mounted. - I can't get past preparing to install. 
I had a look with htop, and ubiquity is a mess. Even when you cancel the installer, it leaves a bucket-load of processes running.

---

### Post by kansasnoob on 2013-03-23
> **The Cog said:**
> I take it all back. Although I managed to install 32-bit, the 64-bit install has the same problem even with all the partitions mounted. - I can't get past preparing to install. 
I had a look with htop, and ubiquity is a mess. Even when you cancel the installer, it leaves a bucket-load of processes running.

Ubiquity has been a mess since mid November. IMHO nothing is more important than installation when it comes to any OS, and changing to "cadence" testing rather than Alpha and Beta builds has been a disaster.

At least Lubuntu is trying to keep the alternate images alive :)

---

### Post by The Cog on 2013-03-23
I agree, dropping the "alternate" install images was a totally brain-dead idea. A working text installer is sooo much more useful than a non-working graphical failure. If anything, they should have dropped the graphical installer. I think maybe Lubuntu is sticking with the text-mode installer because they are aiming at low-end PCs which may not have enough RAM to support the GUI one. But I think the best reason to keep the text installer is *because it flaming works!*

Anyway, I finally have the 64-bit installed. The secret was to mount all the partitions (using gparted's auto-mount). I discovered that for some reason, it didn't mount sda9 so I mounted that manually, and then manually un-mounted **only** the partition I wanted to install to. Then launch the installer, and when it asks if I want to unmount the other partitions, say No. So I'm marking the thread solved again.

---

### Post by rjw1678 on 2013-03-24
Tried mounting all partitions except for my 3rd hard drive(which did not have any partitions).
Said 'no' when the installer asked if it wanted me to let it unmount the partitions.
Then the install worked and now I have 13.04 64bit on my 3rd hard drive.
Thanks for all your info everyone.

Thank you,
Bob W.

---

