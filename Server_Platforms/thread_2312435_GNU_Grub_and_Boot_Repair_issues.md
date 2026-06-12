---
title: "GNU Grub and Boot Repair issues"
date: 2016-02-04
forum: Server Platforms
---

### Post by nate41 on 2016-02-04
Hi all -- new to the forum with a challenge that I am hoping someone can help me with.

First - hardware details:
Dell Poweredge 2850
Raid 5 with (4) 300GB HDD's, (1) 73GB HD in 5th slot (unused), and a tape backup drive in the 6th slot (also unused)
Had been running this server with Ubuntu (I believe 12.04 was installed originally in 2012) as a file sharing server successfully for about 3 years or so.  

I moved over the summer.  Shut down the server, moved, and the server sat for a while.  Reconnected everything about 2 months ago to get to a few files, without issue.  Shut down and again disconnected everything.

Two days ago, I again reconnected the server, and found on boot, that two drives were flashing amber, indicating faillure, and one drive was alternating green / amber, indicating pre-failure.  I created a Dell Support live image DVD with a Centos 7.0 Image.  Rebooted to the DVD drive, went into the log, and determined that Drive 1 entered fault state first, then Drive 0.  I forced Drive 0 online, and used it to rebuild Drive 1.

Then, upon reboot, all drives function normally (one still alternating green / amber indicating pre-failure), but I get the GNU GRUB version 1.99-21ubuntu3.18 screen.

Following other directions that I found on this site, I created a UBUNTU 12.04.5 LTS live image desktop CD.  Booted to the DVD drive, connected to the internet, downloaded the Boot Repair tool, ran the tool, and got an 'Error Occurred During Repair' message.  

The URL listed was 

[http://paste.ubuntu.com/14877316/](http://paste.ubuntu.com/14877316/)

When I re-booted without the UBUNTU live image DVD, it goes right back to the GNU GRUB screen.

I am NOT a network guy by any stretch, obviously.  I had been using this server to store and access music and photo files (i'm an amateur photographer) as well as managing some business related files.  I NEED access to these files again, and any help would be greatly appreciated!!!

Forgot to mention -- server and UBUNTU install were 64 bit.

---

### Post by yancek on 2016-02-04
Your boot repair link is broken.

---

### Post by nate41 on 2016-02-04
Linky fixed . . . .

---

### Post by nate41 on 2016-02-04
I am off to work, but will be available to tackle any suggested solutions when I get home in about 6 hours.  Thanks to all in advance for any and all help!!

-Nate

---

### Post by oldfred on 2016-02-04
Moved to sever sub-forum.

 I do not know RAID, as there are so many different types, and I do not use any of them.

Script sees this as your RAID, so a hardware RAID:
/dev/sda:900GB:scsi:512:512:msdos:MegaRAID LD 0 RAID5 858G

You show Windows partitions also?
They could not be mounted, either hibernated or corrupted. If needing chkdsk you can only do that from Windows and no idea with RAID if the same way to run chkdsk as with standard partitions or not. But may take 5 times longer?

Do not know RAID, but other issues shown are way too many kernels and duplicate sources list issue.

---

### Post by nate41 on 2016-02-04
No, no Windows partition.  I purchased the server without an OS, and decided to install Ubuntu as the OS, as it was open source, and would do what I needed.

Really, I'm looking for help with just getting the server back to the point where it will boot into Ubuntu. . . . I haven't really done anything special other than rebuild one of the drives on my array. . . .

I am wondering if part of the boot file was located on the drive that I rebuilt, and thus I've lost it??  Is there a way to replace the boot sequence file such that it will boot correctly back into my OS?

Essentially, I need help with the details of what I need to do to make things right again. . . . .

---

### Post by nate41 on 2016-02-04
I've also read that some other folks have had success with going into BIOS and changing the boot sequence such that it looks for the boot file on another of the HDD's. . . .would that be a better approach to start off with?

---

### Post by oldfred on 2016-02-04
Is link still not correct as it shows these standard Windows partitions.
>  /dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   572,454,911   572,248,064   7 NTFS / exFAT / HPFS



Boot-Repair tried reinstalling grub, but had error. It should be 0 at end:
/usr/sbin/grub-install /dev/sda: exit code of grub-install /dev/sda:1

But some RAID installs to the root of RAID, not sda?
And that is where I do not fully understand all the versions of RAID. Hardware RAID may just look like a standard one drive configuration?

---

### Post by nate41 on 2016-02-04
The link is correct.  I don't know anything about partitioning. . . .but I can tell you that the server does not have windows on it.  It has Ubuntu.  It may have had windows on it at one time and perhaps those are remnants of a prior install?  Not sure how the installation of Ubuntu works and if it wipes the drives or not.  Regardless, the link is correct.  

An someone out there please help??  I know that there are server users out there with multiple HDD's in RAID configurations that must have run into things like this before. . . .

Thanks

---

### Post by darkod on 2016-02-04
First, you don't have "drives" any more, you have raid array(s). Touching boot order in bios can't help you since the raid controller is presenting your array(s) as devices to the OS. You can not boot except from the array.

Second, those ntfs partitions take about 300GB of your array, which is about one third. If you are happy leaving that space unused, OK. But you should really look into that if you want better usage of the server.

I don't know how familiar you are with raid, but the raid5 can't work with two members failed. You had two disks with amber light. Then you forced one to go online. Depending how "close" the data on that disk was to the two good disks, some parts of the data might have gotten corrupted by forcing it online. After that you rebuilt with the fourth disk but the damage (if any) was already done by forcing one disk from out of sync to come online.

It might be as simple as intending to reinstall grub (even though the script failed). And talking about the bootinfoscript. I have very high respect for it but I do not like running "one size fits all" automated scripts on production servers. And any server that is being used is a prod server unless it is only for testing. Do you know what the script will do, the exact actions, to run it on a prod server???

Learn the specific commands you need for your environment and stick to them... Don't run scripts not designed for your environment. That's IMHO...

Back to the grub reinstall. Use your ubuntu live cd, boot into live mode and in terminal try reinstalling grub (if you are booting from usb make sure which device is the array, here I assume it's sda like in the script):
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and see if that helped. If it didn't, there is a more complex procedure to try. Basically it is chrooting into the installation from live mode, and completely reinstalling grub like that.

---

### Post by nate41 on 2016-02-04
Thanks Darko -- I'll give that a shot. . . .

---

### Post by nate41 on 2016-02-04
Nope, no luck.  Booted fine, but right back to the GNU GRUB screen.

---

### Post by oldfred on 2016-02-04
I agree with Darko, with a server you need to learn about it. 
But Boot-Repairs' script is useful just for its report to see details of your configuration which helps us figure out best way to repair it.

But the script did not even show a grub.cfg which with all those kernels should have been huge.
And the error was on the sudo update-grub which really runs this:
/usr/sbin/grub-mkconfig

---

### Post by nate41 on 2016-02-04
So, what's my next course of action?

---

### Post by darkod on 2016-02-05
Since you say the grub menu does come up, it is probably best to work directly from there, not using the live cd at all. In the grub menu try selecting the Recovery Mode entry (it is usually the second one). That should open a submenu with more options.

Look for the option called "drop to root shell" and select it. That should load a command prompt as root (so you don't need to put sudo in front of system commands). However it loads as read-only and you have to remount the root partition as read-write. You can do that with:
```
mount -o remount,rw /
```

Each reboot, each time you go into this shell, you need to do that if you want to be able to make changes to files. So remember it...

From there on, first test if internet access is working good. Simplest way is to try updating the apt cache:
```
apt-get update
```

If that didn't return errors, it works good. Next try to simply recreate the grub config, in case something is messed up:
```
grub-mkconfig
grub-install /dev/sda
update-grub
```

Now reboot and see if it made any difference. For rebooting from the root shell you can simply enter 'reboot' and hit Enter.

If the normal boot didn't work after this, go into recovery again, remount the partition as RW again (as above), and lets try completely removing and reinstalling grub:
```
apt-get purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
grub-install /dev/sda
update-grub
```

See how that goes and if it returns any errors. Reboot to test if it helped you make the server boot normally.

let us know...

---

### Post by oldfred on 2016-02-05
Are you getting grub menu, or grub rescue> or just a grub> which are grub command lines/terminal not Ubuntu system terminal. 
Grub's terminal has just a few commands and cannot run full system commands.

---

