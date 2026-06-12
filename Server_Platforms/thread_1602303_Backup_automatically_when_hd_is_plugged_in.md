---
title: "Backup automatically when hd is plugged in"
date: 2010-10-21
forum: Server Platforms
---

### Post by twitterritter on 2010-10-21
I am supposed to write a script that backups a share on a server, when the correct hard drive is plugged in.

I have two shares in total and there are also two external hard drives. The server is used by two different organisations that are not supposed to have access to the data of the other one(at least not as normal users).

The script I need should run in the background of the server and when a drive is plugged in, it should check, which organization the drive belongs to, and depending on who the drive belongs to, backup the respective share.

When the drive belong to neither, it should just do nothing.

Unfortunately, I have no clue about scripting and so this makes writing a script like that, at least for me, impossible.

So I wanted to know if somebody could name some good websites for learning to write such a script or give tips.
Of course if somebody wants to write an example script for me to use, I'll gladly use it.

Thanks

---

### Post by rubylaser on 2010-10-21
This is an older post, but this is the idea you're trying to accomplish.  [http://www.linuxquestions.org/questions/linux-desktop-74/running-a-script-when-auto-mounter-detects-usb-thumb-drive-insertion-529113/]("http://www.linuxquestions.org/questions/linux-desktop-74/running-a-script-when-auto-mounter-detects-usb-thumb-drive-insertion-529113/")

---

### Post by HermanAB on 2010-10-21
Well, the first problem is making the removable drive mount with a predictable mount point.  The mount point in /media will be Volume name of the drive if the volume name is not blank.  So use mkfs.ext3 (or whatever the file system on the removable drive is) to set the volume name of the removable.

Once that works, you can hook a script in somewhere in udev, or you can monitor dmesg, or you just make the script run forever and look for the appearance of the mount point in /media.

For scripting, read up on Bash and Perl.

---

### Post by twitterritter on 2010-10-23
Thanks for the replies.

I tried the first one with just a simple script, but it didn't seem to work.
What I wrote in /etc/udev/rules.d/backup.rules was:
BUS="usb", SYSFS{serial}="myserialnumber", SYMLINK="DataTraveler G3",  RUN+="/usr/local/bin/myscript.sh"
I got the serial number from /proc/scsi/usb-storage/*

The script was just:
#!/bin/bash
echo "usb has been plugged in"
exit

unfortunately I did not get an echo. Now I dont know if that was because there is something wrong with the script or something is wrong with the backup.rules. What could be is that my symlink is wrong, but I dont know what exactly I would put there so I just put in what it said behind the line Product from  /proc/scsi/usb-storage/*.


About the second answer: I still have to try that, but it might be helpful for the udev rules(do I take the volume name as SYMLINK?).

Also unlike on my ubuntu desktop machine, the drive doesn't automatically mount on my ubuntu server. I thought about writing an entry in fstab, but then what would happen if the device is not plugged in on boot-up?

I'll try the second suggestion within next week and will then write what happend.

---

### Post by SeijiSensei on 2010-10-23
> **twitterritter said:**
> unfortunately I did not get an echo. Now I dont know if that was because there is something wrong with the script or something is wrong with the backup.rules.

Try writing the string to a file like this:
```
echo "USB plugged in at $(date +%c)" >> /root/usblog
```

which will write a line to /root/usblog each time the script runs.  Using the $(date +%c) construct will log the date and time.

---

### Post by BkkBonanza on 2010-10-23
I use the following to auto start my music server when a specific USB drive is plugged in. The same should work for you with a different script.

```
KERNEL=="sd[b-z]", ENV{ID_SERIAL}=="Hitachi_HDP725050GLA360_GEA534RF1WBA6A", ACTION=="add", RUN+="/usr/sbin/service mpd start"
```

You can monitor the udev actions by using 

sudo udevadm monitor

or also find specific device attributes/details with, eg.

sudo udevadm info -a --path=/sys/block/sda

---

### Post by twitterritter on 2010-11-19
Well I finally got to do what you suggested,but still I've had no success, what so ever.

I tested my script to be run separately, and it turns out that it works.
My udev-rule however does not. When I test the whole thing with udevadm test, I only see that the default-rule and persistent-storage-rule seem to be run, but no other rule.

Ive included my current udev-rule. I got the information about the drive from udevadm info. 

```
SUBSYSTEMS=="usb", ATTRS{idVendor}=="1e68", ATTRS{idProduct}=="001b", ATTRS{serial}==200812034032, RUN+="/usr/local/bin/arbofilia.sh"
```I am really at a loss right now, cause everything I've read so far doesn't help me, in fact 
it would suggest that my rule is correct.

If someone could please help me and tell me what I need to change?

Thanks in advance

---

### Post by twitterritter on 2010-11-19
Okay I finally managed to do it.
Turns out my udev-rule was not correct, because I mixed up some attributes of the disk.

Well anyways I found this command:
udevadm info -a -p  $(udevadm info -q path -n /dev/sdb)
which displayed all the stuff that udevinfo used to, copied it into a textfile and copied a couple of stuff from there into my rule.

I think it was important that everything came from one parent-directory (I faintly remember reading something like that).

Now my rule looks like that:
```
KERNEL=="sde", SUBSYSTEM=="block", ATTR{size}=="1953525168", ATTR{capability}=="52", RUN="/usr/local/bin/arbofilia.sh"
```

thanks for everyone who answered before

---

### Post by BkkBonanza on 2010-11-19
I don't think it's a good idea to use the rule as written even if it does work for now. Some of those atrributes aren't unique and the kernel name can change depending on other devices inserted or changes in your config.

The rule I used for my iscsi setup for auto mounting used,

KERNEL=="sd[b-z]1", ENV{ID_SERIAL}=="Hitachi_HDP725050GLA360_GEA534RF1WBA6A"

which triggers on a specific drive serial number and any kernel name. This allows it to work even if another drive is installed first or in different order, or if later you add/change something else. 

You can determine drive serials with **dir /dev/disk/by-id/** and then use that string in the rule (less the ata- prefix common on all links). UUID can also be used though I fidn the serial more readable as I can tell which one is which more directly.

---

### Post by twitterritter on 2010-11-22
Hmm, I thought that what I found might be unfit, cause it seems like the numbers could be the same for several drives.
But when I tried 4 or 5 times it seemed to work just fine.
But since I didn't know about **dir /dev/disk/by-id/ **I think I might as well change the rules and see if it still works.
Thanks a lot for the warning BkkBonanza

---

### Post by BkkBonanza on 2010-11-22
Typically the drives will get assigned the same unless something changes like a new drive is added or maybe some other device is added/removed. So for the short term you are likely ok but in the longer term one day you'll suddenly find it being assigned differently and then have trouble. A rule matching by id is more robust if you can get it to work (it should work).

---

