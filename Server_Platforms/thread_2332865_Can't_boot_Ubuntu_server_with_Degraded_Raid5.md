---
title: "Can't boot Ubuntu server with Degraded Raid5"
date: 2016-08-04
forum: Server Platforms
---

### Post by jeremy4 on 2016-08-04
Hello I need some help on this one.  First off, Ubuntu server is NOT installed on my RAID5 array, It is on a separate stand-alone disk.  I rebooted my server remotely from work today via SSH and it didn't come back up.  When I got home and plugged a monitor into the server I see the following message indicating one of the 4 disks in my RAID5 array has failed and the array is degraded.  The problem I have is that I am unable to answer "Y" to go ahead and start the degraded array, so my system won't boot!   I need to boot normally so I can see which disk has failed in the array and get a replacement ordered ASAP.  I have tried reboot several times but when I get the message: 

If you abort now, you will be provided with a recovery shell.
Do you wish to start the degraded array? [y/N]:
a

it refuses to take any keyboard input from me and default to N and drops me to the recovery shell.  I tried switching to a wired USB Keyboard but still nothing.  How can I get back into my system to run the MDAM commands neccessary to find my failed drive?  Any help is extremely appreciated.  I would also like to start the degraded array so I can back up a few files, just to be safe until my replacement for the failed drive gets here.

---

### Post by jeremy4 on 2016-08-04
I have read some other threads on this issue online and it appears to be an Ubuntu issue.  I have tried hitting "e" at the grub boot menu and adding the kernel flag "bootdegraded=true" but I still get dumped to the recovery prompt.  What is the point of it asking if I want to start the degraded array if it's just going to ignore the input?    I just found this bug report on the issue:  [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/872220](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/872220).  Does anybody have a valid work around?  I need to get back into this system.  Very frustrating.

---

### Post by darkod on 2016-08-05
I would recommend getting the desktop iso and making live cd or usb with it. Then boot the server in live mode (Try Ubuntu).

Then you have few options...

1. If you want to find out the failed disk ASAP, open terminal, assemble the array and check its details. Don't forget that usually mdadm is not included on the live cd (not sure about 16.04, earlier it was like this) and you need to add it first. So it would be something like:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
sudo mdadm -D /dev/md0   (assuming your array is md0)
```

That will give you the failed member.

2. If you want to try changing the mdadm degraded boot option you can also try with chroot. You can chroot into the server installation from live mode and try something like:
```
sudo dpkg-reconfigure mdadm   (that will show you the options to reconfigure)
sudo update-initramfs -u   (usually you need to update the initramfs after this change)
```

Reboot and let it boot the server OS and see how it goes. If you don't know how to chroot you can google it, it's quite easy and common. Or ask for help if needed.

---

### Post by jeremy4 on 2016-08-05
> **darkod said:**
> I would recommend getting the desktop iso and making live cd or usb with it. Then boot the server in live mode (Try Ubuntu).

Then you have few options...

1. If you want to find out the failed disk ASAP, open terminal, assemble the array and check its details. Don't forget that usually mdadm is not included on the live cd (not sure about 16.04, earlier it was like this) and you need to add it first. So it would be something like:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
sudo mdadm -D /dev/md0   (assuming your array is md0)
```

That will give you the failed member.

2. If you want to try changing the mdadm degraded boot option you can also try with chroot. You can chroot into the server installation from live mode and try something like:
```
sudo dpkg-reconfigure mdadm   (that will show you the options to reconfigure)
sudo update-initramfs -u   (usually you need to update the initramfs after this change)
```

Reboot and let it boot the server OS and see how it goes. If you don't know how to chroot you can google it, it's quite easy and common. Or ask for help if needed.

Thanks!  I will give this a shot tonight.  Yes, I have used chroot before to fix one of my Linux Mint installations.    Do I run the risk of breaking my array by using dpkg-reconfigure mdadm?    The first option might be my best option if so.  It is just kind of annoying that something that is not related to the boot drive for the OS will keep a server from booting.  I'm guessing this might be fixed in the newer Ubuntu server releases.  When I get everything back online it may be time to back data and upgrade the server to the latest LTS.

---

### Post by darkod on 2016-08-05
The reconfigure does not touch the arrays, so it should not put your data in danger. Basically it only asks you again the few questions as if installing mdadm the first time (the most important question being whether you want to boot degraded).

---

### Post by jeremy4 on 2016-08-17
Ok, well it took over a week for my replacement HDD to get delivered.  I think they had some guy ride it down to me from Canada on a Vespa scooter or something. :)

Anyway, I am still fighting the fight here.  I had Linux Mint 18  disc due to a recent laptop installation, so I used that to boot the server from that Live CD.  I then installed mdadm , assembled the array and located the failed disk (it had already been forgotten by mdadm).  I powered down the server after verifying the failed disks S/N via GPARTED (to ensure I physically swapped out the correct disk), and then I replaced the failed drive.

Booted the server back up, and used sfdisk -d command to copy the partion layout/disk info from one of the good RAID HDDs to the new HDD.  Then I re-assembled the degraded array with the 3 good drives.  Next, I added the partition from my newly installed/replaced disk to the md0 array.

cat /proc/mdstat   command showed the array recovery start.   

Issued  watch cat proc/mdstat  to monitor the rebuild and walked away.  

Several hours later I came back and recover was at about 63%.  Checked a few hours later after the screen had gone to sleep again, but this time when the screen came back, it was frozen at the lock screen!  I had to hard power the server off.  Rebooted from the Mint Live CD again, and two disks now showed missing from the array.  sdc1 was now showing as failed & sdb1 (the replacement drive) was now showing up as a spare.  I managed to re-assemble the array using

```
sudo mdadm --assemble /dev/md0 /dev/sd[cde]1 --force
```

After forcing the assemble, the degraded array came back online and I was able to access the data.   I turned off ALL of the power saving features on the running Mint Live system this time and  added the new disk sdb1 back to the array.  mdadm recovery process again started successfully.  

I get up and check it before work this morning and sc1 has dropped out of the array again!  

I guess I will force assemble the degraded array again with sdc1, sdd1, & sde1 and try to back  up as much data as I can.   I don't like having to try to recover the array from a Live CD but it appears I don't have much choice as the Ubuntu Server bug still won't allow me to boot from the local OS because of the degraded array! 

So back to option 2...........chroot

Apparently when I set up my server I used LVM.  That is causing me problems........I can chroot into the first partition on my OS disk (which must be /boot because /bin doesn't exist there). 

Attemping to run "dpkg-reconfigure mdadm" returns all kinds of permission denied errors.........

I was able to finally chroot into the correct /root  partition, but I still get the permission denied errors when trying to run "dpkg-re-configure mdadm".  

I there something else I should be doing via chroot?  Shouldn't i have to bind /sys & /proc or something?

---

### Post by jeremy4 on 2016-08-18
Well I finally figured out how to chroot into my root installation on the Logical Volume.  I tried the suggested:

```

sudo dkpg-reconfigure mdadm
sudo update-initramfs -u
```

However, after rebooting I am STILL prompted and asked if I want to start the degraded array, and dumped to the initramfs recovery shell!  At this point I don't know what to do. I have not been this frustrated with a computer issue in I don't know how long.  This Ubuntu server bug is basically holding my system hostage.    How can I stop Ubuntu from trying to start the array when the system boots, so that I can manually start it after a successful boot?   The most infuriating part about this is not that the bug exists, but that even after using chroot to get into my root partition and re-configuring mdadm to start the array even if it is degraded, Ubuntu servers boot sequence still ignores that and prompts me.  Any help is appreciated.  I do not want a catastropic failure....I have a good new disk installed that I can't get synced back into the array because I can't boot into the freaking OS!

---

### Post by darkod on 2016-08-18
Well, you said you know how to chroot into the installation so we never discussed it. Of course you need to make sure you chroot the correct way (whether its normal root partition, mdadm array, LVM volume, etc).

I'm sorry to hear of all the issues it's giving you.

I also don't like that the system was powered off during a rebuild, you have to be very careful about that when doing raid rebuilds because the new disk is not a full member of the array until the process has finished. It was probably best to leave it running, lock screen or no lock screen, especially if the HDD activity light was showing intensive activity (on all the time). That shows the rebuilding is taking place. When the light goes back to normal, you can assume it finished.

Anyway...

About disabling the array you should be able to do it this way: chroot again into the installation and open /etc/mdadm/mdadm.conf. In there comment out the ARRAY definition of the corresponding array. Save the changes and try rebooting the server OS. As far as I know mdadm uses that definition to assemble arrays on boot. If you comment it out it shouldn't try to assemble it on boot.

Once the server OS has booted you can work from it. I assume you know that commenting out means putting # at the front of the line. :)

Try that...

And one more thing. You say you are forcing now assemble with all three disks but I think you should work only with two of the old disks. As I said, until the rebuild process finishes the third disk is not a full member yet (that's why it was shown as spare I think, after the power off) so basically you are still assembling with 2/3 members and adding the third after that.

And whether the power off did some damage (maybe by dropping another disk) is yet to be seen. You had two good members and it was "easy" to rebuild this raid5 array. Try not to lose another of the good disks otherwise then you are in bigger trouble...

---

### Post by Graham_Willis on 2016-08-18
Have you tried the thread [https://ubuntuforums.org/showthread.php?t=1972690](https://ubuntuforums.org/showthread.php?t=1972690) ?

I haven't read in the details, so I don't know how much it's related to your situation, but it seems that it might help.
But - wouldn't be it simpler and safer to replace the OS disk with a disk with OS which is known for not having such issues, then grab the data?

---

### Post by jeremy4 on 2016-08-18
So this RAID 5 array is a 4 disk array, so I am working 3 of the 4 disks.  The 4th is the disk that was replaced.

I just did the chroot into the system and edited the /etc/mdadm/mdadm.conf array definition and rebooted the server.........and it still hangs on trying to assemble the array.  Since it is affordable now, I have ordered an external 5 TB HDD to back all of my data up to as soon as I can get the array  assembled and mounted again.  I really do not need to lose data so I am being careful.  I guess I can try to re-assemble from the Live CD after installing MDADM there and assembling the array.   Thanks for all of the suggestions.  This is a nasty, nasty bug.

---

### Post by darkod on 2016-08-18
Is your keyboard working at all, on start of boot in the grub menu? If it does what you could try is to boot the recovery mode entry and drop to root shell. That way you should be able to rebuild the array (from recovery mode) and not worry about live cd going into power save.

That is another option to access the system. Now you know the options more or less available, it's up to you how you continue...

---

### Post by jeremy4 on 2016-08-18
Array has been re-assembled and is trying to recover now.  Going to wait it out and see if I can get disk 4 back online and a healthy array.  If that completes successfully.  I'm just going to leave the server running on the Live CD until my external HDD gets in tomorrow.  Then I will back up all data.  

I am thinking once the data has been backed up, I may just blow away current server installation and do a fresh install of the latest Ubuntu server LTS.  If all 4 disks in my RAID are good again, I should be able to install mdadm on the new server OS installation and re-assemble the array  there, correct?

---

### Post by jeremy4 on 2016-08-18
Well crap..........20% into the recovery sdc1 (one of the good disks) drops out of the array.........

---

### Post by darkod on 2016-08-18
Unfortunately that is a real danger with raid5. It only tolerates single member failure and if all disks were bought together and one fails, there is big probability that during the rebuild another member can fail. In such case you are left with 2 members missing, and in real trouble...

That's why it's much better to use raid6 or raidz2 which tolerate 2 failures, and also to have hot spares that kick in automatically... But of course, in home environment we rarely have the option to do that...

---

### Post by jeremy4 on 2016-08-18
Yeah, that's also the reason I don't have a backup of the data currently...........couldn't afford the storage space...........at least with the RAID5 more that one disk has to fail at the same time, so much better than storing data just on a single disk.  Right now I have a ddrescue running to clone the data from the sdc drive that keeps trying to fail during the array rebuild over to the new disk sdb.  if all goes well on that I should have 3 good disks again in a degraded array when all is said and done (3 out of 4 members).  I can remove the sdc disk from the system then.  Next task is to assemble the array with sdb1, sdd1, & sde1.  Then I can mount it and start copying data off of it to the external drive.    I have never had too many issues myself over the years, but have really come to dislike mechanical HDDs. :)

---

### Post by darkod on 2016-08-18
I know it can't help you much right now, but the amount of problems you are having got me interested to do some testing in VirtualBox. I will post results when I finish (probably over the weekend). Not just for you, but also for anyone that might stumble upon this thread in a google search in the future.

Which OS version are you using exactly? One of the 14.04.x releases or what?

---

### Post by darkod on 2016-08-20
Actually I was not able to reproduce your problems in VBox. I tried both 16.04.1 and 14.04.3:

1. Create new VM with single 8GB disk and install ubuntu server.
2. Power down and add three 4GB disks. Create one raid5 array from them.
3. Create a test file on the array.
4. Power down and remove the first raid disk.
5. Power on, and the system booted as normal (without the raid).
6. Interestingly enough, the raid did not assemble on boot with 2/3 disks. Both disks were marked as spare.
7. But that was easy to solve by stopping the array and doing the --assemble --scan.
8. The test file was still there, intact and readable.

So, in both cases the OS was on a separate disk, and booted normally with the raid in degraded state... It did not stop the boot.

Which version are you running exactly? Ubuntu Server, right? I hope it's one of the LTS versions because that's what you should be running on a server...

The bug you linked in one of your first posts does not seem to be resolved yet, but that was reported in 2012 and maybe in later versions of ubuntu they got it resolved but it still remained as unresolved in ubuntu 11.x. I could not see the same behavior in 14.04.3 and 16.04.1.

---

### Post by jeremy4 on 2016-08-20
Sorry for the delayed reply.  I have working to try and recover data without success.  It is definitely a LTS release of Ubuntu Server.  Is the there a way to check this from the Busybox recover console prompt?  I know it is not any newer than 14.04.  Possibly 12.04? (was that the LTS release before that?).  I'm not sure if I'll be able to recover my data.  When that second drive started going I think I'm kind of out of luck.  I now learn that RAID 5 is "not recommended" for large SATA disks.  Apparently, disk sizes have grown substantially over the last several years, but URE (Uncorrected Read Errors) have not improved at the same rate.  I'm still trying to do a sector by sector copy of my second failing disk to the new disk I was trying to install to replace the first disk that failed in the array.  It doesn't look promising as gddrescue hung up after running overnight, and I can't get Clonezilla to even start the clone (gives some Blockppart error).  I think I just got super unlucky here.  Western Digital has moved a little lower on my list, as these were all WD drives in the array.  The worst part is that the second disk that is failing is only maybe a year old and was the one I replaced a previous failed disk with.   As far as Linux mdadm software RAID goes, I still think it is excellent!  It did everything it was supposed to do.  Hard disk hardware failure is still a real problem, and the bad thing is there is really no warning of when a drive is going to fail (if you are lucky you will start getting smart errors).   Thank you for your assistance and advice.  I'm not giving up yet, but my data is most likely gone.  I'm building a server with RAID for a friend soon, and we will not be doing RAID5 there.  Going to go RAID 6 there.  I'm also going to recommend that he get drives from different manufacturers to ensure the drives don't come from the same batch!

---

### Post by jeremy4 on 2016-08-20
I am back with some good news. After one last trying, propping the failing HDD at an angle on top of a screwdriver (lol), was able to use ddrescue to do a sector by sector copy of the failing hard disk to the new good disk.  I was then able to assemble the array via installing mdadm from the live disc.   I'm using rsync to copy some files off to a new 5 TB external HDD now.  

Quick question.   I have a folder that is missing now that I had previously tried to copy when I was able to mount the array for a short time before.  I want to run a file system check on the md0 array to clean up any issues with the partition.  I currently have 3 stable working drives out of the 4, so I'm working off a degraded array.  The goal at this point is to pull most data off the array, and then unmount it and run fsck on it to see if I can get that missing folder to show up again.  The array is still showing the correct tb used, I'm just not seeing that folder.  I want to make sure I do the fsck correctly on the array.  All drives in my array ext4 formatted.  Crossing fingers that I make it out of this one with most if not all data.

---

### Post by darkod on 2016-08-20
Well, once you have copied (and verified) all the data you can right now, there is no real danger trying to run fsck and get more data out of it. Like you said, unmount it and run sudo fsck /dev/md0 on it. I think that should be enough and it would ask you to correct any errors it finds. Or if you prefer to say yes in advance, there are switches to use with fsck but I don't know them from the top of my head...

---

