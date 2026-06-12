---
title: "Help! please, my system has gone..."
date: 2016-05-30
forum: Ubuntu Studio
---

### Post by andrew-q2 on 2016-05-30
In summary, I just upgraded Ubuntu Studio from 14.01 (I think) to 15.10 and now I get "flu" terminal prompts instead of the proper system.
Detail: Running on a Dell Latitude E5530 Intel Core i5 3320M.  It has a win XP system, an Ubuntu "ordinary" system, and an Ubuntu Studio system, 3 systems on the one hard disk.  Today I updated the 14.04 studio system, then saw the 15.10 system shown as an upgrade, so chose it.  It was installing ok then said xscreensaver or something else was blocking something and to stop or restart it, so I went to task manager and stopped xscreensaver. (Restarting it led to a similar blockage so left it stopped.  I couldn't see the other item mentioned (x....?) .
Then it continued upgrading for a while and I got on with something else.  When I came back I had a blank screen with a cursor top left.  The disk was doing stuff but the mouse had no effect.  I left it a while but nothing changed except the disk stopped doing anything much, so I forced a close down via the power button.
On re-booting, the "grub" menu is still there and the ordinary Ubuntu system will boot up, but the Studio one won't.  I get the blank screen with a "flu" prompt.  I can log in, leading to a <username>@flu:~$ prompt, but I have no idea what to do now.
P-l-e-a-s-e can anyone explain how to get it working again.  My audio files still seem to be present (via the other Ubuntu) so that's good.  I'd like to keep them if poss.  I don't know much about Ubuntu (as you may have realised!) so please go slowly with any instructions!  I use Studio for running JACK and ARDOUR audio recording, nothing else really.
Thanks, Andrew

---

### Post by QDR06VV9 on 2016-05-30
Just a guess here but did you uninstall any proprietary drivers (Hint Nividia) before doing the the upgrade?

---

### Post by oldfred on 2016-05-30
Your XP install is crippling your system.
XP will not boot with AHCI, it has to have IDE. But IDE is really only for compatiblity with very old systems.
About 5 years ago I got my first SSD and for trim to work had to change to AHCI. And XP stopped. Or it stopped permanently. :)

From Ubuntu live installer run this:
       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Often best to stay with LTS versions. You can upgrade from 14.04 to 16.04, but it will not offer it directly until 16.04.1 is out.
Your new 15.10 will expire in July, 2016 or not long.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by andrew-q2 on 2016-05-30
Thanks for this.
No, I didn't uninstall any.  You say "proprietary" - I don't think I've installed any drivers myself.  As far as I can remember, I just took the official install image originally, and used that.
What do you suggest now, please?  Will I need a total re-install do you think?
Thanks, Andrew

---

### Post by andrew-q2 on 2016-05-30
hi Oldfred, thanks for the above.  I've produced the sys info and it is here - [http://paste.ubuntu.com/16852135/](http://paste.ubuntu.com/16852135/)
I don't use the XP much so maybe I should re-build the laptop when I get time.  (I think I'd need to set AHCI in the Bios then re-install the two Ubuntus - does that sound about right?)
Andrew

---

### Post by oldfred on 2016-05-30
You should not have to reinstall Ubuntu if just turning on AHCI.
I might just use old XP partition as a data partition.

Summary report looks ok, you have a lot of kernels in both installs. Best to keep only two, most current and one backup. I typically let it grow to 3 or 4 then pare back to 2, but I have lots of room in / for kernels.

At end of script it mentions duplicate sources and 12.04, but all your kernels are 3.13 in both installs which would be 14.04.  But partition entry at top says 15.10, so upgrade did not complete. Probably better to have just gone to 16.04 or wait until 16.04.1 is out. That will be about the same time 15.10 become obsolete.

Can you boot recovery mode in the install in sda9? Under advanced options in grub?

---

### Post by andrew-q2 on 2016-05-31
SDA9 recovery mode: yes, under Advanced there are 4 rec. choices, presumably the kernels you mention, 3.13.0-86, -55, -36 and -32.
If I go into -86, it seems to execute a script for several seconds, then I'm left with an Ubuntu 15.10 flu tty1 login prompt.
If I go into -55, it's the same, 15.10 flu prompt.
I didn't try the other two.

---

### Post by andrew-q2 on 2016-05-31
hi again, have now removed 7 old kernels from my ordinary Ubuntu system!
This hasn't made the Studio system work - didn't really expect it to - just wondered if boot space was shared or something...
Andrew

---

### Post by oldfred on 2016-05-31
The recovery mode should be the most current kernel but give you a menu for several repair options. Often have to go to terminal with Internet on and run various commands to finalize update.
Or from live installer or your other working install, we may have to chroot into your install and repair it.

---

### Post by andrew-q2 on 2016-05-31
Thanks again.  The above sounds messy!  I could re-install Studio, providing a) I can be pretty confident it won't write over the XP and normal Ubuntu partitions, and b) I can copy off my audio projects.
I am getting the latest Studio, 16.04 LTS, and will report back when I've seen what options it provides re. (a).

---

### Post by oldfred on 2016-05-31
When you say projects are these files or programs you have installed?
Your normal backup of /home saves your files and user configurations. If you did system wide configurations they may be in /etc.
But if you have installed lots of applications, you have to export that as a list. I think that only works from a working system. Not sure it even works from a chroot.

There is a "dirty" install. You use Something Else but do not tick the format option. All system settings or default files that Ubuntu installs will be overwritten, but anything that is yours is not overwritten. Still much better to have good backups.
Normally dirty install not recommended as a lot of the files that you should be housecleaning, but many are not are also left. Old kernels, log files etc remain also. But settings in /etc are changed.

       Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872) 
    
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by andrew-q2 on 2016-05-31
hi oldfred,  I'm putting this on the back burner for now.  I've been talking to Ardour users just now about some s/ware issues, and they've persuaded me that AVLinux would be a better solution for my purposes, rather than Studio, so I'm going to try installing that.  **Thanks for your help**.  Andrew

---

