---
title: "Do separate /home partitions provide any advantage anymore?"
date: 2011-10-04
forum: The Cafe
---

### Post by FuturePilot on 2011-10-04
I've been using a separate home partition for some time now. The big advantage was that you could reinstall Ubuntu without losing all of your personal data. However, Ubiquity now supports [preserving your /home.]("https://wiki.ubuntu.com/UbiquityPreserveHome") So I'm thinking about just going back to a single partition. Are there any advantages to having a separate /home partition now?

---

### Post by keithpeter on 2011-10-04
Hello

Having one saved me a *lot* of copying when I decided to move from Ubuntu to Debian on the desktop PC. I deleted all the dotfiles and folders as well, so that there were no 'preference hangovers', but all the music and photos did not need to be restored.

Guess if you are staying in the Ubuntu camp then Ubiquity will be OK for you. We all have complete up to date backups in two places of course :twisted:

---

### Post by CharlesA on 2011-10-04
The big advantage is the one that keithpeter mentioned - less copying.

I have my home folder on the same drive/partition as my main install, but I do backups of it so I have what I need in case I need to reinstall.

---

### Post by undecim on 2011-10-04
If you ever want to try a non-Ubuntu distro (or is Ubiquity a debian thing?) then you will run into problems.

It also offers some degree of damage control if e.g. something causes your file system on / to get corrupted, your /home partition is likely to be unaffected, and you can simply reinstall your OS without losing any data.

---

### Post by ninjaaron on 2011-10-04
It makes clean installs and upgrades a breeze, something handy if you plan on breaking you system a lot (which I do as often as I'm able).  As mentioned, it also makes distro hopping easier.

---

### Post by FuturePilot on 2011-10-04
Ok, I can see an advantage if you're distro hopping or switching distros but I don't do distro hopping anymore and I don't plan on switching distros. So for me personally that's of little or no value to me.

> **undecim said:**
> If you ever want to try a non-Ubuntu distro (or is Ubiquity a debian thing?) then you will run into problems.

It also offers some degree of damage control if e.g. something causes your file system on / to get corrupted, your /home partition is likely to be unaffected, and you can simply reinstall your OS without losing any data.

Ubiquity is Ubuntu's installer. As for damage control, I don't see that as a benefit. Your home partition could become corrupted just as easily as the root partition. Of course, this is why we have backups. ;)

> **ninjaaron said:**
> It makes clean installs and upgrades a breeze, something handy if you plan on breaking you system a lot (which I do as often as I'm able).  As mentioned, it also makes distro hopping easier.
Did you read the link? You can do fresh installs with your /home on the same partition as the root partition without losing anything.

---

### Post by ninjaaron on 2011-10-04
> **FuturePilot said:**
> Did you read the link? You can do fresh installs with your /home on the same partition as the root partition without losing anything.This isn't the same as wiping the system and doing a real fresh install.  When I do it, I wipe all my user config files as well, and only migrate over the ones that I specifically want.  Old config files can cause buggy behavior in Ubuntu upgrades.  I have always had better results when I wipe the system and start with a fresh home folder, run some post-install scripts, and trickle my settings over gradually as I need them.

It does take more work, but it's a cleaner way to do it that leaves less 'cruft of years gone by'.

By the way, did you check the date in that wiki page?  This is nothing new.

---

### Post by forrestcupp on 2011-10-04
I'd say for you, there's not much advantage, other than what other people have said about having to copy the files during the installation. I'm not sure how Ubiquity handles that.

I've always put everything except swap on one partition. But one advantage I've seen about having a separate /home partition is that it makes it easier and less risky if you want to use the same /home partition with multiple linux installations at once. But that obviously doesn't apply to you.

And ninjaaron has a good point about the benefit of wiping your config files to get a true clean install.

---

### Post by StephanG on 2011-10-04
Well, I also split up my /home partition, and it was really helpful to me,when I wanted to upgrade my hard drives.

I had a 320 GB with my / partition on, and  2 TB drive with my /home partition on.  Then, when I upgraded, I installed a 120 GB Solid state drive for my / partition.

Now, that meant that I could get a lot of the speed benefits of SSD, but all my data was on the conventional hard drive with its oodles of storage space.

So, keeping it separate is also an advantage if you're swopping around hardware.

But, keep in mind, the INSTALLER will protect your home directory.  That means the INSTALLER won't mess with your personal files and settings.  But, it won't protect your data if you accidentally format your / partition, or any other threat to your root directory.

---

### Post by Roasted on 2011-10-04
I always keep my data on a separate partition, but I also have a strange setup. Due to being, well, poor... and mdadm being built in, I like to utilize software RAID in Linux as much as possible. As a result, my standard setup is:

Small SATA HDD for Root
Two Large SATA HDD's for /Home

That way my data is not only on a separate partition, but also is redundant in itself. 

Plus, having the advantage of taking my two array drives, putting them in another system, installing mdadm and magically having all of my data there is nice. I haven't had quite that much luck with hardware RAID controllers in the past. While lesser performing, it has enough advantage that makes me a fan of it. That said, yes I keep my data on a separate partition and due to my setup, I swear by it.

---

### Post by wolfen69 on 2011-10-05
Having a separate home partition allows *you* to choose how big you want it to be. That might be important if you have a lot of VM's installed.

---

### Post by FuturePilot on 2011-10-05
> **forrestcupp said:**
> I'd say for you, there's not much advantage, other than what other people have said about having to copy the files during the installation. I'm not sure how Ubiquity handles that.

I've always put everything except swap on one partition. But one advantage I've seen about having a separate /home partition is that it makes it easier and less risky if you want to use the same /home partition with multiple linux installations at once. But that obviously doesn't apply to you.

And ninjaaron has a good point about the benefit of wiping your config files to get a true clean install.

Ah yes. This is pretty much what I was thinking.

---

### Post by ssam on 2011-10-05
> **wolfen69 said:**
> Having a separate home partition allows *you* to choose how big you want it to be. That might be important if you have a lot of VM's installed.

but having it on the same partitions makes it easier to change you mind if you got the sizes wrong at the start.

personally i keep all my big files on a separate disk/partition mounted at /data

---

### Post by Copper Bezel on 2011-10-05
I found it easier to drop in my new root partition and selectively migrate settings on my upgrade to 11.04 this way, but mostly I just like the idea of keeping things organized and limiting my root partition to specified size. It's an eccentrically *nixy thing to do, and it appeals to me.

---

### Post by forrestcupp on 2011-10-05
There might be a slight speed advantage to have a separate /home partition if it is on a separate hard drive from the root. That wouldn't apply for separate partitions on the same drive, though.

---

### Post by lcman on 2011-10-05
> **FuturePilot said:**
> I've been using a separate home partition for some time now. The big advantage was that you could reinstall Ubuntu without losing all of your personal data. However, Ubiquity now supports [preserving your /home.]("https://wiki.ubuntu.com/UbiquityPreserveHome") So I'm thinking about just going back to a single partition. Are there any advantages to having a separate /home partition now?

I use a dedicated partition for /home because of LVM. I can resize the partition anytime I want that way! :popcorn:

---

### Post by ninjaaron on 2011-10-05
> **forrestcupp said:**
> There might be a slight speed advantage to have a separate /home partition if it is on a separate hard drive from the root. That wouldn't apply for separate partitions on the same drive, though.

If you really want the speed, get a small SSD and put root on that sucker, with data on an HDD.

BOOM.

---

### Post by forrestcupp on 2011-10-05
> **ninjaaron said:**
> If you really want the speed, get a small SSD and put root on that sucker, with data on an HDD.

BOOM.

That's exactly what I'm doing with Win7 on my nettop. If I didn't, it would run like a snail. Nettops aren't known for being fast.

---

### Post by wolfen69 on 2011-10-05
> **ssam said:**
> but having it on the same partitions makes it easier to change you mind if you got the sizes wrong at the start.


But I don't make mistakes, so..... ;)

---

### Post by forrestcupp on 2011-10-05
> **wolfen69 said:**
> But I don't make mistakes, so..... ;)I've only made one mistake. That was when I thought I was wrong about something, but I wasn't.

---

### Post by ninjaaron on 2011-10-05
> **wolfen69 said:**
> But I don't make mistakes, so..... ;)
> **forrestcupp said:**
> I've only made one mistake. That was when I thought I was wrong about something, but I wasn't.


I, on the other hand, rm'ed my home folder a couple of weeks ago.

8^)

---

### Post by CharlesA on 2011-10-05
Try rsync -a * instead of rsync -a / and then reinstall without checking to make sure everything was copied..

Blarg!

---

### Post by Legendary_Bibo on 2011-10-05
When 11.10 comes out I plan on wiping 10.10 and only backing up the media files in my /home folder then when I install 11.10 I'll make a separate partition for my /home this time around. It's also a dual boot system with Windows 7. Would it be a good idea to make it a NTFS?

---

### Post by Copper Bezel on 2011-10-05
If the 11.10 installer can scoot itself around an existing /home, then the simplest thing would be to delete all hidden (config) files in ~, then trust Ubiquity to do the rest. Alternately, you can make the old / into a new /home (move your personal folder to the root and nuke the rest) and still not have to copy anything off and back again.

NTFS doesn't store permissions the same way as ext4, does it? Particularly execute permissions?

---

### Post by earthpigg on 2011-10-05
> **FuturePilot said:**
> I've been using a separate home partition for some time now. The big advantage was that you could reinstall Ubuntu without losing all of your personal data. However, Ubiquity now supports [preserving your /home.]("https://wiki.ubuntu.com/UbiquityPreserveHome") So I'm thinking about just going back to a single partition. Are there any advantages to having a separate /home partition now?

I'm still on 10.10 out of laziness, and I'd backed up and then restored /home in conjunction with a fresh install for the couple releases prior to that. I have a separate /home partition.

Does this mean when 12.04 comes out and I pop the 12.04 USB in that the backing up of /home will truly be only cursory 'just in case'?

Does ubiquity recognize separate /home partitions and simply give you a 'keep existing /home' option and then works the rest out itself?

---

### Post by forrestcupp on 2011-10-06
> **Legendary_Bibo said:**
> It's also a dual boot system with Windows 7. Would it be a good idea to make it a NTFS?
For dual booting with Win7, I always leave most of the space on my Windows partition, and just use the Windows Documents, Music folders, etc., to store all of my media. Then I just set up Nautilus or whatever file browser I use in Linux to have shortcuts in the left panel to my Windows media folders. I hardly use my /home directory at all, other than for all of those config files, and some 3rd party software that installs there.

It's a lot easier and less messy to get Linux to read NTFS than it is to get Windows to read Ext file systems.

---

### Post by el_koraco on 2011-10-06
> **Legendary_Bibo said:**
> When 11.10 comes out I plan on wiping 10.10 and only backing up the media files in my /home folder then when I install 11.10 I'll make a separate partition for my /home this time around. It's also a dual boot system with Windows 7. Would it be a good idea to make it a NTFS?

No need for such actions. If you're dual booting with Windows, don't even make a separate /home, just back your desired config files. Make a shared NTFS partition for Linux and Windows, then install oneiric in a single partition, bring back your config files, edit fstab to mount the shared partition as /media or something. 

Delete all the Music, Video, Downloads and other folders in $HOME, recreate those folders on the media partition and symlink them to $HOME. It sounds like a lot of work, but the it's only editing fstab, symlinking is done easiest by slitting the pane in Nautilus, dragging the from the media partition with the middle button, and selecting "link here".  

That way your data will always be safe from both Linux and Windows going crazy. You can even resize the Windows system partition to some acceptable level (I have my mothers C:\ at 30 GB with no problems at all, the Libraries thing does everything else easy for her, even though Explorer is still a dreadful file manager, almost as bad as Nautilus). 

I'd also suggest you boot the Windows rescue CD, fix the MBR, make sure you can boot Windows, then during the new install put GRUB in /, and have BOOTMGR chain-loading to the GRUB in /. I'm saying this because I just came back from a rescue operation for a poorly made dual boot, where the sysadmin did some monkeying around with the partitions, so the original GRUB didn't want to boot anything, and the reinstalled one doesn't boot XP (and I couldn't do anything, since I didn't have a Windows CD around).

---

### Post by Legendary_Bibo on 2011-10-06
> **el_koraco said:**
> No need for such actions. If you're dual booting with Windows, don't even make a separate /home, just back your desired config files. Make a shared NTFS partition for Linux and Windows, then install oneiric in a single partition, bring back your config files, edit fstab to mount the shared partition as /media or something. 

Delete all the Music, Video, Downloads and other folders in $HOME, recreate those folders on the media partition and symlink them to $HOME. It sounds like a lot of work, but the it's only editing fstab, symlinking is done easiest by slitting the pane in Nautilus, dragging the from the media partition with the middle button, and selecting "link here".  

That way your data will always be safe from both Linux and Windows going crazy. You can even resize the Windows system partition to some acceptable level (I have my mothers C:\ at 30 GB with no problems at all, the Libraries thing does everything else easy for her, even though Explorer is still a dreadful file manager, almost as bad as Nautilus). 

I'd also suggest you boot the Windows rescue CD, fix the MBR, make sure you can boot Windows, then during the new install put GRUB in /, and have BOOTMGR chain-loading to the GRUB in /. I'm saying this because I just came back from a rescue operation for a poorly made dual boot, where the sysadmin did some monkeying around with the partitions, so the original GRUB didn't want to boot anything, and the reinstalled one doesn't boot XP (and I couldn't do anything, since I didn't have a Windows CD around).

So 3 partitions, one for Windows install, one for Ubuntu install, and the third to store everything as an NTFS partition so that Windows and Ubuntu can access the same files? This would be a better setup than what I have now. I have a dual boot system where windows is 80gb but for Music I have to make a copy from the ubuntu partition to the Windows partition which is just a waste of space. I'm always struggling to make room on my Windows partition (I use it for games)

---

### Post by el_koraco on 2011-10-06
> **Legendary_Bibo said:**
> So 3 partitions, one for Windows install, one for Ubuntu install, and the third to store everything as an NTFS partition so that Windows and Ubuntu can access the same files? 

Yup, two primary ones for Windows and shared, one extended for / and swap. Dunno if you can install games to the second partition in Windows, I haven't played a game since Neverwinter Nights, but if you can, you don't need to keep the Windows partition big. The symlinking does the trick for Ubuntu's files, and the Explorer Libraries for Windows ones.

There's no noticable lag when accessing an NTFS partition for data in Linux, but you don't get file permisions and stuff (which is not important for data anyway). I'd say, the whole Ubuntu partition doesn't need to be bigger than 30 GB (and that's just to compensate for stuff you might want to install in $HOME, where permissions matter). 

My / partition is 10 GB, about 50 percent full, and i don't think the config files in /home take up more than a GB.

---

### Post by ninjaaron on 2011-10-06
> **el_koraco said:**
> My / partition is 10 GB, about 50 percent full, and i don't think the config files in /home take up more than a GB.

It's something like that, but it can be more or less, depending on what programs you're using.  Mozilla apps and LibreOffice store extensions in /home, so if you plan on using a lot of them, it can take more space.  Saves for some games can also take up a lot of space (I'm thinking especially of Battle for Wesnoth at the moment, but I'm sure others do as well).

If you really want to keep the Ubuntu partition to a minimum, you can make a folder with your dot files and folders inside of the data partition, and make a symbolic link to it /home/ (not ~), and then fill that will links to your data folders.

It's kinda nuts, but it's exactly what I do with my Ubuntu and Debian partitions, and it keeps them both at 3.4 of 5.4 GB partitions (without to many programs).  My main Arch system only takes up 4.5 of 9.2GB, and that's with LibreOffice, Gimp, Inkscape, ffmpeg and several other heavy programs (course, I don't have some large things like a DE that you normally have, but still, a large DE is only like 600MB... except KDE...).  Anyway, if your careful about system maintenance, remove unused programs, clear you package cache, etc., you can run a very slim system.  [s]You could theoretically even put some of your system folders in the data partition and link them (like /usr), to make your / partition positively tiny.  You should probably only do that with /usr, actually[/s]... doing it with /etc /var /bin /lib... that could potentially cause huge problems.

/usr is where all the big stuff is anyway.  I think I'm going to try that now with one of my "playground partitions."  I'll report back if anything gets jacked.

[edit]
On second thought, don't move /usr into your home folder and link it to /.  I just broke Debian.  Should be fixable, and there should even theoretically be possible to do what I did, but there might be a permissions problem.  Anyway mess with it at your own risk.  I have to go fix Debian.

---

### Post by ninjaaron on 2011-10-06
Yeah, so that thing I said about moving /usr.  Don't do that until further notice.  That was a bad idea.  Had I done that I my main system, I would be rather upset at the moment.

---

### Post by ninjaaron on 2011-10-06
*double post*

---

### Post by wolfen69 on 2011-10-06
> **el_koraco said:**
> No need for such actions. If you're dual booting with Windows, don't even make a separate /home, just back your desired config files. Make a shared NTFS partition for Linux and Windows, then install oneiric in a single partition, bring back your config files, edit fstab to mount the shared partition as /media or something. 

Delete all the Music, Video, Downloads and other folders in $HOME, recreate those folders on the media partition and symlink them to $HOME. It sounds like a lot of work, but the it's only editing fstab, symlinking is done easiest by slitting the pane in Nautilus, dragging the from the media partition with the middle button, and selecting "link here".  

That way your data will always be safe from both Linux and Windows going crazy. You can even resize the Windows system partition to some acceptable level (I have my mothers C:\ at 30 GB with no problems at all, the Libraries thing does everything else easy for her, even though Explorer is still a dreadful file manager, almost as bad as Nautilus). 

I'd also suggest you boot the Windows rescue CD, fix the MBR, make sure you can boot Windows, then during the new install put GRUB in /, and have BOOTMGR chain-loading to the GRUB in /. I'm saying this because I just came back from a rescue operation for a poorly made dual boot, where the sysadmin did some monkeying around with the partitions, so the original GRUB didn't want to boot anything, and the reinstalled one doesn't boot XP (and I couldn't do anything, since I didn't have a Windows CD around).

Too. Much. Work. I just have an extra hard drive in my machine for storage, then backed up again on an external drive. Done.

---

### Post by el_koraco on 2011-10-07
> **wolfen69 said:**
> Too. Much. Work.

Only the first time. Once you get used to that, I bet you can handle the whole process in five minutes.

---

### Post by CharlesA on 2011-10-07
> **el_koraco said:**
> Only the first time. Once you get used to that, I bet you can handle the whole process in five minutes.
Or just write a script to do it for you. :P

---

### Post by forrestcupp on 2011-10-07
> **el_koraco said:**
> Dunno if you can install games to the second partition in Windows, I haven't played a game since Neverwinter Nights, but if you can, you don't need to keep the Windows partition big.

A 2nd NTFS partition is just another drive letter in Windows. Most games will let you choose where to install them, so you could install them to the other partition easily. It's just that during an installation, most people just click Next->Next->Next->Finish without even looking at what things say. One of those Nexts usually lets you set where to install it to.

---

### Post by el_koraco on 2011-10-07
> **forrestcupp said:**
> Most games will let you choose where to install them, so you could install them to the other partition easily.

Yup, that's how I remember it. But I didn't play any games on Vista and don't have Windows 7, so I had no idea if that changed. If that's the case, Bibo's good to go, 30 GB for C:\, 10-30 for / and swap, and the rest for E:\ (/media). And he can reinstall both as much as he wants to.

---

