---
title: "Is Ubuntu 9.10 one big step back???"
date: 2010-01-13
forum: Testimonials &amp; Experiences
---

### Post by jl2035 on 2010-01-13
I'm a big fan of Ubuntu for two years now but i think I'm not the only one sceptic about 9.10 Karmic. It's less frendly and more complex and I think that's not what Ubuntu is about. I have this Dell Studio 505 laptop and I have great performance. With 4GB of Ram and Ubuntu 9.10 I can almost do anything(Like running MS Visual Studio 2008 on virtual machine with WinXP - this was impossible with my old laptop). I'm not complaining about the speed or anything like that, I just hate this next few issues... 

1. File/Folder Permissions
The whole FileSystem is unwritable. If you try to copy or change a file anywhere except "home folder" you will have to use console with sudo. In one month of using Ubuntu 9.10 I had multiple problems with this issue. 

2. GUI and Nautilus nonsense
If you "right click on the file or folder"->Properties->Permissions tab, you have some dropDown options here for Folder access and File access - both for owner, group and others. My problem is: when I select File access and change it to Read an Write, it changes automatically back to it's original option. I have to use the terminal(sudo chmod 777 folder). So I'm asking now why is there an option to edit permissions in GUI if it's just to make you angry and does not work?! And than the option "Open as root" is gone from Nautilus... why is that???

3. Storage devices
I have two partitions - Filesystem and Storage. Somehow(in the Storage Device Manager I think...) I enabled writing to device so than I could put some data on it. Now I'm still unable to copy or change any files on this Storage device. And I also can't change permissions from Nautilus so the only option is sudo from the Terminal. I think an average user don't want that. 

4. File sharing
I connected two machines in my home LAN network - PC(Ubuntu 9.04) and my laptop(Ubuntu 9.10). I was unable to see any shared folders from both machines. Neither the machines. Setting all permissions Read and Write didn't change anything. I asked for some help on Ubuntu irc chat channel, but we didn't solve the problem. I don't know if this is 9.10 version problem but anyway - I can't exchange files using LAN!

5. GRUB loader
I noticed that the menu.lst file is gone. The file is grub.cfg but it's a little different. I always change the boot menu(after installation of Ubuntu) into minimum items. I successfully did that, but after two weeks, when I applied the Updates the boot menu was back to default. That's a strange think... and it's new in 9.10. 

6. Sound
On my friend's HP Compaq laptop I had this stupid problem. Every time when the machine starts, the sound is checked as Mute in Volume Control. I also set up Ubuntu 9.10 on a Fujitsu Siemens laptop. There was no sound here. I set everything to full volume and all Mutes unchecked. In the Rhythmbox songs were playing but the speakers were mute.

So the older versions of OS are better than the new one. I knew this is possible in Microsoft but not you guys! OK now it's enough of me being a smart ***. I really want to hear what you have to tell the disappointed user, although I know you guys are giving your best.

---

### Post by howefield on 2010-01-13
You probably don't know this forum exists.

[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

---

### Post by muteXe on 2010-01-13
> 
Is Ubuntu 9.10 one big step back??? 


yes. imo.

1 - Are you implying that in previous versions of ubuntu you were never once prompted to type in your password in when modifying files outside of your home folder?

---

### Post by mick222 on 2010-01-13
> **jl2035 said:**
> 

1. File/Folder Permissions
The whole FileSystem is unwritable. If you try to copy or change a file anywhere except "home folder" you will have to use console with sudo. In one month of using Ubuntu 9.10 I had multiple problems with this issue. 

2. GUI and Nautilus nonsense
If you "right click on the file or folder"->Properties->Permissions tab, you have some dropDown options here for Folder access and File access - both for owner, group and others. My problem is: when I select File access and change it to Read an Write, it changes automatically back to it's original option. I have to use the terminal(sudo chmod 777 folder). So I'm asking now why is there an option to edit permissions in GUI if it's just to make you angry and does not work?! And than the option "Open as root" is gone from Nautilus... why is that???


  You never had permission to alter files when not root if you want right click then look here [http://ubuntuguide.net/add-open-as-root-to-filefolder-right-click-menu-in-ubuntu](http://ubuntuguide.net/add-open-as-root-to-filefolder-right-click-menu-in-ubuntu) couldn't be easier

> 3. Storage devices
I have two partitions - Filesystem and Storage. Somehow(in the Storage Device Manager I think...) I enabled writing to device so than I could put some data on it. Now I'm still unable to copy or change any files on this Storage device. And I also can't change permissions from Nautilus so the only option is sudo from the Terminal. I think an average user don't want that. 
gksudo nautilus will open nautilus as root either do it in terminal or alt f2 
No 4 ask on the forums or search google will solve this it can be a pain with windows to.
[QUOTE]5. GRUB loader
I noticed that the menu.lst file is gone. The file is grub.cfg but it's a little different. I always change the boot menu(after installation of Ubuntu) into minimum items. I successfully did that, but after two weeks, when I applied the Updates the boot menu was back to default. That's a strange think... and it's new in 9.10. 

 Grub2 is different it generates it's own grub entries I did like the old grub . I think you can uninstall grub2 and go back to grub legacy but check with someone more knowledgeable . Their is a really good guide to grub2 in the forums.

[/QUOTE]
  

 Every new version has it's problems if you want a long term stable Ubuntu better to use Hardy then move to lucid when it's stable .The LTS version is usually very stable after being out a few months.

---

### Post by Ugluk on 2010-01-13
Large software companies like Microsoft have whole departments to ensure backward compatibility and regression prevention. Canonical has smaller budget, and depends on hundreds of 3rd-party developers. So it is not possible to complete prevent such regressions.

---

### Post by Uncle Spellbinder on 2010-01-13
> **howefield said:**
> you probably don't know this forum exists.

[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

+1

---

### Post by philinux on 2010-01-13
> **jl2035 said:**
> I'm a big fan of Ubuntu for two years now but i think I'm not the only one sceptic about 9.10 Karmic. It's less frendly and more complex and I think that's not what Ubuntu is about. I have this Dell Studio 505 laptop and I have great performance. With 4GB of Ram and Ubuntu 9.10 I can almost do anything(Like running MS Visual Studio 2008 on virtual machine with WinXP - this was impossible with my old laptop). I'm not complaining about the speed or anything like that, I just hate this next few issues... 


[http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

Personally I find it every bit as good as previous releases if not better.

---

### Post by jl2035 on 2010-01-13
> **muteXe said:**
> yes. imo.

1 - Are you implying that in previous versions of ubuntu you were never once prompted to type in your password in when modifying files outside of your home folder?

I was but it wasn't such a pain in the ***. I just typed a password and everything worked. When moving files from the other partition it was just "Right click-Copy" and "Right click-Paste".

mich222:

[http://ubuntuguide.net/add-open-as-root-to-filefolder-right-click-menu-in-ubuntu](http://ubuntuguide.net/add-open-as-root-to-filefolder-right-click-menu-in-ubuntu)
- I did this once, but it's gone now - after the updates I think...

anyway Alt+f2 and "gksudo nautilus" is going to save me a lot.. thanks!

---

### Post by ratcheer on 2010-01-13
To date, I have used Ubuntu 8.04, 9.04, and 9.10. 9.10 is, by far, my favorite.

Tim

---

### Post by doas777 on 2010-01-13
there do seem to be a few problems with karmic (I'm having panel freezing issues on several boxes), but none of the issues you bring up appear to be specific to karmic itself.
1) it's always been this way.
2) the gui permissions menu has never really worked, and offers no options for changing ownership, which is likely your issue.
3) how are you mounting the external device, and what filesystem type is it? often new volumes are owned by root:root
4)samba is not simple. you will have to work at it.
5)your boot.cfg is regenerated when a new kernel is added. that is a change in grub2, not ubuntu per se, but I'm not getting what you mean by this being new. the old way would just ask you if you wanted to keep your old file or replace it with a new one. 
6) look around. i'm pretty sure a fix/workaround has been found for that.

lastly, this is not really the place for complaints. the ubuntu/oss developers do not read or post here a lot, so all your really doing is complaining about your issues to other users. it's like going onto a site devoted to discussion of playing with tonka trucks, and then telling everyone there that tonka sucks.

---

### Post by philinux on 2010-01-13
> **jl2035 said:**
> 

1. File/Folder Permissions
The whole FileSystem is unwritable. If you try to copy or change a file anywhere except "home folder" you will have to use console with sudo. In one month of using Ubuntu 9.10 I had multiple problems with this issue. 

2. GUI and Nautilus nonsense
If you "right click on the file or folder"->Properties->Permissions tab, you have some dropDown options here for Folder access and File access - both for owner, group and others. My problem is: when I select File access and change it to Read an Write, it changes automatically back to it's original option. I have to use the terminal(sudo chmod 777 folder). So I'm asking now why is there an option to edit permissions in GUI if it's just to make you angry and does not work?! And than the option "Open as root" is gone from Nautilus... why is that???



Install nautilus-gksu [plugin]("apt:nautilus-gksu") then when you right click there's an option to open as administrator.

---

### Post by mikewhatever on 2010-01-13
I think 9.10 is a very good release. Everything the OP mentioned permissions wise was in every previous release, and sound issues are nothing new too. In what way is it more complex exactly?

---

### Post by drs305 on 2010-01-13
> **jl2035 said:**
> 
5. GRUB loader
I noticed that the menu.lst file is gone. The file is grub.cfg but it's a little different. I always change the boot menu(after installation of Ubuntu) into minimum items. I successfully did that, but after two weeks, when I applied the Updates the boot menu was back to default. That's a strange think... and it's new in 9.10. 

Grub legacy probably worked the same way - it's just there are more updates to Grub 2 and more chances to install the maintainer's version. This will remove changes you make.

You can copy any of the menuentry items in /boot/grub/grub.cfg into /etc/grub.d/40_custom and then rename it 06_custom. Make it executable, run update-grub, and the entries will be at the top of the menu and stay there unchanged. If you are interested in more details we can provide them to you.

---

### Post by jl2035 on 2010-01-15
> **doas777 said:**
> there do seem to be a few problems with karmic (I'm having panel freezing issues on several boxes), but none of the issues you bring up appear to be specific to karmic itself.
1) it's always been this way.
2) the gui permissions menu has never really worked, and offers no options for changing ownership, which is likely your issue.
3) how are you mounting the external device, and what filesystem type is it? often new volumes are owned by root:root
4)samba is not simple. you will have to work at it.
5)your boot.cfg is regenerated when a new kernel is added. that is a change in grub2, not ubuntu per se, but I'm not getting what you mean by this being new. the old way would just ask you if you wanted to keep your old file or replace it with a new one.
6) look around. i'm pretty sure a fix/workaround has been found for that.


1. Let's be specific: I was trying to copy a virtual machine and a disk into storage partition. Somehow I gave all the permissions but now I'm having this alert: 
[IMG]http://www.shrani.si/f/3k/R7/4Hzyl5kf/screenshot.jpg[/IMG]

3. It's a fat32 partition. It's mounted at boot time, and the owner is me - not root. So my problem is this: if I use command "sudo chmod -R 777 sda6" it only gives 777 permissions to root folders on this partition. Subfolders and files have not changed. I still can't write to files on this partition. I have to copy the file to my home folder and than change permissions, edit and save... and copy back to Storage partition.

I never saw this in older versions, on my old laptop. I had ntfs storage partition but I don't think fat32 is the problem.

OK... I know now that it's not smart to use new release sooner than in a few months. I thought that everything that worked in the old versions, should definitely work in new.

> **doas777 said:**
> 
lastly, this is not really the place for complaints. the ubuntu/oss developers do not read or post here a lot, so all your really doing is complaining about your issues to other users. it's like going onto a site devoted to discussion of playing with tonka trucks, and then telling everyone there that tonka sucks.

Actually I posted this with a hope to get some problems solved. And I'm getting it, you see... :P

> **drs305 said:**
> Grub legacy probably worked the same way - it's just there are more updates to Grub 2 and more chances to install the maintainer's version. This will remove changes you make.

You can copy any of the menuentry items in /boot/grub/grub.cfg into /etc/grub.d/40_custom and then rename it 06_custom. Make it executable, run update-grub, and the entries will be at the top of the menu and stay there unchanged. If you are interested in more details we can provide them to you.

Thanks for this too...

---

### Post by ssulaco on 2010-01-15
> **mick222 said:**
> Every new version has it's problems if you want a long term stable Ubuntu better to use Hardy then move to lucid when it's stable .The LTS version is usually very stable after being out a few months.
I agree.Hardy is solid as a rock......will wait for Lucid.

---

### Post by bobbob1016 on 2010-01-15
> **jl2035 said:**
> 1. Let's be specific: I was trying to copy a virtual machine and a disk into storage partition. Somehow I gave all the permissions but now I'm having this alert: 
[IMG]http://www.shrani.si/f/3k/R7/4Hzyl5kf/screenshot.jpg[/IMG]

3. It's a fat32 partition. It's mounted at boot time, and the owner is me - not root. So my problem is this: if I use command "sudo chmod -R 777 sda6" it only gives 777 permissions to root folders on this partition. Subfolders and files have not changed. I still can't write to files on this partition. I have to copy the file to my home folder and than change permissions, edit and save... and copy back to Storage partition.


If you read the error, it isn't a permissions error, it is a file size error.  FAT32 can only have files 4gig and under, I'd assume your Virtual Machine and Disk are over 4gig.

Edit:  Your original problem 1 is there for safety.  If you could write to anything other than /home/username/ and /media/drivesyouadded/ viruses could easily run.  If you feel you must write to the filesystem (root folder) then alt+f2 "gksu nautilus" should work, but the plugins suggested above would be safer.

Your original "3" is the same safety thing, if you could change permissions on files you don't own or have read/write to already, a virus could do the same.

File-sharing does leave something to be desired for a new user, but you can try right clicking a folder, and doing sharing options, and it is pretty simple from there.  It shares them in Windows sharing format, iirc, so your Ubuntu and Windows machines should see it.

A quick search for "modify grub.cfg" on the forums gave me [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) which gave me:
#grub.cfg is overwritten anytime there is a update, a kernel is added/removed, or the user runs update-grub
#The user can use a custom file, /etc/grub.d/40_custom, in which the user can place his own entries. This file will not be overwritten. 
So edit /etc/grub.d/40_custom not grub.cfg

The only thing I can see as an actual "issue" is the sound, but if you think about it, Windows doesn't have all the drivers from the start, so Linux/Ubuntu shouldn't be expected to have everything from square 1.

---

### Post by Methuselah on 2010-01-15
9.10 is actually an ambitious step forwards that's why it can be a bit temperamental: excellent on some machines not so much on others.

Anyway, some of the things mentioned are standard behavior.
For example, you could never write outside of your home folder with admin rights.

---

### Post by Cabs21 on 2010-01-15
Bobbob is correct your error displayed is not a permissions error its a file size error.  If FAT32 can NOT handle a single file being larger then 4 GB of memory.  You would have to repartition a section of your drive as NSTF or something that can handle a 4GB or larger file.  I have been using 9.10 for a few months now and the only issue I have is that my brightness keys dont work but they never worked on 9.04 either so I didnt care cause I never change them.

I would like to get my finger print reader to work but i dont need it to so again i dont care.

---

### Post by beniwtv on 2010-01-15
> **jl2035 said:**
> 
1. File/Folder Permissions
The whole FileSystem is unwritable. If you try to copy or change a file anywhere except "home folder" you will have to use console with sudo. In one month of using Ubuntu 9.10 I had multiple problems with this issue. 


This is normal. You aren't supposed to write anything outside /home, /tmp and maybe /media (for USB devices). If you do, this means you must know what you are doing, and need to be administrator. Else, you could break your system.

> **jl2035 said:**
> 
2. GUI and Nautilus nonsense
If you "right click on the file or folder"->Properties->Permissions tab, you have some dropDown options here for Folder access and File access - both for owner, group and others. My problem is: when I select File access and change it to Read an Write, it changes automatically back to it's original option. I have to use the terminal(sudo chmod 777 folder). So I'm asking now why is there an option to edit permissions in GUI if it's just to make you angry and does not work?! And than the option "Open as root" is gone from Nautilus... why is that???


I agree. Changing permissions from Nautilus is awkward sometimes. Feel free to report a bug about it. The "Open as root" option, IIRC, is a package you need to install. I don't think it ever came as default...

> **jl2035 said:**
> 
3. Storage devices
I have two partitions - Filesystem and Storage. Somehow(in the Storage Device Manager I think...) I enabled writing to device so than I could put some data on it. Now I'm still unable to copy or change any files on this Storage device. And I also can't change permissions from Nautilus so the only option is sudo from the Terminal. I think an average user don't want that. 


As some of the people pointed out, FAT32 has limited file size. Your file is too large. I would recommend using NTFS or EXT2. I got no permission problems with them. Also, FAT32 doesn't have permissions, so you can't change them (and to change permissions for the drive you need to be root!)

> **jl2035 said:**
> 
4. File sharing
I connected two machines in my home LAN network - PC(Ubuntu 9.04) and my laptop(Ubuntu 9.10). I was unable to see any shared folders from both machines. Neither the machines. Setting all permissions Read and Write didn't change anything. I asked for some help on Ubuntu irc chat channel, but we didn't solve the problem. I don't know if this is 9.10 version problem but anyway - I can't exchange files using LAN!


You actually need to share any files/folders. Ubuntu will then install the required software, which needs a reboot. Works every time for me. Also, keep in mind that sometimes it will take a while until machines "discover" each other. That's a limitation of the Windows file sharing protocol, not Ubuntu.

> **jl2035 said:**
> 
5. GRUB loader
I noticed that the menu.lst file is gone. The file is grub.cfg but it's a little different. I always change the boot menu(after installation of Ubuntu) into minimum items. I successfully did that, but after two weeks, when I applied the Updates the boot menu was back to default. That's a strange think... and it's new in 9.10. 


We're using Grub2 now. See here for instructions:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

> **jl2035 said:**
> 
6. Sound
On my friend's HP Compaq laptop I had this stupid problem. Every time when the machine starts, the sound is checked as Mute in Volume Control. I also set up Ubuntu 9.10 on a Fujitsu Siemens laptop. There was no sound here. I set everything to full volume and all Mutes unchecked. In the Rhythmbox songs were playing but the speakers were mute.


That is(was) a bug. [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732)
If you still experience it, please help by adding to the bug report.

Cheers,

---

### Post by jl2035 on 2010-01-18
About Grub 2... It's just more complex, isn't it? I didn't have to google any "Grub instructions" before! 

> **beniwtv said:**
> I agree. Changing permissions from Nautilus is awkward sometimes. Feel free to report a bug about it. The "Open as root" option, IIRC, is a package you need to install. I don't think it ever came as default...

I think it did... or maybe I'm wrong because I was using Linux Mint at that time but this option was there - so it was probably also in Ubuntu! Anyway now I know the alternative "alt+f2 and gksudo nautilus" ... so this is no longer my problem... but changing permissions still is(even as root). I'll report a bug. 

> **beniwtv said:**
> As some of the people pointed out, FAT32 has limited file size. Your file is too large. I would recommend using NTFS or EXT2. I got no permission problems with them. Also, FAT32 doesn't have permissions, so you can't change them (and to change permissions for the drive you need to be root!)

I have another funny story here...
First of all: I don't know why but ntfs was disabled in Partition Manager(or GParted), and it still is. I formated this Fat32 partition to EXT2 now. Here's the problem: I can't mount the partition, so I opened Storage Device Manager and here I can't see any changes. It looks like I didn't just format. 'Options' are still the same and even type is still 'vfat'. I reinstalled Storage Device Manager but no changes. This is really strange...

[IMG]http://www.shrani.si/f/h/Xb/34vpYQZB/screenerror.jpg[/IMG] 

> **beniwtv said:**
> You actually need to share any files/folders. Ubuntu will then install the required software, which needs a reboot. Works every time for me. Also, keep in mind that sometimes it will take a while until machines "discover" each other. That's a limitation of the Windows file sharing protocol, not Ubuntu.

I did share folders! I waited for something like 3 hours but machines didn't discover each other. I wonder what does 'Windows file sharing protocol' has to do with this. I had Ubuntu on both machines.

---

### Post by muteXe on 2010-01-18
> **ssulaco said:**
> I agree.Hardy is solid as a rock......will wait for Lucid.

+ 1 million for this. If lucid is as retarded in it's evolution as karmic, in terms of stability, then bye bye ubuntu :(

---

### Post by gabo.cr on 2010-01-18
I was using Hardy and I never used 8.10 or 9.04.
I was waiting for Lucid, but then I had to reinstall everything on my laptop when I decided to go for Karmic and I have to say, I am very happy with Karmic, if fixed some of the video issues I had and it installed with no complaints at all.
But I know I will get Lucid as soon as I can, since I like the LTS versions better.

---

### Post by Tamlynmac on 2010-01-18
[> ]("http://ubuntuforums.org/member.php?u=451394")[doas777]("http://ubuntuforums.org/member.php?u=451394")
lastly, this is not really the place for complaints. the ubuntu/oss developers do not read or post here a lot, so all your really doing is complaining about your issues to other users. it's like going onto a site devoted to discussion of playing with tonka trucks, and then telling everyone there that tonka sucks.

Truer words haven't been posted in this section of the forum for quite some time. It's unfortunate that few will actually heed your words. I often wonder why so many believe that posting rants here would have any effect on Canonical and what agenda they may have.

I enjoyed your analogy, using Tonka as the example. Much like Ubuntu - they are tough to destroy.

---

### Post by HappyFeet on 2010-01-18
> **muteXe said:**
> If lucid is as retarded in it's evolution as karmic, in terms of stability, then bye bye ubuntu :(

Could you preface that statement with "*for me*"? Thank you. Not everyone will have *your* experience. No problems here with karmic on several machines. Not bad, huh?

I don't know why people speak as if their experience is a universal truth.

---

### Post by beniwtv on 2010-01-19
> **jl2035 said:**
> About Grub 2... It's just more complex, isn't it? I didn't have to google any "Grub instructions" before! 


Let's say it's... different. We just need to get used to it. After that, I think it will be pretty simple. Not to mention all the good features we didn't have in Grub 1.

> **jl2035 said:**
> 
I think it did... or maybe I'm wrong because I was using Linux Mint at that time but this option was there - so it was probably also in Ubuntu!

I think the package to install is nautilus-gksu. Ubuntu Mint could have installed this by default. Also, you might want to look into 
nautilus-scripts, they are even more awesome.

> **jl2035 said:**
> 
I have another funny story here...
First of all: I don't know why but ntfs was disabled in Partition Manager(or GParted), and it still is. I formated this Fat32 partition to EXT2 now. Here's the problem: I can't mount the partition, so I opened Storage Device Manager and here I can't see any changes. It looks like I didn't just format. 'Options' are still the same and even type is still 'vfat'. I reinstalled Storage Device Manager but no changes. This is really strange...

I did share folders! I waited for something like 3 hours but machines didn't discover each other. I wonder what does 'Windows file sharing protocol' has to do with this. I had Ubuntu on both machines.

Have you created support threads for these problems? I'm sure we can help you out there. Here in the T&E section not much people stop by to solve technical problems.

Cheers,

---

### Post by gabo.cr on 2010-01-19
> i don't know why people speak as if their experience is a universal truth.

+10 !

---

### Post by muteXe on 2010-01-20
> **HappyFeet said:**
> Could you preface that statement with "*for me*"? Thank you. Not everyone will have *your* experience. No problems here with karmic on several machines. Not bad, huh?

I don't know why people speak as if their experience is a universal truth.

Yep, I agree. Apologies mate. *For me* every release after 8.04 has been rather wank.

---

### Post by XubuRoxMySox on 2010-01-20
Karmic Ubuntu, apparently, was released before it was truly ready, judging by what I have read in these forums. But Karmic [COLOR="Blue"]**_X_**ubuntu[/COLOR] was perfect right out of the gate! Pro'lly because it doesn't ship with alot of the software that has given some people fits in "vanilla" Ubuntu (PulseAudio, for a notable example, but other packages as well - Xubuntu uses ALSA). It's a far less buggy Karmic than either of it's two siblings.

That said, though, it's pro'lly to be expected for a distro that is based on *Debian _Unstable_* to be, well, um, unstable. The Long-Term Support versions are built on *Debian Testing*, so they're bound be, well, a little testy maybe. ;) But not as unstable as the non LTS versions.

Lucid will probably be rock solid because it's an LTS. And Lucid *Xubuntu*? Pro'lly even more solid!

-Robin

---

### Post by HappyFeet on 2010-01-20
> **muteXe said:**
> Yep, I agree. Apologies mate. *For me* every release after 8.04 has been rather wank.

Thank you for that. Not every OS will work for everyone in the world, that's just the way it is. Considering there are 1000's of possible hardware configurations and other variables such as faulty hardware, and user experience, I think ubuntu overall, does pretty good.

---

### Post by HappyFeet on 2010-01-20
> **dixiedancer said:**
> Karmic Ubuntu, apparently, was released before it was truly ready, **judging by what I have read in these forums**.

How good of a gauge is that though? Considering there are now millions of people using ubuntu, the number of posts with people that have problems seems rather small. Ever look at it that way?

---

### Post by Irihapeti on 2010-01-20
Does anyone remember how much yelling and screaming there was about the awfulness of Hardy just after its release?

Substitute the name of any other release for "Hardy", and that still applies. Because it happened a long time ago, it tends to be forgotten.

The question then becomes, what are you or I going to do about it. We can apply workarounds and report bugs, or we can manage without the functionality that isn't working properly, or we can choose to use something else.

To each their own choice. I don't mind which one you make. I just get a bit irritated when people present their own experience and choice as the one that every reasonable person should agree with.

But then, maybe I'm just unreasonable.

---

### Post by XubuRoxMySox on 2010-01-20
> **HappyFeet said:**
> How good of a gauge is that (judging by what one reads in these forums) though? Considering there are now millions of people using ubuntu, the number of posts with people that have problems seems rather small.

Prob'ly true. And there's always a rush of new complaints with every new release - always accompanied by a rush of praise posts for huge improvements!

So yessir... you're pro'lly right. But I don't think there's any excuse for including experimental or beta software by default in a brand-new release of any Linux distro that claims to be stable or suitable for beginners. It's okay for Sidux or one of those other bleeding edge, high risk distros where users *willingly* assume that risk and *expect* to run into issues and workarounds - which is part of the fun - for *them*. Not so fun for a Linux beginner!

-Robin

---

### Post by HappyFeet on 2010-01-20
> **dixiedancer said:**
> It's okay for Sidux or one of those other bleeding edge, high risk distros where users *willingly* assume that risk and *expect* to run into issues and workarounds - which is part of the fun - for *them*. Not so fun for a Linux beginner!

-Robin

That's the nature of the beast. How are they supposed to make improvements to software if they don't get the software out to the masses, so they can report problems? Or do you think the developers should have a huge room filled with 1000's of computers and test every possible hardware configuration? Or should they use every application in the repos, every way that it can be used? I got it! Just install every known app, in every possible way, on every possible hardware configuration!!!!

See where this is going?

Bottom line: Don't like something? Don't use it. Freedom of choice is wonderful.

---

### Post by Malakai on 2010-01-22
I am confused, since 9.10 is the first version of Ubuntu I've ever used. Did ubuntu previously allow more than read permissions for users for the entire file system?

Coming from many years of Gentoo, and havinb dabbled in a few other flavors, the only directory where **users** are supposed to have full filesystem permissions is in their folder.

At least nearly every other linux distro I have ever used works this way. I would intentionally set it up that way if it didn't.

I like that I can let my mom and sys use my netbook, and not worry that they are going to get confused with something, say accidentally opening a terminal, and damage the file system or anything important.

Linux is not windows. Windows does not have the detailed and thoughtful permissions system linux does, which is why there are viruses and spyware that rampage out of control on windows machines. If you use linux, you should go in with your eyes open. The price of having a secure os where spy and malware hardly exists is that it is a secure operating system and you cannot just modify any aspect of the system on a whim. All you need to do is type sudo before a command anyway, or enable the root account (which I do coming from other linux flavors that use root, tho now that I am getting used to sudo it's really not an issue at all and Im finding I rather like it). And even tho that is so simple to do, having to do that is one of the reasons a virus or malware executed under your username cannot infect the whole system, it would only be able to modify files in your home directory, and generally nothing of importance, certainly no system executables or libraries, are located there.

The perissions system seems like a hassle, but its actually one of linuxes greatest features!

---

### Post by XubuRoxMySox on 2010-01-22
> **HappyFeet said:**
> That's the nature of the beast. How are they supposed to make improvements to software if they don't get the software out to the masses, so they can report problems? 

That's what Alpha and Beta testing is for. **It's simply inappropriate to use newbies as guinea pigs to test out unstable software.** The LTS versions of Ubuntu are based on *Debian Testing* rather than *Debian Unstable* (like the other Ubuntu releases are), and are thus less prone to bugs that would frustrate newbies and send them looking elsewhere for stability and reliability.

For newbies to Linux I can no longer in good conscience recommend any but the latest *LTS* version of Ubuntu, or a distro like Mepis that is based on Debian Stable.

-Robin

---

### Post by gabo.cr on 2010-01-22
> I like that I can let my mom and sys use my netbook, and not worry that they are going to get confused with something, say accidentally opening a terminal, and damage the file system or anything important.

I believe that to destroy something in the system with Terminal you actually have to know how to do it.
:D

---

### Post by Jackzor on 2010-01-23
> **gabo.cr said:**
> i believe that to destroy something in the system with terminal you actually have to know how to do it.
:d

+10

---

### Post by kg4cna on 2010-01-23
> **ssulaco said:**
> I agree.Hardy is solid as a rock......will wait for Lucid.

+1

I also use Hardy and am awaiting the next LTS release.

---

### Post by JoeWheeler on 2010-01-25
Hmmm, I don't have much experience with ubuntu, Jaunty was the first version(and the first non-windows OS!) I've used but I've found karmic to be less stable, throwing up errors not encountered in jaunty. I'm looking forward to a nice LTS to settle down with :)

However having said these things I still prefer it to windows

---

### Post by XubuRoxMySox on 2010-01-25
**I stand corrected** on something I said earlier: *Previous* LTS versions were _not_ necessarily based on Debian Testing, but Lucid _will_ be. It's bound to be more stable than Karmic.

-Robin

---

### Post by Odense on 2010-01-25
On a side note to this - what file is it I can modify - and what am I to write in it if I install 8.04 LTS and only want to upgrade when the next LTS version arrives.

I read about this somewhere - maybe on this forum - but I cannot find it again now :(

---

### Post by XubuRoxMySox on 2010-01-25
> **Odense said:**
> On a side note to this - what file is it I can modify - and what am I to write in it if I install 8.04 LTS and only want to upgrade when the next LTS version arrives.

I read about this somewhere - maybe on this forum - but I cannot find it again now :(

System > Software Sources > Updates - choose "LTS releases only" from the Release Upgrade menu.

-Robin

---

### Post by Odense on 2010-01-26
Thank Robin - that was fast :KS

---

### Post by caravel on 2010-01-26
> **Odense said:**
> On a side note to this - what file is it I can modify - and what am I to write in it if I install 8.04 LTS and only want to upgrade when the next LTS version arrives.

I read about this somewhere - maybe on this forum - but I cannot find it again now :(

I wouldn't be too eager to upgrade.  The changes between 8.04 and 10.04 are very significant.  Being LTS won't make it any more compatible than 9.10.  I would download the 10.04 livecd first and run that before upgrading to ensure that all of your hardware runs ok, even then expect problems if you have proprietary drivers installed.  Remember that those are built for a specific kernel.

> **dixiedancer said:**
> **I stand corrected** on something I said earlier: *Previous* LTS versions were _not_ necessarily based on Debian Testing, but Lucid _will_ be. It's bound to be more stable than Karmic.

-Robin

Testing is coming along nicely.  I run two boxes, Testing (Squeeze) on one and Stable (Lenny) on another.  So far I've no issues with testing, it's very solid.  If you want to give it a try be aware that it's a text mode installer at the moment.

---

### Post by Flash858 on 2010-01-26
9.10 is a step back in many respects. 

There are annoyances GALORE. 

There were a ton of packages that simply stopped working (and were "disabled" in the source list) when 9.10 arrived.

Lack of root access in Ubuntu has always baffled me. Why do I not have "permission" to write to and from my own drives? Do I LOOK like I am wearing short pants? If you are computer literate enough to even KNOW THAT LINUX EXISTS, you probably want root access. I have a couple of Nautilus scripts that work fine for root file management, but they are not system wide. Lack of root access is just plain FATUOUS, and makes me crazy. 

The argument is that it prevents the "average user" from corrupting their system. That is utterly and completely untrue, and in my experience (many years of tech support), it is also IMPOSSIBLE based on the following POSTULATES:

The "average user" does not use the file manager.
The "average user" does not know he/she HAS a file manager. 
The "average user" also does not go poking around their system to see if they can screw it up. They are AFRAID of it.

Also, in 9.10, the ability to kill the STUPID 60 second shutdown delay is gone. POOF! In the wind...

"Are you sure you want to do that Mr. User?"
"Um...yea...actually I am...that's kinda why I clicked it in the first place..."
"Just what do you think you're doing Dave?"
"Huh? My name is Matthew...who are you talking to??? I just want you to shut down, OK? I have to get to the gym, and I'm trying to be responsible and green and all that, and conserve energy so future generations don't have to eat each other..."
"Daisy...Daisy...give me your answer do..."

And this goes on ad nauseum...

I have looked at the other major distributions, and some are decent enough, but all have their drawbacks, they just don't have the Ubuntu "feel" that I like and have grown accustomed to, and frankly I seriously believe eventually Ubuntu will be the only Distro left with any measurable resources. 

It is already the face (and voice) of Linux in the PC/Mac world, and many non-users who have actually heard of it already equate Ubuntu to Linux ("Linux...you mean YOU-buntu, right?"), and have no idea there are any other distros.

So I am "stuck" with Ubuntu (if only I didn't have all of those Ubuntu shirts, and stickers on virtually everything I own...). I am hoping that someday Ultimate edition or Mint give root access, but in the interim, at least I have been able to create a near-perfect desktop (save the annoyances above).
[B]
Maybe a "Professional" edition of Ubuntu with no restrictions would be in order...are you listing Cannonical??? I would happily PAY for it. [/B]

 Until that happens, I will keep Puppy Linux on a separate partition...

---

### Post by sithlordkyle on 2010-01-26
it has some major problems indeed.  on both the netbook remix version and desktop version i have lost my gui only to get to terminal after logging in.

my only solution was to go back to 9.04.  i definitely am not a fan of karmic, still too buggy.

---

### Post by ratcheer on 2010-01-26
> **Flash858 said:**
> 

Also, in 9.10, the ability to kill the STUPID 60 second shutdown delay is gone. POOF! In the wind...

"Are you sure you want to do that Mr. User?"
"Um...yea...actually I am...that's kinda why I clicked it in the first place..."
"Just what do you think you're doing Dave?"
"Huh? My name is Matthew...who are you talking to??? I just want you to shut down, OK? I have to get to the gym, and I'm trying to be responsible and green and all that, and conserve energy so future generations don't have to eat each other..."
"Daisy...Daisy...give me your answer do..."

And this goes on ad nauseum...



So, I just use "sudo init 0" to shut down or "sudo init 6" to restart. It happens, immediately.

Tim

---

### Post by aysiu on 2010-01-26
> **Flash858 said:**
> 
Lack of root access in Ubuntu has always baffled me. It's for security purposes. This privilege level separation happens in every sane Linux distro (the only exception I know of is the crappy Xandros for the Eee PC). The only difference between Ubuntu and other mainstream distros is that Ubuntu uses *sudo* instead.

If you want a persistent root prompt, just use ```
sudo -i
``` If you want a root file manager, create a launcher or keyboard shortcut for ```
gksudo nautilus
``` Done. What's the big deal?

---

### Post by BigSilly on 2010-01-26
Totally agree. I much prefer the permissions system on Linux than the current Windows solution. It makes sense imho, though it did take a bit of getting used to when I first switched to Linux a few years ago admittedly.

---

### Post by wojox on 2010-01-26
> **Flash858 said:**
> 
Also, in 9.10, the ability to kill the STUPID 60 second shutdown delay is gone. POOF! In the wind...

```
gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool true
```

---

### Post by jl2035 on 2010-02-03
I see I started an interestnig thread...

---

### Post by XubuRoxMySox on 2010-02-03
> **caravel said:**
> 
Testing is coming along nicely.  I run two boxes, Testing (Squeeze) on one and Stable (Lenny) on another.  So far I've no issues with testing, it's very solid.  If you want to give it a try be aware that it's a text mode installer at the moment.

**Debian Squeeze/Xfce totally rawks!!** I do hope they get a graphical installer to make it noobie-friendly. I've read that they are working on an installer for future versions. I had to run GParted first to prepare the HDD (using a LiveCD), but after that it's pretty easy even for a silly little dixiedancer! I hope Xubuntu Lucid will be as awesome as Squeeze/Xfce!

-Robin

---

### Post by jl2035 on 2010-02-08
And I forgot to mention CD burning problem. I posted it here:
[http://ubuntuforums.org/showthread.php?t=1397384](http://ubuntuforums.org/showthread.php?t=1397384)

---

### Post by DeusExM1 on 2010-02-09
idk how it is for other people but for me 9.10 is a huge step back when compared to 9.04. I am having many issues with my karmic machine...  Some recent examples:

1. sometimes when computer boots a black screen is displayed where i have to log in and enter my password. (although it is set up to boot automatically without password prompt). Once i enter my password i have to write "startx" to get the normal desktop to boot up. Then i do whatever i want for 5 minutes, at which point everything is interrupted by the ubuntu logo and the LOADING screen which was supposed to appear when the system was booted the first time. So after ubuntu loads AGAIN, all of the programs i had running are no longer visible in the taskbar, but are running in the background as processes. ANNOYING.

2. Open office is crappy like usual but... at least in 9.04 it didnt cause my machine to crash. 2 days ago i was writing a bio lab report and was trying to move some graphs from OO Spreadsheet to OO Word processor. Bad idea as my machine crashed and after waiting for 10 minutes i was forced to do a HARD shut down. Wow.... hows that for productivity when you are writing a report at 2 am... 

3. Missing icons are annoying. I am talking about the top right button on the taskbar where you can shut the computer down. Why do i have to read through all of the text instead of just seeing an icon that im familiar with? Its silly, and 9.04 had better implementation.

The list goes on, but you get the idea. These problems arent minor. Having said that im not considering jumping the boat at all... I know that every OS has its problems, no OS is perfect, and so im just waiting for Ubuntu 10.04. (I have windows xp, windows vista, and even windows 7 in my drawer)... But i dont plan to switch back..Patience my friend, you need patience. :D

---

### Post by cariboo on 2010-02-09
I think this thread has served it's purpose. Closed

---

