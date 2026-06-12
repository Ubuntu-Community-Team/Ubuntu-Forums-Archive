---
title: "Let's talk partitioning."
date: 2007-05-06
forum: The Cafe
---

### Post by picpak on 2007-05-06
^ That should say...let's watch me rant about partitioning. That being said, this is a rant.

Alright, I've been using Linux for over 2 years now. I've compiled kernels. I've been stuck in a terminal for days on end. I've destroyed my Linux installs to the point of no return and repaired them back. But, and I know some of you will disagree, I think that partitioning is the single most cryptic, single most scary, and, quite frankly, downright useless thing a Linux user ever has to face. I applaud any new user who even grasps the concept of partitioning...because I just simply can't.

Take my sister's computer, for example. She's got a dual boot, so she's figured out more than me at this point. Her Windows drive is so full of bugs and viruses it's not even funny, so what she decided to do was delete the Windows drive and give all the free space to Linux. Sounds easy, huh? If only it was.

(Now, this was all said over the phone, so sometimes she may have not explained something clearly or I may have misinterpreted it. I REALLY wish she'd wait to bring her computer home to do these things...but I digress.)

Ok, so we boot into the Ubuntu CD, and run the partition manager. She has a lot of unallocated space, but we figure we can get to that later. Obviously removing the Windows drive was easy; right-click, delete. Now we have a huge amount of unallocated space. Ok, let's resize Linux. Linux won't resize any higher. OK then, let's try deleting the extended partition, free up some space. To delete it, you also need to delete the swap. Okay, She has a new enough computer...delete the swap. Now let's resize Linux. It resizes a little bit...but still ignores the space from Windows. Okay then...let's just start over.

She's still done more with her drive than I can. Mine just shows the majority of the options grayed out. Useful. But, I do use Knoppix to repartition because my computer's too slow for the Ubuntu CD, so that could be a problem.

After many hours, and many a starting over...it works! Good then, let's reboot into Linux. So far so good...but the Linux drive thinks it's empty?!? (How it even booted into it, I don't know). It's extremely slow and freezy, and when she goes to do anything with her files, it says the drive is empty. God knows we don't wanna mess with the partitioner again...so we reinstall.

THIS? This is what it takes to REPARTITION A DRIVE? Insane.

IMO, partitioning should be a very automated process. Repartitioning should consist of checking the Windows drive, clicking delete, and Linux automatically taking up the other space. Mark this on the calendar, this is one moment where I fully respect Gnome's "less is more" approach.

Dual booting could be easier too. Heck, when I started Linux I thought it would automatically use both Linux and Windows. Nothing told me otherwise. I was crushed when I found Windows missing...the same problem exists today. I don't know about Feisty, but apparently in other releases using "automatically partition my drive" resized Windows and Linux...but is there anything telling you that? There is no visual idea that Linux will resize itself with Windows. There's nothing even telling you it KNOWS there's a Windows drive.

The dialog could be changed to: "Automatically partition to use both Windows and Linux". From thereon, you can choose the size of the Windows drive and the size of the Linux drive...y'know, something like 50/50 or 60/40.

I'm sure these ideas have been regurgitated thousands of times before, and I apologize. But what I don't understand is, after all these years, Ubuntu has done little to overcome the partitioning hurdle.

---

### Post by raja on 2007-05-06
Most of these are really your problems than problems with the partitioning scheme. I find the current approach to partitioning very satisfactory. The automatic partitioning works well for those who want to install a linux only system. If you want to do manual partitioning or dual booting, it is your responsibility to read up a bit about partitions. There are too many options to make it all automatic. 
Changing from a dual boot to a linux only pc is also not something straightforward. But my suggestion would be to reformat the windows partition and then mount it somewhere in your filesystem (like /mnt/data) rather than deleting and resizing your existing partitions.

---

### Post by H.E. Pennypacker on 2007-05-06
I am surprised you pick a fight with one of Ubuntu's most widely recognized areas.  The installation part is commonly considered a breeze, even for those who don't really have Ubuntu experience.

Let's dive into your post.

> Now we have two unallocated drives (why not just one?).

This is an issue with how partitions work to begin with, regardless of which partition manager you use.  You could use a Windows or Mac one.  It does not matter.  Unallocated spaces remain separate partitions instead of combining them into one piece.  I agree with you that this should not be the case, but this is not the only limitation of modern hard drives.

You could read more about the history of partitions and hard drives, but this has long been worked out, and apparently, this has been settled.  There is no way of going around, for example, a hard drive's four partition maximum.  We have no control over this.

> 
Okay, She has a new enough computer...delete the swap. Now let's resize Linux. It resizes a little bit...but still ignores the space from Windows. Okay then...let's just start over.

If it is a new computer, and she really does not care about what's on the hard drive, why won't she make things easier by simply wiping the entire drive?  The installer partition manager (GParted) does offer this.  If you go to the following website, you'll notice that the installer does ask if you want to use the entire drive for Ubuntu:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The newer installer, Ubuntu 7.04, is even more clear about this.

> THIS? This is what it takes to REPARTITION A DRIVE? Insane.

No, that is not what it takes.  Within a few days, I've had to install Edgy, Feisty, Mepis, and I have had to do this several times, and I never had an issue with the partitioning part, or any other installation part.  You and your sister clearly were jumping through hurdles, and doings things that were unnecessary.  It is still not clear why you guys didn't go for a standard installation.  

Check out the same website URL I posted earlier:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

It goes through the entire process.  

> 
The dialog could be changed to: "Automatically partition to use both Windows and Linux". From thereon, you can choose the size of the Windows drive and the size of the Linux drive...y'know, something like 50/50 or 60/40.

Well, you could do that too.  Select manual partitioning, and make sure you do not format the Windows partition.  If a partition is not being formatted, there is no reason why it should be lost.  In your case, you must have formatted your Windows partition.  

Manual partition still provides a GUI way of looking at your partitions.  Make note of which one is Windows, and make sure not to format that one.  

As for the installer, it really does not have much to do with dual booting.  Dual booting is taken care of by GRUB.  

I say the installer is almost perfect, and I can say that because I've been used it many times.

---

### Post by FuturePilot on 2007-05-06
Partitioning was one thing that I never ran into problems with and I've done it many many times. You do hope that nothing gets corrupted, but it's never happened to me out of all the times I've done it. I would recommend the [GParted live CD]("http://gparted.sourceforge.net/livecd.php") It's what I've always used. It's a great tool.

---

### Post by picpak on 2007-05-06
> **raja said:**
> Most of these are really your problems than problems with the partitioning scheme. I find the current approach to partitioning very satisfactory. The automatic partitioning works well for those who want to install a linux only system.

That's very nice, but there are a lot of users (re: millions) who want to boot both Linux and Windows. I'm not one of them...but my family is.

> **raja said:**
> If you want to do manual partitioning or dual booting, it is your responsibility to read up a bit about partitions. There are too many options to make it all automatic. 

Manual partitioning is one thing, but why dual booting? Ubuntu's gotten to the point where the most confusing things (enabling repos, system management, installing programs) has been reduced to just clicks. Surely the partitioner can be the same? I mean, of course there can be an "Advanced" button or something that opens up GParted, but this can just be something to get people off the ground.

> **raja said:**
> Changing from a dual boot to a linux only pc is also not something straightforward. But my suggestion would be to reformat the windows partition and then mount it somewhere in your filesystem (like /mnt/data) rather than deleting and resizing your existing partitions.

That's an interesting idea, but it's a little late now. It's too bad I haven't read that anywhere I looked.

I just finished buying an oxygen tank, first aid kit and body bag, booted into Knoppix and tried resizing my partitions. Of course, "Resize" was grayed out. I tried unmounting it even though it already was and deleted the folders in /mnt. Went I went online to check on this, the CD crashed.

I should just burn a CD with nothing but cfdisk...it's the only partitioner I've had any luck with.

---

### Post by ceelo on 2007-05-06
I agree with FuturePilot, the GParted live CD is a great tool. I've used it to partition my drive numerous times and have never had any issues. I even recommend it over commercial partitioning software such as PartitionMagic. Oh man, don't get me started on PartitionMagic. ](*,)  Used it once to resize my Windows drive and my next step was reinstalling Windows. But yeah, the GParted CD really makes partition your drive pretty simple.

---

### Post by picpak on 2007-05-06
> **H.E. Pennypacker said:**
> This is an issue with how partitions work to begin with, regardless of which partition manager you use.  You could use a Windows or Mac one.  It does not matter.  Unallocated spaces remain separate partitions instead of combining them into one piece.  I agree with you that this should not be the case, but this is not the only limitation of modern hard drives.

You could read more about the history of partitions and hard drives, but this has long been worked out, and apparently, this has been settled.  There is no way of going around, for example, a hard drive's four partition maximum.  We have no control over this.

And here's where I screwed up. After rereading it I recall it being an unallocated and an extended partition. My bad.


> **H.E. Pennypacker said:**
> If it is a new computer, and she really does not care about what's on the hard drive, why won't she make things easier by simply wiping the entire drive?  The installer partition manager (GParted) does offer this.  If you go to the following website, you'll notice that the installer does ask if you want to use the entire drive for Ubuntu:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The newer installer, Ubuntu 7.04, is even more clear about this.

My sister REALLY did not want to reinstall, and I don't blame her: she has an 80GB hard drive and I wouldn't be suprised if she had filled it all up. She must have enough music to run a radio station with 10 different genres. It's a pain to back up. It's a pain to put back on. It's a pain to configure all her programs back to her liking.

It's a pain.

> **H.E. Pennypacker said:**
> Well, you could do that too.  Select manual partitioning, and make sure you do not format the Windows partition.  If a partition is not being formatted, there is no reason why it should be lost.  In your case, you must have formatted your Windows partition.

That's great, but we didn't want to reinstall, remember? I'm at a loss as to how the computer can even boot up if it complains the disk is empty...I really wish she did this here.

---

### Post by mech7 on 2007-05-06
I think linux partitioning is not user friendly and it could be made much easier, it is very unclear on how to setup things when you install ubuntu.

---

### Post by starcraft.man on 2007-05-06
Frankly picpak while I find your case to be somewhat disheartening and I'm sorry that you had such a bad experience, its not typical. I've used the gparted cd and the alternate/live partitioners of Ubuntu and I'm happy with them both, I've also helped many people to use it in the forums and over IM (converted a few friends :)) and they have all been happy as well. In addition, a significant portion of the problems you mentioned were as a result of the very way partitions and hard drives work, and we have no input into how that functions.

You say that the partitioner in Ubuntu and in fact all of them in general should be simpler with selectable choices. I find this to be wrong, its already very simple, in fact likely as simple as it will ever be given the way partitions, HDDs and Operating systems all interact. So in reality, I would argue the opposite point, we need to make the users take more responsibility, its up to them to educate themselves by reading one of the MANY free sources of information available on any subject they need and to ensure they are completely prepared when they undertake an advanced thing as moving paritions and existing data and resizing. This atittude is of course largely to blame upon windows and how with its proliferation people have come to expect things to "just work" which is a fantasy. It takes an ungodly mess of tangled code, legacy and extra baggage to attempt to make windows work with everything and even then, it often fails.

In the end though, if you really want to implement change in how the paritioner works... go to the forum/site of the developpers of the gparted tool and make a suggestion, or take up coding yourself and write your own program to do it, or join their dev team... but DON'T post an inflammatory topic in the cafe which outlines your anomalous (if sad) experience with a program and expect a magic fairy to make it all better.

I do however wish you better luck with Ubuntu in the future, have fun :)

---

### Post by Tomosaur on 2007-05-06
> **picpak said:**
> That's very nice, but there are a lot of users (re: millions) who want to boot both Linux and Windows. I'm not one of them...but my family is.
[QUOTE]
Well, I'm one of them, and partitioning was a piece of cake.

[QUOTE]
Manual partitioning is one thing, but why dual booting? Ubuntu's gotten to the point where the most confusing things (enabling repos, system management, installing programs) has been reduced to just clicks. Surely the partitioner can be the same? I mean, of course there can be an "Advanced" button or something that opens up GParted, but this can just be something to get people off the ground.
I don't know what you've been looking at - but the installer does ask you very clearly which method you wish to use:
1) Take over the whole drive.
2) Use the largest free space.
3) Repartition manually
What more do you want? Psychic abilities? :P

---

### Post by koenn on 2007-05-06
> **picpak said:**
>  I think that partitioning is the single most cryptic, single most scary, and, quite frankly, downright useless thing a Linux user ever has to face.

I partially agree. 
cryptic ? yes and no. since your working on the disks themselves, and not in some file system hierarchy, you need to keep your head with it - even more so on a system with multiple disks. On the other hand, GUI tools such as GPartEd make it almost as easy as cutting a cake.

Useless ? No. How else are you going to set up dual boot or a seperate partition for /home. You need partitions for that, That's just the way it is. 

most scary ? Defenitely. On an empty disk, it's fun, but on a disk with data that you don't want to lose, it's scary. I actually consider it a small miracle that you can actually modify partitions without loosing the data , and boot an operating system of a storage subsystem that's been rearranged completely. 

I'd say that repartitioning over the phone is insane.

---

### Post by picpak on 2007-05-26
Alright....you people seemed compelling enough. I decided to take the plunge, and try partitioning again. It should be noted that I didn't have any Xubuntu desktop CDs with me and this was done with a 3-year old Knoppix CD. I would've burned a new one, but I'm out of CDs.

Ok, so this was the plan: shrink the root partition, and give the remaining space to my /home partition. So I start up QtParted and, just like last time, my resize button was grayed out. After enough searching I found out that QtParted doesn't actually resize the ext3 file system (This is a partitioner Knoppix finds good enough to include on their CD that can't resize its own file system? Anyway...). So I converted it to ext2 which, thankfully, worked. I resized the root partition down to what I wanted it.  So far so good, but...

My /home partition starts at 5.74GB. It won't see anything before those 5.74GBs...including the free space.

Eventually, it finally hit me that I should create a new partition using the free space, and move my files into that partition. The new partition skipped over hda3 and created itself as /dev/hda4. A little weird, I thought, but nothing serious. I copied my files onto the new partition, double-checked, crossed my fingers, and deleted the old /home partition.

It seemed to delete safely...until I tried resizing the new partition. I got a badly translated error that said something about file_error_something_something. I don't exactly remember right now.

I figured, since I couldn't use the space, to just recreate the partition and put it back. I was expecting the recreated partition to be hda6 (hda5 is swap)...it was hda2. I didn't really care, so I copied everything back over to hda2.

Being curious, I rebooted and checked back into QtParted if I could possibly resize it again. Obviously I couldn't, because guess what? THE PARTITION STARTS AT 5.74GB.

Suffice to say, I would've much rather spent the past 2 hours stabbing my eye out with a fork, but I digress. I don't care if a third of my system is now wasted. The partitioner has, once again, defeated me.

---

### Post by smoker on 2007-05-26
the best thing to do before attempting any partition work on a drive is to back up your essential data. then if disaster strikes, it is not the end of the world.

personally, i prepare all my partitions beforehand. and i use the 'gparted live-cd' for this, and i have never had a problem. but, in any case, the fact i have my stuff backed up means there is no stress involved!

info about gparted here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

best of luck

---

### Post by FuturePilot on 2007-05-26
GParted is golden\\:D/

---

### Post by juxtaposed on 2007-05-26
>  I think that partitioning is the single most cryptic, single most scary, and, quite frankly, downright useless thing a Linux user ever has to face.

I remember partitioning being easy for me when I started ubuntu, way back at 5.04.

Resized windows, added ubuntu to take the rest but leave a bit for swap, then I was done. This was on the debian text installer.

I knew very little about linux then, having only used Slax and DSL live CDs before.

> There is no way of going around, for example, a hard drive's four partition maximum.

Wow, i've never heard of this.

That means you can't have more then three OSes? (One partition for swap).

---

### Post by jerrylamos on 2007-05-26
Hard drive has four primary partitions max.  You can do three primary and one extended partition.  The extended partition can then be set up with several partitions.  That way you can get more than 4 partitions.

This is a quad boot system, hard drive 1 has Windoze on the 1st partition (Microsoft demands to be at the head of the line) then a 512 MB swap and then a Edgy 6.10. 20 MB.

Hard drive 2 has a Gutsy 7.10 partly built as they add stuff with 19 MB (this is it I'm using, not to ship until October so of course some things are broken now) then a 512 MB swap and a Feisty 7.04. 20 MB.

Note you only need one swap; whichever Linux is booted up will use the same swap.

I always like to have at least two Linux partitions, one with an "old reliable" and one for upgrades or new installs.  Some people upgraded from Edgy to Feisty and run great.  Some people various things broke like wireless.  Some people can install Feisty from CD but the  upgrade didn't work.  You could get any combination.

The Windoze is for things I can't do in Linux like clean the heads on my Epson Stylus printer and change its cartridges.  Wine won't do it.  ReactOS won't either.  Qemu and VirtualBox are slow on this 1.2 MHZ Celeron.

Do note on a multi boot system, the boot loader Grub looks for /boot/grub/menu.lst on whichever Linux was installed last, to see what Linux's and Windows you want to boot.

Cheers, Jerry

---

### Post by mips on 2007-05-27
> **juxtaposed said:**
> 
Wow, i've never heard of this.

That means you can't have more then three OSes? (One partition for swap).

You can only have 4 Primary partitions on a HD.

Nothing however stops you from creating 3 Primaries with one extended partition into which you can put many logical partitions.

Thing is you have to be carefull as some OS' cannot install to a logical partition, BSD comes to mind.

So you can install more than 4 OS' on a drive.

The above does not apply to to non-pc(i386) hardware and OS' that are not Linux or Windows. Most bsd/unixes will provide 8-32 slices(partitions) or even more with logical volumes.

---

### Post by MrHorus on 2007-05-27
[QUOTE=picpak;2603363
I think that partitioning is the single most cryptic, single most scary, and, quite frankly, downright useless thing a Linux user ever has to face.
[/QUOTE]

Put it this way.

Place your root filesystem onto a seperate partition from /home.

The next time you screw up a system and reinstall, you will thank me that you can just mount your pre-existing partition as /home and have every single one of your files there with everything intact.

---

