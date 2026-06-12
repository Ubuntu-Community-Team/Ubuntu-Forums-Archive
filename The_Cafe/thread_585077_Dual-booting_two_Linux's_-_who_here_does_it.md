---
title: "Dual-booting two Linux's - who here does it?"
date: 2007-10-21
forum: The Cafe
---

### Post by BigSilly on 2007-10-21
...And can offer a bit of advice? I'm looking to dump my XP install tomorrow with Ubuntu replacing it, after six months of a very positive experience with Feisty. I only have a fairly small HDD, with currently 40Gb for XP, a 20Gb FAT32 partition for storing files and backing up, and another 20Gb which currently runs Ubuntu Feisty. 

Now, obviously you guys can't see into the future, but are there any potential pitfalls and perils of dual-booting two different Linux flavours? I have a disc with PCLOS, and a Mandriva 2008, one of which will replace the current Feisty install on the last partition on my drive, with as I say Ubuntu Gutsy going over my Windows install. Is there anything I need to be aware of before I attempt this? I'm completely happy to be removing Windows, that's not an issue, but I was just a bit concerned about GRUB recognizing both installs. I intend putting Ubuntu on my PC last, after either Mandriva or PCLOS is installed, so the Ubuntu GRUB is the default.

Any advice or warnings you can offer will be greatly appreciated. I'm not a noob, and I'm no expert either but I know when I like an OS and I like Ubuntu! Oooh, also which Linux would you dual boot with out of PCLOS and Mandriva? Let me know.

Many thanks. Sorry for the long post. :)

---

### Post by multifaceted on 2007-10-21
When I installed Mint Xfce, it went pretty well.  Mint now owns GRUB and will load it by default after the timers finishes. I can still choose to boot into Ubuntu or WinXp from the boot loader screen.

Before you do it, ask yourself if it's really something you will use. I do but, not as much as I thought. Now I am thinking about removing it and growing my Ubuntu partition.

I would still do a* little* more research before you go and actually do it. Every computer and it's hardware is different, and could create unique problems.

---

### Post by rsambuca on 2007-10-21
You shouldn't have any problems.  Grub is highly adaptable, configurable, and easy to use.  My only advice would be to try and decide beforehand how you want your drives set up, and partition prior to installing anything.  Then install your OS's into the existing partitions.  I currently have XP, Vista, and 5 different distros running with no problems.  There are many in these forums who have a lot more distros than this, as well.

---

### Post by original_jamingrit on 2007-10-21
multi-booting is fun!  I've had 3 different OSes (XP, Feisty, and Vector Linux) on a 55 GiB drive at one time.  Multibooting linux distros is really cool though, because playing with partitions can give you interesting configurations.  Here's one that I like:

[linux1] [linux2] [extended[store] [swap]]

where linux1 and linux2 are both small (5 - 10 GiB) partitions, the "store" is a ext3 partition where I store extra stuff, and swap is the swap.  Here's the trick I used; I used the store partition just to dump shared files, but in it I also created two protected directories, we can call them "linux1-home" and "linux2-home", and mapped each OS's home directory to those, respectively.

Also, if you use your /usr/local directory for installing stuff, you could map that to an extra storage partition as well.  Thus minimizing the partition size you need for the OSes themselves.  Which is important for people with small hard drives, it can really make things lighter.

As long as you watch your permissions, symbolic links are great for mapping directories across partitions.  Although this may be needlessly complicated for most people, but hey, it's there if you want it!


But like said above, make sure only one of those OSes is in charge of booting, having different bootloaders, even if they're all GRUB, can mess things up.  Also, get the Linux System Rescue CD to help with booting/configuring GRUB in case your bootloader does get messed up.

---

### Post by BigSilly on 2007-10-21
Thanks for your replies people. :)

@original_jamingrit - Thanks for your advice! How do I ensure that only one OS is in control of GRUB? I'd presumed (and hoped!) that the last OS I install would take care of the bootloader and that would be fine. If I install say, Mandriva first and then Ubuntu second at the beginning of my HDD, shouldn't Ubuntu's GRUB just take care of things, or will Mandriva cause problems in this regard? Also, I already have one Linux swap partition at the end of my drive, will I need to make another at the end of my first partition for my fresh install of Ubuntu, or will Ubuntu just use the one I already have at the end of my HDD? 

Sorry for the crazy questions. I'm really looking forward to doing this, but I'm a bit nervous and I want to cover all bases. Cheers again.

---

### Post by rsambuca on 2007-10-21
There are a couple of ways you can go about installing them.  

1.  Just install the distros as usual and let the last distro's grub handle everything.  Less configuring initially, but you have to manually update grub with the kernel changes from the other distros later on.

2.  Use the grub from your 'main' distro as the controlling grub, and chainload to the other distro's grub loaders from there.  More configuring initially to input the chainloaders, but less maintenance going forward.

I personally prefer method 2 - chainloading grub menus.  Basically, I use Ubuntu as my main distro.  I then added chainloading entries to point to my other distros' grub menus.  You only do this once, and when each distro updates their kernel, you don't have to worry about it, since everything is automatically updated.

Also, you can share one swap amongst all of your linux distros.  I have attached a screenshot from gParted of my partition scheme for your reference.  As you will see, I have the five linux distros as logical partitions within one extended partition.  The swap is shared.  The large media partition is at the end.

---

### Post by happysmileman on 2007-10-21
> **BigSilly said:**
> If I install say, Mandriva first and then Ubuntu second at the beginning of my HDD, shouldn't Ubuntu's GRUB just take care of things, or will Mandriva cause problems in this regard? 

Yes that should work fine, and Ubuntu generally sets up GRUB very well, though I'm not sure about Mandrive, so you probably should install Ubuntu last

> Also, I already have one Linux swap partition at the end of my drive, will I need to make another at the end of my first partition for my fresh install of Ubuntu, or will Ubuntu just use the one I already have at the end of my HDD?

No, they'll both use the same swap partition, and it should set itself up at install automagically, if not you need to edit the /etc/fstab file for one of the distros, but very unlikely you'll need to.

---

### Post by rsambuca on 2007-10-21
> **happysmileman said:**
> Yes that should work fine, and Ubuntu generally sets up GRUB very well, though I'm not sure about Mandrive, so you probably should install Ubuntu last



No, they'll both use the same swap partition, and it should set itself up at install automagically, if not you need to edit the /etc/fstab file for one of the distros, but very unlikely you'll need to.
It is actually quite likely you will have to edit your fstab afterwords since the UUID of the swap will change each time you install a distro.

---

### Post by jersoncito on 2007-10-21
> **BigSilly said:**
> 

I intend putting Ubuntu on my PC last, after either Mandriva or PCLOS is installed, so the Ubuntu GRUB is the default.



That is the right way to do it. 
Mandriva 2008 then Ubuntu
or
PClinux then Ubuntu

Mandriva 2008 (one) is great, but for some reason Mandriva never lists others linux distro on its grub/lilo. No problem with Windows. its a shame. you have to do it manually after. But Ubuntu is really friendly with the rest of distros. When the installation is done, you will see Mandriva and Ubuntu.
Mandriva One 2008 and Ubuntu Gutsy, the best!!!

---

### Post by happysmileman on 2007-10-21
> **rsambuca said:**
> It is actually quite likely you will have to edit your fstab afterwords since the UUID of the swap will change each time you install a distro.

Well in my fstab file it's listed as /dev/hda6 instead of it's UUID so i thought maybe that'd be the same, though I think I made my fstab file myself anyway

---

### Post by rsambuca on 2007-10-21
> **happysmileman said:**
> Well in my fstab file it's listed as /dev/hda6 instead of it's UUID so i thought maybe that'd be the same, though I think I made my fstab file myself anyway

You must have manually changed it at one point (I did as well), since Ubuntu uses UUID's by default.

---

### Post by malspa on 2007-10-21
I have Mepis 6.5, Mepis 6.0, PCLinux2007, and Dapper.  Dapper takes over Grub.  Some of the permissions in PCLOS were kind of funky and needed to be fixed.  I have a separate partition outside of all distros for my personal files.  Everything works out really well.  Much easier dual- or multi-booting with all Linux than if Windows is involved.

---

### Post by BigSilly on 2007-10-21
My heartfelt thanks to all who have offered advice here. It's what makes these forums (and this distro) so special. 

I'm going to do this tomorrow. Is it too cheeky to ask for further advice if I have any problems? I'll post back in this thread and let you know how I get on if that's OK. As I say, I'm no expert by any stretch, but all the family loves Ubuntu here and I want to make it our main system. If worse comes to the worst, I'm just going to tell Gutsy to wipe the entire drive!

Again, thanks to all for the help and advice. I think I'll go with Mandriva One 2008 with Gutsy.

---

### Post by Toadmund on 2007-10-21
I have 2 XP partitions (of which I no longer use :) )
I have 2 Ubuntu partitions, that way I can have a backup ubuntu and it helps when 'pulling a freshy' a fresh install, I just move my files over and delete the partition that is out of date.
(what I would like to do is have a separate home partition, just too lazy to do that right now)
Just be careful you delete the right one!

As far as choosing which OS gets the default boot, as far as I can remember you simply put it at the first of you boot grub list.

In terminal:
sudo gedit /boot/grub/menu.lst

Find where it lists the the OS, cut and paste your chosen one to the top of that list.
Then save.

---

### Post by malspa on 2007-10-21
> Again, thanks to all for the help and advice. I think I'll go with Mandriva One 2008 with Gutsy.

Good luck, BigSilly.  Multi-booting Linux has some really great plus sides.  By comparing different distros, I think I've learned a lot more about Linux than I would have otherwise.  Also, you get to see and use different applications that you might not become familiar with if you were only using one distro.

I've been marking off 7 GB for my root partitions and 5 GB for my home partitions, but you don't really need that much space.  And everybody will tell you different amounts of space to use, anyway.

Anyway, have fun with it!  I feel that it has really enhanced things for me!!

---

### Post by original_jamingrit on 2007-10-21
In my experience, the last OS you install will overwrite the MBR, but most of the OSes I've tried will ask you first.

Also, something I forgot to mention:  Your partitions should be able to share one swap space comfortably, but there is some experimental stuff some people are doing that saves your linux session onto the swap while you power down.  If you ever use that sort of suspend feature, it might cause problems when you save a session and then boot to another OS that wants to use that swap.  Just a heads up, if you think you'll ever use any new suspend features (like Suspend2).

Anyways, Good luck!

---

### Post by multifaceted on 2007-10-21
> **rsambuca said:**
> There are a couple of ways you can go about installing them.  

1.  Just install the distros as usual and let the last distro's grub handle everything.  Less configuring initially, but you have to manually update grub with the kernel changes from the other distros later on.

2.  Use the grub from your 'main' distro as the controlling grub, and chainload to the other distro's grub loaders from there.  More configuring initially to input the chainloaders, but less maintenance going forward.

I personally prefer method 2 - chainloading grub menus.  Basically, I use Ubuntu as my main distro.  I then added chainloading entries to point to my other distros' grub menus.  You only do this once, and when each distro updates their kernel, you don't have to worry about it, since everything is automatically updated.

Also, you can share one swap amongst all of your linux distros.  I have attached a screenshot from gParted of my partition scheme for your reference.  As you will see, I have the five linux distros as logical partitions within one extended partition.  The swap is shared.  The large media partition is at the end.

Dang,... pretty-slick looking! That configuration is very logical and seemingly efficient. 

Kudos to you. Mind if I model my disk after yours?

---

### Post by Vansinnesvisan on 2007-10-21
I just use virtualbox if I want to tinker with another distro. Or LiveCD if to just take a peak at it.

---

### Post by BigSilly on 2007-10-22
Just like to post up to say thanks for all your excellent advice. I successfully installed Mandriva 2008 over Feisty, and now put Ubuntu 7.10 where XP used to be. It was all so easy, and again underlined just how ahead of Windows Linux is. Ubuntu's Grub has detected both OS's just fine, and I'm going to use Grubed from these very forums to maintain it.

I am a very, very happy person right now! Thanks again, and see you around the forums. \\:D/

---

### Post by ferebee on 2007-10-22
Linux is addictive and multibooting feeds the need for more!

I started out with Mepis on a spare partition on my second hard drive with windows taking up the entire first drive, and fell in love with it immediately, to the point that Windows only gets booted up if I want to use itunes. Windows now occupies a much smaller partition, and hda has been carved up with four linux partitions and swap space plus the linux partition on hdb, and more often than not, four or five have distros occupying them.

Ubuntu gets pride of place as my main distro, and Puppy always has a partition ( It was my first experience with linux - got a soft spot for it.) The rest change fairly often, just for fun.

I've never had any problems with grub - most distros installers will ask where you want grub to install. Since I've got Ubuntu's grub installed in the mbr and configured the way I like it, I want to keep it that way.  When I install a new distro to play with, I have the new distro's installer put grub in the partition I'm installing on, boot up Ubuntu, and fix things up. (fix the new UUID in fstab, and add new distro to Ubuntu's grub menu.lst file) 

It was daunting the first few times, but the more you do it the easier it gets. Just use caution, and don't panic.

Linux is fun! Can't wait to get my hands on Gutsy!

---

### Post by Kapre on 2007-10-22
Guess I'm out of the topic...But you can actually do triple boot..I had Fedora, Ubuntu and Dreamlinux (plus Windows) before..

KK

---

