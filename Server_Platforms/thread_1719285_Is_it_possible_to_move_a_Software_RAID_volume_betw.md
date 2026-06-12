---
title: "Is it possible to move a Software RAID volume between servers?"
date: 2011-04-01
forum: Server Platforms
---

### Post by MakOwner on 2011-04-01
I have a software raid array (in this test case a mirrored set of two 500GB volumes) and I want to move them to another OS installation on the same hardware. 

(This is testing in preparation for a physical move two arrays onto a single server.)


I had the array up and working (surviving reboots), wrote a test backup onto it in a folder.

Shut the  machine down, re-installed ubuntu, got it up and running, then installed mdadm, rebooted with the array powered up and ran mdadm --detail --scan , expecting to see mdadm at least find the parts of the array.  

Instead, I get nothing.  I even added -vv to get more verbose output.
de nada.

So, I went ahead and did this:

mdadm --assemble --scan -vv
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/sdc1
mdadm: /dev/sdc is not built for host PE1750-2.
mdadm: no recogniseable superblock on /dev/sdb1
mdadm: /dev/sdb is not built for host PE1750-2.
mdadm: cannot open device /dev/sda2: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: No arrays found in config file or automatically



I do find that the raw volume now has a defined partition, but it's type 83, not fd


fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
10 heads, 44 sectors/track, 2219939 cylinders
Units = cylinders of 440 * 512 = 225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00015693

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               5     2219934   488384448   83  Linux

fdisk -l /dev/sdc

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
10 heads, 44 sectors/track, 2219939 cylinders
Units = cylinders of 440 * 512 = 225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00015693

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               5     2219934   488384448   83  Linux




So, if I move another array will I lose it too?
Is there a way to move array between hosts, or is the array stuck with that particular OS?

Would saving and transferring the mdadm.cfg file have been sufficient to save this?

---

### Post by rubylaser on 2011-04-01
Let me see if I understand what you're saying.  You want to set up a RAID1 for the OS in Ubuntu.  Then install a different linux OS in it's place on that RAID1 array?  If so, why?  Why, not just install whatever OS you want from the start on a mdadm RAID1 array?

---

### Post by MakOwner on 2011-04-01
> **rubylaser said:**
> Let me see if I understand what you're saying.  You want to set up a RAID1 for the OS in Ubuntu.  Then install a different linux OS in it's place on that RAID1 array?  If so, why?  Why, not just install whatever OS you want from the start on a mdadm RAID1 array?

Ah, sorry, I'm doing too many things at once, I was unclear.

I have two separate hosts that have external disks attached in software raid arrays (RAID 5, if that makes any difference).

I want to move both of these arrays, with data intact to yet another host.

To test this move, I set up the third host with a third external array with only two disks and created a mirrored array.  I re-installed Ubuntu and mdadm and tried to get the array back up and running.  

What I have now are two separate disks with the data from the mirrored array and apparently no way to make an array.

Will this limitation hold true with a RAID 5 array?
Is there any way to guarantee the ability to rebuild the array after moving it?

---

### Post by rubylaser on 2011-04-01
Okay, I think I'm following now.  So, the new host with the RAID1 mirror works fine, am I correct?  If so, can you post the output of this command?

```
cat /etc/mdadm/mdadm.conf
```

Then from each of the other hosts that you want to transfer over can you run the same command on those boxes?  If you're just trying to transfer RAID arrays to different hosts, that's very easy and definitely doable.  typically you don't even need to bring over the mdadm.conf files (although it's a very good practice to do).

---

### Post by 1clue on 2011-04-01
What you're talking about should be possible.

Formatting/installing onto an array and then using that same array to add an OS is definitely possible because I've done it.  

Rewriting over the top of the original OS is definitely possible, I've done it.

If your CPU type and hardware are compatible, then moving the array to another machine should be possible, but there are more variables that can go wrong.  Obvious things like 32->32 and 64->64 bit architectures will matter, at the very least that if you installed 64-bit then you MUST move them to a 64-bit machine of the same processor family (i7 to i7 etc)

Then you get the disk controller, you may need compatible "generations" of disk controller hardware, meaning SATA2 to SATA2 or SATA3, not SATA1.

Here are some things to check that I ran into or that I heard of people running into:
[LIST=1]
[*]Make sure the kernel on the new distro supports RAID and 
[*]Make sure the kernel supports ALL the filesystem types you use.  EXT4, for example, does not come on most distros automatically.
[*]Make sure your new installer doesn't write anything to the disks unless you specifically tell it to.  That type=83 thing is exactly what I'm talking about.
[*]If you have things set up with RAID autodetect or LVM autodetect, then any kernel which understands that will look for proper partitions.
[*]In this case, the partitions are grouped by UUID, so make sure all the UUIDs match for partitions you want to be in any cluster.
[/LIST]

---

### Post by MakOwner on 2011-04-01
> **rubylaser said:**
> Okay, I think I'm following now.  So, the new host with the RAID1 mirror works fine, am I correct?  If so, can you post the output of this command?

```
cat /etc/mdadm/mdadm.conf
```

Then from each of the other hosts that you want to transfer over can you run the same command on those boxes?  If you're just trying to transfer RAID arrays to different hosts, that's very easy and definitely doable.  typically you don't even need to bring over the mdadm.conf files (although it's a very good practice to do).

Well, in this test, I set up a server, created the array, and then re-installed the (same) OS.   the mdadm.cfg is the default and the ARRAY= line isn't there.

---

### Post by MakOwner on 2011-04-01
> **1clue said:**
> What you're talking about should be possible.

Formatting/installing onto an array and then using that same array to add an OS is definitely possible because I've done it.  

Rewriting over the top of the original OS is definitely possible, I've done it.

If your CPU type and hardware are compatible, then moving the array to another machine should be possible, but there are more variables that can go wrong.  Obvious things like 32->32 and 64->64 bit architectures will matter, at the very least that if you installed 64-bit then you MUST move them to a 64-bit machine of the same processor family (i7 to i7 etc)

Then you get the disk controller, you may need compatible "generations" of disk controller hardware, meaning SATA2 to SATA2 or SATA3, not SATA1.

Here are some things to check that I ran into or that I heard of people running into:
[LIST=1]
[*]Make sure the kernel on the new distro supports RAID and 
[*]Make sure the kernel supports ALL the filesystem types you use.  EXT4, for example, does not come on most distros automatically.
[*]Make sure your new installer doesn't write anything to the disks unless you specifically tell it to.  That type=83 thing is exactly what I'm talking about.
[*]If you have things set up with RAID autodetect or LVM autodetect, then any kernel which understands that will look for proper partitions.
[*]In this case, the partitions are grouped by UUID, so make sure all the UUIDs match for partitions you want to be in any cluster.
[/LIST]


I am losing it -- I'm not being clear at all.

These are just data volumes, the OS is on separate disks.
So no overwrite on the volume(s) at all, just trying to transfer them from one host to another.

I'm pretty sure all the boxes are all 32 bit, and thanks for that tip, I'll check! But during this test, I'm actually using the same hardware -- just doing a re-install of the OS. 

These are all on SiL3124 multi port controllers addressing enclosures with port multipliers.

This is for Ubuntu 10.04.2 LTS, it does ext4 out of the box, so far as I'm aware -- the install let's me put / on it in any event - on separate disk from the arrays I'm talking about.

---

### Post by MakOwner on 2011-04-01
> **1clue said:**
> What you're talking about should be possible.

If your CPU type and hardware are compatible, then moving the array to another machine should be possible, but there are more variables that can go wrong.  Obvious things like 32->32 and 64->64 bit architectures will matter, at the very least that if you installed 64-bit then you MUST move them to a 64-bit machine of the same processor family (i7 to i7 etc)




This will be a problem?
All three of these are dual processors,just one displayed for brevity.

Machine Source 1
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
stepping	: 13
cpu MHz		: 1200.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 4389.35
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual

```


Machine source 2 
```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 6
model name	: AMD Processor model unknown
stepping	: 2
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5999.63
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```

Target machine
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Xeon(TM) CPU 3.06GHz
stepping	: 9
cpu MHz		: 3050.646
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips	: 6101.29
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

```

---

### Post by rubylaser on 2011-04-01
I'm not really sure what you're trying to do.  But, to answer your original question, mdadm is portable, and the different processor types do not matter.

---

### Post by 1clue on 2011-04-01
Data drives only?  OK then the processor family doesn't matter, unless you have dramatically different architecture like one does big-endian and the other little-endian or something stupid like that.

Same hardware, and data drives, then what I find most helpful is to open a term, zoom it out, and then do **sudo fdisk -l /dev/sda**, then the same for sdb, etc.  Compare the output of all of them and make sure they're essentially identical or different in ways you expect them to be different.

If you have Linux RAID autodetect (I assume you're going with RAID on the bottom and LVM2 on top?) for all the drives and the same UUID on anything intended to be a pair, then all should work fine when you reassemble the array.

The only thing i can think of offhand would be if ordering makes a difference, which I don't think it does.  If your original sda is now sdb for example, then that might make a problem.

I started putting UUIDs in my /etc/fstab when I started messing with RAID/LVM.  My backup device is a 1.5 TB drive that I just plug into a slot, and it changes the drive letter (sda/sdb) of everything depending if it's plugged in or not.

---

### Post by 1clue on 2011-04-01
Oh yeah, if one of the operating systems is Windows you're screwed.  Windows doesn't do fakeraid.

---

### Post by MakOwner on 2011-04-01
> **1clue said:**
> Oh yeah, if one of the operating systems is Windows you're screwed.  Windows doesn't do fakeraid.

two desktop ubuntu 10.4 to one ubuntu 10.04.2 LTS minimal install server.

---

### Post by MakOwner on 2011-04-01
> **rubylaser said:**
> I'm not really sure what you're trying to do.  But, to answer your original question, mdadm is portable, and the different processor types do not matter.

That's a relief.

---

### Post by MakOwner on 2011-04-09
So, I have successfully moved an 8 disk external (eSATA) array from a 32 bit desktop to a 64 bit server installation without (so far) data loss.

I expected to be able to power the new server down, connect in the array, and with mdadm installed, power up and run mdadm --detail --scan as root and find the array.  

This DID NOT work. /proc/mdstat showed no arrays.

I went back to the original host where the array was attached and obtained the ARRAY line of the mdadm.conf file, appended it to the mdadm.conf file on the new machine and after a reboot, I was able to find the array and then mount the filesystem.

So, if you ever plan to move arrays at least take the precaution to have a copy of the .conf file.  I am probably missing something basic that will make this happen without the need of this, so if anyone has the magic, please share.

---

### Post by rubylaser on 2011-04-09
Sure, you can always get info to assemble the array from any of your disks that where part of the array (in the example below /dev/sdc1).  Here's a simple (not very optimized) script that I wrote that will extract info to create a valid mdadm.conf file.

```
sudo -i
nano mdadm_creator.sh
```
and paste...
```

#! /bin/bash
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
metadata=`mdadm -E /dev/sdc1 | grep Version | cut -d ":" -f2 | tr -d ' ' | awk 'sub("...$", "")'`
uuid=`mdadm -E /dev/sdc1 | grep UUID | sed -e 's/^[ \t]*//' | cut -d " " -f3`
echo "ARRAY /dev/md0 metadata="$metadata "UUID="$uuid >> /etc/mdadm/mdadm.conf

```

Run it.
```
. mdadm_creator.sh
```
It will output something like this...
```
DEVICE partitions
HOMEHOST fileserver
MAILADDR root@localhost
ARRAY /dev/md0 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41

```
A perfectly valid mdadm.conf file.  Hope that helps :)

---

### Post by MakOwner on 2011-04-09
> **rubylaser said:**
> Sure, you can always get info to assemble the array from any of your disks that where part of the array (in the example below /dev/sdc1).  Here's a simple (not very optimized) script that I wrote that will extract info to create a valid mdadm.conf file.

```
sudo -i
nano mdadm_creator.sh
```
and paste...
```

#! /bin/bash
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
metadata=`mdadm -E /dev/sdc1 | grep Version | cut -d ":" -f2 | tr -d ' ' | awk 'sub("...$", "")'`
uuid=`mdadm -E /dev/sdc1 | grep UUID | sed -e 's/^[ \t]*//' | cut -d " " -f3`
echo "ARRAY /dev/md0 metadata="$metadata "UUID="$uuid >> /etc/mdadm/mdadm.conf

```

Run it.
```
. mdadm_creator.sh
```
It will output something like this...
```
DEVICE partitions
HOMEHOST fileserver
MAILADDR root@localhost
ARRAY /dev/md0 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41

```
A perfectly valid mdadm.conf file.  Hope that helps :)

Or just cut and paste the ARRAY line from the previous mdadm.conf.
The point was that until I had the ARRAY line in the mdadm.conf file, the scan for the array didn't work.

Edit:  Also, including the "metadata-0.90" in the ARRAY line causes non-fatal errors.

---

### Post by rubylaser on 2011-04-09
> Or just cut and paste the ARRAY line from the previous mdadm.conf.
Yes, but I thought you asked for a solution that didn't involve that...
> I am probably missing something basic that will make this happen without the need of this, so if anyone has the magic, please share.
It's not magic, but that's what querying the disk's superblock does.  Any disk from your array contains all the info you'd need to re-assemble the array on another computer.

> Edit: Also, including the "metadata-0.90" in the ARRAY line causes non-fatal errors.
What?!? If you mean leaving metadata=00.90 causes non-fatal errors, then yes. But, if you remove the first zero, you will receive no errors. This "solution" has been around since 2008.

[http://ubuntuforums.org/showthread.php?t=1007464]("http://ubuntuforums.org/showthread.php?t=1007464")

---

### Post by MakOwner on 2011-04-10
> **rubylaser said:**
> Yes, but I thought you asked for a solution that didn't involve that...

It's not magic, but that's what querying the disk's superblock does.  Any disk from your array contains all the info you'd need to re-assemble the array on another computer.


What?!? If you mean leaving metadata=00.90 causes non-fatal errors, then yes. But, if you remove the first zero, you will receive no errors. This "solution" has been around since 2008.

[http://ubuntuforums.org/showthread.php?t=1007464]("http://ubuntuforums.org/showthread.php?t=1007464")



I would have thought using mdadm --detail --scan would have picked up the information off the disks/partitions and given up the array definition.

And I have just always taken the metadata bit out.  Works fine without it.
Seems to anyway.  

If the problem has been known for that long, why no fix?  Must be  a really hairy problem.

---

### Post by rubylaser on 2011-04-10
mdadm --detail --scan should have worked. I'm not sure why it didn't in your case.  Luckily, there's always another way to solve a problem :)

The metadata portion is important to include, especially if you're using one of the newer metadata versions.  With the new 1.x subversions the superblocks get stored in different locations on the disk. I'd much rather tell mdadm the correct version than have it guess it. It does default to 0.90 though.

Ubuntu runs a very old version of mdadm 2.6.7. The newest stable version is 3.1.4 and is included in Debian Squeeze's Repos.  In the newest version contains this patch, and is part of the reason, I install this version of mdadm.

```
root@fileserver:~# mdadm -V
mdadm - v3.1.4 - 31st August 2010
root@fileserver:~# mdadm --detail --scan
ARRAY /dev/md0 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41
```

I'm the wrong person to ask about why the version hasn't been updated. You'd have to ask the package maintainer.

---

### Post by MakOwner on 2011-04-10
> **rubylaser said:**
> mdadm --detail --scan should have worked. I'm not sure why it didn't in your case.  Luckily, there's always another way to solve a problem :)

The metadata portion is important to include, especially if you're using one of the newer metadata versions.  With the new 1.x subversions the superblocks get stored in different locations on the disk. I'd much rather tell mdadm the correct version than have it guess it. It does default to 0.90 though.

Ubuntu runs a very old version of mdadm 2.6.7. The newest stable version is 3.1.4 and is included in Debian Squeeze's Repos.  In the newest version contains this patch, and is part of the reason, I install this version of mdadm.

```
root@fileserver:~# mdadm -V
mdadm - v3.1.4 - 31st August 2010
root@fileserver:~# mdadm --detail --scan
ARRAY /dev/md0 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41
```

I'm the wrong person to ask about why the version hasn't been updated. You'd have to ask the package maintainer.


Great.  Good to know I'll be having even more issues down the road with an upgrade some day.  Have you been through an upgrade from the Ubuntu version to the real latest stable release?  Any issues?

The question about the version update was rhetorical -- it seems to be getting more and more common that official Ubuntu repositories keep old, or broken versions of stuff.  :(

---

### Post by rubylaser on 2011-04-10
I wasn't implying that's there's anything wrong with 2.6.7 other than that 3.1.4 fixes the small bug that you mentioned.  I certainly never mentioned you should expect problems in the future.  I've upgraded mdadm in many systems including migrating to new servers, and different versions of mdadm.  It works great, is very stable, and is way more flexible than a vendor specific hardware controller.

What are some other examples of the repos holding out of date versions (that have incomplete feature sets)? I'm asking, because I don't have this same feeling.  You're running a stable distribution, one that's well tested.  That's a compromise that's made for the stability that it offers.  If you want something with cutting edge packages, run a Debian Sid or Arch.  You'll have all of the latest packages, and all of the problems that come with a system that doesn't have all of the test coverage to go along with it.  Besides, you're running Linux;  if you want the latest and greatest, just  compile from git or svn  (I do this with ffmpeg, ffms2, or x264).

---

### Post by MakOwner on 2011-04-10
> **rubylaser said:**
> I wasn't implying that's there's anything wrong with 2.6.7 other than that 3.1.4 fixes the small bug that you mentioned.  I certainly never mentioned you should expect problems in the future.  I've upgraded mdadm in many systems including migrating to new servers, and different versions of mdadm.  It works great, is very stable, and is way more flexible than a vendor specific hardware controller.

I have only used what's in the main repositories as much as possible.  I was just concerned that if the 00.90 versioning causes issues what would arise once I upgraded.  So you have had no issues with upgrading on a live array with data?  That makes me feel better. 
 
> 
What are some other examples of the repos holding out of date versions (that have incomplete feature sets)? I'm asking, because I don't have this same feeling.  You're running a stable distribution, one that's well tested.  That's a compromise that's made for the stability that it offers.  If you want something with cutting edge packages, run a Debian Sid or Arch.  You'll have all of the latest packages, and all of the problems that come with a system that doesn't have all of the test coverage to go along with it.  Besides, you're running Linux;  if you want the latest and greatest, just  compile from git or svn  (I do this with ffmpeg, ffms2, or x264).

Gallery comes quickly to mind.  Webmin.  If the repos are not kept current, what's the point?  I use these two products, and the only way to install them is to either add a third party repository, or in the case of Gallery download the installer from their site.  And endure the political issues that arise there when asking questions once they know it's on Ubuntu.  

I have no idea why or where the animosity comes from.

In any event, I use Ubuntu because it's easy to duplicate a server installation - and I can use the same distro as desktop.  What I learn in one leverages itself in the other.

---

### Post by rubylaser on 2011-04-10
Yes, you can feel confident with mdadm, at least I do :)

I don't use Webmin, or Gallery, so I haven't come across those older versions.  If you're talking about the web photo website Gallery.  I'm not surprised that's not up to date in the repos.  It has very minimal installation requirements, similar to most php web apps. So, downloading an installer would be common.  I am surprised to hear Webmin's really out of date as it's a common tool for some.

If you feel this way...
> I have no idea why or where the animosity comes from.

I'd personally be looking for a different photo website, it's a very common application, and I'm sure you could find a more willing to help group of people :)

---

### Post by MakOwner on 2011-04-10
> **rubylaser said:**
> Yes, you can feel confident with mdadm, at least I do :)

I don't use Webmin, or Gallery, so I haven't come across those older versions.  If you're talking about the web photo website Gallery.  I'm not surprised that's not up to date in the repos.  It has very minimal installation requirements, similar to most php web apps. So, downloading an installer would be common.  I am surprised to hear Webmin's really out of date as it's a common tool for some.

If you feel this way...


I'd personally be looking for a different photo website, it's a very common application, and I'm sure you could find a more willing to help group of people :)


I'm new to webmin, so if you poke around someone out there runs a repository for it, so I have just been using that.  

The Gallery thing -- it actually does have a pretty healthy list of dependancies - you can install Gallery2 from Ubuntu, but you really can't get any assistance on the version from Ubuntu.  I use the Ubuntu install to get all the dependancies and then try and overlay the supported version over that.  

I'ld love to find a good substitute that lives in the standard repos that will work both facing the internet and internally.  If you have suggestions, I'm all ears!

---

### Post by rubylaser on 2011-04-10
> I'ld love to find a good substitute that lives in the standard repos that will work both facing the internet and internally. If you have suggestions, I'm all ears!

Can't help you here.  I'm a Rails developer, so when I'm faced with something like this, I always write my own application. This is really such a simple application.  It's basically HTML + CSS + some jquery for lightboxes, + an exif library + and a simple authentication system.

Personally, I'd just setup a LAMP stack, and then pick a php photo gallery. Sorry, I couldn't be more help with this. I don't publish my family photos like this, and if I did, I'd write my own app :)  Maybe someone else will have a suggestion if you post in the General Forum.

---

### Post by MakOwner on 2011-04-10
> **rubylaser said:**
> Can't help you here.  I'm a Rails developer, so when I'm faced with something like this, I always write my own application. This is really such a simple application.  It's basically HTML + CSS + some jquery for lightboxes, + an exif library + and a simple authentication system.

Personally, I'd just setup a LAMP stack, and then pick a php photo gallery. Sorry, I couldn't be more help with this. I don't publish my family photos like this, and if I did, I'd write my own app :)  Maybe someone else will have a suggestion if you post in the General Forum.

And therein lies the rub - It's been many years since I have done any serious coding - way before ruby or php even existed :)

Not that I wouldn't mind learning perl better, but I just don't see the value in re-inventing this wheel - if I can find an easy enough to use and learn application that already exists.


***************************
How opportune.  My gallery2 set up just crapped the bed and I have yet again a web site with nothing but broken links.
I'm really getting to hate this package.

---

