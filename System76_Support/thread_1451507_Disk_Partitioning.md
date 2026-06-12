---
title: "Disk Partitioning"
date: 2010-04-10
forum: System76 Support
---

### Post by HegonBadde on 2010-04-10
So while I'm waiting on my new Laptop thought I'd think about disk partitions.

I'm thinking
/boot (so both can share same boot files) 10Gb *(maybe turn this into an LFS console install or "usb" install later on)*
<swap> 4Gb
/home 100gb
/backuphome 100Gb
/ (ubuntu 9.10 64) 20Gb
/ (ubuntu 10.4 64) 20Gb
<empty logical space> remainder

That way default boot will be active install.
Home and backup stay in sync.
When I go to install, 10.4, I'll tell it that /backup is /home, 
If I like it I'll turn original home into backup and clean off the 9.10 for the experimental installs.
If I don't like it I'll try Kubuntu, Xbuntu over there.

I've got an external 7200RPM 320Gb usb drive.
Thinking I'll turn it into Milestone backups.
Maybe a dd copy from head to tail, including boot sector.

---

### Post by satsujinka on 2010-04-10
Your boot partition is a bit large. Unless you plan to have dozens of kernels you can probably get away with <1GB.
Also you have 6 partitions. There's a 4 partition max on most drives (you can change the type with Gparted, but I can't tell you if it will boot.)
A better set up might be:

/boot (1GB)
swap (4GB)
/ [9.10] (200GB)
/ [10.04] (50GB)

Since you'll have back ups of your home directory there's really no reason to have a separate /home at this stage.
While I don't have two O.S.s on my computer this is my setup:

/boot (256MB)
swap (1GB)
/ (15Gb)
/home

---

### Post by HegonBadde on 2010-04-10
I don't need the space of the boot partition. and by making it large enough I can put a boot directory inside of it and use it for repairs and unmounted backup jobs.

it would look something like this
/dev/sda1 10Gb Ext3
/dev/sda2 4Gb Swap
/dev/sda3 Extended partion <remainder>
[INDENT]/dev/sda5 100Gb Ext3 <home>
/dev/sda6 100Gb Ext3 <backup>
/dev/sda7 20Gb Ext4 <active />
/dev/sda8 E20Gb xt4 <next />
<empty space for future development>
[/INDENT]

---

### Post by satsujinka on 2010-04-10
Okay, then that makes sense. I never use extended partitions, due to a variety of reasons, so I frequently forget they exist. Even if you don't need the space, I would still go with a smaller or non-existent boot partition. Live CDs/USB drives do the recovery job just fine.

---

### Post by HegonBadde on 2010-04-10
I don't want to spend *time* with it, I just want the space.
First time I repair from CD I'll fix it up.

Most likey just add another Extened /, and mount a CD image there.

---

### Post by HegonBadde on 2010-04-10
Which brings up a good question!

Whats the best way to install/mount an Ubuntu Live install? with a saved data area?

/dev/sda1 10Gb Ext3
/dev/sda2 4Gb Swap
/dev/sda3 Extended partion <remainder>

    /dev/sda5 100Gb Ext3 <home>
    /dev/sda6 100Gb Ext3 <backup>
    /dev/sda7 20Gb Ext4 <active />
    /dev/sda8 E20Gb xt4 <next />

    /dev/sda9 E2Gb iso  />
    /dev/sda10 E5Gb /home/live  <next />
    <empty space for future development>

---

### Post by oldfred on 2010-04-10
Generally you do not share /boot nor /home as settings can conflict. You share swap if you do not hibernate and can create data partitions that you can share across many installs.
Whatever you other plans are for /boot I would suggest using the data partition.

see my post #6
[http://ubuntuforums.org/showthread.php?t=1451279](http://ubuntuforums.org/showthread.php?t=1451279)

---

### Post by HegonBadde on 2010-04-10
Looks Good, I'll review it before installing, /home is a single partitoin but each user is specific to a "/home/hegon910"  they just all happen to share the default userId of new installs.


Thanks guys!

---

### Post by HegonBadde on 2010-04-10
> **oldfred said:**
> You share swap if you do not hibernate 
[http://ubuntuforums.org/showthread.php?t=1451279](http://ubuntuforums.org/showthread.php?t=1451279)

Can I use 2 swaps? 1 for hibernate and another just in case?
*(basically abuse priority routing so that different installs hibernated to different swaps)*?


*More Details added*
makes me think too many mounts...
how about

Internal HD (9.10 64 Installed)
/dev/sda1 20Gb Ext3 /
/dev/sda2 4Gb Swap
/dev/sda3 200+Gb Ext3 /home
/dev/sda4 2Gb iso *9.10 Live install media*


[I]
/dev/sdb3 2Gb iso *10.4 live install Media*
/dev/sdb4 200+Gb Ext3 /home/backup[/I]



External HD  (10.4 64 Installed)
/dev/sda1 20Gb Ext3 /
/dev/sda2 4Gb Swap
/dev/sda3 2Gb iso *10.4 Live install media*
/dev/sda4 Remainder Ext3 /home

[I]
/dev/sdb3 200+Gb Ext3 /home/backup
/dev/sdb4 2Gb iso *9.10 Live install media*[/I]

that way both sides have their own /boot directory, External always try to boot itself
Both hibernate to their own copy of /dev/sda2, and leave /dev/sdb2 alone.

---

### Post by oldfred on 2010-04-10
When you install you just specify not to use the existing swap and to create a new swap, then each swap is unique to each install.

---

### Post by jdb on 2010-04-10
> **oldfred said:**
> Generally you do not share /boot nor /home as settings can conflict. You share swap if you do not hibernate and can create data partitions that you can share across many installs.
Whatever you other plans are for /boot I would suggest using the data partition.

see my post #6
[http://ubuntuforums.org/showthread.php?t=1451279](http://ubuntuforums.org/showthread.php?t=1451279)

Because you can't share /home, I make a really big partition & mount it on /data.
That's where I put all my "stuff".
I don't even bother with a separate partition for /home, I only use it for configuration files.
I make my system partitions 10 G & that includes /home.

I can mount /data & use it no matter what system I boot from.

On Desktops I always have 2 disks with /data1 on the second disk to backup /data on the first disk.
rsync is a great app for that.
I don't like raid because if I do something stupid on /data I don't want it to immediately propogate to /data1.

jdb

---

### Post by HegonBadde on 2010-04-11
> **jdb said:**
> 
...
On Desktops I always have 2 disks with /data1 on the second disk to backup /data on the first disk.
...
jdb

right now on old desk top I use /home/xxx/data and /home/xxx/backup
Move my music, pictures, saves, downloads, etc to those partitions.

But I don't like to copy all that, it's nice it shows up as another drive for wine, but I think I'd rather put it in ~

---

### Post by jdb on 2010-04-11
> **HegonBadde said:**
> right now on old desk top I use /home/xxx/data and /home/xxx/backup
Move my music, pictures, saves, downloads, etc to those partitions.

But I don't like to copy all that, it's nice it shows up as another drive for wine, but I think I'd rather put it in ~

you can use
ln -s file-path link-path
to make files in /data look like they're in ~/

I do that with thunderbird files for my mail, virtualbox files, etc.
I don't use wine so I don't know if it works with links.

jdb

---

### Post by HegonBadde on 2010-04-11
Here's a problem I don't have a solution for.

On other Laptops when I install onto an External USB Drive, I have to physically disconnect the internal hard drive to keep Grub completely off of it.
(Other wise I end up needing internal hd boot sector to boot external drive)

And when I do Kernel updates, it auto (re)installs grub to the internal HD with no check. (Yes there's a grub there, but it's not yours)

---

### Post by HegonBadde on 2010-04-11
> **jdb said:**
> you can use
ln -s file-path link-path
to make files in /data look like they're in ~/

I do that with thunderbird files for my mail, virtualbox files, etc.
I don't use wine so I don't know if it works with links.

jdb

It usually does, but there was an issue with hard links, sym links, or a bad drive. Something went funky one time and like a superstitous villager, I never tried that again.


Ok so the new plan would be
**Internal HD (9.10 64 Installed)**
/dev/sda1 20Gb Ext3 /
/dev/sda2 4Gb Swap
/dev/sda3 Remainder Ext3 /home/xxx/data
[INDENT]Directories symlinked into /home/xxx/data [/INDENT]

/dev/sdb3 Remainder Ext3 /home/xxx/dup


**External HD (10.4 64 Installed)**
/dev/sda1 20Gb Ext3 /
/dev/sda2 4Gb Swap
/dev/sda3 Remainder Ext3 /home/xxx/data
[INDENT]Directories symlinked into /home/xxx/data [/INDENT]

/dev/sdb3 Remainder Ext3 /home/xxx/dup

---

### Post by jdb on 2010-04-11
> **HegonBadde said:**
> Here's a problem I don't have a solution for.

On other Laptops when I install onto an External USB Drive, I have to physically disconnect the internal hard drive to keep Grub completely off of it.
(Other wise I end up needing internal hd boot sector to boot external drive)

And when I do Kernel updates, it auto (re)installs grub to the internal HD with no check. (Yes there's a grub there, but it's not yours)

I have a lot of system partitions on my disk & it can be a nightmare when the competing grubs all try to take control :)

I have a separate partition I mount as boota and I keep a grub directory there with a menu I maintain manually.
I used to do it with the old grub but I use grub2 now & it works just as well.

When I install a new system it writes it's own /boot entries and installs grub in the disk mbr (master boot record).
I then boot to a live flash and re-install grub to the mbr but point it towards /boota.
I then make a new entry in my /boota menu for the new system.

The only trick is to remember to update the /boota menu when a system upgrades the kernel.

It's nice to have control over the boot menu look & feel, boot options, etc.

jdb

---

### Post by HegonBadde on 2010-04-11
I seem to remember there was a trick to this where you can *edit* the contents of the boot partition into the /boot mountpoint directory.

Then while you had actually booting it was reading the directory, and when you were making saves it's a partition?


*More Edit magic*
Basically during boot time the other device isn't mounted.
So it's working off it's "native" copy.

Run mode Desktop
I think it causes problem because you want each side to be "stand alone" and your now set to edit someone elses native.

---

### Post by HegonBadde on 2010-04-11
Set the boot entry for the Other device as a chainloader and select the other drives active boot entry. when it's setup it right, you should be able to go back and forth from Internal -> External -> Internal -> Ext. etc... and never boot anything.

(e)External has (i)Internals back up and Internal has a reference to Externals backup.

Basically one has data of the other (din)"data in"
It sees its own back up as (dup)"duplicate" data.
it sees the the (ddin)"duplicate data in" which should not be modifiable, just a read only place to get a stable copy.




Internal HD (9.10 64 Installed)
/dev/sda1 20Gb Ext3 /
/dev/sda2 4Gb Swap
/dev/sda3 Remainder/2 Gb Ext3 /home/xxx/din
/dev/sda4 R/2 Gb Ext3 /home/xxx/data
    Directories symlinked into /home/xxx/

/dev/sdb3 R/2 Gb Ext3 /home/xxx/dup ->  External /dev/sda3
/dev/sdb4 R/2 Gb Ext3 /home/xxx/ddin -> External /dev/sda4


External HD (10.4 64 Installed)
/dev/sda1 20Gb Ext3 /
/dev/sda2 4Gb Swap
/dev/sda3 R/2 Gb Ext3 /home/xxx/din
/dev/sda4 R/2 Gb Ext3 /home/xxx/data
    Directories symlinked into /home/xxx/

/dev/sdb3 R/2 Gb Ext3 /home/xxx/dup ->  Internal /dev/sda3
/dev/sdb4 R/2 Gb Ext3 /home/xxx/ddin -> Internal /dev/sda4

---

