---
title: "I'm Destroyed, totally, totally disappointed in this ver."
date: 2013-05-10
forum: Ubuntu, Linux and OS Chat
---

### Post by Agencyman on 2013-05-10
Just installed 13.04 on my laptop, had about 2/3 of the 500Gb HDD unused.

When the menu came up for the type of install, I unchecked the top one, BECAUSE it said it would overwrite the whole drive, and I still wanted my Windows operational in a dual boot.

Looked briefly at "Something Else", decided to not bother this time, I usually go that route, and do the partitioning my way with a shared part.

Went "Back" from this choice, and checked the middle two for encrypted, which assured me it would not encrypt existing files.

Huge surprise!  Never had this happen before, and I'm furious.  I have all the Windows user files externally backed up from a couple of weeks back, but the rather "loaded out to the max" install is gone, EVERYTHING is gone just as if I had specified the "Erase Disk" install option that I so scrupulously avoided!!!

From now on, I must consider even Ubuntu as potentially hostile.  I sincerely regret letting that .iso have a shot at my computer; the shot is quite fatal.  Nothing in Gparted or file management, or even anything on Hiren's BCD has anything to offer, except to tell me how new the drive now is.  :(  :(

Bruce

Oh, yeah, don't pop the CD out when it says it has "completed" the install, and wants to re-boot...  Kernal panic set in, it won't shut down by itself and leaves a lot of text on the screen instead of shutting down.

---

### Post by oldos2er on 2013-05-10
Doesn't appear to be a support request, moved to Ubuntu, Linux & OS chat.

---

### Post by TheFu on 2013-05-10
From your comments, you seem to be an end-user better served by using only LTS releases.  I'm that way too.  I don't want to risk my data.  12.04 is the last LTS release, FYI.  The next one should be 14.04 in about a year.

Clearly, it is time to restore the HDD from one of your backups.

---

### Post by CharlesA on 2013-05-10
Backup, backup, backup. This is even more important when you are going to be messing with a dual boot.

If I am going to be messing with partitions, I clone the OS drive so I can restore it if anything goes wrong.

---

### Post by Agencyman on 2013-05-10
Yes, sorry, not a plea for tech assistance, better here.

I can salvage the data, I back up constantly, like I tell my clients to do, on several local HDDs plus cloud, but it takes a long time to build the other machine back.

I just hope I have a reasonably current image somewhere, but I let my guard down on that count...

I had just gotten **over-confident**, because all of my previous Ubu builds had been on balance, gold plated, though not through any programming achievements of my own.

Bruce

---

### Post by TheFu on 2013-05-10
> **Agencyman said:**
> Yes, sorry, not a plea for tech assistance, better here.

I can salvage the data, I back up constantly, like I tell my clients to do, on several local HDDs plus cloud, but it takes a long time to build the other machine back.

I just hope I have a reasonably current image somewhere, but I let my guard down on that count...

I had just gotten **over-confident**, because all of my previous Ubu builds had been on balance, gold plated, though not through any programming achievements of my own.

Bruce
Glad to hear this.  Backups are great, but that really isn't the point. It is all about the recovery.

Rebuilding a Linux machine with less than 20G of OS/Apps and data should be possible in 20-30 minutes.  On Linux, I don't use image-based backups.  Too inefficient. I do not think that is necessary and it definitely is not as efficient as other methods. Alas, that is a different topic that this thread.

---

### Post by tgalati4 on 2013-05-10
Unfortunately, there are several ways to mess up a dual-boot system.  You have found yet another.  This forum is littered with posts about dual-boot install disasters--many of them completely wiping the Windows partition and all of its data--and many without a backup.

It would be helpful to isolate user-error from installer error to see if there is something harmful in the 13.04 installer.

---

### Post by Agencyman on 2013-05-10
> **tgalati4 said:**
> Unfortunately, there are several ways to mess up a dual-boot system.  You have found yet another.  This forum is littered with posts about dual-boot install disasters--many of them completely wiping the Windows partitionI need to spend more time here!>  and all of its data--and many without a backup.  It would be helpful to isolate user-error from installer error to see if there is something harmful in the 13.04 installer.  It was that very busy Windows re-install that was going to take so long, but I just don't think I'll put it back.  Ubuntu only, for now, and BTW this is the 32 bit version, first one in years.  For folding proteins, Pande Group's Stanford distributed computing project, F@H, all of the recent ones have been 64 bit by necessity.   

 Now for the really vague part.  I had some unusual results a couple of years back, in the mists of memory where the details are obscured, but I came away believing that it was the going back a step, after starting to do manual file type settings for folding proteins, in the partitioning, that I had my problems.  On a new build, as you say no problem, just format it and re-do, relatively quick and easy.   

 Back then I decided, for roomy desktops, (and haven't looked back), that I would install each OS on its own HDD or SSD, with the others disconnected and unseen by the installer.  Then use the boot selection to choose the OS to launch.  

But with this old lappy, I wrongly figured it was a familiar piece of cake to go dual.  

 I was still in the shock and denial stage when I posted that, and simply wanted to put the red flag out there because backup data is not enough.  If you put another OS at risk, make sure you have today's clone/image at the ready.   Bruce

---

### Post by tgalati4 on 2013-05-10
I'm not familiar with the Ubiquity installer, but hitting the "back" button takes you to the previous dialog box, but I'm not sure if the state of the system is preserved.  So your initial instinct was "Something Else"--meaning manual partitioning, but instead you chose "I Feel Lucky" instead.  That works for Google searches, but unfortunately the installer has no way of knowing what your intentions are.  You have to admit, the ubiquity installer is quite efficient at wiping the old operating system.

---

### Post by Agencyman on 2013-05-10
For me, for the forseeable; no more "Back" button!  > **tgalati4 said:**
> You have to admit, the ubiquity installer is quite efficient at wiping the old operating system.  Top drawer! First rate! Absolutely steamrollered the competition!!!    :D :D Bruce

---

### Post by iamkuriouspurpleoranj on 2013-05-11
That's really annoying. It really does make sense to use "something else", even if it takes a little bit more effort.

Moral of the story: Never send ubiquity to do a man's job.

---

### Post by Tamlynmac on 2013-05-11
> tgalati4
I'm not familiar with the Ubiquity installer, but hitting the "back"  button takes you to the previous dialog box, but I'm not sure if the  state of the system is preserved.  So your initial instinct was  "Something Else"--meaning manual partitioning, but instead you chose "I  Feel Lucky" instead.  That works for Google searches, but unfortunately  the installer has no way of knowing what your intentions are.  You have  to admit, the ubiquity installer is quite efficient at wiping the old  operating system.


Logic might suggest that when one  uses the back button and doesn't advance - the system shouldn't retain  the state. In my mind, by retaining the state, it negates the whole  concept of the "Back Button".  #-o

IMHO when  one of the options implies "I feel lucky", that alone questions the quality  of the installer. No OS installer should include such an option.  Especially, when considering new users who may not understand/realize the associated  risks (not saying the OP is a new user). Obviously, there's no  associated risk with a Google search other than a bad search result. But  for an OS install? Seriously.

 If the installer isn't capable of  "knowing" the intentions, it shouldn't continue the process - it should  request additional input. Or at the least, halt the process and provide feedback as to why it halted.

Just my $0.02

---

### Post by kevdog on 2013-05-12
Just curious -- what are you guys using for disk cloning?? I'm not talking about rsync or similar such programs that I use for backup -- I'm talking partition cloning!

---

### Post by CharlesA on 2013-05-12
Clonezilla or Ghost for me.

---

### Post by drawkcab on 2013-05-12
My advice is to manually partition your drives during installation rather that trust things to ubiquity.  I've dual-booted off and on for about 10 years and never had a problem.

---

### Post by VinDSL on 2013-05-12
> **drawkcab said:**
> My advice is to manually partition your drives during installation rather that trust things to ubiquity. [...]
Same here...

If the dual-boot machine is going to be infected with winders:

[LIST]
[*]Manually partition using GParted
[*]Install winders
[*]Hide the winders partition(s) using GParted
[*]Install Linux
[*]Unhide the winders partition(s)
[/LIST]

Works every time!

---

### Post by mastablasta on 2013-05-13
it could be though that the whole thing got messed up becuase of enabled encryption. so it might be worth posting this in detail on launchpad or something or perhaps in forums first. perhaps it is somethign wrong in installer.

or perhaps if one encrypts the main root of disk get's modified or something. i am not exactly sure how these encryption work. but you have to admit that this info should be written somewhere on local disk (i.e. that there are multiple partition and that some are encrypted and usign such and such key).

---

### Post by TheFu on 2013-05-13
> **kevdog said:**
> Just curious -- what are you guys using for disk cloning?? I'm not talking about rsync or similar such programs that I use for backup -- I'm talking partition cloning!

I only use cloning for non-Linux systems.  Then I use **PartImage**.

I find it quicker to restore from backups, run a few grub commands from a liveCD and be done than to spend all the storage and extra time cloning entire partitions.  Since PartImage doesn't understand EXT4, this has become more the case. If you stay with EXT2 of EXT3, it does understand the format and will be much more efficient.  **Boot Repair** has made this step trivial.

I can't speak for recent versions of other disk cloning tools.  I tried Ghost and Clonezilla yrs ago, but found both of those to be less than intuitive.

---

### Post by orb9220 on 2013-05-14
I use an easier version of Clonezilla called [Redo Backup]("http://redobackup.org/") with same engine under the hood.
Much easier and less confusing for simple partition backup.

My setup is triple boot Win7,Winxp & Linux. Linux has / and separate /home & Swap and grub loaded at / root as don't want to mess up win7 loader. And use EasyBCD to add the linux grub to the Win7 loader. Otherwise I would have to always backup the Win7 partition to save the bootloader for restoring. My way is end up with 2 boot menu's but simplifies backing up one less 35 gb partition. As bootloader is backed up when / root is backed up. Also changing distro's I don't have to touch win7 loader as just points to whatever grub is there on root.

Using it I do a complete all 3 OS's 5 partitions backup to external usb drive. Then individual backup Win7 partition and Individual Linux partitions of / and /home partitions backups. Makes it easy to try out new distro's as can clean install to my Linux partitions with the backup ready to restore if something goes wrong. Once I install a new distro and install and setup my desktop to working for me with apps and tweaks. Then will back that up also. As a results have many distro's to working desktop in about 15 mins can switch to Ubuntu,Linux Mint Cinnamon or KDE,Voyager12.10 xfce,Bodhi,Funduntu,etc...

---

