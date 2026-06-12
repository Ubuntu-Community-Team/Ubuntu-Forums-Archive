---
title: "experiment with btrfs-tools for long rollback"
date: 2013-06-08
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-06-08
My new experiment will be with btrfs-tools using the 'convert' tool.

Here is the pseudo:

Creat fresh install of Lucid Lynx on ext4. 40GB hdd

Convert to btrfs using btrfs-tools (which are in the Lucid repos).

Upgrade to 12.04 , install apt-btrfs-snapshot and then DO sudo apt-get install htop

Upgrade to 13.04 and or 13.10 Saucy.

If all is successful, roll back to the original 10.04 Lucid ext4  install using the btrfs-tools option. If all is still successful then 
theoretically those snapshots of Raring and Saucy  would still be on the disk.

*note* to moderators

This experiment may seem off topic but I think it is relevant to those who are beta testing dev releases or even new commers who want a solid option (other than standard backups) to rollback to a more stable state if there testing in the newer development releases becomes unstable (and/or could be used as a system recovery sequence).

---

### Post by ventrical on 2013-06-08
Major problems right off the bat. Although one can convert the Lucid system  to btrfs using Raring Live Session , it will not update in grub and the result is GRuB Rescue prompt. The Grub Rescue CD will not work either. However the converted file system can restored BACK to it's original, working state by simply  entering from terminal while in Raring Live Session:

```

sudo btrfs-convert -r /dev/sda1

```

therefore it boggles my mind how this rollback process can successfully roll back the original GRuB !!

I am going to re-try this using one of Grahammechanical's  method of creating a 1MB partion before the btrfs partition.

---

### Post by grahammechanical on 2013-06-08
Tricky. I am following in your footsteps. !0.04.4 does not have btrfs as an option. So, Ext4 has to be converted and the conversion process changes the partition UUID. so, fstab has to be edited. I am also thinking that things might go better if we had Grub 2.0 and not such an old Grub 1.99. It definitely hasn,t detected the two btrfs Ubuntu on this hard disk. Nothing unusual there! Although the upgrade to 12.04 should bring in Grub 2.0. I just have this feeling about Grub picking up a btrfs install when it is being installed. I am not so sure it can detect btrfs once Grub has been installed.

---

### Post by ventrical on 2013-06-08
There is an image file once the conversion process has taken place.  It will not compress and it will not move. The actual image file is as large as the original partition, 38 GB in my Lucid case. I am assuming then that the image snapshot is not of the system , but , rather a schema of the entire hdd making it almost impossible to paste a etx4.saved image file to another system.

 I think there is an actual bug with Grub (or conflict).

Otherwise .. onwards...

Thanks for your input. Always insightful to fall back on.

 I am going to try that 1MB partition now on the Lucid... hmmmm .. the wheels are spinning now ... It's like If I can make a snapshot of a Lucid install using apt-btrfs-snapshot in Raring .. but I got to get to Lucid first ... 

Regards,
Ventrical

---

### Post by grahammechanical on 2013-06-08
What is the point of a Grub rescue prompt if it cannot recognise the commands in its own Grub boot parameters! I have got the same grub rescue prompt as you have. I was unable to run grub-install from the live session. It said that autodetect could not recognise a module. I do definitely think the issue is with Grub on this. We should be able to boot to a partition from Grub rescue. It can be done from the grub command line at the Grub menu but the same commands do not get recognised at Grub rescue.

Richard Stallman is not my favourite person at the moment.

Would it not be simpler to just fresh install 12.04 over 10.04 rather than go to all this messing around just to roll back? :) :) 

If you can't take a joke, you shouldn't have joined.

Regards.

---

### Post by ventrical on 2013-06-08
:):)

I just got this little amazing script msg when I went to update grub from a raring Live USB. I converted the Lucid ext4 on sda2 to btrfs using the Live USB

```

Free inodes count wrong (2237603, counted=2237607).
Fix<y>? yes

/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda2: 138073/2375680 files (0.1% non-contiguous), 733556/9496064 blocks
ubuntu@ubuntu:~$ sudo btrfs-convert /dev/sda2
creating btrfs metadata.
creating ext2fs image file.
cleaning up system chunk.
conversion complete.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.
ubuntu@ubuntu:~$ 

```

cannonical path of /cow :)

That means Copy on Write which =s btrfs.

devs working fast in the background.

here goes reboot anyways.

---

### Post by ventrical on 2013-06-08
> **grahammechanical said:**
> 

Would it not be simpler to just fresh install 12.04 over 10.04 rather than go to all this messing around just to roll back? :) :) 

Regards.

Well .. yes of course .. but then there would be no fun :) err .. breakage ! :)

---

### Post by grahammechanical on 2013-06-08
I found this

[http://lists.gnu.org/archive/html/info-gnu/2011-05/msg00008.html](http://lists.gnu.org/archive/html/info-gnu/2011-05/msg00008.html)

Btrfs support first in Grub 1.99. I think that 10.04 has grub 1.98. Now if only I could boot into that 10.04 and install grub 1.99 or grub 2.0. I have been reading the grub manual. Grub rescue is for fixing Grub not for booting into an OS.

> 
Add `grub-probe' support for the btrfs filesystem, permitting / to  reside on btrfs as long as /boot is on a filesystem natively supported  by GRUB.

It is like snakes and ladders, with more snakes than ladders.

I might try grub-install from grub rescue. Or grub-probe. I try this on Monday.

---

### Post by ventrical on 2013-06-08
I went and loaded lilo from the repos .

What a complete disaster that was :)

aww .. you don't want to know...:)

---

### Post by ventrical on 2013-06-08
> **grahammechanical said:**
> 

It is like snakes and ladders, with more snakes than ladders.



I could not have said it better myself ! :) 

Have a great weekend.

---

### Post by grahammechanical on 2013-06-10
I decided to press restart on this experiment. Install 10.04+Ext4; set raring or precise CDs as a repository; install grub 2.0 and then do the conversion. I am stopped at installing Grub 2.0. I seem to have both precise and raring CDs as a repository in Synaptic but I am only offered Grub 1.98 which is already installed. I think that we will need at least Grub 1.99 or better still Grub 2.0 to have any chance of getting Grub to work with a btrfs Ubuntu of whatever vintage.

Back to the drawing board. What if I put a precise, quantal or raring install back in control of the MBR. Then do the conversion but not run update-grub or grub-install on the newly converted btrfs partition? That should at least get me a grub menu that will let me boot into 10.04+btrfs. May be. Fingers crossed. Then I can experiment with snapshots and rollbacks of a distribution upgrade from 10.04 to 12.04 as far forward as Ventrical  wants to push it.

Regards.

---

### Post by ventrical on 2013-06-10
> **grahammechanical said:**
> 

Back to the drawing board. What if I put a precise, quantal or raring install back in control of the MBR. Then do the conversion but not run update-grub or grub-install on the newly converted btrfs partition? That should at least get me a grub menu that will let me boot into 10.04+btrfs.

Regards.

I have surmised the same scenario. This could be the fix. My observations so far are that Lucid (10.04 raw)  once converted, will not boot  from GRuB  (or be recognized by GRuB after the conversion). So I have to ask this interim question; Why did they put the btrfs-tools (convert tool) in the Lucid repos?

 When I try to do the convert from Lucid it will give me a warning after entering"

fsck.ext4 -f /dev/sda#

 It warns that my system will be destroyed. However, I can do a fsck.ext4 from a Raring or Saucy Live USB .

 I am back to reset on this experiment.

edit: 

@grahammechanical
aahhhh .. yes .. I can see where your method can work here.!

---

### Post by ventrical on 2013-06-10
Before I try grahammechanicals method I just thought I would eliminate this possibility. I have an already loaded Lucid install on a 40GB hdd. That install has been converted using the btrfs-tolls <convert> tool. naturally I got the GRub Rescue prompt> on reboot.

  I stuck in a raring  USB live and here is the screen shot from where I will start from.

Theoretically the upgrade to raring will upgrade in the btrfs format making the install bootable and saving the saved.ext4 file that was created on the Lucid install when I evoked btrfs-convert  /dev/sda2

If raring installs successfully ( and also carried the saved .ext4 file over with it then I should  be able to roll back the whole upgrade to ext4 Lucid. However if systems settings will be 'cleared' then it may also clear  the btrfs format.

here goes !

---

### Post by ventrical on 2013-06-10
Upgrade was a success!!

```

ventrical@ventrical-P4M266A-8237:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring
ventrical@ventrical-P4M266A-8237:~$ 

```

so the raring upgrade from Lucid was able to  detect the btrfs filesystem.*note* that I had added a 1MB partition on the hdd before I did the Lucid install and that partition is still there.

 Now, I should be able to rollback to the Lucid install by using the 
```


sudo btrfs-convert -r /dev/sda2


```

 If this works  then it could be used as a sort of alternative ultimate backup system.

 I am sort of expecting that it will not work .. but .. here goes..

---

### Post by ventrical on 2013-06-10
Long Rollback a success!

The only extra thing that I had to do was use the Grub Rescue CD and <restore-grub> and I am now back in  the original Lucid install.

 This is very efficient because when I had upgraded to raring and then check my hdd diskspace there were only 3.2GBs used up (that would included the saved Lucid ext4.image file). However,currently, at this point I cannot rollup back to the raring install using any of the btrfs tools. I would have to upgrade manually or use the Live Raring USB

 In this phase of the experiment I have discovered that the btrfs-tools can be used as a hard back-up system for long rollback.

 If (a) end_user converts (b) Lucid system  to btrfs format THEN (c) upgrades to raring using Live USB, (a) can then use the btrfs convert -r option to roll back to Lucid ext4. The one caveat is that  GRub has to be restored using Grub Rescue CD (or other recommended methods).

Also, as a bonus, the conversion rollback remembers installed files.

```

ventrical@ventrical-desktop:~$ sudo apt-get install btrfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
btrfs-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 531 not upgraded.
ventrical@ventrical-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid
ventrical@ventrical-desktop:~$ 


```

---

### Post by ventrical on 2013-06-10
> **grahammechanical said:**
> 

Back to the drawing board. What if I put a precise, quantal or raring install back in control of the MBR.
Regards.


 I am going to try  natty to saucy with this proceedure. Thats where GRuB 1.99 first showed up. So it still at least has Unity 2D and is a little faster than Precise. I know it is no longer supported , but who says it has to be ? :)

btw .. just noting .. Lucid updated seamlessly. I thought those repos were closed.

Edit:

The natty 11.04 repos are closed so apt-btrfs-snapshot will not upgrade from the repos . However the btrfs format can be chosen from Ubiquity  with <something else> option

 Next test in this sequence: Convert Lucid Ext4 to btrfs. Load a bunch of pics and documents. Upgrade to Saucy. Use btrfs-convert -r to roll back to Lucid.

---

### Post by grahammechanical on 2013-06-10
I have just thought of a flaw in my cunning plan. The conversion process changes the partition's UUID. Does it not? So, a Grub menu from an Ext4 Ubuntu partition will still have the boot option for 10.04 but the boot will fail unless we edit Grub boot parameters to include the new UUID. Do not forget that we have already proved that we can do rollback from a live session and recovery mode. So, all is not lost.

I would like to somehow get grub 1.99 on to this 10.04 installation. I would also like Grub to be much improved but it is a rare thing for me to get what I want in life.

---

### Post by ventrical on 2013-06-11
Successful  rollback to Lucid from Saucy Salamander. While I was in saucy I installed apt-btrfs-snapshot and took a snapshot, then rolled back to ext4 Lucid. All files are in tact.

That would mean now, by using Saucy Live USB that I can switch back and forth between the two installs.  All I have to do now is convert the Lucid ext4 back to btrfs, load the Live saucy USB, install apt-btrfs-snapshot and then roll up to Saucy install without having to actually install it!

Edit:

  This did not work. The apt-btrfs-snapshot tool will not port out to the hdd path even when mounted and it is not supported (since the USB iso image is ext4. But it still may be possible if a USB Live CD were in btrfs format. 

 We'll see ... :)

---

### Post by grahammechanical on 2013-06-11
Now, you have got me imagining things. A live USB ISO image with pre-recorded snapshots of precise, quantal and raring as well as saucy. If the user does not like saucy they can roll the session back to one of the other snapshots and install that. Or am I day dreaming again. These snapshots only take up the space of the packages that are different. So, the ISO image would be larger but not by four distributions but by the size of the packages that are needed in addition to what is all ready there.

---

### Post by ventrical on 2013-06-11
Actually you are not daydreaming at all. It is sort of like a roll-o-dex snapshot library type concept bundled into one .iso. Yeah .. that would work. :) However, it will not work with Lucid, I presume, because there is a chasm between Lucid and  the 1.99GRuB that just cannot seem to be bridged at this stage of the game. So we would have to go with Precise mainly because the repos are open where as the 10.10, 11.04,11.10 repos are closed and this would cause a lot of breakage.

For soundess, Precise would be the starting point, however, Lucid can be used as a solid btrfs-tools/convert back-up development backup system as long as the Lucid repos remain open. Thats questionable. So Precise would have to be the default starting point. It would depend on how far on the edge a particular tester would want to be ! :) Play is safe and go with the flow or push  Ubuntu and your hardware  beyond it's recommended specifications while courting maximum breakage but, also discovery of hidden Ubuntu treasure. :) One of the hidden treasures I have found is that I can roll back to a stable Lucid install  with the btrfs-tools/convert option from the most current development release (saucy) without any breakage .

---

### Post by grahammechanical on 2013-06-11
I could see a use for this. Supposing the devs asked us to test the 3.9 or 3.10 kernel on raring or precise. We would not need to specially install raring and precise just to run that test. We could take an existing saucy install and roll it back to raring and then to precise and run the test each time and then roll forward to saucy again. That would be useful on a machine with limited hard disk space.

---

### Post by ventrical on 2013-06-11
Exactly. Less downtime. If anything goes south (breakage) then there is always the failsafe of rolling back to  the stable release with btrfs-convert -r. Either way it works.

  I'll try that with a 40GB hdd starting at Precise.

edit:

Of course ... keeping in mind what Chris Halse Rogers wrote to me:

> 
Right - *when it works* it's super-awesome. And most of the time it *will*  work. But as soon as Saucy gets a version of a package you use with a  new data format - such as Shotwell, which is bumping the database schema  in the next release - rolling back to Raring will mean you won't be  able to access your Shotwell database.
  This is not to discourage you from using it. Merely to point out that  there are significant pitfalls you can fall into, and they may not  necessarily be obvious.


---

### Post by ventrical on 2013-06-11
Precise LTS iso really balked at pre-existing btrfs format. It reported that it could not restore some system files. apt-btrfs-snapshot broke on it as I forced it through  on that btrfs convert. I'll try another full 40GB hdd and use <nomodeset> as it seems Precise is still very pernikety about video drivers on some machines.

 Through all of todays testing I could not help notice that Raring final  and Saucy (week old daily) are far superior to Precise final.

btw .. through all of this the  btrfs-convert -r ext2.saved image survived unscathed.

interesting ..

---

### Post by grahammechanical on 2013-06-11
Well, it has got me beat. I did the conversion, edited fstab with the new UUID and edited the grub menu (controlled by another install of precise) with the new UUID but I get busybox. It is still looking for the old UUID.

I think I will now try putting precise+btrfs on a USB stick and upgrade through to raring taking snapshots all the time. As regards the comment by Chris Rogers, the idea is to roll back to raring if the user has a broken upgrade or dislikes the new Ubuntu. It is not intended that the user puts in heavy use of the new Ubuntu and then after months decides to roll back. 

Here is a thought. If, for example, Shotwell starts using a different database format (as has been hinted at) then an upgrade from raring to saucy will have to include a conversion process. A fresh install would require the photographs to be reloaded into the upgraded Shotwell. This stuff happens already. I have to import my music files into Rhythmbox every new install I put in. For all I know, Rythmbox may have changed database formats. True, a roll back would roll back to an earlier Shotwell with its earlier database format but I would expect that importing the image files again would sort it out.

It is in this area that practical experimentation has the advantage over theory.

---

### Post by ventrical on 2013-06-11
> **grahammechanical said:**
> 

It is in this area that practical experimentation has the advantage over theory.

 I intend to keep working away at it. The fact that the ext2.saved image survives terrible breakage has captured my interest. It makes recovery in some cases , not so cumbersome and difficult. Also , the  set-default option in apt-btrfs-snapshot seems to go above and beyond the chances of broken depends. So, basically , the art of recovering broken Ubuntu installs can be streamlined and explained with language that the layman can understand.


 There is also the potential to streamline  and inject new backup concepts and end_users  who would normally stray from backups may feel more inclined to take up the roll-back , roll-up method  as which we have proved out.

  regards...

---

### Post by ventrical on 2013-06-11
Installed Precise on a pre-existing btrfs. Created two snapshots of the Precise install.Removed apt-btrfs-snapshot. Upgraded to Raring. This presented major breakage. No Unity etc...I was able to install fvwm-crystal desktop from terminal, then synaptic. Reboot and choose fvwm-crystal window manager. Then synaptic and  just keep reloading, marking and <apply>ing and the broken packages will fix. Then, reinstall apt-btrfs-snapshot.

I chose:

sudo apt-get install mc (midnight commander) to create my snapshot in raring. I am now about to attempt to rollback to Precise. I haven't tried this one yet. Precise is a horse of a different color in all of this btrfs rollback. I am not sure it will work .. here goes ..


*edit*

Failed. Grub Rescue> Recovery disk will not recognize the partitions. All the snapshots are still there .. but no way I can get them to load  up in GRuB. I think having a working btrfs USB is about the only way to do this right now. Will try that in a bit .

break  :)

---

### Post by Mark_in_Hollywood on 2013-08-08
Not Off-Topic and not On-Topic.

I have installed btfrs. On re-boot from btfrs format, my 2 partitions / and /home cause btfrs to ask for (I)gnore (S)kip or (M)anually Mount. If (I)gnore is selected, / and /home mount and OS works pretty much as normal until I try to shutdown, which the OS cannot/willnot do. Diskutility app shows partitions as unmounted, while they are in operation. (/dev/sda1 and /dev/sda3) - All Ubuntu.

I am in the habit of closing all open programs before shutdown. Shutdown is accomplished by depressing power switch until the power goes down. This is the third day in a row and would like some help with shutdown. Then onto the strange mount/unmount idea.

---

### Post by grahammechanical on 2013-08-09
I do not get that on btrfs and I have several installs of Ubuntu+flavours on btrfs. I got that notification during the Raring development cycle when I used Disks utility to edit mount options and set a partition to mount on startup. Removing the option removed the message. It seems that Disks utility was not up to the task. I notice that on Saucy Salamander (13.10) Disks utility is showing my partitions as Mount on startup and I do not see the problem.

Regards.

---

