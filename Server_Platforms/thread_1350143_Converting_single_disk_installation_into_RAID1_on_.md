---
title: "Converting single disk installation into RAID1 on Ubuntu Server 8.0LTS"
date: 2009-12-09
forum: Server Platforms
---

### Post by fukc on 2009-12-09
Hello,

It's hard to believe, but for such a simple operation as converting single-disk installation into raid1 so many steps are needed on a typical linux box. 

It's so simple in Opensolaris compare to the same operation on Linux. Just one command:
zpool attach rpool drive_paths 
and you done.

Well, unfortunately I have to run Linux for this particular installation of the mail system and it requires raid1 which wasn't setup from the beginning. 

No luck so far...

I'm using this guide as a reference, but probably it's not a very accurate one:
[http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub-configuration-debian-lenny](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub-configuration-debian-lenny)

So, I need some help to sort things out, especially with setting up grub. 

Are these correct steps?

1. create raid1 with missing device on the second drive
2. change menu.lst to boot the system from the second drive
3. update initrd image (update-initramfs -u)
4. copy / to the mounted md device
5. install grub on the second drive 
grub-install  /dev/sdb
6. setup grub on the second drive
grub-setup -v  /dev/sda

At this point the system is trying to boot from sdb, but fails - initrd panic. It can boot from sda having / partition on /dev/md0, but obviously this doesn't make much sense as I can't edit sda in this case (attach it to md).

Is there something I'm missing? I'm using grub2, not sure if this is a good idea.

I'm quite frustrated with all this stuff already...
Any help is much appreciated.

--
Roman

---

### Post by fukc on 2009-12-09
Has anybody converted singe-drive Ubuntu into raid1?

---

### Post by munky99999 on 2009-12-09
I have a feeling nobody has because it's pretty bad practice. Doing this would pretty much half your drive's performance automatically. Not to mention the added overhead because of the raid. You are practically killing the drive.

Why no use a basic disk and do backups appropriately?

Not to mention the impracticality of the whole thing. 

If the drive dies. So does the mirror... so really you lose those backups. Furthermore all changes are happening pretty quick. So any of the ability that backups provide... like being able to recover lost data. Is gone.


Seriously. This is just a bad idea. Just do backups.

I'm feeling trolled =D>

---

### Post by fukc on 2009-12-09
> **munky99999 said:**
> I have a feeling nobody has because it's pretty bad practice. Doing this would pretty 
...
gibberish skipped
...
I'm feeling trolled =D>

You definitely are.

Any other ideas except this is a "bad practice" as munky joked?

---

### Post by memilanuk on 2009-12-09
What specifically in that guide are you having problems with?

The biggest potential snafu I see is that its written for Debian Lenny, which is closer to Ubuntu 8.04.3 LTS than 9.10 (which I presume your using if you have grub2).  I'm no boot-loader expert, not even close... but if I was a betting man, I'm guessing that (grub vs. grub2) might be where your problem lies.

---

### Post by munky99999 on 2009-12-09
> **fukc said:**
> You definitely are.

Any other ideas except this is a "bad practice" as munky joked?

I'm so confused. Are you seriously trying to make a single disk a raid 1? So the parity is on the same drive?

Or do you have a second disk that you want to migrate the single disk to? Whatever. I dont know what you're doing.

Here's what you could do.

[http://ubuntuforums.org/showpost.php?p=4391983&postcount=2](http://ubuntuforums.org/showpost.php?p=4391983&postcount=2)

another

[http://www.tenshu.net/archives/2008/01/14/migrating-ubuntu-to-raid1/](http://www.tenshu.net/archives/2008/01/14/migrating-ubuntu-to-raid1/)

---

### Post by fukc on 2009-12-09
> **munky99999 said:**
> I'm so confused. Are you seriously trying to make a single disk a raid 1? So the parity is on the same drive?

Or do you have a second disk that you want to migrate the single disk to? Whatever. I dont know what you're doing.

Here's what you could do.

[http://ubuntuforums.org/showpost.php?p=4391983&postcount=2](http://ubuntuforums.org/showpost.php?p=4391983&postcount=2)

another

[http://www.tenshu.net/archives/2008/01/14/migrating-ubuntu-to-raid1/](http://www.tenshu.net/archives/2008/01/14/migrating-ubuntu-to-raid1/)

Why would you think I might want put mail server on Ubuntu LTS OS on raid1 consisting of 1 drive???

raid1 - it's a mirrored array. Anyway, thanks for the links but they are not related much to what I have.

---

### Post by memilanuk on 2009-12-09
munky,

Read the original post again carefully, and look for these words: 'second drive'... ;)

Speaking of 'reading for comprehension... looks like I stumbled on that also.  I see fukc is using 8.04 LTS, not 9.10.  My bad.  

I do think the grub2 thing is whats keeping the HowtoForge tutorial from working for you.

---

### Post by fukc on 2009-12-09
> **memilanuk said:**
> What specifically in that guide are you having problems with?

The biggest potential snafu I see is that its written for Debian Lenny, which is closer to Ubuntu 8.04.3 LTS than 9.10 (which I presume your using if you have grub2).  I'm no boot-loader expert, not even close... but if I was a betting man, I'm guessing that (grub vs. grub2) might be where your problem lies.

I tried both grub version, no difference. 

I have issues with initramfs and with installing grub on the second drive (which is the part of degraded md0).

When and how to update iniramfs  correctly? After copying data to the degraded array inside chroot on this raid? Or maybe on old drive and then copy init image to the raid and reboot?
 
How to install grub on the array drive? Should the menu.lst be corrected before or after grub install? Inside chroot or just point grub to the second drive?

So, all this is such a big confusion to me... 
The idea is very clear - copy data to the degraded array, reboot, attach the second drive, update grub again.
But it just doesn't work - too much small hidden "linux-way" things to know. 

Hell, why it takes half-an-hour on Solaris to perform such operation and so much time on Linux?

--
Roman

---

### Post by Seq on 2009-12-09
Are you using LVM? It would make it substantially easier as you could set up your degraded raid set, migrate your LV over, then add the original disk to your raid set and wait for it to sync.

You could also just set up LVM mirroring instead of using the device mapper. I'm not sure how that handles booting in a sda failure situation though.

I'm actually setting up a new home server currently on one drive, with a plan on switching it to raid 1 when I move the drive to it's permanent home in my current server's chassis. I can move my transition up to tomorrow evening, but unfortunately tonight I'm busy with a server migration for work.

---

### Post by Seq on 2009-12-09
> **munky99999 said:**
> I have a feeling nobody has because it's pretty bad practice. Doing this would pretty much half your drive's performance automatically. Not to mention the added overhead because of the raid. You are practically killing the drive.doing disk mapper raid in-kernel definately has a performance hit over doing it on a dedicated hardware raid card, but I wouldn't say you halve your performance. If you use device-mapper you can actually improve your read speed quite a bit if it staggers reads (using a lvm mirror does not stagger reads, but you may not care). It's not like it has to calculate parity like other forms of raid.

> **munky99999 said:**
> Why no use a basic disk and do backups appropriately?Sounds like somebody hasn't been called at 2:00 before.

> **munky99999 said:**
> If the drive dies. So does the mirror... so really you lose those backups. Furthermore all changes are happening pretty quick. So any of the ability that backups provide... like being able to recover lost data. Is gone.Yes, simultaneously is pretty quick indeed. And they do survive a single disk failure. You usually test by crossing your fingers and pulling a disk. Also note that RAID of any kind are not backups, and I haven't heard anybody claim as such.

> **munky99999 said:**
> I'm feeling trolled =D>I hope I didn't just feed one.. :)

---

### Post by munky99999 on 2009-12-09
> **memilanuk said:**
> munky,

Read the original post again carefully, and look for these words: 'second drive'... ;)

Read the subject. Single disk installation.

second drive is possibly meant as "second logical drive" is how I took it.

i dunno. ignore me.

---

### Post by memilanuk on 2009-12-09
Okay... bear with me here.  My 'real' Ubuntu 8.04.3 LTS server with RAID1 has the OS on a separate 13.8GB IDE HDD (hda) and then /srv mounted on RAID1 on two 500GB SATA HDDs - and I did that during installation, not after the fact.

I can perhaps mock something up inside Virtualbox and give it a whirl, though.

> **fukc said:**
> 
When and how to update iniramfs  correctly? After copying data to the degraded array inside chroot on this raid? Or maybe on old drive and then copy init image to the raid and reboot?


So you're saying that the part on page 2 (tail end of section #5)where it says:

> *Next we adjust our ramdisk to the new situation:*
```

update-initramfs -u

```


doesn't work for you?

>  
How to install grub on the array drive? Should the menu.lst be corrected before or after grub install? Inside chroot or just point grub to the second drive?


So part #6 where it specifically talks about preparing grub to boot off the 2nd HDD (which should by then have the RAID stuff on it) doesn't work?

---

### Post by fukc on 2009-12-09
> **Seq said:**
> Are you using LVM? It would make it substantially easier as you could set up your degraded raid set, migrate your LV over, then add the original disk to your raid set and wait for it to sync.

You could also just set up LVM mirroring instead of using the device mapper. I'm not sure how that handles booting in a sda failure situation though.

I'm actually setting up a new home server currently on one drive, with a plan on switching it to raid 1 when I move the drive to it's permanent home in my current server's chassis. I can move my transition up to tomorrow evening, but unfortunately tonight I'm busy with a server migration for work.

Again, it doesn't solve the complications with grub setup and initram image generation. 
Not to mention LVM management itself which is another nice Linux invention.

Are you setting your server completely without raid? Let me know if you succeed converting it to the raid1.

---

### Post by fukc on 2009-12-09
> **memilanuk said:**
> Okay... bear with me here.  My 'real' Ubuntu 8.04.3 LTS server with RAID1 has the OS on a separate 13.8GB IDE HDD (hda) and then /srv mounted on RAID1 on two 500GB SATA HDDs - and I did that during installation, not after the fact.

I can perhaps mock something up inside Virtualbox and give it a whirl, though.

So you're saying that the part on page 2 (tail end of section #5)where it says:

doesn't work for you?

So part #6 where it specifically talks about preparing grub to boot off the 2nd HDD (which should by then have the RAID stuff on it) doesn't work?

No problem with creating arrays in mdadm, copying files and so on. The problem is only about generating image and installing grub.

Let me quickly check what I have in virtual box (I gave up trying to set it up on a real server so far):

Ubuntu 8.04 LTS, I installed grub2 but the grub is all the same.

hd0 - dev/sda
hd1 - dev/sdb

md0 - dev/sdb1 with missing dev/sda1 root
md1 - dev/sdb5 with missing dev/sda5 swap

#mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
....

So, I have tried grub-install, grub-setup, update-initramfs -u and everything else from the original guide.

Now I'm trying now to boot from the second drive with md0 as a root device.
linux (hd1,1)/boot/vmlinux... root=/dev/md0
initrd (hd1,1)/boot/initrd...

...
/init: 184 cannot open root/dev/console: no such
 file
kernel panic - not syncing: Attempted to kill init!

After "Running /scripts/local-premount ..." I see
kinit: name_to_dev_t(bla-bla) = sda5(8,5)

As I understand it should be something related to md0 or md1. sda shouldn't be involved on this step... Apparently init image wasn't generated properly. Booting from hd0 works fine, even if root filesystem is mounted on /dev/md0 in fstab.

--
Roman

---

### Post by memilanuk on 2009-12-10
Well... you probably ain't gonna like hearing this but...

I worked through the guide pretty much step by step, and it worked *perfectly*.  

Really there were only a few points where I deviated from the howto:

1) Initially I went with the default 'Guided Partitioning - Use whole disk) during install, which gives you '/' on sda1 and swap on sda5 and sda2 just kind of sitting there.  I wasn't *sure* at first, so I went back and reinstalled (this is all on Virtualbox) and manually partitioned so that I had sda1 = /boot, sda2 = /, sda3 = swap.  Then after I got into it a bit I realized the tutorial switched / and swap on sda2 and sda3, but I left it alone at that stage.  Point is, I don't know if it matters if your raid partitions be on primary partitions, or if you *need* a /boot partition for this - I doubt it - but I opted to not be adventurous in that regard when working through a tuturial.

2) Some of the commands just wouldn't work as 'sudo foo', I had to do 'sudo su -l' and just work as root - which was actually easier for a long session like this.

3) I initially installed initramfs-tools and mdadm via apt-get, *watched* it install, but the first time I went to use mdadm, the system complained that it was not installed and couldn't find a trace of it.  So I installed it again, and everything went without a hitch.

4) Those dang UUIDs... most of my Linux usage predates these PITA, so I've been avoiding anything that required me to really work with them (fairly successfully, too).  Couldn't dodge 'em anymore; had to list 'em out (and write them down) for md0, md1, & md2, and enough of the numbers for sda1 and sda2 to be able to recognize them inside config files.  After that, all the places where the howto said 'change /dev/sda2 to /dev/md1' or similar, I looked for the appropriate UUID and entered the new values for md0/1/2... in /etc/fstab, /etc/grub/menu.lst, *except* I believe /etc/mtab.

HTH,

Monte

---

### Post by fukc on 2009-12-10
memilanuk, thanks for following up. 

But you see - nobody knows how these dumn linux things work. You've mentioned about /boot on dedicated partition. I don't have this partition and I wouldn't like to create it. The raid might boot without it, might not. Nobody knows and who really cares? I just wander how people run their production boxes though...

And that's the difference between real OS like Solaris and crowd-created-nobody-knows-how-it-works fake OS like Linux. No real documentation, no real engineers here, it's pity. 

I don't know.
The easiest way is to reinstall the whole server on the 2 disk raid1 from the beginning and copy the application back to it. 
But again - has anybody seen how unbelievably complex the process of installation on raid in ubuntu?

Poor thing...

--
Roman

---

### Post by memilanuk on 2009-12-10
Generally speaking... it is a lot cleaner/simpler in the distros that I've tried to set up RAID (and LVM for that matter) during installation.  The installer programs limit your options somewhat, but make fairly intelligent default choices from what I can tell.  

I've never mucked about with Solaris in the past - something about Sparc equipment and a home hobbyist budget that were incompatible ;) I have to admit, I'm somewhat tempted to give it a spin now that OpenSolaris is out and correct me if I'm wrong, works on generic x86 hardware?

You're saying that Solaris lets you just add a drive to an existing install, and convert the whole shebang over to RAID click click done?  Sounds impressive.  

So... it sounds like since this isn't going to work just the way you want, based on your experience in a different operating system with different conventions, you're just going to wash your hands of the whole thing even after I demonstrated that the tutorial *does* work if you follow it with some Ubuntu specific variation (UUIDs).  Then you condemn the whole Linux pantheon based off this one thing.  Sounds more like you were looking for things to fail to justify your favored choice (Solaris).

As for comparing Linux to Solaris based on Ubuntu... ah, I may get flamed for this, but I don't think thats best comparison.  I'm not sure the process is necessarily any simpler on say, CentOS (the open source version of RHEL) or openSuSE (open source version of SLES/SLED) or Debian (obviously not), but I think if you asked your original question on the appropriate mailing list or forum for those distros (which tend to see more use in formal settings, at least at this point) you'd probably run into people more equipped to answer your question - closer to the 'power user' end of the spectrum.  There are some in the Ubuntu crowd as well, but this is a somewhat obscure variation of the normal 'set up RAID1' question.  Of course, some of them would likely also tell you to go RTFM before they spent several hours working through something for you...

Edited to add...

More Linux RAID info for you:

[Linux Software RAID HOWTO]("http://www.tldp.org/HOWTO/html_single/Software-RAID-HOWTO/")

[Linux-RAID mailing list]("http://marc.info/?l=linux-raid")

---

### Post by fukc on 2009-12-10
> Generally speaking... it is a lot cleaner/simpler in the distros that I've tried to set up RAID (and LVM for that matter) during installation.  The installer programs limit your options somewhat, but make fairly intelligent default choices from what I can tell.  


It's not, unfortunately. There are like dozen step process to create simple raid1 and couple dozens if you want lvm on top of that. Complete failure on whole software-raid design.
RedHat-based are more intuitive in making raid during installation, although converting single-disk into raid is painful as on Debian-based. I can bet on this. 

> I've never mucked about with Solaris in the past - something about Sparc equipment and a home hobbyist budget that were incompatible ;) I have to admit, I'm somewhat tempted to give it a spin now that OpenSolaris is out and correct me if I'm wrong, works on generic x86 hardware?

It works on x86, although it's destined to run on sparc. 

> 
You're saying that Solaris lets you just add a drive to an existing install, and convert the whole shebang over to RAID click click done?  Sounds impressive.  

So... it sounds like since this isn't going to work just the way you want, based on your experience in a different operating system with different conventions, you're just going to wash your hands of the whole thing even after I demonstrated that the tutorial *does* work if you follow it with some Ubuntu specific variation (UUIDs).  Then you condemn the whole Linux pantheon based off this one thing.  Sounds more like you were looking for things to fail to justify your favored choice (Solaris).



Well, Solaris installs the system on 1 disk initially but with considering it as a device for a raid1. That's why it's so easy to make it mirrored.
Actually there are many more things to condemn Linux for...

> 
As for comparing Linux to Solaris based on Ubuntu... ah, I may get flamed for this, but I don't think thats best comparison.  I'm not sure the process is necessarily any simpler on say, CentOS (the open source version of RHEL) or openSuSE (open source version of SLES/SLED) or Debian (obviously not), but I think if you asked your original question on the appropriate mailing list or forum for those distros (which tend to see more use in formal settings, at least at this point) you'd probably run into people more equipped to answer your question - closer to the 'power user' end of the spectrum.  There are some in the Ubuntu crowd as well, but this is a somewhat obscure variation of the normal 'set up RAID1' question.  Of course, some of them would likely also tell you to go RTFM before they spent several hours working through something for you...

Probably I should've asked my question on dedicated list. 

But what I wanted to say that such basic thing as raid1 installation is overcomplicated and undocumented for Linux. Developers should probably try Solaris and then think carefully how things are designed on Linux.

--
Roman
PS eventually it worked out, with all these mounts-remounts, creating /dev /sys /var/run, dozen reboots and so on. I swear I won't be able repeat this ever. Poor linux...

---

### Post by memilanuk on 2009-12-10
> **fukc said:**
> It's not, unfortunately. There are like dozen step process to create simple raid1 and couple dozens if you want lvm on top of that. Complete failure on whole software-raid design.

Well, if you're such the expert on what constitutes a 'proper' RAID setup... I'm sure the developers are eagerly awaiting your sage advise. :-s

> 
Well, Solaris installs the system on 1 disk initially but with considering it as a device for a raid1. That's why it's so easy to make it mirrored.


Interesting... so the default installation is as a degraded RAID array consisting of one disk.  I guess it makes sense if you assume people are going to want to add a disk later... guess most Linux distros assume if you want RAID, its something big enough to do as a part of a planned system upgrade/install.  Often it is joined with LVM - make *one* RAID device on each disk, rather than multiple partitions, and then do your partitioning as desired via the volume manager.  One could probably argue either way.


> 
Probably I should've asked my question on dedicated list. 

And right about now they'd be using you to toast marshmellows with... ;)

> 
But what I wanted to say that such basic thing as raid1 installation is overcomplicated and undocumented for Linux. Developers should probably try Solaris and then think carefully how things are designed on Linux.

Over complicated, maybe.  Poorly documented, no.  The Linux Software-RAID HOWTO I linked to has been around for years - may not be the easiest reading, but it's been there the whole time you've been griping here.  

> 
PS eventually it worked out, with all these mounts-remounts, creating /dev /sys /var/run, dozen reboots and so on. I swear I won't be able repeat this ever.

I don't know what the heck you're talking about.  I installed the system, at initial boot did the usual system upgrade (because 8.04.3 is a little long in the tooth) with 'apt-get update' followed by 'apt-get upgrade', rebooted (not because I had to, but because I felt it was a good idea after a kernel upgrade) then started the RAID tutorial.  In the process of that little evolution, I rebooted *twice*.  Once to kick over from /dev/sda to /dev/md* (/dev/sdb), then once more to 'simulate' recovering a failed drive (i.e. shutdown and 'remove' the 'failed' disk, install a new one, and restart the machine - so that restart was technically optional.  As for the creating /dev /sys /var/run and other allegations... either you're following a very different document than the one originally linked to, or you're just plain making stuff up for the sake of drama.

Monte

---

### Post by fukc on 2009-12-10
> I don't know what the heck you're talking about.  I installed the system, at initial boot did the usual system upgrade (because 8.04.3 is a little long in the tooth) with 'apt-get update' followed by 'apt-get upgrade', rebooted (not because I had to, but because I felt it was a good idea after a kernel upgrade) then started the RAID tutorial.  In the process of that little evolution, I rebooted *twice*.  Once to kick over from /dev/sda to /dev/md* (/dev/sdb), then once more to 'simulate' recovering a failed drive (i.e. shutdown and 'remove' the 'failed' disk, install a new one, and restart the machine - so that restart was technically optional.  As for the creating /dev /sys /var/run and other allegations... either you're following a very different document than the one originally linked to, or you're just plain making stuff up for the sake of drama.


Drama? This is complete disaster - making raid array on Linux :) Well, I didn't copy stuff to the raid drive, I synchronised it with rsync. Without copying all that /dev and /sys for obvious reason. Then I had to recreate them when trying to boot from the second drive. Probably my mistake. Anyway...

Look at this [http://docs.sun.com/app/docs/doc/817-2530/6mi6gg88t?a=view](http://docs.sun.com/app/docs/doc/817-2530/6mi6gg88t?a=view) and compare with Linux documentation.

See the difference in how it's organised and what most important, you can see real engineering approach for system development behind this documentation.

Ok, thanks for helping, memilanuk!
Try Solaris sometime to have the real taste of enterprise system compare to a crowd-created one.

--
Roman

---

### Post by rangegate on 2011-11-21
Did you ever get resolution on converting your single disk to RAID-1 and then adding the 2nd?  I wanted to do the same thing, but couldn't risk the production disk and install, so just use the 2nd disk for backups.

---

