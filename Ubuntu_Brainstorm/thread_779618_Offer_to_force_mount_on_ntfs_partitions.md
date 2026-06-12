---
title: "Offer to force mount on ntfs partitions"
date: 2008-05-02
forum: Ubuntu Brainstorm
---

### Post by whitewizardcoder on 2008-05-02
When a ntfs partition isn't cleanly unmounted (with either Ubuntu or another OS), the logfile is altered so that Ubuntu can't mount the partition without the "force" option on the command line like such:
```
sudo mount -t ntfs-3g -o force [device] [mount path] 
```
This cleans the logfile and allows the partition to be mounted.  Currently, when a user wants to access a drive that wasn't unmounted cleanly, a dialog box is displayed saying that Ubuntu is unable to mount the volume.  If you click on details, the information about how to fix this problem is presented, but it requires the user to use the terminal.  Therefore I propose that Ubuntu either automatically use the "force" option when mounting external/internal ntfs partitions or give the user the option to attempt a forced mount if it fails the first time.

---

### Post by unityofsaints on 2008-05-03
+1. Definitely a worthwhile idea- I get this problem with my external HD all the time and it sure would be a timesaver having a button.

---

### Post by Gina on 2008-05-05
Another +1 from me.

---

### Post by smartboyathome on 2008-05-05
There is a down side to this. If the power went out and Windows was running, then someone booted up Ubuntu and tried to get files off of the partition, the drive could become unusable.

---

### Post by marine63 on 2008-05-07
+1 annoying little problem for me

---

### Post by whitewizardcoder on 2008-05-08
> **smartboyathome said:**
> There is a down side to this. If the power went out and Windows was running, then someone booted up Ubuntu and tried to get files off of the partition, the drive could become unusable.

I have tried both hard restarting my computer from windows and unplugging the power from my external hard drive (with an ntfs partition) without unmounting it cleanly and so far I have had a good experience with using the --force option (no data corruption).  I'm pretty sure that if Windows detects an error in a file (or several files) it automatically prompts the user to run a checkdisk on the partition.  Obviously, however, the "attempt to force" button should come with a strong warning to ensure user's understand what they are trying to do...

---

### Post by rogerdean on 2008-05-10
+1, but only with the safeguards in the last post...

---

### Post by dixelpixel on 2008-06-14
+1 from me too.

I cannot undo the unclean uninstall from windows and so far none of the force mount related code I have found on the forum seems to work. Unless I can solve it soon this problem can render my fairly expensive external HDD useless.

.dixpix.

---

### Post by smartboyathome on 2008-06-14
This probably wouldn't help then. Most likely, the partition is no longer recognised as NTFS as there is too much of it lost.

---

### Post by ChameleonDave on 2008-06-14
I disagree with this.  There is a reason why the force option is a force option.  It is risky.  Use it if you like.  You'll probably be OK.  But such things ought not to be the default.

If an NTFS partition is complaining, you should run CHKDSK on it in Windows before trying to rape it (sorry, force-mount it) in Linux.  And then you should probably reformat it to a sensible cross-platform filesystem like FAT or Ext2.

---

### Post by berthiggins on 2008-06-14
I usually use ntfsfix on the command line as this does a bit more than force a mount, this is usefull when you know that it is just because windows was not shut down properly or similar.
The syntax is sudo ntfsfix /dev/sdaX

It is part of the ntfsprogs suite from the repo I have used it for a while with no problems.

---

