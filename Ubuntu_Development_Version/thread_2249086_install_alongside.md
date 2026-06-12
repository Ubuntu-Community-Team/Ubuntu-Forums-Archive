---
title: "install alongside"
date: 2014-10-19
forum: Ubuntu Development Version
---

### Post by sudodus on 2014-10-19
The 'install alongside' test case:

Installing from a USB pendrive to another USB drive does not work. I remember doing such installations many times before, but maybe I have been using 'Something else'. I think this is another indication, that the option 'Install alongside' is buggy and risky.

See this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1382991](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1382991)

and the corresponding entry in the qa-tracker

[http://iso.qa.ubuntu.com/qatracker/milestones/325/builds/82012/testcases/1301/results](http://iso.qa.ubuntu.com/qatracker/milestones/325/builds/82012/testcases/1301/results)

Passed or failed? I think 14.10 passes, but 'Install alongside' should be removed, because it has created and still creates too much problems.

Should we consider this test case a success or failure?

---

### Post by Elfy on 2014-10-19
I'd expect that to be marked as a Fail with the bug in the critical bug box :) 

You can edit that :)

---

### Post by sudodus on 2014-10-19
Ok

---

### Post by kansasnoob on 2014-10-19
I have a dumb question of sorts. Ever since the ubiquity redesign during the Maverick dev cycle there is no longer a separate option to "use the largest continuous free space". It's just sort of jammed into the "install alongside" option with the only difference being that the button in the lower right hand corner of the screen says "continue" if you're going to be offered the option of resizing an existing partition, but if adequate free space exists the button with say "install now".

So my dumb question is, did that button say Continue or Install Now?

---

### Post by sudodus on 2014-10-20
> **kansasnoob said:**
> I have a dumb question of sorts. Ever since the ubiquity redesign during the Maverick dev cycle there is no longer a separate option to "use the largest continuous free space". It's just sort of jammed into the "install alongside" option with the only difference being that the button in the lower right hand corner of the screen says "continue" if you're going to be offered the option of resizing an existing partition, but if adequate free space exists the button with say "install now".

So my dumb question is, did that button say Continue or Install Now?

I don't remember, but I can check later today ... 

***Edit***: Indeed, it does say 'Install Now', so obviously it finds empty space on the live drive (behind the image of the iso file) and tries to install Lubuntu there. So it seems that the tests cannot see, which is the live drive, and exclude it from the possible targets.

---

### Post by sudodus on 2014-10-20
I was asked to remove the red bug from the testing tracker and it was classified 'opinion' at Launchpad. And I was asked to test with an internal drive as target instead of a USB drive.

I do not trust the option 'Install alongside'. Right now I have no suitable internal drive for testing what might overwrite the drive. So I can remove my test report, but I cannot change the test case to use an internal drive for dual boot. Maybe someone else can do that. Or the testcase will remain undone for Lubuntu.

---

### Post by vasa1 on 2014-10-20
I've been using install alongside from 11.04 onwards. I have a Windows 7 partition that I wish to retain "just in case". My laptop has the "old" BIOS and not UEFI.

It's not clear what hardware and operating systems are affected. Is it systems with UEFI? Systems with Windows 8? I asked this some months before in a similar UF thread on this issue.

My laptop is 64-bit.

Removing "install alongside" will make using Linux a lot more difficult for people who would not want to switch over entirely.

---

### Post by sudodus on 2014-10-20
I see your point, *vasa1*. A good and reliable 'Install alongside' option in Ubiquity would be very helpful, particularly for people who try Ubuntu for the first time.

The major bug of 'Install alongside' is being squashed. I think it affected UEFI installations, maybe also some other cases according to the Ubuntu Forums threads I have read and the Launchpad bug report(s). I think the worst scenario was that Windows was there but not detected (by Ubiquity).

But the 'Install alongside' option has other peculiar properties, and may create a false peace of mind, when people try dual boot, even when the 'major bug' is definitely squashed. This particular case (described in my opening post) is not dangerous, it only tries to install into the live drive. But there are other problems with systems containing more than one drive (in the standard case more than one internal hard disk drive). I think these problems are not related to the 'major bug'.

---

### Post by ventrical on 2014-10-20
In the past week I have done 3 successful "install alongside"s to hdds witn ubuntu-desktop next and xubuntu (but not with Lubuntu yet) [I did with ltrusty and it worked fine]. It has worked just fine this cycle. I have not tired the 'alongside' option to a USB with an ISO already on it.

---

### Post by sudodus on 2014-10-20
I think it can work in standard configurations:

[FONT=courier new]+ [/FONT]Boot from DVD and install to an internal HDD
[FONT=courier new]+ [/FONT]Boot from USB made with Startup Disk Creator or Unetbootin, so that the FAT32 partition fills the whole drive and install to an internal HDD
[FONT=courier new]- [/FONT]Maybe the problem is that I made my USB boot drive with mkusb (or actually cloned the iso file with dd). Ubiquity's 'install alongside' was not made for this scenario, and cannot manage it.

Kansasnoob identified the problem: Ubiquity finds some unallocated space in the boot drive (behind the image of the iso file), and tries to install Lubuntu to that space (but fails). I had expected to be offered to shrink the ext4 partition on what I consider the target drive (the other and bigger USB drive), not to try to install into the live drive.

---

### Post by kansasnoob on 2014-10-20
Prior to Colin Watson adding that new warning dialog just a few days ago you wouldn't even have known that Lubuntu was going to be installed in the incorrect place so there is at least a minor improvement in that regard. But not clearly defining the difference between "auto-resize" and "use largest continuous free space" is IMO a serious design flaw. I've argued that since Maverick to no avail.

---

### Post by jerrylamos on 2014-10-20
In this testing forum I use multiple partitions on two drives on four test pc's,  
I have windows7 on two of them that I do not want touched, certainly not by buggy grub.  Over the years grub has caused me lots of grief..
I use gparted to set up the partitions and I know what iso I want on which partition.
I'm not interested in having install sprinkle around the various levels of utopic and tahr and debian.

So I'm happy to let you people test all the other options - I stick with "something else".

BTW, having good luck lately with Ventrical's post in the sticky "Commonly used" thread:> Download the ISO
Insert your USB stick in the knowledge that it&#8217;s going to get wiped
Open the &#8220;Disks&#8221; application
Choose your USB stick and click on the cog icon on the righthand side
Choose &#8220;Restore Disk Image&#8221;
Browse to and select the ISO you downloaded in #1
Click &#8220;Start restoring&#8221;
Wait
Boot and select &#8220;Try Ubuntu&#8230;.&#8221;
Done *
I do mostly boot the iso directly from hard drive, faster than usb.  The usb stick is useful when getting close to release and actually wanting to install the same level on more than one pc.

---

### Post by sudodus on 2014-10-21
> **jerrylamos said:**
> In this testing forum I use multiple partitions on two drives on four test pc's,  
I have windows7 on two of them that I do not want touched, certainly not  by buggy grub.  Over the years grub has caused me lots of grief..
I use gparted to set up the partitions and I know what iso I want on which partition.
I'm not interested in having install sprinkle around the various levels of utopic and tahr and debian.

So I'm happy to let you people test all the other options - I stick with "something else".

I wish I had done that too, and avoided a lot of bad feelings.
> 
BTW, having good luck lately with Ventrical's post in the sticky "Commonly used" thread:[quote]Download the ISO
Insert your USB stick in the knowledge that it&#8217;s going to get wiped
Open the &#8220;Disks&#8221; application
Choose your USB stick and click on the cog icon on the righthand side
Choose &#8220;Restore Disk Image&#8221;
Browse to and select the ISO you downloaded in #1
Click &#8220;Start restoring&#8221;
Wait
Boot and select &#8220;Try Ubuntu&#8230;.&#8221;
Done *
I do mostly boot the iso directly from hard drive, faster than usb.  The  usb stick is useful when getting close to release and actually wanting  to install the same level on more than one pc.[/QUOTE]

Interesting! Do you know if this tool uses dd or some more advanced thing like zsync?

---

### Post by sudodus on 2014-10-21
> **kansasnoob said:**
> Prior to Colin Watson adding that new warning dialog just a few days ago you wouldn't even have known that Lubuntu was going to be installed in the incorrect place so there is at least a minor improvement in that regard. But not clearly defining the difference between "auto-resize" and "use largest continuous free space" is IMO a serious design flaw. I've argued that since Maverick to no avail.

I can't rely on "Install alongside", but it is obvious to me that this option is very popular, and most of us want to keep it to make things simple for newcomers.

---

### Post by ventrical on 2014-10-21
> **sudodus said:**
> I can't rely on "Install alongside", but it is obvious to me that this option is very popular, and most of us want to keep it to make things simple for newcomers.

 I have such a surplus of hdds that actually it could be called a "hoard"! :) Currently I have 9 desktops (towers) surrounding me in my "ubuntu-shack". Plus 3 other towers that alternate and three laptops.

  I am always swapping drives. Bricking an hdd or mobo doesn't worry me.

 "Install alongside" is always very useful when I am experimenting with xubuntu and all the flavours. I just want to test the installability of that daily image and I haven't got time to do commit, at that very moment, to a solitary install.

  When I am ready to dispose of one install for the next 'daily' I use jerryalamos's method and choose "something else". I only had one fail and that was with UEIF but I had learned how to overcome that.

  Lubuntu has also worked well with Install Alongside and I think I will test that thismorning.

Whoops .. gotta go.Edit .. had to do a wake up call :)

---

### Post by kansasnoob on 2014-10-21
It's hard to find Fix Released bugs :(

But I wanted to provide some history on this so:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

As you can see there I fought and only partially won - that's when they changed the UI so the button in the lower right hand corner changes from Continue to Install Now. I hope I can find another old report that's very relevant to that, one where Colin Watson even said it needs to be changed but the design team won't allow it.

BTW if you wonder why Colin Watson finally fixed [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192") it's because I threw a fit like a petulant child beginning here:

[https://lists.launchpad.net/ubuntugnome-qa/msg00559.html](https://lists.launchpad.net/ubuntugnome-qa/msg00559.html)

Shortly thereafter things went PM and I won't share the contents of PM's because they are by definition "private mail" but I've acquired a number of battle scars fighting with devs since the redesign of ubiquity during the Maverick dev cycle. I'm getting old and tired of fighting though ](*,)

---

### Post by kansasnoob on 2014-10-21
More history here:

[http://ubuntuforums.org/showthread.php?t=1825662](http://ubuntuforums.org/showthread.php?t=1825662)

---

### Post by ventrical on 2014-10-21
> **jerrylamos said:**
> In this testing forum I use multiple partitions on two drives on four test pc's,  
I have windows7 on two of them that I do not want touched, certainly not by buggy grub.  Over the years grub has caused me lots of grief..
I use gparted to set up the partitions and I know what iso I want on which partition.
I'm not interested in having install sprinkle around the various levels of utopic and tahr and debian.

So I'm happy to let you people test all the other options - I stick with "something else".

BTW, having good luck lately with Ventrical's post in the sticky "Commonly used" thread:
I do mostly boot the iso directly from hard drive, faster than usb.  The usb stick is useful when getting close to release and actually wanting to install the same level on more than one pc.

I have had the same problems with Windows 8, UEFI or no UEIF. However , with no UEFI I am able to use Grub Rescue to restore my bumped Windows 8 bootloader.  ( I used Lubuntu .iso to do a side by side on an E-machine but all the flavours do this) and if I use "something else" to replace an exiting install grub will bork it again and I will have to use Grub rescue again to get the dual boot. It's real downtime in the true sense of the word.

  Grub rescue CD does a really good job of fixing these borked bootloaders but it is still less efficient than the direct '.iso off the hdd' method that you are using.

Regards..

Addon:

Note : I have had success with "Install alongside" with Windows 7 but not Windows 8.

---

### Post by ventrical on 2014-10-21
> **kansasnoob said:**
> It's hard to find Fix Released bugs :(

But I wanted to provide some history on this so:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

As you can see there I fought and only partially won - that's when they changed the UI so the button in the lower right hand corner changes from Continue to Install Now. I hope I can find another old report that's very relevant to that, one where Colin Watson even said it needs to be changed but the design team won't allow it.

BTW if you wonder why Colin Watson finally fixed [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192") it's because I threw a fit like a petulant child beginning here:

[https://lists.launchpad.net/ubuntugnome-qa/msg00559.html](https://lists.launchpad.net/ubuntugnome-qa/msg00559.html)

Shortly thereafter things went PM and I won't share the contents of PM's because they are by definition "private mail" but I've acquired a number of battle scars fighting with devs since the redesign of ubiquity during the Maverick dev cycle. I'm getting old and tired of fighting though ](*,)

 I don't get it because  have had nothing but success with my last three "Install alongside" Ubuntu/xubuntu Beta2s.

edit >
 Only bug I have had is with Windows 8 bootloader.

---

### Post by kansasnoob on 2014-10-21
Here's an unrelated one regarding replacing the add & delete buttons with + and - icons:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

I lost there even though + and - clearly do not always = add or remove. They can also mean increase or decrease! But the devs always know best.

---

### Post by kansasnoob on 2014-10-21
> **ventrical said:**
> I don't get it because  have had nothing but success with my last three "Install alongside" Ubuntu/xubuntu Beta2s.

edit >
 Only bug I have had is with Windows 8 bootloader.

Try it some time with unpartitioned space on any connected drive.

---

### Post by kansasnoob on 2014-10-21
This was about the beginning of the problem:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

Oh that's where Colin Watson "agreed" with me:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852/comments/40](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852/comments/40)

He was eluding to this comment:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852/comments/35](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852/comments/35)

> 

If there is more space free in a partition that could be resized than is available in unallocated space, then the unallocated-space option is dropped. I'm guessing that the theory here may be that you can just use the "Install alongside" option and leave the other OS' size unchanged, thereby reducing the number of automatic partitioning options we need to present. However, the "Install alongside" option doesn't actually let you use unallocated space - it always resizes. **[COLOR="#FF0000"]I think we should present unallocated space, as people may well prefer not to reduce the amount of space available to their other OS.[/COLOR]**

Another problem I notice is that if the only other partitions present are data partitions - that is, os-prober outputs nothing - then you get neither the unallocated-space option nor the resize option. This seems like a bug, as resizing is perfectly possible here. Perhaps the 'if os_count == 0:' branch in calculate_autopartitioning_options needs to consider resize options.

I'll ask Evan to comment on this, and reopen or spin off a new bug report as necessary.


---

### Post by ventrical on 2014-10-21
just rolling here, testing

@sudodus

Don't mind me... I'll ask mod to remove later

thnxs

edit .

Ok I freed up some space 32 gigs and now it asks me 'Install Alongside'? (using utopic-xubuntuamd64)

---

### Post by ventrical on 2014-10-21
now here (using xubuntu 'live' )

Choose continue

---

### Post by ventrical on 2014-10-21
begginign normal install

What did I do wrong?? that was not right to duplicate your bug?

---

### Post by ventrical on 2014-10-21
fini

Question

Do I need to *completely* remove the extended partiton to test this case correctly?

---

### Post by ventrical on 2014-10-21
Ok.. onwards and upwards... I will now install yet another install of xubuntu and see what the resizer does.

This is on 80GBWDSATA

---

### Post by sudodus on 2014-10-21
I think you freed up space on a drive, that is not the live drive, or at least that does not have a read-only iso9660 file system.

'My free space' was found on a pendrive behind a cloned read-only iso9660 file system (cloned with mkusb from the iso file), and Ubiquity did not manage to squeeze a working ext4 root partition and a swap partition there. The error message was that it failed to create swap.

I think that Ubiquity should not select such a location to install the system.

I wanted to install Lubuntu into the other drive, hoping that the installer would resize an existing partition (creating space for Lubuntu's root partition and sharing the existing swap partition with an existing Trusty installation). This is the meaning of 'alongside' for me.

-o-

I would not bother with the install option 'Install alongside', if I were only to think about myself, because I can use 'Something else'. But I don't want to read about beginners, who get unpleasant surprises, when they 'misunderstand' what will happen. Many of these beginners do not realize that it is risky, so they have no backup ...

---

### Post by ventrical on 2014-10-21
All works well but so far will not let me see the other <Select Drive>

 I can move the slider etc..

so will also try Advanced Partitoning Tool (see where other drive is)

---

### Post by ventrical on 2014-10-21
Yes .. serious bug. It will not let you choose the *primary* partiton from ubiquity to choose the resizer option. It automagically chooses the exended partiton.
It just keeps looping back when try to choose the primary partition. Not neccesarily a design flaw. Could be  some built in security... but xubuntu installs good regardless.. however @kansasnoob .. your points well taken..

---

### Post by ventrical on 2014-10-21
> **sudodus said:**
> I think you freed up space on a drive, that is not the live drive, or at least that does not have a read-only iso9660 file system.

'My free space' was found on a pendrive behind a cloned read-only iso9660 file system (cloned with mkusb from the iso file), and Ubiquity did not manage to squeeze a working ext4 root partition and a swap partition there. The error message was that it failed to create swap.

Ok .. got it.

> 

I think that Ubiquity should not select such a location to install the system.

I wanted to install Lubuntu into the other drive, hoping that the installer would resize an existing partition (creating space for Lubuntu's root partition and sharing the existing swap partition with an existing Trusty installation). This is the meaning of 'alongside' for me.

-o-

I would not bother with the install option 'Install alongside', if I were only to think about myself, because I can use 'Something else'. But I don't want to read about beginners, who get unpleasant surprises, when they 'misunderstand' what will happen. Many of these beginners do not realize that it is risky, so they have no backup ...

  I can agree somewhat with this. But for me as a 'push-the-envelope' tester it's a handy tool and saves me time when doing very basic testing of daily .isos. I would give it an 80% rating of reliability. I am going to continue to test this with xubuntu 'live' as it's obvious that xubuntu is the more  extremely stable, fast and patient of all  the live mode flavours (discard on shutdown option). It is a real quick install on slower machines also.

 I am going to test your case in a bit.

thnx

Ok.. I'm back . Willing to emulate your test case. I just wanted to add a note. In my recall a couple of years ago I remember I had a similar situation and this was caused by a firmware problem with the USB itself. I had to take the USb and use WindowsXP (of all things) to remove the partitions and then reformat the USB in FAT32. Then , I got the USB back and was able to install an ubuntu OS on it.. but thats not exactly what oyu have described.

So I am re-reading your test case.

---

### Post by grahammechanical on 2014-10-21
> [COLOR=#000000]I would not bother with the install option 'Install alongside', if I were only to think about myself, because I can use 'Something else'. But I don't want to read about beginners, who get unpleasant surprises, when they 'misunderstand' what will happen. Many of these beginners do not realize that it is risky, so they have no backup ...[/COLOR]

I think there have been examples on the forum of users installing and having an external hard drive connected and finding that the Install Alongside option put Ubuntu onto the external drive. I think that I have seen something like that. We know that too many choices can be scary to the uninitiated but maybe there are situations where the user should be asked to make a decision. Such as, "You have more than one drive. Where do you want Ubuntu installed to?"

Regards.

---

### Post by sudodus on 2014-10-21
Yes I agree Graham,

There should be an option
[I][B]
'Select drive' - and a list of drives[/B][/I]

 if more than one drive is considered suitable by Ubiquity.

Would you consider the live drive suitable, or maybe I should ask: Can you think of situations, where partitions on the live drive or unallocated space on the live drive are the target of the installation? - In that case all writable mass storage devices should be listed (including a USB boot drive but excluding a CD/DVD boot drive).

Edit: Something like the following list, maybe with a little more eye-candy

```
Name: ata-SAMSUNG_HD322HJ        Dev: /dev/sda  Size: 320GB
Name: ata-OCZ-AGILITY3           Dev: /dev/sdb  Size: 60GB
Name: ata-WDC_WD1003FBYZ-010FB0  Dev: /dev/sdc  Size: 1000GB
Name: usb-SanDisk_Cruzer_Blade   Dev: /dev/sdd  Size: 4005MB
Live drive: /dev/sdb
```

---

### Post by ventrical on 2014-10-21
First test case - USB to USB.

 There is a problem, perhaps , with my hardware. I am going to abort this test case as it is taking too long. I will use USB ver3.

---

### Post by ventrical on 2014-10-21
> **sudodus said:**
> The 'install alongside' test case:

Installing from a USB pendrive to another USB drive does not work. I remember doing such installations many times before, but maybe I have been using 'Something else'. 

Ubiquity (in the USB to USB test case) is not determining correctly to erase the information on the USB hdd when choosing 'Erase Disk and Install Xubuntu'  on my MSi B75MA-P45 tower. However , I am going to try the operation on an older Acer laptop which seems to be able to handle these problems. I certainly conceed that there have been problems with USB to USB since after maverick meercat with the inception of unity in the natty cycle.

---

### Post by ventrical on 2014-10-21
Ahhh .. yes .. I remember now . There was this bug with the live session in unity-ubuntu (and the other flavours) where if you chose  "Install to Disk" from the "live session" desktop icon it would fail but if you chose  "install to disk" from the Unity panel , then it would work. I don't remember exactly the circumstances or why this was happening but it was a good work-around at the time.

Currently installing  from USB to USB with no problems so far on Acer Extensa 4420.

*edit*

Ubiquity at this stage of the game is an absolute failure in regards to USB to USB installs. I got it to finish/restart but locks up on log-in screen and is -super- slow.  With hdd installs it works great but I think it is actually in worse shape that kansasnoob has described. Even my Lucid/Maveric  USB installs shame Utopic [s]and all the other cycles in between.[/s] Looks like a cardinal rule was broke here -if it ain't broke - don't fix it -- and they did!



Regards..

---

### Post by sudodus on 2014-10-21
Trying with the next uploaded Lubuntu desktop iso file, dated 20141020 and with the md5sum 42a489628386a2b7faacc67db1ab8649  there was an improvement. I don't know exactly why, because I haven't  saved the old iso file to try again, and I cannot easily find if it was a  temporary glitch the last time or some debugging action, that makes it  work now. (Maybe there was a quick fix by someone who knows this part of  Ubiquity well after the recent debug action of 'Install alongside'.)

Ubiquity still wants to install into the unallocated space behind the  iso9660 file system on the live drive and complains that it cannot  create the swap space, ***but now, when I click on OK, it does not get  stuck***, but returns to the partitioning page, ***and the next time I try  'Install alongside' it lets me share the space in the other drive*** (by  dividing the ext4 partition into one part for the existing system and  one part for the system to be installed now).

 I could drag the boundary, as expected, and the installation succeeded :-)

See the attached pictures (the first one from the failed attempt, with a Trusty installation, the second one from now, with another Utopic installation made earlier today).

The partitions looked like this before:

```
lubuntu@lubuntu:~$ sudo lsblk -fm
NAME   FSTYPE   LABEL              UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                                                                sda     14.6G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4     Lubu_1410@sda1     8741dd00-09dc-4b22-bca4-e805316fc8d5            &#9500;&#9472;sda1  10.7G root  disk  brw-rw----
&#9500;&#9472;sda2                                                                             &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5 swap                        931d834c-405f-4c2a-b58a-8506fee118ee            &#9492;&#9472;sda5   3.9G root  disk  brw-rw----
sdb    iso9660  Lubuntu 14.10 i386 2014-10-20-20-24-44-00                          sdb      7.5G root  disk  brw-rw----
&#9492;&#9472;sdb1 iso9660  Lubuntu 14.10 i386 2014-10-20-20-24-44-00                          &#9492;&#9472;sdb1   705M root  disk  brw-rw----
sr0                                                                                sr0     1024M root  cdrom brw-rw----
loop0  squashfs                                                         /rofs      loop0  638.5M root  disk  brw-rw----
zram0  swap                        a4291959-d91c-4906-ae98-14f323fbba64 [SWAP]     zram0  491.3M root  disk  brw-rw----
zram1  swap                        1e3b1ef0-07d2-4645-ab16-7db78a96a1de [SWAP]     zram1  491.3M root  disk  brw-rw----
zram2  swap                        b03ecd57-b11b-41d3-8a3f-4e69d5b65b90 [SWAP]     zram2  491.3M root  disk  brw-rw----
zram3  swap                        617b1c1c-e660-40f6-95e8-2859443f4244 [SWAP]     zram3  491.3M root  disk  brw-rw----
lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            2.0G   20M  2.0G   1% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           394M  1.1M  393M   1% /run
/dev/sdb        705M  705M     0 100% /cdrom
/dev/loop0      639M  639M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.0G  4.0K  2.0G   1% /tmp
none            5.0M  8.0K  5.0M   1% /run/lock
none            2.0G     0  2.0G   0% /run/shm
none            100M   24K  100M   1% /run/user
lubuntu@lubuntu:~$ 

```

This is good, but there are still things to improve with 'Install alongside', before I am ready to recommend it ...

---

### Post by kansasnoob on 2014-10-21
There is also this bug:

[https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/351473](https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/351473)

At least two of the newer duplicates are mine.

---

### Post by sudodus on 2014-10-21
Another indication that we need an option to select drive (manually).

---

### Post by kansasnoob on 2014-10-21
> **sudodus said:**
> Another indication that we need an option to select drive (manually).

+1! And also the option of placing grub somewhere other than /dev/sda if desired w/o being required to use the advanced partitioning tool.

In the real world I always create the desired partitions using Gparted and then use advanced partitioning to properly assign each partitions mount point, but since we do offer options for the noobs we need to be sure those options work in a manner that a real noob can use. We should at least be able to do everything with ubiquity that we could do with the d-i.

---

### Post by sudodus on 2014-10-21
> **ventrical said:**
> -[COLOR=#ff0000]if it ain't broke - don't fix it -- [/COLOR]and they did!

+1

---

### Post by sudodus on 2014-10-22
> **sudodus said:**
> Trying with the next uploaded Lubuntu desktop iso file, dated 20141020 and with the md5sum 42a489628386a2b7faacc67db1ab8649  there was an improvement. I don't know exactly why, because I haven't  saved the old iso file to try again, and I cannot easily find [COLOR=#ff0000]if it was a  temporary glitch[/COLOR] the last time or some debugging action, that makes it  work now. (Maybe there was a quick fix by someone who knows this part of  Ubiquity well after the recent debug action of 'Install alongside'.)

Now I think it was a glitch due to flaky cooperation with a USB 3 hub, that I used at the first testing instance. That hub is rather new (bought this year) and has worked before except with one particular pendrive (which was not used in any of these tests). It has worked with many linux operating systems, also for booting, including Ubuntu 12.04.5 LTS, Ubuntu 14.04.1 LTS, Arch, Fedora, Mageia, openSUSE, Debian Wheezy and Jessie, Puppy Wary and Tiny Core. But it works only sometimes with Lubuntu 14.10 (otherwise boots to a text screen with some error output), and I suspect it was involved in the failure to continue from the window, which complained that swap could not be created in the live drive.

I'll test if the hub is failing, but at least some of those other distros still boot properly via it ...

Tiny Core, ToriOS, Mageia work,

xubuntu-14.04.1-desktop-i386.iso and ubuntu-14.04.1-desktop-amd64.iso do not work (but worked until some week ago) ... so I think the USB 3 hub is failing, or at least, it has changed somehow and lost the ability to cooperate with some operating systems and or pendrives during booting.

The modern Ubuntu based distros, versions, flavours work when booted directly from the USB port in the computer (but not via the hub and the same USB port).

---

### Post by sudodus on 2014-10-22
> **ventrical said:**
> ... Ubiquity at this stage of the game is an absolute failure in regards to USB to USB installs. I got it to finish/restart but locks up on log-in screen and is -super- slow ...

If the target drive is a fast USB 3 pendrive, you can write many small files relatively fast (even via a USB 2 port, but of course faster via a USB 3 port). My target drive is a Sandisk Extreme, which I think gives good value for the money. See these links:

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/")
[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

A USB 2 HDD is much better than an average pendrive (because you can write many small files relatively fast).

---

### Post by ventrical on 2014-10-22
I'm just using basically cheap Dane USB pens, Kingstons  and Transcend. Point it , I have had problem  before on these machines using maveric or Lucid.  I was able to  do a Trusty USB to USB on ver 3.0Transcend 32GB and that OS is still going. All my Lucid USB are still operational.

  I think I mis-spoke .. The Trusty USB to USB worked really well on ubuntu-desktop-amd64.iso.

---

### Post by ventrical on 2014-10-22
> **sudodus said:**
> If the target drive is a fast USB 3 pendrive, you can write many small files relatively fast (even via a USB 2 port, but of course faster via a USB 3 port). My target drive is a Sandisk Extreme, which I think gives good value for the money. See these links:

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/")
[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

A USB 2 HDD is much better than an average pendrive (because you can write many small files relatively fast).

Please disregard my original comment.. it was written when I was tired. :)

thnx 

Regards..

---

### Post by sudodus on 2014-10-22
> **ventrical said:**
> Please disregard my original comment.. it was written when I was tired. :)

thnx 

Regards..

Do you want me to remove what I have quoted? Just tell me and I'll remove it :-)

---

### Post by sudodus on 2014-10-23
Report from  iso-testing Utopic Final Lubuntu amd64 desktop iso:

[TABLE="class: sticky-enabled tableheader-processed sticky-table"]
[TR="class: odd"]
[TD]1a. The 'Install alongside' option was not available with a 16 GB USB 3 pendrive with Utopic with this amd64 iso file. (It was available and worked with the i386 iso file).

1b. Reinstalling a minimal system (Trusty-nonpae-txt5.tar.xz via the One Button Installer) it *worked* with the 16 GB USB 3 pendrive with this amd64 iso file. Either the installer is sensitive to the space left, or it suggests overwriting 'itself' (another instance of the same version).

 2. With an SSD drive containing Windows Technical Preview (Windows 10)  and Ubuntu Trusty, only Trusty was acknowledged, and it was suggested to  'install alongside Ubuntu 14.04.1'. However, at the next window the  NTFS partition was suggested to be preserved as 'Files', and Lubuntu to  be installed behind it (so overwriting Ubuntu Trusty). This is  confusing. (I did not want to destroy the system, so I quit the  installer.)

 Whoever needs more tests or details, please advice what to do and where to report it.[/TD]
[TD="align: center"][[IMG]http://iso.qa.ubuntu.com/modules/qatracker/misc/test.png[/IMG]]("http://iso.qa.ubuntu.com/qatracker/testcases/1301/revisions/1404/info") [[IMG]http://iso.qa.ubuntu.com/modules/qatracker/misc/edit.png[/IMG]]("http://iso.qa.ubuntu.com/qatracker/milestones/325/builds/82594/testcases/1301/results/55352/edit")[/TD]
[/TR]
[/TABLE]

---

### Post by ventrical on 2014-10-23
> **sudodus said:**
> Do you want me to remove what I have quoted? Just tell me and I'll remove it :-)

No , thank you. I  have struck out the superfluous comment  "all other cycles in between" so my original comment stands .. of course with the correction that - on an average basic , during development cycles, most Ubiquity bugs are ironed out at release , but not necessarily outstanding bugs  that have been shevled.

Regards..

---

### Post by ventrical on 2014-10-23
> **sudodus said:**
> Report from  iso-testing Utopic Final Lubuntu amd64 desktop iso:

[TABLE="class: sticky-enabled tableheader-processed sticky-table"]
[TR="class: odd"]
[TD]1a. The 'Install alongside' option was not available with a 16 GB USB 3 pendrive with Utopic with this amd64 iso file. (It was available and worked with the i386 iso file).

1b. Reinstalling a minimal system (Trusty-nonpae-txt5.tar.xz via the One Button Installer) it *worked* with the 16 GB USB 3 pendrive with this amd64 iso file. Either the installer is sensitive to the space left, or it suggests overwriting 'itself' (another instance of the same version).

 2. With an SSD drive containing Windows Technical Preview (Windows 10)  and Ubuntu Trusty, only Trusty was acknowledged, and it was suggested to  'install alongside Ubuntu 14.04.1'. However, at the next window the  NTFS partition was suggested to be preserved as 'Files', and Lubuntu to  be installed behind it (so overwriting Ubuntu Trusty). This is  confusing. 
                                                             ^^^^^^^^^^^
[/TD]
[TD="align: center"][[IMG]http://iso.qa.ubuntu.com/modules/qatracker/misc/test.png[/IMG]]("http://iso.qa.ubuntu.com/qatracker/testcases/1301/revisions/1404/info") [[IMG]http://iso.qa.ubuntu.com/modules/qatracker/misc/edit.png[/IMG]]("http://iso.qa.ubuntu.com/qatracker/milestones/325/builds/82594/testcases/1301/results/55352/edit")[/TD]
[/TR]
[/TABLE]


Exactly.

---

### Post by mikodo on 2014-10-26
> **kansasnoob said:**
> +1! And also the option of placing grub somewhere other than /dev/sda if desired w/o being required to use the advanced partitioning tool.

**In the real world I always create the desired partitions using Gparted and then use advanced partitioning to properly assign each partitions mount point**, but since we do offer options for the noobs we need to be sure those options work in a manner that a real noob can use. We should at least be able to do everything with ubiquity that we could do with the d-i.

Thanks, for looking out for noobs, people.

It's good to know I am doing it right.

---

