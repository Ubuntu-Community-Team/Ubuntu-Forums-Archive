---
title: "Let Me Assure You, Ubuntu Is Really Great, But..."
date: 2010-06-16
forum: Testimonials &amp; Experiences
---

### Post by oldefoxx on 2010-06-16
I'm not kidding.  Ubuntu is terific, and probably best suited for anyone ready to move beyond Windows.  That is what I thought when I first started with it, and is what I firmly believe many versions later.

For those that feel they cannot leave Windows behind, you can include a few packages that let you bring Windows or just some Windows applications along as well.  The two I will mention at this point is Wine nd VirtualBox.  You can read about both elsewhere.

So what is the Big "But" in the title in reference to?  A number of things, mostly minor.  You will likely be visiting the forums fairly often with a question or two, to which you will find interest in helping you or just someone else wanting to learn what you learn.  And actually, since Ubuntu is organized by category and names, with some brief descriptions included where most helpful, almost anyone can learn how to get around and do things pretty much on their own.

Going further, Ubuntu and Windows are not totally dissemular in look and feel, so getting comfortable with Ubuntu should not take that long.

One of the first places that the Big But kicks in is that in the matter of command line operations, where you type in the command yourself, Ubuntu is much more involved, particularly when it comes to spelling out the needed path and filenames.  Now on the good side, many of the instructions and operatons that might involve the Command Line are detailed out in articles and posts on the internet, and with copy-and-paste, you can save a lot of typing.  So that is really to the good in many cases.

But there are two Buts that might come forth and bother you at some point.
One is how to backup your programs and data easily.  There are a number of approaches to doing this, but it is not as simple as copy and paste.

But the final Big But is the one that I am fighting right now.  The boot process is called Grub, and comes in several versions.  Ubuntu is moving from Grub 1 to Grub 2, and that can produce some real problems, espcially if you have another version of Ubuntu or Linux on the same PC that this verson has to live along side of.  Grub 1 and Grub 2 are not compatible with each other to begin with.  But while I do not have any real knowledge o Grub 2, I have been painfully gaining some insights into Grub 1.  The boot process involves a text file /boot/grub/menu.lst.  Near the the end of the file, you will find a collection of boot choices, each starting with a Title.  The title is what you see on the screen during the boot effort.

Now there are two ways to refer to the boot partition here.  One is by assigning a locaton for root, which might appear as (hd0,0).   The other is to set a UUID equal to the one assigned to that partition.  If these two do not agree as to the partition being pointed to, or if the partition being pointed to is not a boot partition with the needed file on it, the boot process will fail.  Makes sense, right?

The problem could be that working with multiple installs, something goes wrong with a specific boot choice.  For one thing, Grug has it own way of recognizing the order of partitions, and this information is stored in a text file called device.map.  The order may mean that instead of using (hd0,0) you really needed to use (hd1,0), because the drive order is reversed.  You can of coure change that.

The other problem is the UUID used with that entry.  If it does not match the one assigned to that partition, the one first identified by setting root, then again it will fail to boot.  To fix tis, you need to find out what the assigned UUID is for that partition, possibly after booting from the LiveCD, and then correct it.  The third possible problem might be if the boot file cannot be found or is corrupt.  That has not been a real problem for me yet.

In other words, if you find you cannot boot after an install, the problem may be traceable and fixable on your part.

Personally, I think a grub management tool would be highly appropriate for occasions like this, one that verifies what is assigned and what it really should be for the boot to run properly.

Personally, I think Ubuntu could do more to validate and restore any defect that might occur in the boot process itself.  You have a recovery mode, but it does very litle of real value.  It it fails to work, where do you go from there?  A reinstall?  How typical of Windows, so nothing to brag about with Ubuntu.  Ubuntu also insists on clean file system sweeps of all partitions, and fails if any partition fails, regardless of whether it is to be used, or even if it has no bearing on the boot process itself.

I'm no expert in this area, but the lack of adequate restore or repair capabilities applies to more than just Ubuntu, so its lack here is more in the nature of something that should be but isn't.

---

### Post by marshmallow1304 on 2010-06-17
Grub2 tends to be much more automagic in this area.  It might require a little more know-how for some situations (menu.lst is gone, replaced with boot scripts), but in most cases, you can run one simple command (grub-update) and grub will do the rest.

---

### Post by ukripper on 2010-06-17
Grub 2 is just great, for more info this guide details clears basics - [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) Grub1 soon will be obsolete.

---

### Post by stalkingwolf on 2010-06-17
one problem i have encountered is that when using multiple systems the las system installed is the version of grub used.

For instance this drive has 4 OS's installed.  Win xp, super os, UE, and 8.04..  i learned that if i install 8.04 last grub doesnt recognize the other ubuntu systems.

The solution, easy. I installed 8.04 first then UE then Super.  everything works fine all 4 are in the menu and boot with no problems.

---

### Post by XanII on 2010-06-18
Got really riled up when i realized Grub 2 comes as default in was it 9.10? wrecked my current boot there. 

Now that it's Grub 2 all the way and i know for sure older computers got Grub 1 then its fine. I try to avoid configuring it as much as possible and dont fall into any traps anymore. 

Luckily it is indeed more automagic in it's actions and it works quite well. Takes a wee too long to scan the disks though.

---

### Post by oldefoxx on 2010-06-22
I more than agree with you about disk scanning.  What I have run
up against is that all disks must pass with flying colors.  If they don't the boot dies.  What this might mean is that you try a normal boot, but any disk failure stops it.  Try again with an
alternative install, and it runs into the same problem. And think of how much boot time would be saved if the initial boot effort was only against the needed, designated root drive, plus whatever additional drives/partitions were picked to be /home and such.

Another problem that seems to factor in sometimes is what you add to /etc/fstab.  The boot process does not just look to see what devices you specified in /etc/fstab, it rushes ahead to mount them.  Then it fails with error=8 because it knows it is not smart to check a mounted drive.  You can bypass the whole check by doing a Ctrl+D, but that is not so smart either.

I'm not gifted with a knowledge of things like Ubuntu, but I can generally work out some things by studying the details.  But how about someone who is not even to my level?  Once I see something that sort of puts a pinch on the process, which is suppose to be fully automated, I have to find the lack of an appropriate way to deal with it a flaw in and of itself.  Computers are not smarter than people, but in the hands of smart developers, they should be good enough to take care of certain matters on their own.  Developers just have to remain aware that others are not to their level, and need something extra there to move on to the next step without expecting too much from them.

---

