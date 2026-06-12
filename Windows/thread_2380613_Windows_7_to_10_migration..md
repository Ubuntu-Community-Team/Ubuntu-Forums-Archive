---
title: "Windows 7 to 10 migration."
date: 2017-12-19
forum: Windows
---

### Post by 77_GCSX on 2017-12-19
Hi all. Not new here (Currently using Ubuntu on a few PC's) but I have a Windows question.

I don't have a business but I do work on other people's PC's. This is a friends of my fathers PC.

The PC in question is a Win 7 machine. He's been having some issues: Strange sounds coming from the tower, web browsing EXTREMELY using both IE and Chrome, just to name a few, and he wants to upgrade to Windows 10.

My main question is: Does this "File History Transfer" deal work going from Windows 7 to 10 that I've read about or is there an easier way to migrate all of his settings and documents (including programs) over to 10 from 7?

I've done some preliminary research on this and the file transfer deal keeps coming up as the easiest way to do this.

BTW: Except for NEEDING a Windows 7 PC for Coupons for my wife, we are all Ubuntu users and have been for a few years.:D

Thanks in advance!
Paul

---

### Post by QIII on 2017-12-19
Hello!

I think that before you do anything you need to sort out the issue with the strange sounds.  If there is a drive failing, you may have specific hardware issues to deal with.

---

### Post by oldfred on 2017-12-19
If a dual boot with Ubuntu and system is in a MBR(msdos) partition, then be very careful.
Have full backups, but also create a copy of partition table.
Windows for years has a bug that updates a MBR partition table, but forgets to include Linux partitions. Data is still there and partition entry just needs to be restored.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ parts.txt
for a drive seen as sdb:
sudo sfdisk -d /dev/sdb > parts_sdb.txt

---

### Post by 77_GCSX on 2017-12-19
> **QIII said:**
> Hello!

I think that before you do anything you need to sort out the issue with the strange sounds.  If there is a drive failing, you may have specific hardware issues to deal with.

I've done this part. The drive seems to be ok. Defrag went well and CHKDSK didn't find anything wrong.

> **oldfred said:**
> If a dual boot with Ubuntu and system is in a MBR(msdos) partition, then be very careful.
Have full backups, but also create a copy of partition table.
Windows for years has a bug that updates a MBR partition table, but forgets to include Linux partitions. Data is still there and partition entry just needs to be restored.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ parts.txt
for a drive seen as sdb:
sudo sfdisk -d /dev/sdb > parts_sdb.txt

Nope. Strictly Windows > Windows on this PC. I have enough spare drives to back things up JUST in case something goes wrong so I could start over from scratch.

The main link I found in my research is this one: [https://www.pcworld.com/article/3034527/windows/restore-a-windows-7-backup-in-windows-10.html](https://www.pcworld.com/article/3034527/windows/restore-a-windows-7-backup-in-windows-10.html)

This "appears" to be my best shot at this migration/transfer. 

Any thoughts on it?

** Sorry. I forgot to say that the guy is buying a PC with 10 already installed**

He wants me to transfer his 7 stuff to the 10 PC.  I was in a rush posting this..:(

---

### Post by QIII on 2017-12-19
Ah!  A whole 'nother kettle of fish.  ;)

---

### Post by 77_GCSX on 2017-12-19
After thinking this over for a few days and actually researching it I may, just MAY talk him into converting to Ubuntu! The only problem I can foresee is he has an F1 game and the steering wheel/related hardware. I have to find out what version he has and see if it works with 16.04.

Mind you I'm not against Windows but ever since I converted to Ubuntu I have had nothing but luck with everything I have ever wanted to use, with the exception of the coupon printing app that my wife uses. Yes, we have a Windows 7 PC JUST for that..lol!

---

### Post by QIII on 2017-12-19
Personally, I'm opposed to attempting to "convert" people. This is not a religion, nor is it a marriage.  One need not cleave to the one and foresake all others.

This attitude may, in fact, be the greatest hindrance of all to the adoption of Linux.

There is no rule requiring the use of one or the other.  Why not rather encourage the use of Linux in addition to Windows?  That way, he would not need to leave behind the software and functionality he has come to depend on and expect.

---

### Post by 77_GCSX on 2017-12-19
I believe the only software he uses, besides a browser, is the F1 game. 

I'm not trying to 'make' any one use Linux, but my experience with it has been all good.

My father and his PC was the 1st converted. Why? He had XP with Norton protecting him. He some how got a virus that knocked out his internet. I made up a recovery stick and attempted to clean his PC. The da** virus jumped to my stick as well. 

long story short, I was paying good $$ for protection and it didn't work. So far, knock on wood, Linux (Ubuntu) has been awesome. Timely updates, no issues with software, etc.

I can explain the options to the guy and let him decide.

---

### Post by QIII on 2017-12-19
Sorry.  I don't mean to side-track this into a philosophical discussion.  :)

Back to the technical advice!

---

### Post by 77_GCSX on 2017-12-19
Not a problem :)

---

### Post by mastablasta on 2017-12-20
> **77_GCSX said:**
> 
He wants me to transfer his 7 stuff to the 10 PC.  I was in a rush posting this..:(

backup before move.

in that case (new pc, new OS) easiest is to reinstall the apps and then move the data. for some apps you can move the config files, for others you can't (search in user folders and program files).

---

### Post by 77_GCSX on 2017-12-21
Update: I got a good look at the 7 PC. He doesn't have a lot of software installed. He mainly uses it for email through a browser and the PITA F1 2002! <---That's my biggest issue but more in a bit on this.

He does makes CD's using Nero but I know there is the CDBurnerXP that may work for him. All I have left then is just some files that I can just copy to my usb stick.

The MAIN problem I have is his F1 2002 that he states was running on his 7 PC. I have yet to confirm this but if it is a fact then how do I get it to run on 10? I have another 10 PC I've been messing around with, the specs are almost identical to his new one, but I cannot get it to run. I can install it but when I run it I click on the shortcut and nothing happens.

I'm going to do an experiment to see what I can do to get it running: I'm going to install it on my Ubuntu 16.04 PC and see if I can get it run there without the headaches I've had trying on my test 10 PC.

"IF" this works better than the 10 machine then I'll ask/inform him of this and see if he wants to make the change to Ubuntu.

I would REALLY like to try to get the F1 2002 to run on the 10 PC though...just being tenacious here, so any help/insight in this issue would be great!

Thanks again everyone :)

P.S. I've used the Compatibility settings for Windows XP, and Windows 7 and it still does nothing when I click on the shortcut.

---

### Post by 77_GCSX on 2017-12-22
So I've been busy. I got the F1 to run with the Drive Force steering wheel the guy has and after a few hiccups I got everything to work - ON the TEST PC that is.

Now I'm working on the PC he bought. I got the game to run but the graphics are messed up. This screen cap is what I see whenever there is a car on the screen:

---

