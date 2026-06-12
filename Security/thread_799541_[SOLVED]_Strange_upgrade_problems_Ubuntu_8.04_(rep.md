---
title: "[SOLVED] Strange upgrade problems Ubuntu 8.04 (repost from installation forum)"
date: 2008-05-19
forum: Security
---

### Post by FruitCase on 2008-05-19
Hi list,

after a seemingly flawless upgrade i'm stuck with some strange problems. I'm a perpetual newbie so i don't know if my problems with the ubuntu installation are upgrade related, security related or otherwise?

My machine starts automatically in the middle of the night, every night, when i've switched it off. Where can i start to address this problem? When i switch it off i want it to remain switched off until i start it up. Where can i find a way to force it to remain switched off?

When i log in and log out the screen goes black, blank and i can't log in, apart from another box with ssh (or via nx). I can see the Xorg (xserver?) is running at nearly all CPU capacity. Only thing i can do is hard reset the machine. Reading the forums i can't find a solution that works, does anyone know any leads to what i can do?

Rkhunter finds modified files, like sudo, slocate, logger, mount, more, dmesg, whereis. Combined with the middle nightly startups spooky indeed, but it might just be upgrade related. How can i tell?

I consider dismissing the upgrade and falling back to the ol' and nice 7.10 version of ubuntu. What is wisdom here?

Thanks for helping me,
kind regards

---

### Post by Aearenda on 2008-05-19
The automatic turning on sounds like a BIOS setting - there's no way it could be caused by Ubuntu itself, unless it is actually failing to switch the machine off when closing down. Take a look through the BIOS setting at startup.

For the modified files, you could try reinstalling the relevant packages.

For Xorg, I would go into a recovery startup (from the GRUB menu), enter the command line and do ```
lspci | grep VGA
```Post the output here as the first step so we can see what Xorg ought to be doing. If it produces no output, just do 'lspci' and look for the line you think should be the video controller and post that.

---

### Post by FruitCase on 2008-05-19
Thank you Aearenda for helping me, great.

I will look through the BIOS settings, though i have no clue as to which setting might cause this (every night @ 1:43 exactly?). Also i can't remember changing the BIOS setting, and only after upgrading to 8.04 noticed the nightly startups - must be a causality delusion :)

I'm in the business of reinstalling the affected packages refered to by rkhunter now (in one sweep) as you proposed.


The lspci | grep VGA gives:

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

Perhaps relevant in my xorg.conf:
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
EndSection

Thank you again,
kind regards

---

### Post by Aearenda on 2008-05-19
Some BIOSes have a 'start up at hh:mm' setting - probably in the power management page. I'm not suggesting you did it - if there is substance to the rootkit idea, that could explain it. If you do find a setting and unset it, then it comes back, I'd suggest a complete wipe & reinstallation and virus check on your data files. Likewise if rkhunter still complains, for safety's sake.

I can't really help with the ATI driver since mine are all Nvidia. Several threads look relevant  - try searching for 'ati fglrx cpu black' with all open forums selected.
[http://ubuntuforums.org/showpost.php?p=4837735&postcount=21](http://ubuntuforums.org/showpost.php?p=4837735&postcount=21) looks interesting.
[http://ubuntuforums.org/showpost.php?p=4901004&postcount=11](http://ubuntuforums.org/showpost.php?p=4901004&postcount=11) or 
[http://ubuntuforums.org/showthread.php?t=785072](http://ubuntuforums.org/showthread.php?t=785072) or
[http://ubuntuforums.org/showthread.php?t=796139](http://ubuntuforums.org/showthread.php?t=796139) might help.
Also check that the monitor you are using is able to show the max resolution the ATI card is capable of. You could switch the driver from 'fglrx' to 'vesa' to verify that. EDIT: This is silly - I forgot your problem was at logout.

EDIT: BTW, on my system rkhunter's output looks like this:
```
sudo rkhunter --checkall --cronjob --report-warnings-only
Warning: Suspicious file types found in /dev:
         /dev/shm/pulse-shm-2884350722: data
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
```

I think these are ok. See [https://bugs.launchpad.net/ubuntu/+source/rkhunter/+bug/86153](https://bugs.launchpad.net/ubuntu/+source/rkhunter/+bug/86153), bearing in mind that Hardy has added Pulse for sound.

---

### Post by FruitCase on 2008-05-19
I found a setting /proc/acpi/alarm which seems to be related to the nightly restarts. I've set it to 2108, so perhaps in a 100 years this machine will start up somewhere. 

The reinstalls of the rkhunter reported files are done by means of apt-get --reinstall install <reported files>.

So, wonder how "the black screens after logout" can be resolved. Hopefully in the security department this thread can be marked as solved.

Thanks for helping me out! Excellent
Hope i can return the favour some day

---

### Post by Aearenda on 2008-05-19
Interesting - the acpi alarm would be the programmatic way to set the same settings as the BIOS gives access to. I wonder how it got set?? That's useful to know, so you have returned the favour already. 

I have modified /etc/rkhunter.conf on my system to suppress the spurious warnings that show up on my system, as listed in the edit to my previous post.

Good luck with the video driver, there are plenty of people around with ATI systems who should be able to give you a hand.

---

### Post by FruitCase on 2008-05-19
:)


onwards, Ubuntu Rocks!

---

