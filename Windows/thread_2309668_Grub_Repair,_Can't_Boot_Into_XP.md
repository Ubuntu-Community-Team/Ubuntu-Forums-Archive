---
title: "Grub Repair, Can't Boot Into XP"
date: 2016-01-12
forum: Windows
---

### Post by jetman350 on 2016-01-12
Hey guys! My Grub is not working after a I did some re-structuring of my partitions dual booting with Windows XP and installed LXLE over Mint Xfce.  I only changed the Linux Partitions, not XP.  Prior to this I did a Frugal/Full? Install (Sorry Can't remember now with so many problems along the way) of Puppy Precise Retro, and used Grub4dos as the bootloader.  Things worked fine at this point, until after I Deleted Retro, did the restructuring and new install of LXLE.  After installing lxle I was not able to boot into XP and the only reason I used Grub4dos is could not get Grub2 to work after Editing.  Now I can boot into LXLE but not XP.

I just ran Grub Repair and got the pastebin link here.  Actually this was before running Repair as the directions weren't clear to me.  If I need to run again just say so: [B][http://paste.ubuntu.com/14479081/](http://paste.ubuntu.com/14479081/)
[/B]
After running Grub Repair XP is not shown in Grub2 but it was before

Got the Grub Repair Info here: [B][https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[/B]Thanks in advance

---

### Post by Seanan on 2016-01-12
When you boot up does it say this or something similar:
error: no such partition
entering rescue mode
grub rescue>

Edit: Ignore this reply

---

### Post by Seanan on 2016-01-12
Any info you have (errors, pictures) would help. Do you mean that when you are in the Grub bootloader it shows LXLE but not Xp?

---

### Post by jetman350 on 2016-01-12
> **Seanan said:**
> Any info you have (errors, pictures) would help. Do you mean that when you are in the Grub bootloader it shows LXLE but not Xp?

Seanan, thanks for all the time, yes it shows LXLE but not XP and LXLE Boots fine.  It did show XP until I ran that grub-repair tool, but XP would not Boot anyhow.  I was not getting help on another forum so I posted here, but now I am, so maybe we should hold off here for now.  Don't want to **** anyone off.  

Did you look at the pastebin link, that tells you everything, if one knows what they are looking at lol, I surely don't.  I am going to try and repair Grub2, even though G4 has been written to XP.  Grub2 is being used now so me thinks it can be EDITED to suit, hopefully.

Thanks again

---

### Post by grahammechanical on 2016-01-12
> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 320D-180E
	drivemap -s (hd0) ${root}
	chainloader +1

Windows XP should be in the Grub boot menu. It looks for the XP boot files at hd0,msod1 = first hard drive & first partition. But I do not see a win.exe file. May be XP does not use one. What do I know? The last Microsoft OS I used was Win98.

Regards.

---

### Post by yancek on 2016-01-12
You do have Grub code installed to the MBR pointing to the correct partition and the grub.cfg file clearly showns windows xp as an entry.  Not sure what's up with your windows partition but there is obviously a problem per the output below:

> Grub2 (v1.97-1.98) in the file /sda_mbr.bak looks at                         sector 1 of the same hard drive for core.img, but                         core.img can not be found at this location

Might be a left over from your Puppy install.  Have you tried running:  sudo update-grub?  Have you made any changes since running the boot repair script?  I've never used Grub4Dos so I'm not sure what one would expect to see.  It shows on this partition a different version of Grub than the one you have with your LXLE and it also has a menu.lst file which is not used with Grub2.

---

### Post by jetman350 on 2016-01-12
@yancek, yes that is what I was looking at also, but I'm lost really.  Need to find directions that match what I need.  

Yes ran sudo update-grub, but nothing.  Was also wondering if deleting Grub4dos=menu.lst/menu-advanced.lst would help.  But it seems as though Grub2 is working but somehow not picking up to boot.

I ran the boot-repair again from the HDD install in LXLE and now have the XP Listed but still won't boot.  Okay guys, all the help is awesome but no hurry to fix.   Just need to get into XP sometime to maintain, and, to learn how to fix this issue.  I knew puppy Grub4 would give me issues LOL.  There was a Notification to reverse this action upon install, I took a screenshot but puppy lost it as it don't act like installs I'm used to when saving stuff.  I dug though all the png's in puppy CD to find the little sucker, because it had a Command to run to reverse this action.  Why in the world would it be so hard to find the Command to reverse this?  Maybe you guys would like to see this?

[http://i.imgur.com/cG0e01p.png](http://i.imgur.com/cG0e01p.png)

---

### Post by oldfred on 2016-01-12
Grub really only boots working Windows.
And Boot-Repair cannot do much to fix Windows. It can install a Windows type boot loader to boot Windows directly to see if it works. Then you can use Boot-Repair to reinstall grub.
Often you need a Windows repair disk or the original XP installer to run the Windows repair console and run chkdsk or other repairs.

---

### Post by jetman350 on 2016-01-14
> **oldfred said:**
> Grub really only boots working Windows.
And Boot-Repair cannot do much to fix Windows. It can install a Windows type boot loader to boot Windows directly to see if it works. Then you can use Boot-Repair to reinstall grub.
Often you need a Windows repair disk or the original XP installer to run the Windows repair console and run chkdsk or other repairs.

This is what I was thinking but don't know how to proceed.  Was hoping someone here would steer me to a GOOD tutorial so I don't make things worse.  I will find one my self I guess, then fix XP, then re-run sudo update-grub, or the grub repair tool?
That being said, I take it that Grub4 or the reinstall of linux did this, because XP is/was fine and am pretty careful with it.

Thanks!

---

### Post by oldfred on 2016-01-14
Windows XP EOL will be April, 2014.
[http://www.microsoft.com/en-us/windows/endofsupport.aspx](http://www.microsoft.com/en-us/windows/endofsupport.aspx)

Your request for Windows repair is really a Windows issue and this is a Linux forum. Moving thread to Windows sub-forum.
I last used XP in 2011.
But one of the first things to do is run chkdsk from Windows repair console.

 Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

      
 chkdsk c: /r

 You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by jetman350 on 2016-01-15
Thank you very much Oldfred, this will be a Bookmark for sure.  I am unfamiliar with this stuff for the most part so could not get the XP disk run any commands(lack of experience)it was not evident how to get to that point even though I was reading the tutorials.  I then used the boot-repair tool and chose Fix MBR.  Now I can boot into XP, but don't get Grub2 anymore.  I'm tempted to run boot-repair again and Fix, or re-install Grub2.  It does ask where to put it, I'm guessing that would be on root partiton of my linux install?  Need to read up on how all this works, as there are many files associated with Booting.  grub.cfg, menu.lst, mbr etc.

Need to learn how to do this manually.

---

### Post by oldfred on 2016-01-15
With BIOS based systems you have to install to the MBR or first sector of the drive. Never to a partition. So install grub to sda, not sda2 or any other partition.

Windows boot loader will then be overwritten, but if you made Windows repairs like chkdsk or others then grub should be able to boot Windows.

---

