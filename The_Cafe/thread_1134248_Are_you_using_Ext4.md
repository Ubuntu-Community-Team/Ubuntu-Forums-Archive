---
title: "Are you using Ext4?"
date: 2009-04-23
forum: The Cafe
---

### Post by artir on 2009-04-23
Just I want to know some people's experiences with ext4 to decide wheter to change or keep ext3.

---

### Post by Darkhack on 2009-04-23
It's still a brand new file system and there are bugs.  Ubuntu backported some of the patches that fix the rename() sans fysnc() bug, but I'm still weary about switching.  I'll probably wait until the next LTS before going with ext4.  That way it will have gone through plenty of testing with the 9.04 and 9.10 releases.

---

### Post by adamlau on 2009-04-23
Not yet, not until all the extension are fully supported. Until then, ext2 for /boot and XFS everywhere else...

---

### Post by jelle_ on 2009-04-23
root partition is ext4. /home is ext3 to keep my data on the partition

---

### Post by Brian_the_King on 2009-04-23
I'm using it without a single problem.. only been one day though :p

---

### Post by markp1989 on 2009-04-23
im using ext4 now, the firts day i used it , i ran in to problem, i did a fresh install of arch, then when i started x, x froze, because of the hot plug bug. so i had to do a hard power off. when i done that i ended up with a bunch of zero byte files, because of the delayed allocation . then when i tried to install gtk again, pacman refused, because the files already existed. 

here is the thread about it
[http://bbs.archlinux.org/viewtopic.php?id=68134](http://bbs.archlinux.org/viewtopic.php?id=68134)


 i did a reinstall, and now im running fine with ext4, mounts, and checks faster then ext2 did,

---

### Post by SuperSonic4 on 2009-04-23
> **markp1989 said:**
> im using ext4 now, the firts day i used it , i ran in to problem, i did a fresh install of arch, then when i started x, x froze, because of the hot plug bug. so i had to do a hard power off. when i done that i ended up with a bunch of zero byte files, because of the delayed allocation . then when i tried to install gtk again, pacman refused, because the files already existed. 

here is the thread about it
[http://bbs.archlinux.org/viewtopic.php?id=68134](http://bbs.archlinux.org/viewtopic.php?id=68134)


 i did a reinstall, and now im running fine with ext4, mounts, and checks faster then ext2 did,

Ah the input hotplugging is very annoying, luckily the arch wiki came up trumps again :popcorn:

I'm using ext4 in / and /home (still using reiserfs in /var) and I don't notice an appreciable gain but it's probably there. No problems though

---

### Post by Eisenwinter on 2009-04-23
I have an Ext3 /boot, Ext4 root, home, and /Music.

Have been on Ext4 for about 3 weeks now.

---

### Post by Xero Xenith on 2009-04-23
I'm considering moving to ext4 for my root partition for better boot time, but I'm not switching my /home over any time soon. 450 GB of stuff would take too long to replace.

So for now, ext3 all the way.

---

### Post by khelben1979 on 2009-04-23
I only use the Extended 3 filesystem and don't care about version 4 until it has been accepted as stable of those who use it.

I don't want to experience data losses with the things that I have.

---

### Post by markp1989 on 2009-04-23
> **khelben1979 said:**
> I only use the Extended 3 filesystem and don't care about version 4 until it has been accepted as stable of those who use it.

I don't want to experience data losses with the things that I have.

i have only use ext4 on my root and home, my data partition is still ext2 . i dont store anything in home , just a few .dot files

---

### Post by linux_paul on 2009-04-23
Using ext4 for root, home and var. No problems in the last two weeks. XFS for data, media and backups.

---

### Post by wolfen69 on 2009-04-23
been using it for a month with no problems.

---

### Post by mister_k81 on 2009-04-23
I reformatted my harddrive and did a fresh install with EXT4 (windows is on a separate HDD). I'm not exactly sure if this is the best route to go, but I'll give it a shot I guess.. and if I start experiencing problems, It's back to EXT3.

So far, it does feel speedier... and I haven't noticed any issues yet (though, that's not saying much, since I've been only using it for an hour now).

---

### Post by the8thstar on 2009-04-23
Yes.

---

### Post by billgoldberg on 2009-04-23
> **khelben1979 said:**
> I only use the Extended 3 filesystem and don't care about version 4 until it has been accepted as stable of those who use it.

I don't want to experience data losses with the things that I have.

EXT4 is considered stable.

Any piece of software has bugs.

---

### Post by Dragonbite on 2009-04-24
> **jelle_ said:**
> root partition is ext4. /home is ext3 to keep my data on the partition

That's the schema I was thinking of but with /boot being ext2

---

### Post by kpkeerthi on 2009-04-24
ext2 for /boot
reiserfs for /var
jfs for /home and all my back up drives.

---

### Post by AndyCooll on 2009-04-24
Briefly used it recently. Didn't experience any problems with it.

However I've recently been dual booting with other distros. And if the MBR is on an ext3 partition, ext4 isn't supported so you can't then boot into a distro that's on an ext4 partition.

So, I'm staying with ext3 for now until the distros I use offer ext4 partitioning.

Might revisit it when I've a bit more time.

:cool:

---

### Post by lukjad on 2009-04-24
I've heard horror stories. I'm letting other brave souls to test it out for me. ;)

---

### Post by meeples on 2009-04-24
ive been using ext4 since yesterday, the only major difference ive seen is my boot time has drastically changed, it now goes from power on to login screen in under 15 seconds which is amazing considering i have a pretty low spec system :D

---

### Post by Sand &amp; Mercury on 2009-04-24
I've been using it for a few months now, since it was first included in Jaunty's development builds. No problems at all.

---

### Post by JohnFH on 2009-04-24
> **AndyCooll said:**
> 
However I've recently been dual booting with other distros. And if the MBR is on an ext3 partition, ext4 isn't supported so you can't then boot into a distro that's on an ext4 partition.

So, I'm staying with ext3 for now until the distros I use offer ext4 partitioning.


The MBR isn't on a partition.  It sits before it.  However, it sounds like the grub version you are using doesn't support ext4 partitions.  Just update your grub version (choose to install grub from the Jaunty installation is one way) and it should work.

---

### Post by Lunx on 2009-04-24
Upgraded to ext4, all went well. Boots faster, but that's only difference I'm noticing.

---

### Post by Delever on 2009-04-24
I am still using ext3 for my data, but ext4 for system partition. I don't care so much about system partition :). But it works fine so far.

---

### Post by whoop on 2009-04-24
I converted my ext3 file system to ext4 a while back using this method:
HOWTO: Convert your ext3 file system to ext4 (in Jaunty) [http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

running sweet.

---

### Post by Dragonbite on 2009-04-24
I've used numerous LiveCDs to access partitions on a hard drive that won't boot. 

Usually this is Windows and for a while I was limited in which distros I could use because not all of them could read NTFS out of the box.

If this is the same, only a handful of distro's being able to handle Ext4, then I'm definitely keeping my /home directory on Ext3 which is more widely accessible even from a Windows machine if push-comes-to-shove.

Until Fedora 11 comes out is there anybody other than Ubuntu which can handle Ext4?

---

### Post by calrogman on 2009-04-24
I'm using Ext4 for / and Ext3 for /home, both because I wanted to keep my personal files intact during the install (I installed using a CD, deleted all my configuration files) and also to keep my personal files safe in event of error.

---

### Post by Mehall on 2009-04-24
Arch can, IIRC. Not an easy thing to do in Arch yet, iirc though.

ubuntu is the only major release since ext4 was announced as "ready"

---

### Post by frup on 2009-04-24
Considering I have everything meticulously backed up, I see no problem in using ext4, unless it break my hard disk.

Having said that it is functioning amazingly. Boot speed for me is 15 seconds according to bootchart. I don't even have a fast laptop, it's a centrino duo 1.75ghz. I'm impressed.

9.10 is apparently going to improve more and hopefully BTRFS will get faster too, I can only be pleased. My flat mate(room mate) uses windows but will dual boot with 9.04 after using my computer on and off for 6 months and appreciating the good sides. His windows XP installation takes 3 minutes to be usable after logging in - it's pretty messed up though. Still, I'm on a functioning computer before he gets to his login screen.

---

### Post by Dragonbite on 2009-04-24
> **frup said:**
> Considering I have everything meticulously backed up, I see no problem in using ext4, unless it break my hard disk.

That's the other side of my thinking.. if I back it up consistently in a format that is more accessible then running Ext4 won't be so scarey because I will only loose the changes since the previous backup.

Obviously, though, I don't have a good backup regiment yet.

---

### Post by master5o1 on 2009-04-24
/ = Ext4
/home = Ext3 (So I didn't format my data)

---

### Post by will1911a1 on 2009-04-24
Ext3 for the moment.

---

### Post by SomeGuyDude on 2009-04-24
> **Dragonbite said:**
> Until Fedora 11 comes out is there anybody other than Ubuntu which can handle Ext4?

A whole slew of Archers have been using ext4 for a while now. I'm rearing up on a month with it and it's leaps and bounds ahead of all the others (although I admit I haven't tried Reiser yet).

---

### Post by Dragonbite on 2009-04-24
> **SomeGuyDude said:**
> A whole slew of Archers have been using ext4 for a while now. I'm rearing up on a month with it and it's leaps and bounds ahead of all the others (although I admit I haven't tried Reiser yet).

I would either try Reiser now while the corpse is still warm, or don't bother at all.  Actually it wasn't all that bad.

Maybe Oracle will release ZFS when the acquisition of Sun is complete?!

---

### Post by cellerit on 2009-04-24
I put my / on ext4 and kept my /home on reiserfs. Maybe it's just an impression but it seems to boot a lot faster!

---

### Post by khelben1979 on 2009-04-24
> **lukjad007 said:**
> I've heard horror stories. I'm letting other brave souls to test it out for me. ;)

Same here.

---

### Post by insane_alien on 2009-04-24
i've heard the horror stories too but haven't for the life of me been able to recreate them.

ext4 is stable and i use it.

---

### Post by Skripka on 2009-04-24
> **Mehall said:**
> Arch can, IIRC. Not an easy thing to do in Arch yet, iirc though.

ubuntu is the only major release since ext4 was announced as "ready"

Um...yea.

Ext4 is as hard in Arch, as telling the installer to partition your drive Ext4...it was that hard 2 months ago too.

---

### Post by LightB on 2009-04-24
I won't use it until grub supports it.

---

### Post by NightwishFan on 2009-04-24
I used to use XFS, and ext3 for my data partition.

My hardrive set up is like this:

P1: 100gb ext3 /mnt/backup
P2: Extended
P5: 200mb ext3 /boot
P6: 1.3gb SWAP
P7: 60gb ext4 /

I figure ext4 will be a slight improvement on XFS, so I use that for my root partition.

---

### Post by JohnFH on 2009-04-24
> **LightB said:**
> I won't use it until grub supports it.

I don't understand this.  I have / and /home as ext4 partitions, and I just needed to update the grub in my bootloader.

This is taken directly from the Jaunty release notes:
> 
If you choose to upgrade your / or /boot filesystem in place from ext2 or ext3 to ext4 (as documented on the ext4 wiki), then you must also use the grub-install command after upgrading to Ubuntu 9.04 RC to reinstall your boot loader. If you do not do this, then the version of GRUB installed in your boot sector will not be able to read the kernel from the ext4 filesystem and your system will fail to boot. 


Links:
[Jaunty Release Notes - Feature List]("http://www.ubuntu.com/getubuntu/releasenotes/904overview")

[Ext4 HowTo]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto")

---

### Post by Stan_1936 on 2009-04-24
> **khelben1979 said:**
> I only use the Extended 3 filesystem and don't care about version 4 until it has been accepted as stable of those who use it.

I don't want to experience data losses with the things that I have.

If you put /home on ext3 aren't your important files safe?  Who cares what happens to the rest.....your data,pics, etc. will be safe!!!  Won't they?

---

### Post by Stan_1936 on 2009-04-24
> **JohnFH said:**
> I don't understand this.  I have / and /home as ext4 partitions, and **I just needed to update the grub in my bootloader**....

**How did you do that?**

---

### Post by JohnFH on 2009-04-24
> **Stan_1936 said:**
> **How did you do that?**

Use the grub-install command.  If you choose not to install grub as part of the Jaunty installation, or if you are upgrading, then you must run grub-install.  If you do a clean install of Jaunty and allow the installer to install grub during installation (this is the default), then you don't need to call grub-install.

---

### Post by Stan_1936 on 2009-04-24
> **JohnFH said:**
> ...If you do a clean install of Jaunty and allow the installer to install grub during installation (this is the default), then you don't need to call grub-install.

When does it ask you to "Install Grub"????  I've never seen it...even on Manual Installation?:confused::(:confused::(

---

### Post by icp on 2009-04-24
No i still use ext3

---

### Post by JohnFH on 2009-04-24
> **Stan_1936 said:**
> When does it ask you to "Install Grub"????  I've never seen it...even on Manual Installation?:confused::(:confused::(

Can't remember exactly, but it probably doesn't mention grub explicitly.  It just mention installing the MBR.  I think I also used the alternate CD image which might have different options.

---

### Post by Spiritous on 2009-04-24
I'm new to Ubuntu so I'm keeping all the Default critical settings 'till I'm more confident ;)

---

### Post by khelben1979 on 2009-04-24
> **Stan_1936 said:**
> If you put /home on ext3 aren't your important files safe?  Who cares what happens to the rest.....your data,pics, etc. will be safe!!!  Won't they?

Maybe, but I do have patience to wait until it get's better.

---

### Post by jowilkin on 2009-04-24
Been using ext4 on my laptop which is running Arch for quite a while now with no problems.

Just did a fresh install of jaunty on my HTPC over an old install of intrepid and used ext4 for everything except data which is on an external drive using NTFS.  No problems yet with this setup.

---

### Post by FuturePilot on 2009-04-24
I was using Ext4 until I came across a nasty lockup bug triggered by deleting a lot of files at once. I'm back on Ext3 for now. I think I'll wait at least another release cycle before going back to Ext4. Also if you have an Ext4 partition don't try to resize it, it will get corrupted.

---

### Post by Polygon on 2009-04-24
> **FuturePilot said:**
> I was using Ext4 until I came across a nasty lockup bug triggered by deleting a lot of files at once. I'm back on Ext3 for now. I think I'll wait at least another release cycle before going back to Ext4. Also if you have an Ext4 partition don't try to resize it, it will get corrupted.

is this a gparted bug or a ext4 bug? either way, ubuntu should patch gparted so it doesn't allow you to do that until it gets fixed...

---

### Post by FuturePilot on 2009-04-24
> **Polygon said:**
> is this a gparted bug or a ext4 bug? either way, ubuntu should patch gparted so it doesn't allow you to do that until it gets fixed...

It's a bug in resize2fs which I'm pretty sure is what Gparted calls when resizing. [http://www.ubuntu.com/getubuntu/releasenotes/904#Possible%20data-loss%20problems%20resizing%20ext4]("http://www.ubuntu.com/getubuntu/releasenotes/904#Possible%20data-loss%20problems%20resizing%20ext4")

---

### Post by Dragonbite on 2009-04-24
So, does Gparted handle Ext4 if I install and then install Gparted from the repos (I don't think Ubuntu includes it by default, they just have it for installation purposes).

What about fdisk?

---

### Post by FuturePilot on 2009-04-24
> **Dragonbite said:**
> So, does Gparted handle Ext4 if I install and then install Gparted from the repos (I don't think Ubuntu includes it by default, they just have it for installation purposes).

What about fdisk?

Gparted supports Ext4. I'm pretty sure all of the necessary file system tools were updated to support Ext4

---

### Post by TDK800 on 2009-04-24
what about full disk encryption on Ext4 - possible? good idea?

---

### Post by divague on 2009-04-24
My / partition is ext4 and my /home partiton is using ext3

---

### Post by unclebeer on 2009-04-24
I just installed Xubuntu Jaunty on 2 machines at home today using ext4 on both, and now every time I go to delete more than a couple of files at a time, the computer locks up.  Back to reiser for me.

---

### Post by oomingmak on 2009-04-25
> **Stan_1936 said:**
> When does it ask you to "Install Grub"????  I've never seen it...even on Manual Installation?
It's under the stupidly named "advanced" button on the last page of the partitioning sequence (where you review your choices before committing them). This option used to just have a text box with (HD0,0) in it, but now there is a more sensible device list to choose from (if needed).


> **Dragonbite said:**
> So, does Gparted handle Ext4 if I install and then install Gparted from the repos
Yes.

> **Dragonbite said:**
> I don't think Ubuntu includes it by default, they just have it for installation purposes
Correct.

---

### Post by bobbocanfly on 2009-04-25
I'm using ext4 for all partitions (/ and /home) on my desktop, my Eee 701 and my sister's HP MiniNote 2133. Each of them boots in about 20 seconds and I haven't had any problems with it at all.

---

### Post by Euphorion on 2009-04-25
No, I will stick with EXT3 for a while longer. EXT4 is very new and is coming into mass use. This will reveal problems which no one has thought about.

For example I have a dual boot system with Vista and Ubuntu. I backup the whole system using Acronis under Vista. Presently my Acronis Version can read Ext3, I don't know if it can read Ext4, will have to ask Acronis.

Further I use a utility in Vista to read the Linux Ext3 partition (read only), will also have to check if the utility can read Ext4. And so it goes on. Until I have resolved all these issues in my small world, I will remain with Ext3. When I have answers to everything I will migrate to Ext4.

---

### Post by NightwishFan on 2009-04-25
> **Euphorion said:**
> No, I will stick with EXT3 for a while longer. EXT4 is very new and is coming into mass use. This will reveal problems which no one has thought about.

For example I have a dual boot system with Vista and Ubuntu. I backup the whole system using Acronis under Vista. Presently my Acronis Version can read Ext3, I don't know if it can read Ext4, will have to ask Acronis.

Further I use a utility in Vista to read the Linux Ext3 partition (read only), will also have to check if the utility can read Ext4. And so it goes on. Until I have resolved all these issues in my small world, I will remain with Ext3. When I have answers to everything I will migrate to Ext4.

Try XFS if you want to have some advanced features until a more stable ext4.

---

### Post by roachk71 on 2009-04-25
From what I've read about Ext4 so far, It's much better than most of the alternatives. However, I usually wait until at least a few months after a new Ubuntu release goes public, so that the developers have a real chance to whack most of the bugs out of the packages.

That said, I'm still hanging on to 8.10, using Ext3 for my boot partition, and XFS for root.

Another problem some of us have to deal with is the reinstallation of packages from source that can't be found in the repositories. This also makes us reluctant to upgrade just yet.
:p

---

### Post by pw_f100_220 on 2009-04-25
ext3...i probably would've gone with ext4 if i saw the option...but i kind of flew through installation...i was excited.  but it sounds like a better idea to wait for other people to find the kinks.

works great...but my ext3 external hard drive unmounts randomly...
it was fat32 but had more problems in hardy. ext3 worked great in hardy.

---

### Post by markp1989 on 2009-04-25
currently i have 

/ ext4
/home ext4
/media/data ext2

---

### Post by itreius on 2009-04-25
Yes, but only for my / partition, and I haven't encountered any issues so far. My documents, video, music, etc. are all on a HFS+ partition.

---

### Post by Yathi on 2009-04-26
All of u who have installed Grub on ext4, are u having any problems?? Coz i read grub is not supported.

And what about the partition getting corrupted if there is a crash or if u try to resize it. Anyone experienced this???

---

### Post by Lupi on 2009-04-26
Heck yes. It's as fast as Flash Gordon and I have nothing important to lose.

---

### Post by cdwillis on 2009-04-26
I've been using Jaunty since the 6th alpha release. I'm using ext4 for /, /boot, and /home. No problems so far, but I haven't tried to delete a large mass of files, resize my partitions, or had sudden power loss.

---

### Post by cariboo on 2009-04-26
@Yathi

Grub has been patched by the Ubuntu devs to work with ext4.

---

### Post by Phreaker on 2009-04-26
I'm brave enough to use ext4 on jaunty as my primary os :)

---

### Post by toupeiro on 2009-04-26
Using EXT4 for / on an OCZ MLC SSD.  Works well, but I'm not /quite/ getting my full write speed out of it.  Drive is rated at 230MB Read, 110MB write.  Using noop scheduler.  No problems with EXT4 as a filesystem, that I can prove, at this time. :)

---

### Post by jespdj on 2009-04-26
ext4 on my netbook (Dell Mini 9, with 32 GB SSD)
ext3 on my laptop (Dell XPS M1530)

I am still using ext3 on my laptop because I use it for the administration of my business, and so stability is more important than the small performance gain. I don't want to risk losing data or having lockups or other problems because of ext4 on my laptop.

---

### Post by wiebeest on 2009-04-26
> **jelle_ said:**
> root partition is ext4. /home is ext3 to keep my data on the partition

Same here. My theory when installing was: I want the speedy experience of EXT4 for my new Jaunty install on my root partition, but don't want to risk losing data on my seperate /home partition which is "old" EXT3. 

Seems to work out really fine so far...

---

### Post by NotTheMessiah on 2009-04-26
ext4 on my netbook(wind U100) and ext3 on my laptop.

---

### Post by Yathi on 2009-04-26
Ok then.. I think i'll also make the leap..:)

---

### Post by rudihawk on 2009-04-26
I am using it everywhere :) Its awesome!

---

### Post by kenweill on 2009-04-26
i'll stick with ext3 for now. i dont have a reason to switch to ext4.
unless ubuntu will use it as the default file system in future releases, then that's the time to switch to ext4.

Just want to stick with my signature's message.

---

### Post by blastus on 2009-04-26
I'm using ext4 for root and boot. But I don't use ext4 for data that I would like to keep; I still use ext3 for everything else.

---

### Post by Dragonbite on 2009-04-27
Ok, took the plunge. When I installed Jaunty I've doen
[INDENT]/boot = ext2
/ = ext4
/home = ext3[/INDENT]

Chances are Koala+ will have Ext4 the default.

---

### Post by The Keeper on 2009-04-27
Why a separate boot partition? Jaunty's GRUB supports booting from ext4.

---

### Post by skymera on 2009-04-27
> **toupeiro said:**
> Using EXT4 for / on an OCZ MLC SSD.  Works well, but I'm not /quite/ getting my full write speed out of it.  Drive is rated at 230MB Read, 110MB write.  Using noop scheduler.  No problems with EXT4 as a filesystem, that I can prove, at this time. :)

Check out sreadahead, it's suppose to be better for SSDs since seek time is not an issue.

---

### Post by itsStephen on 2009-04-27
I've been using ext4 for a few hours with no problems. It's so much faster too!

---

### Post by kirsis on 2009-04-27
100% ext4. No probs so far.

Converted 3 days ago.

---

### Post by dark_phantom on 2009-04-27
Been using ext4 on my laptop since beta.

---

