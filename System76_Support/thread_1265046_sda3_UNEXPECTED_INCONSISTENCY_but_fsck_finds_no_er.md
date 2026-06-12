---
title: "sda3 UNEXPECTED INCONSISTENCY but fsck finds no errors"
date: 2009-09-12
forum: System76 Support
---

### Post by eaone2 on 2009-09-12
Hi,

I have a wild dog system with a 500G hard drive, running 9.04 64bit os.   Lately, I have been getting the following errors when I restart the system.

/dev/sda3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
fsck died with exit status 4

so I boot the machine with a live CD, make sure sda3 is unmounted, and ran fsck.  here is the result
ubuntu@ubuntu:~$ sudo fsck -f /dev/sda3
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda3: 16969/58753024 files (12.5% non-contiguous), 5600467/117484585 blocks

then I restart the computer with the hard drive and it went fine.  From within nautilus, I restart the machine. I got the "unexpected inconsistency" message again upon reboot .  If I resume the system boot, I would get to the normal login screen.  This process can be replicated consistently.

Is there anything wrong with the hard drive?  I have been thinking about adding windows to the system.   But if the hard drive is bad and can't be repaired, it may damage the disk if I try to repartition it.  Any advice on how to get to the root of the problem?  Thanks in advance for your help.

---

### Post by thomasaaron on 2009-09-14
Try booting from the live cd and running...

sudo fsck -y /dev/sda3

---

### Post by eaone2 on 2009-09-15
Hi Tom,
here is the result from running the fsck command via live cd.
```

ubuntu@ubuntu:~$ sudo fsck -y /dev/sda3
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda3 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda3: 18046/58753024 files (13.5% non-contiguous), 5611835/117484585 block
```

I then reboot the box with the hard drive.  the first time it hanged (which happened before and i doubt it is related to the live cd or fsck command).  I then restart the machine by mean of the power button.   Here is the error message I got

```
/dev/sda1: unexpected inconsistency; run fsck manually
fsck from util-linux-ng 2.16
/dev/sda1: super block last mount time (..... now = ....) is in the future

/dev/sda1: unexpected inconsistency; run fsck manually
/dev/sda3: super block last mount time (.... now = ... ) is in the future

/dev/sda3: unexpected inconsistency; run fsck manually
init: mountall main process (1234) terminated with status 2
rm: cannot rem `/forcefsck`: read-only file system
init: mountall post-stop process(1612) terminated with status 1
filesystem check failed
a maintenance shell will now be started
```

The machine hanged again.  so I repeat the power cycle process and got to the logon screen.  

Any other suggestion?  Do you think the kernel is corrupted?  I still can't tell if there is a problem with the hard drive or not.  Please advice.  Thanks for your help!

---

### Post by Yumi on 2009-09-15
I updated Karmic two days ago. First it went find, then just what you describe. It is not our harddisk I believe. I did a fresh install and still the same problem.

There is a bug report Bug #423247 which seems to relate to this problem. Have not found a way round it, but might try

#16   	 smurf  wrote on 2009-09-14:

the big problem is that there is no way to set/unset UTC time, gnome utlities for clock settings are not properly working.
I fixed the problem editing /etc/default/rcS, UTC=no.


Michael

---

### Post by thomasaaron on 2009-09-16
Please try booting into your account (i.e. *not* with a live CD) and running...

```
sudo rm /forcefsck
```

See if that fixes the problem.

It appears that you have some problems with your filesystem, a gap between data that fsck may not be able to fix. That's not really all that big of a deal in this instance. The above command, though, may stop the system from trying to run fsck all the time.

---

### Post by eaone2 on 2009-09-19
Hi Tom,

the rm command returns "cannot remove `forcefsck`: No such file or directory.  I booted the OS from my hard drive.  Anything else I can try?

Also, the disk usage analyzer reported that sda3 is 90% used with 21G.  I have a  500 G hard drive.  df reported sda3 has 462G disk space and 21G is used.  I read reports that disk usage analyzer returns incorrect result.  

If there is a bad block on my hard drive, is there a way to tell the size of the bad block?  Also, is it save for me to repartition the hard drive to install windows?

Thanks!

---

### Post by eaone2 on 2009-09-21
I could not resist the temptation and went ahead to create a new XP partition with the instruciton on [http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

I was at the very last step where I finished updating grub and reboot the machine.  2 things happened:
1. when i boot windows, I got
```
Error 13: Invalid or unsupported Executable Format.

Press any key to continue.
```

2. when I boot ubuntu, I got the same error as I mentioned in my previous postings (inconsistency, run fsck manually...).  Unlike last time, before I repartition sda3, I can no longer get pass the error via power cycling.   I kept getting to the same stage where I was ask to get to a root shell to run fsck manually.  

The current status is that XP is now being booted automatically.  I cannot boot from grub to XP.  I cannot get in to my linux OS.  The only thing I can do is to mount sda3 manually to read some files.

Can I still salvage my linux partition?  Is the hard drive corrupted?
thanks in advance for your help!

---

### Post by thomasaaron on 2009-09-21
It sounds like Windows created its own Master Boot Record (which of course would not incorporate your Ubuntu installation). If you're well backed up, you might just want to re-install Linux. You will have to manually delete the linux partitions from the Live CD during the installation process. 

When you do this, Ubuntu will recognize your Windows installation and create an MBR so that it includes Windows in your boot-up menu.

If you don't want to do this... did you run the "Reinstall GRUB Bootloader and MBR (Master Boot Record) " section of the dual-booting tutorial? That should have set the MBR up correctly.

---

