---
title: "RAID Drives not recognized with new install"
date: 2011-11-05
forum: Server Platforms
---

### Post by jen.r.magas on 2011-11-05
Hardware specs:
[LIST]
[*]Motherboard: Gigabyte Z68MX-UD2H-B3
[*]Quad-core Intel i7-2600K, 3.4GHz
[*]16Gb RAM
[*]OS Harddrive: SATA ST31000528AS - 1Tb
[*]Two RAID 1 drives: SATA Hitachi HDS72101 - 1Tb each
[/LIST]

It's been a long saga, but I'll try to keep it brief. I had a good setup on Ubuntu Server 11.04 with a software-based RAID 1 on the two 1Tb drives. A failed upgrade led me to need to fully reinstall the OS, at which point I decided it was a good idea to move to Ubuntu Server LTS (10.04).

Two attempted installs failed before it occurred to me that the additional RAID drives being connected might be an issue, so I removed them and reinstalled. All was good until I reconnected them; now the OS wouldn't load. I rearranged my BIOS boot order to put the OS drive first, and all was happy. I've got an OS again.

Unfortunately, the OS isn't recognizing my RAID 1 setup from the prior install. Being entirely new to the world of RAID in general, I'm a bit at a loss of how to deal with this.

VIA the server GUI, I've pulled up GParted and gotten info on each of the two RAID drives, as attached.

I assume my problems are two-fold: I may have gotten a boot sector on one or both of them, and being a software RAID configuration, may need to add / reconfigure software.

So the question is, can anyone point me down the right path to restore this RAID configuration and all the associated data? Any help is appreciated!

---

### Post by darkod on 2011-11-05
During the 10.04 install did you try to let the OS know there is a raid array existing and to try to mount it?

---

### Post by jen.r.magas on 2011-11-05
The install sequence never gave an opportunity to do so, so I'd say no.

---

### Post by darkod on 2011-11-05
I haven't used the server version much, but if I recall correctly when setting up RAID, you create the partitions and mark them as raid type.
After that there will be option above the disks/partitions list, something like Activate Software RAID, or just Software RAID, etc.

It's probably safe to boot with the 10.04 cd again and "start" a new install. Just to see what the partitioning section will show you. If you cancel it without writing any new partitions, it will not change anything to the current install.
And don't forget to use the Manual option about the partitioning/installng. Ignore the automatic options suggested because they wouldn't search for your array.
Look around in the partitioning for any signs of options to activate the RAID.

On the other hand maybe just using mdadm can reassemble it, but as I said I have never tried something like that before.

If it helps with any ideas, I was just investigating how to replace a failed drive from raid1 array (which is not exactly your case):
[http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

---

### Post by darkod on 2011-11-05
PS. I wonder if simply using mdadm commands and creating manually now md0 and md1, then adding the partitions and activating the array would do the job. Makes sense to me.

---

### Post by darkod on 2011-11-06
I am not sure if you are still working on this, but I just found a link to an old thread and it has just what you need. Look under number 7) here: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Basically, as I thought. You can easily assemble an existing raid in your new install. Since the server version already has mdadm you should not need to install it.

Just use:

sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
sudo mdadm --assemble /dev/md1 /dev/sda2 /dev/sdb2

If that is the configuration you had.

You can also let it autodetect:

sudo mdadm --assemble --scan

For assembling existing raid the command --assemble is used. You use --create just the first time to create the raid. In your case you already have an existing raid and you don't need --create.

If assembling it like this works, I am not sure if the array is entered automatically into /etc/fstab. Otherwise you will have to make entries manually so that it is mounted at each boot.

---

### Post by jen.r.magas on 2011-11-08
I might not have been entirely clear in my original post, so I should specify something - when I did my reinstall, I moved from originally having installed 11.04 to installing 10.04 LTS. I'm wondering if this is part of the problem - did Ubuntu change the formats used, and I'm possibly one one not known by 10.04? I'm not quite sure where to look to find that kind of detail.

Anyway...

I went through the 10.04 install just far enough to see the drives, as suggested, and here's what's displayed:

```
SCSI1 (0,0,0) (sda) - 1.0 TB ATA Hitachi HDS72101
     #1   primary   1.0 TB     K   raid
SCSI2 (0,0,0) (sdb) - 1.0 TB ATA Hitachi HDS72101
     #1   primary   1.0 TB     K   raid
SCSI3 (0,0,0) (sdc) - 1.0 TB ATA ST31000528AS
     #1   primary   959.7 GB   B   ext4
     #5   logical   40.5 GB    F   swap    swap
```

I also attempted to use mdadm to rebuild it. The initial thought was to attempt the assemble option, so I did this:

```
$ mdadm --assemble --scan
mdadm: unrecognised word on ARRAY line: (RAID)
mdadm: unrecognised word on ARRAY line: (RAID)
mdadm: /dev/md/Media does not exist and is not a 'standard' name so it cannot be created

```

That's kind of a good sign - "Media" was the name of the drive on the prior install, so it's seeing something of what it should be.

I tried again with specifying a new array:

```
$ mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
mdadm: unrecognised word on ARRAY line: (RAID)
mdadm: unrecognised word on ARRAY line: (RAID)
mdadm: failed to create /dev/md0

```

To be honest, I really don't know where to go with this. I would be ok with starting over with the array, but I have to recover the data first, and I'm not sure I can do that in its current state.

Perhaps an 11.04 Live CD would be enough to get it mounted long enough to pull the data? I think I'll give that a try, but any assistance in the meantime would be much appreciated!

Thanks for all the help.

---

### Post by jen.r.magas on 2011-11-08
Ok, that just blows my mind. Don't forget to use 'sudo', folks!

```
sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
mdadm: unrecognised word on ARRAY line: (RAID)
mdadm: unrecognised word on ARRAY line: (RAID)
mdadm: /dev/md0 has been started with 2 drives.
```

So it's mounted, but I'm not sure how I feel about the "unrecognised word" error message. Then again, it's up and happy, so for the time being, I"m not complaining. I wonder if after a reboot it'll stay mounted? I suppose that's a different problem to tackle...

---

### Post by darkod on 2011-11-08
Yeah, you need sudo for most system commands. :)

If it doesn't stay mounted after reboot, you need to add it to /etc/fstab yourself. I can not give you the exact spelling for it, but I'm sure there are plenty of posts on the internet what it should look like. Something line

/dev/md0      /      ext4      etc

device/mount point/filesystem/options

It's the options part what I am not sure about.

---

### Post by rubylaser on 2011-11-09
Your WORD error is stemming from your /etc/mdadm/mdadm.conf file having an invalid option.  You can re-create a valid mdadm.conf file like this.

```
sudo -i
```

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Havng a valid mdadm.conf file is actually just as important as adding the line to /etc/fstab.  If it's not valid, your array will not auto assemble correctly, and as result, won't be available for mounting via fstab.

I normally mount my arrays on /storage, so here's how you'd do that.

```
mkdir /storage
```
and then add this line to /etc/fstab
```
/dev/md0	/storage	    ext4	defaults	0	0
```
After a reboot, your array should be mounted at /storage.

---

### Post by jen.r.magas on 2011-11-13
Before having restarted, I modified the /etc/mdadm/mdadm.conf to have the following:

```
DEVICE partitions
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=01.02 name=:Media (RAID) UUID=71614f91:84d85999:a47549cb:a6e99160

```

The last line was the result of 'mdadm --detail --scan' at the time.

/etc/fstab contains:

```
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda1 during installation
# UUID=f92a91ee-1d68-49cc-91e2-5b82b6bd045f /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda5 during installation
# UUID=a4c58e30-7810-4a08-9447-c1048af0eecc none            swap    sw              0       0

/dev/md0        /storage            ext4        defaults        0       0
```

I commented out the lines that appeared to be incorrectly referencing the RAID array.

And of course, I created /storage.

Upon rebooting, I get the following message:

```
fsck from util-linux-ng 2.17.2
/dev/sdc1: clean 1485858580992 files, 4519783/234306048 blocks
The disk drive for /storage is not ready yet or not present
Containue to wait; or Press S to skip mounting or M for manual recovery
```

After the reboot, I get this output from 'sudo mdadm --detail --scan':

```
mdadm: metadata format 01.02 unknown, ignored.
mdadm: unrecognised word on ARRAY line: (RAID)
```

I can still assemble the drive, but I get the following output first:

```
$ sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
mdadm: metadata format 01.02 unknown, ignored.
mdadm: unrecognised word on ARRAY line: (RAID)
mdadm: /dev/md0 has been started with 2 drives.
```

And once it's been started, it shows up under /media/Media - I suspect that's perhaps something in a config I haven't found, or on the RAID drives themselves?

Any more magical commands that will make this thing behave!?

---

### Post by rubylaser on 2011-11-13
Have you tried to reconfigure mdadm?  I'm betting that it not trying to auto start any arrays.  You'll want to run.

```
dpkg-reconfigure mdadm
```
And answer the question for arrays to start with all.  Reboot and let me know how that goes.

---

### Post by jen.r.magas on 2011-11-18
rubylaser -

Thanks for the suggestion, and sorry for not trying this sooner. Work, and a million other things, have me a bit backed up.

I answered all the questions during the reconfigure, and after the prompts went away, I saw this:

```
$dpkg-reconfigure mdadm
 * Stopping MD monitoring service mdadm --monitor                                                                                       [ OK ] 
Generating array device nodes... /var/lib/dpkg/info/mdadm.postinst: 170: /dev/MAKEDEV: not found
failed.
 Removing any system startup links for /etc/init.d/mdadm-raid ...
update-initramfs: Generating /boot/initrd.img-2.6.32-35-server
update-rc.d: warning: mdadm start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (S)
update-rc.d: warning: mdadm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
 * Starting MD monitoring service mdadm --monitor                                                                                              mdadm: metadata format 01.02 unknown, ignored.
mdadm: unrecognised word on ARRAY line: (RAID)

```

I'm not sure what to make of that, but I'm thinking it's not a good sign.

After a reboot, I still see:

```
...The disk drive for /storage is not ready yet or not present...
```

I notice that "Media" is listed in the File Browser, and if I double-click it, it prompts for the root password to mount it.

---

