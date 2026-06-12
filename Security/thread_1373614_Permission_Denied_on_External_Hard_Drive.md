---
title: "Permission Denied on External Hard Drive"
date: 2010-01-05
forum: Security
---

### Post by goodlukeing on 2010-01-05
I have recently bought a new laptop, installed my first linux OS on it (Ubuntu 9.10) and an external hard drive with 500GB on it for backup. For the first few days my external hard drive was working fine, but then eventually it wouldn't let me copy/move/delete stuff to and from it. So I kept trying to change the permissions but it wouldn't let me.

I figured this would be a very very common problem, so I looked up some forums to try out the methods but they didn't work. So I thought I would ask you guys for help because I am pleased with the support. I wouldn't think this would be a hard problem to solve.

PS: I would prefer a more GUI-driven approach, but if not well I guess I can't argue.


BTW: First impressions of Ubuntu (not including trying to get windows programs to work through wine) are very high.

---

### Post by drs305 on 2010-01-05
> **goodlukeing said:**
> I have recently bought a new laptop, installed my first linux OS on it (Ubuntu 9.10) and an external hard drive with 500GB on it for backup. For the first few days my external hard drive was working fine, but then eventually it wouldn't let me copy/move/delete stuff to and from it. So I kept trying to change the permissions but it wouldn't let me.

What type of formatting are you using on the new drive?  The external drive should mount automatically.

If you post the results of the following we may be able to figure out what is happening, or if not, construct an fstab entry that should make you the owner.

```

sudo blkid
cat /etc/fstab
mount # with the drive connected

```

Also tell us the mountpoint/name you would like for the drive if we have to make an fstab entry.

---

### Post by goodlukeing on 2010-01-06
The external drive does mount automatically. But as far as format I don't know, so here is what came out for the external drive:

/dev/sdc1: LABEL="My Passport" UUID="4A75-97DA" TYPE="vfat" 

I'm guessing that means fat32 format or something?

---

### Post by BkkBonanza on 2010-01-06
Normally you should be a member of the usbfs group to have use of usb filesystems. Type the command "id" and check the groups listed to be sure you are.

It sounds like something related to permissions has been messed up because in a default install you should have no problems with permissions on an external usb drive. 

The output of your /etc/mtab file would indicate if there were unusual filesystem options on that device.

While the drive is mounted,
cat /etc/mtab

---

### Post by goodlukeing on 2010-01-06
When I typed "id" there was no usbfs listed anywhere. What am I looking for when I do "cat /etc/mtab"?

All I know is when I click on properties when in the drive and go to the permissions tab it says:

[INDENT]Owner: luke - Luke
Folder Access: Create and Delete Files
File Access: ---

Group: luke
Folder Access:
File Access:---

Others:
Folder Access: None
File Access:---
[/INDENT]

---

### Post by BkkBonanza on 2010-01-06
Assuming your username is "luke" then that appears to be normal.

Usually the id command would output a list including "groups=" and a bunch of group names. On my system usbfs(1001) is one of the groups. I'm not sure that is the default but I think it may be. In which case the easiest way to for you to fix that in the gui would be to use menu item System, Administration, Users and Groups and select Manage Groups and find the usbfs in the list and add your name to that group.

For /etc/mtab it will list the various current mounted filesystems. You should see one in the list for your external drive. On that line there will be details of the mount like type=vfat and options=... this info may be useful in figuring out if it was mounted incorrectly.

---

### Post by goodlukeing on 2010-01-06
Ahhh Users and Groups....................what does it mean if I can't find usbfs in the list?

Well this is what came under the cat /etc/mtab thing:
```
/dev/sdc1 /media/My\040Passport vfat rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0

```

---

### Post by BkkBonanza on 2010-01-06
That mtab entry appears fine.

You should have usbfs mounted at boot. Check your /etc/fstab file has an entry,

none 	/proc/bus/usb 	usbfs 	devgid=1001,devmode=664 0 0

If it's not there then somehow it got messed up and needs to be fixed. It's possible the values may be different - I just output mine here as an example. The devmode=664 indicates that the device is read/write for owner/group (you?) but read only for other users. In my case the devgid indicates the device belongs to group 1001 which on my system is "usbfs".

You can use,

cat /etc/group

to list your groups and should see usbfs listed in there. Sorry for all the command line stuff but it's usually required when something gets messed up.

---

### Post by goodlukeing on 2010-01-06
Ok I checked that file and theres no trace of a usbfs thing in there at all, only cdrom. So if that means it's messed up, how would I go about fixing it.

---

### Post by BkkBonanza on 2010-01-06
I'm not sure at all the missing usbfs is the problem. I think you could add that entry and add a group but it may not help. The reason I say that is that I think on my system the usbfs may have been added by another program, and is not the default. 

The properties dialog indication you have in your permissions for the drive seems to show that you do have permission and that wouldn't be true if this was the problem. I think the next step is to look in your logs for hints of why the drive isn't behaving as expected.

You can view various logs in menu item System, Admin, Log File Viewer. In particular syslog and messages may have something. You'll want to look for entries near the end that are related to /dev/sdc1 and/or permissions. Anything you think may be relevant you should post as the exact wording will be important.

---

### Post by cariboo on 2010-01-06
I think the group you are looking for is **plugdev**, Have a look [here]("http://wiki.debian.org/DebianDesktopHowTo") for more on plugdev.

---

### Post by goodlukeing on 2010-01-06
Ok, I didn't expect the problem to be this hard. But I tried to change the permissions and then looked at the file and it said this (whatever it means?):

```
Jan  7 12:46:37 Luke kernel: [21491.450776] FAT: Filesystem error (dev sdc1)
Jan  7 12:46:37 Luke kernel: [21491.450786]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan  7 12:46:37 Luke kernel: [21491.450794]     File system has been set read-only
Jan  7 12:46:37 Luke kernel: [21491.690710] FAT: Filesystem error (dev sdc1)
Jan  7 12:46:37 Luke kernel: [21491.690715]     fat_get_cluster: invalid cluster chain (i_pos 0)
```

---

### Post by goodlukeing on 2010-01-06
Oh sorry, didn't see the 2nd page. I went to user groups in administration and it says I am already in the plugdev group thing.

---

### Post by BkkBonanza on 2010-01-06
That log message indicates that your drive has been corrupted and got an error. When that happens it gets set to read-only for safety. So the problem isn't permissions but that you need to fix the file system on the drive.

What you need is called chkdsk on Windows. You could mount it on Windows and run chkdsk or on Linux there is the dosfsck tool that will fix it as well.

You need to unmount the drive, using the icon and right click, or at cmd line,

umount /dev/sdc1

and then run the disk repair,

sudo dosfsck -a /dev/sdc1

You will see some messages as it repairs. No guarantee it will be successful but with luck your drive will be fine after. Then unplug and replug it in and see how it works.

---

### Post by goodlukeing on 2010-01-08
IT WORKS!!!! I don't know what that command actually did, but it fixed the problem, now I can move and delete stuff from the drive. Thanks a lot, I'm amazed that you returned to the forum days after I did the first post, the support for ubuntu is amazing. I am really starting to love this OS, wish I found out about it sooner. Cheers.

---

### Post by BkkBonanza on 2010-01-08
It's just community based. If I help people then I think eventually when they gain knowldege they'll help others too. 

So hope someday you'll contribute some back when you can. I just come and help out when I'm bored and have nothing better to do. Lately that's been more than usual.

---

### Post by Dr. Moreau on 2010-01-08
Thanks from me, also.  I had the same problem, perhaps caused by a brief encounter with a Windows 7 machine corrupting the boot sector.  Easy fix, thanks again!

---

### Post by BkkBonanza on 2010-01-08
Usually an external drive gets corrupted by removing it or cutting power before the data has been sync'd to disk fully. To be safe always be sure to unmount the drive first, it'll usually give you a message that it's safe to remove the drive. If not then give it a few seconds anyway before removing it.

---

### Post by ecosseman on 2012-04-08
Tried instructions from BKKBonanza (#14), thanks, but no success.
*In terminal type:* sudo nautilus
Follow prompt ...access to all folders and files, and to delete.

---

### Post by coffeecat on 2012-04-08
Old thread - closed.

@ecosseman, if you need help, please start your own thread giving all details. This one concerns a now-obsolete version of Ubuntu.

---

