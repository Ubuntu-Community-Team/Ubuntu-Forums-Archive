---
title: "Ubuntu 14.04 final beta - is anyone seeing &quot;new&quot; files go missing??"
date: 2014-04-10
forum: Ubuntu, Linux and OS Chat
---

### Post by bmullan2 on 2014-04-10
A week ago I upgraded to the final beta of Ubuntu 14.04 from the earlier beta.
Since then I have had 2 instances of files going missing from the file system.
Last week I had downloaded a movie (.mpg) from the web and had actually watched 1/2 of it using VLC before I decided it was too late at nite so I shutdown my Ubuntu 14.40 desktop system
Next morning I restarted the system and used Nautilus to browse to the directory I had stored that .mpg file in... and it was gone ??
At first I thought maybe I'd somehow deleted it... but my trash didn't have it either.

The next occurrence was yesterday.   I had 15 Microsoft Word documents I had transferred from my work laptop to this same Ubuntu 14.04 machine using an external USB drive.

I edited each of those 15 files using Libre-writer to add additional content and saved each as a .ODT file. 
Afterwards there were 30 files in that directory... the original 15 Word documents and the 15 modified .ODT files.
I printed each of the .ODT files and still have the hard copies.

Today... I needed to make some more changes and upon looking in that document directory... all 30 files were not there.

I know for certain I did not delete them.

Next I searched the entire 2TB (ext4) disk using
sudo find / -name *.docx -print

and it came back with nothing.   Those Word docs were the ONLY Word docs (re .docx) I had on my Ubuntu system??

So now I believe something in the final Beta is causing these files to go missing.

Since I have not noticed any files that were on the file system BEFORE the recent "final" beta upgrade missing... I am suspecting only "new" files since the upgrade may be affected.

I did check the file system and there were NO errors reported.

So I wanted to ask if anyone else using the Final 14.04 beta has seen anything like this?   If you are like me and this did happen to you ... you may have just assumed you misplaced the files or delted them.   But after 2 occurrences now I do not think its me any longer.

Brian

---

### Post by cariboo on 2014-04-10
I've been using Trusty since the toolchain was uploaded, and haven't had any files disappear. You may want to run disks, and run Smart Data & Self-Tests to see if there is a problem with your hard drive.

---

### Post by ventrical on 2014-04-11
> **bmullan2 said:**
> A week ago I upgraded to the final beta of Ubuntu 14.04 from the earlier beta.
Since then I have had 2 instances of files going missing from the file system.
Last week I had downloaded a movie (.mpg) from the web and had actually watched 1/2 of it using VLC before I decided it was too late at nite so I shutdown my Ubuntu 14.40 desktop system
Next morning I restarted the system and used Nautilus to browse to the directory I had stored that .mpg file in... and it was gone ??
At first I thought maybe I'd somehow deleted it... but my trash didn't have it either.

The next occurrence was yesterday.   I had 15 Microsoft Word documents I had transferred from my work laptop to this same Ubuntu 14.04 machine using an external USB drive.

I edited each of those 15 files using Libre-writer to add additional content and saved each as a .ODT file. 
Afterwards there were 30 files in that directory... the original 15 Word documents and the 15 modified .ODT files.
I printed each of the .ODT files and still have the hard copies.

Today... I needed to make some more changes and upon looking in that document directory... all 30 files were not there.

I know for certain I did not delete them.

Next I searched the entire 2TB (ext4) disk using
sudo find / -name *.docx -print

and it came back with nothing.   Those Word docs were the ONLY Word docs (re .docx) I had on my Ubuntu system??

So now I believe something in the final Beta is causing these files to go missing.

Since I have not noticed any files that were on the file system BEFORE the recent "final" beta upgrade missing... I am suspecting only "new" files since the upgrade may be affected.

I did check the file system and there were NO errors reported.

So I wanted to ask if anyone else using the Final 14.04 beta has seen anything like this?   If you are like me and this did happen to you ... you may have just assumed you misplaced the files or delted them.   But after 2 occurrences now I do not think its me any longer.

Brian

What is your hardware specs? Do you haev UEFI?

---

### Post by ventrical on 2014-04-11
> **cariboo907 said:**
> I've been using Trusty since the toolchain was uploaded, and haven't had any files disappear. You may want to run disks, and run Smart Data & Self-Tests to see if there is a problem with your hard drive.

+1 .. same here.

---

### Post by bmullan2 on 2014-04-14
answering some questions posted 

no ... not using UEFI
no ... Disks reports SMART that the disk is clear of any errors ...

 Up until 2 weeks ago by testing of beta 14.04 had no problems.

Tonite I booted the system and some of Virtualbox files were gone/missing/deleted
virtualbox
virtualbox-qt
and virtualbox-dkms

other virtualbox components were still on the system (guest utils etc).

Regarding my original post... the .docx and the .odt files magically reappeared a couple days/reboots later but the .mpeg movie never did come back.

I have booted from a liveCD and checked this hard disk as well ... several times and there are no errors or corruption.    I am not getting corrupted files... the file system links to some files just seems to disappear.
I am using ext4

I realize I'm still using beta code but I've been using ubuntu since 6.x and I've never had this happen and its really bugging me.

And... yes I do have a backup of my system before I ever installed the Trusty beta so I am not that worried other than I am concerned about this continuing.

---

### Post by slooksterpsv on 2014-04-16
If you remember the exact names you could try the following:

sudo updatedb
sudo locate *filename.odt*

I had that issue in the past with ext4 on 10.04 I think it was. Ahh 10.10 - [http://ubuntuforums.org/archive/index.php/t-1625743.html](http://ubuntuforums.org/archive/index.php/t-1625743.html)

So the issue I never figured out what it was. But ext4 works fine for me now. I wonder if it's something to do with the kernel and how it handles the transferring data to the disk. You may want to check dmesg for errors.

---

### Post by matt_symes on 2014-04-17
Hi

What filing system are you using ? ExtX, BTRFS, etc ?

What do your log files say ?

Kind regards

---

### Post by steeldriver on 2014-04-17
files disappearing and then mysteriously reappearing after a reboot makes me wonder whether something got mounted over the original containing directory...?

---

### Post by bmullan2 on 2014-04-20
This has occurred to me again.   For the past 3 days I had been working in  a VirtualBox Ubuntu 14.04 VM on my Ubuntu 14.04 Desktop pc.   The Desktop 14.04 was updated to all of the released Ubuntu 14.04 packages last Thursday (17th).

This morning after rebooting the VirtualBox VM & its associated files were not on my system (last night they were).

Again, **booted GPARTED off CD and ran file system check on my SDA1**...** no errors found.**

Booted  that drive and ran the DISKS program... ran the extensive version of  the **SMART disk tests... Disk is reported OK and no errors.**

I am hoping someone can tell me how I can even troubleshoot something like this.

I  am cloning the drive to a 2nd HD ... just in case there is any  possibility it is the HD itself... but I don't think so or it would seem  to me that some error would be detected by either SMART tests of  FSCK...???

I think this may be something with the **EXT4** file system & ubuntu itself?

Some of the missing files in the past occurences reappeared days later after some number of shutdown/reboots... I am hoping this latest VirtualBox VM reappears as I'd done alot of "documentation" type work in that VM over the last 3 days ... and I love documentation so much (not) that I'm hoping the VM reappears and I can avoid having to recreate it.

The drive I am cloning to now is a brand new drive.   However, I am starting to get worried that I may either be cloning the problem also
-or- if the problem is in EXT4 file system & ubuntu itself I may see this again even on the new HD.

I'll try some of the suggestions in the above posts... but this is such a random problem that if it is affecting others... many people may be like me
and not be noticing that a dozen files somewhere on their disk disappeared ... or later reappeared.

Any help or ideas would be greatly appreciated.

Thanks
brian

---

### Post by bmullan2 on 2014-04-20
Matt... this is such a wierd problem I am not sure what log file i'd check.
File system is EXT4 which I've used with my previous Ubuntu versions & with Ubuntu Beta.

Running FSCK and SMART drive tests show no errors and that the Drive is healthy.

Its a 2TB sata3 drive as are my other 2 spares ... all identical.

I am only using 540GB of the 2TB drive.

---

