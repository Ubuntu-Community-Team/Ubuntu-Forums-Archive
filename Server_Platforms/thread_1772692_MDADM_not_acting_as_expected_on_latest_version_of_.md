---
title: "MDADM not acting as expected on latest version of ubuntu"
date: 2011-05-31
forum: Server Platforms
---

### Post by Underpants on 2011-05-31
All, This is a x-post from the Linuxmint forums. I did this testing on Mint 11 install - but also tried the exact same thing on an Ubuntu 11.04 release and had the exact same output to deal with...

Hopefully you guys can help me out..

Follow along: I'm having trouble with MDADM.... It's not acting like I expect it to.... hopefully someone can enlighten me. 

```
MintRAID aaron # mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd
MintRAID aaron # mkfs.ext3 /dev/md0
```

Added this line to /etc/fstab:
```
/dev/md0        /mnt/data       ext3    defaults        0 0
```

```
MintRAID aaron # mount -a
```

```
MintRAID aaron # mdadm --detail --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=1.2 spares=1 name=MintRAID:0 UUID=21c26d8c:3efb74a0:74f000ab:e3e0a134
   devices=/dev/sdb,/dev/sdc,/dev/sdd
```

```
MintRAID aaron # mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf
```

Then we reboot and upon boot are presented with:
"The disk drive for /mnt/data is not read yet or not present" 
"S to skip, M for manual recovery.."

I choose S. 

After logging in:
```
MintRAID aaron # mount -a
mount: special device /dev/md0 does not exist
```


```
MintRAID aaron # mdadm --detail --scan --verbose
ARRAY /dev/md/MintRAID:0 level=raid5 num-devices=3 metadata=1.2 name=MintRAID:0 UUID=21c26d8c:3efb74a0:74f000ab:e3e0a134
   devices=/dev/sdb,/dev/sdc,/dev/sdd
```

   (Notice how the ARRAY name has changed from "/dev/md0" to "/dev/md/MintRAID:0")
   
  
So I check mdstat one last time just for my sanity and the array is there, named **md127** 
```
MintRAID aaron # cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md127 : active (auto-read-only) raid5 sdd[3] sdc[1] sdb[0]
      41939968 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
```

I update my fstab with /dev/md127 instead of /dev/md0 and it seems to be working ok. 

What in the heck is going on? Why all of the naming descrepencies? Can someone help me understand what's going on? I have used the same steps on other (and older) distros and haven't had these troubles. (Ubuntu 9 or 10 something and Cent/RHEL 5.5) I've always named the first array md0, and it's always stayed md0 through reboots, etc etc etc...

---

### Post by Perfect Storm on 2011-06-01
Moved to Other OS/Distro Talk.

---

### Post by Underpants on 2011-06-01
I dont think this should have been moved to a forum where nobody talks about MDADM. As I said in the first post, the exact same results occur on Ubuntu 11.04.

---

### Post by Perfect Storm on 2011-06-01
> **Underpants said:**
> I dont think this should have been moved to a forum where nobody talks about MDADM. As I said in the first post, the exact same results occur on Ubuntu 11.04.

Ok, missed that. I'll remove it back.

---

### Post by Underpants on 2011-06-01
Thanks.

---

### Post by ian dobson on 2011-06-01
Hi,

Did you update your mdadm.conf and rebuild your inital ram disk?

I have 3 mdadm arrays on my backend server and they all work as expected, aslong as the mdadm conf file is ok.

Regards
Ian Dobson

---

### Post by Underpants on 2011-06-01
> **ian dobson said:**
> Hi,

Did you update your mdadm.conf and rebuild your inital ram disk?

I have 3 mdadm arrays on my backend server and they all work as expected, aslong as the mdadm conf file is ok.

Regards
Ian Dobson

I did exactly what I posted. Does that answer the question? Not sure why you're asking.

---

### Post by YesWeCan on 2011-06-01
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/776908](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/776908)

Pants is right. I reproduced this scenario in VirtualBox just now using Mint11. Perhaps this is the reported defect in 11.04.

A couple of incidental things I noticed in your OP:

```
MintRAID aaron # mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf
```
You want the >> directive rather than > or you'll erase the existing contents. The verbose option may not be helpful as it defines the drive numbers. This is not necessary with the UUID.
```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

> What in the heck is going on? Why all of the naming descrepencies?
mdadm is a little hard to figure out and the documentation is sparse to say the least, IMO. My understanding is that at boot mdadm tries to assemble all arrays based on mdadm.conf. If it fails to create the array with the name designated in mdadm.conf it makes up an alternative name. This is why md0 can become md_0 or md_d0 or md_127 or whatever it likes depending on its mood. This is extremely confusing for the uninitiated.

The question is why could it not assemble the drives as /dev/md0. It seems it is probably a goof in 11.04 or the 2.6.38 kernel. I am not expert but sometimes race conditions cause such things - like the kernel tries to mount the array before mdraid has assembled it. I don't know.

As a work-around, you may have to remove the entry from fstab so it always boots and then manually assemble and mount the array. Put the mdadm.conf ARRAYS entry back to the original.
sudo mdadm --assemble /dev/md0
sudo mount /dev/md0 /mnt/raid

[edit] It appears to assemble my array automatically at boot and calls it /dev/md127. So I suppose I can just mount it as such. Why it does not assemble it as md0 as in mdadm.conf is a mystery to me.

---

### Post by Underpants on 2011-06-01
Thanks for taking the time to go through all of that. I'll check out that bug and offer what I can to the cause.

---

### Post by YesWeCan on 2011-06-02
It is a little disconcerting that this "high importance" defect was reported on the 4th of May and still hasn't been assigned to anyone. :o

---

### Post by Underpants on 2011-06-02
> **YesWeCan said:**
> It is a little disconcerting that this "high importance" defect was reported on the 4th of May and still hasn't been assigned to anyone. :o

Sounds like business as usual. :) MDADM doesn't get a lot of use, I'm guessing.

---

### Post by ian dobson on 2011-06-02
> **YesWeCan said:**
> [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/776908](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/776908)

Pants is right. I reproduced this scenario in VirtualBox just now using Mint11. Perhaps this is the reported defect in 11.04.

A couple of incidental things I noticed in your OP:

```
MintRAID aaron # mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf
```
You want the >> directive rather than > or you'll erase the existing contents. The verbose option may not be helpful as it defines the drive numbers. This is not necessary with the UUID.
```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```


mdadm is a little hard to figure out and the documentation is sparse to say the least, IMO. My understanding is that at boot mdadm tries to assemble all arrays based on mdadm.conf. If it fails to create the array with the name designated in mdadm.conf it makes up an alternative name. This is why md0 can become md_0 or md_d0 or md_127 or whatever it likes depending on its mood. This is extremely confusing for the uninitiated.

The question is why could it not assemble the drives as /dev/md0. It seems it is probably a goof in 11.04 or the 2.6.38 kernel. I am not expert but sometimes race conditions cause such things - like the kernel tries to mount the array before mdraid has assembled it. I don't know.

As a work-around, you may have to remove the entry from fstab so it always boots and then manually assemble and mount the array. Put the mdadm.conf ARRAYS entry back to the original.
sudo mdadm --assemble /dev/md0
sudo mount /dev/md0 /mnt/raid

[edit] It appears to assemble my array automatically at boot and calls it /dev/md127. So I suppose I can just mount it as such. Why it does not assemble it as md0 as in mdadm.conf is a mystery to me.

Did you update your inital ram disk after editing your mdadm.conf? When linux boots, it loads the inital ram disk which contains mdadm and the conf file. If you don't update your initramfs then mdadm will load an old/nolonger valid configuration.

Just run sudo update-initramfs -u

Regards
Ian Dobson

---

### Post by YesWeCan on 2011-06-02
Ok Ian, that seems to have fixed it for me. :)

I didn't realise that was necessary. Noted, thanks.
I need to learn more about initramfs and under what circumstances it needs to be manually updated.

---

### Post by Underpants on 2011-06-02
> **YesWeCan said:**
> Ok Ian, that seems to have fixed it for me. :)

I didn't realise that was necessary. Noted, thanks.
I need to learn more about initramfs and under what circumstances it needs to be manually updated.

Me too I guess. I've seen a lot of tutorials about MDADM and haven't ever heard mention of this.

---

### Post by YesWeCan on 2011-06-02
Perhaps you can explain this, Ian.
I have called the array /dev/md0
mdstat calls it md0
I have mounted /dev/md0 at /mnt

BUT...mdadm --examine --scan gives:
[COLOR="Green"]ARRAY /dev/md/0 metadata=1.2 UUID=973772d8:c6d01e01:295210b4:a416708c name=mint:0[/COLOR]

Why is it being called /dev/md/0?

---

### Post by YesWeCan on 2011-06-02
To explore this further, I unmounted, stopped and zero'ed the superblocks on the disks. I removed the ARRAY statement from mdadm.conf.

I then used Disk Utility to create a new array. It automatically called it /dev/md0. I formatted it. All good.

I notice that there is no new ARRAY statement in mdadm.conf. So I gather Disk Utility doesn't update this. Should I?

Now when I do sudo mdadm --examine --scan:
[COLOR="DarkGreen"]ARRAY /dev/md/New RAID Array metadata=1.2 UUID=17070c4e:6171d616:c4af4251:e778f1f5 name=:New RAID Array[/COLOR]

So the array is called **/dev/md0** and it is also called **/dev/md/New RAID Array**.

What does this mean?

I have not tried to reboot. Should I add this ARRAY statement to mdadm.conf or should I add ARRAY /dev/md0...? And should I do an initramfs update in either or one case?

It is very confusing.

---

### Post by Underpants on 2011-06-02
> **YesWeCan said:**
> To explore this further, I unmounted, stopped and zero'ed the superblocks on the disks. I removed the ARRAY statement from mdadm.conf.

I then used Disk Utility to create a new array. It automatically called it /dev/md0. I formatted it. All good.

I notice that there is no new ARRAY statement in mdadm.conf. So I gather Disk Utility doesn't update this. Should I?

Now when I do sudo mdadm --examine --scan:
[COLOR="DarkGreen"]ARRAY /dev/md/New RAID Array metadata=1.2 UUID=17070c4e:6171d616:c4af4251:e778f1f5 name=:New RAID Array[/COLOR]

So the array is called **/dev/md0** and it is also called **/dev/md/New RAID Array**.

What does this mean?

I have not tried to reboot. Should I add this ARRAY statement to mdadm.conf or should I add ARRAY /dev/md0...? And should I do an initramfs update in either or one case?

It is very confusing.

Hmm. Maybe I'll just do it from the disk utility from now on. Let me try some things in my VM.

---

### Post by YesWeCan on 2011-06-02
Yes, VirtualBox is so very useful.

More learning by doing has revealed that the output of
mdadm --examine --scan
is no longer compatible with mdadm.conf

It used to be but it has changed. I found this out because the spaces in the name "New RAID Array" upsets mdadm.

1) You have to **manually put an ARRAY statement in mdadm.conf** using the proper device name, eg: /dev/md0. There must not be any other garbage in the line such as the array text label. Mine is now:

```
[COLOR="DarkGreen"]# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Wed, 01 Jun 2011 21:28:17 +0100
# by mkconf $Id$
ARRAY /dev/md0 metadata=1.2 UUID=17070c4e:6171d616:c4af4251:e778f1f5[/COLOR]
```

2) The array will fail to mount at boot (as defined in /etc/fstab) unless you also do:
**sudo update-initramfs -u**


I am used to mdadm on 10.04 and things seem to have changed a bit in Natty/Mint 11.

---

### Post by Underpants on 2011-06-02
When you built an array with Disk Manager, did you get an error/warning about misaligned partitions?

---

### Post by YesWeCan on 2011-06-02
I used "Disk Utility" under System/Administration. I had no errors.
I used 3 3GB disks. I gave them new MBRs (although that is not necessary) so they were just free space. Then created a RAID5 with them.

---

### Post by Underpants on 2011-06-02
> **YesWeCan said:**
> I used "Disk Utility" under System/Administration. I had no errors.
I used 3 3GB disks. I gave them new MBRs (although that is not necessary) so they were just free space. Then created a RAID5 with them.

Where/How did you do the new MBR? 


I'm reading over this thread about the error:
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by YesWeCan on 2011-06-02
Click on each disk in turn, then on "Format Drive".

---

### Post by Underpants on 2011-06-03
Did the "update-initramfs -u" command help you? I'm still scratching my head a little bit...

:rant:
The disk manager thing is crappy IMO. I think the sector offset error is a bug, and I've never been able to expand arrays, it just always gives errors about things being in use, something holding something open, etc etc etc.... I don't think it's implemented very well, but that's another thread :)

---

### Post by tgalati4 on 2011-06-03
I presume you mean 3 x 3 TB drives.  Could be a timing issue reading the drives causing mdadm to fail.

dmesg | tail -50

---

### Post by YesWeCan on 2011-06-03
> **Underpants said:**
> Did the "update-initramfs -u" command help you? I'm still scratching my head a little bit...
Yes. I think the concept is that when Ubuntu first boots it actually runs from an image file that is not the same as the files on your hard drive. This image file is initramfs (I think - short for initial RAM filesystem). It turns out that assembling the array at boot requires mdadm.conf info to be in the initramfs because the arrays have to get assembled before the proper filesystem is accessed. I suppose this is necessary when the OS is installed on an array itself.

If when using Disk Utility it says the drive is busy, it may be that the array is running, even if it is not mounted. So you have to "stop" the array. From a command line you can see what is running using
cat /proc/mdstat
and stop using
sudo mdadm --stop /dev/md0

mdadm sort of runs behind the scenes. That's why a drive may be busy even though it is not mounted.

The other thing is that mdadm stores some data in a special location on each drive so that it can recognize them as previously being part of an array (and some other details). This data is stored in the "superblock". To permanently remove a disk from an array you have to stop the array and then erase the superblocks of each array member
sudo madam --zero-superblock /dev/sdn

Hope that helps.

---

### Post by YesWeCan on 2011-06-03
> **tgalati4 said:**
> I presume you mean 3 x 3 TB drives.
I simulated it in VirtualBox using small disks to save time on the formatting.

---

### Post by Underpants on 2011-06-03
> **YesWeCan said:**
> Yes. I think the concept is that when Ubuntu first boots it actually runs from an image file that is not the same as the files on your hard drive. This image file is initramfs (I think - short for initial RAM filesystem). It turns out that assembling the array at boot requires mdadm.conf info to be in the initramfs because the arrays have to get assembled before the proper filesystem is accessed. I suppose this is necessary when the OS is installed on an array itself.

If when using Disk Utility it says the drive is busy, it may be that the array is running, even if it is not mounted. So you have to "stop" the array. From a command line you can see what is running using
cat /proc/mdstat
and stop using
sudo mdadm --stop /dev/md0

mdadm sort of runs behind the scenes. That's why a drive may be busy even though it is not mounted.

The other thing is that mdadm stores some data in a special location on each drive so that it can recognize them as previously being part of an array (and some other details). This data is stored in the "superblock". To permanently remove a disk from an array you have to stop the array and then erase the superblocks of each array member
sudo madam --zero-superblock /dev/sdn

Hope that helps.

I'm pretty happy with the way things are right now. I'm still doing everything command line, but updating initram seems to do the trick. I'll read the man pages on that so I understand better what's going on. I really appreciate your help with this. Hero.

---

### Post by Underpants on 2011-06-03
While I have everything working happily, I still don't understand the naming mismatch...

[IMG]http://dl.dropbox.com/u/2209048/mint_md0.png[/IMG]

It's mounted and recognized as /dev/md0 but look at what the mdadm scan calls it.... :confused:

---

### Post by ian dobson on 2011-06-03
Hi,

It looks like your superblock for the array has corruption or a strange name defined. Or it could be a bug in mint/mdadm. I see that your array has meta data version 1.2, which is new to me.

Regards
Ian Dobson

---

### Post by psusi on 2011-06-03
You should be using the UUID not the device name in /etc/fstab.

---

### Post by Underpants on 2011-06-03
> **psusi said:**
> You should be using the UUID not the device name in /etc/fstab.

I've always heard the opposite.

---

### Post by Underpants on 2011-06-03
> **ian dobson said:**
> Hi,

It looks like your superblock for the array has corruption or a strange name defined. Or it could be a bug in mint/mdadm. I see that your array has meta data version 1.2, which is new to me.

Regards
Ian Dobson

I think I rebooted once before doing the "update-initramfs -u" command which messes it up. I started over from scratch and it looks OK now.

---

### Post by Underpants on 2011-06-03
Here's the quick and dirty. This is what I've saved to my personal wiki to reference. 

```
* create array
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd

* format array
mkfs.ext4 /dev/md0

* /etc/fstab
/dev/md0        /mnt/data       ext4    defaults        0 0

* mount lines from fstab
mount -a

* visual check of array config
mdadm --detail --scan --verbose

* write it to the mdadm.conf file
mdadm --detail --scan --verbose >> /etc/mdadm/mdadm.conf

* add MAILADDR to the mdadm.conf file 
MAILADDR me@me.com

* install ssmtp and remove postfix
apt-get install ssmtp

* edit /etc/ssmtp/ssmtp.conf to fit your specs

* reconfigure MDADM: use obvious answers for mail and checking
dpkg-reconfigure mdadm

* update initramfs
update-initramfs -u


```

---

### Post by psusi on 2011-06-03
> **Underpants said:**
> I've always heard the opposite.

From where?!

They added UUIDs for a reason...

---

### Post by YesWeCan on 2011-06-03
> **ian dobson said:**
> It looks like your superblock for the array has corruption or a strange name defined. Or it could be a bug in mint/mdadm. I see that your array has meta data version 1.2, which is new to me.
I don't know whether it is a bug but it now seems possible to give an array a textual name, and the --examine command prints this out. Is that deliberate, might be. Trouble is the old method of adding this output to mdadm.conf doesn't work.
Someone needs to write a decent user's guide for mdadm.

---

### Post by Underpants on 2011-06-03
> **YesWeCan said:**
> I don't know whether it is a bug but it now seems possible to give an array a textual name, and the --examine command prints this out. Is that deliberate, might be. Trouble is the old method of adding this output to mdadm.conf doesn't work.
Someone needs to write a decent user's guide for mdadm.

After re-doing the array with the code block I most recently posted, I get this from  the examine command:

```
aaron@mint ~ $ sudo mdadm --examine /dev/md1
[sudo] password for aaron:
mdadm: No md superblock detected on /dev/md1.

```

---

### Post by psusi on 2011-06-03
That is because examine is for looking at the underlying physical disks.

---

### Post by Underpants on 2011-06-03
So are my results bad, or to be expected?

---

### Post by YesWeCan on 2011-06-04
> **psusi said:**
> That is because examine is for looking at the underlying physical disks.
Let me elaborate a little.

--examine displays the metadata (superblock data) for a particular **partition**.
I have 4 disks which contain 2 partitions, one is a member of md0 and the other md1.
If I do [COLOR="Blue"]mdadm --examine /dev/sdb1[/COLOR] or [COLOR="Blue"]mdadm --examine /dev/sdb2[/COLOR] I get a superblock display. But if I do [COLOR="blue"]mdadm --examine /dev/sdb[/COLOR] I get "no superblock detected".

--detail gives superblock data for a specific **md device**. Eg: [COLOR="blue"]mdadm --detail /dev/md1[/COLOR].

If instead of specifying a device or partition you use --scan then the info is found from /proc/mdstat and mdadm.conf.

It would be a lot simpler if there was just one command to display superblock data for whatever you specify. Sigh.

---

### Post by YesWeCan on 2011-06-04
> **Underpants said:**
> So are my results bad, or to be expected?
Expected. Counter-intuitive, but expected.

---

