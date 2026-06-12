---
title: "Ubuntu/Linux is a lifesaver"
date: 2007-08-31
forum: Testimonials &amp; Experiences
---

### Post by durrell on 2007-08-31
So I've been using Ubuntu since the beginning of May off and on, I've tried Gentoo for awhile too, among other distros, but Ubuntu is by far my favorite. Well starting this semester I've had some online classes at school that have required me to use WIndows (sad, I know). So I was running Windows, Feisty, and Gutsy Tribe 5 with no apparent issues, but last night I went to delete both Ubuntu installs with plans to reinstall just Feisty. I normally keep all of my important files on a separate partition from any operating system partition. Well I was trying to "clean up" my partitions last night and I moved all of my backups (music, movies, documents, etc.) to the NTFS partition that Windows XP was on. I had not had any issues with it and I figured if I moved it there then I could move it back when I made a new storage partition.

So the deleting commenced, and I do the Windows XP Recovery console normal stuff..fixmbr and fixboot to overwrite GRUB. Go to boot into Windows and what happens? Nothing. Blinking cursor. So I thought.."Ok, it just didn't rewrite the boot sector correctly." I tried it again with the same result. I boot Gparted and see that the Windows partition has errors, so I reboot the Recovery console and try to run chkdsk /r. What does Windows tell me? "One or more unrecoverable errors on the volume." So at this point I go into panic mode, because all of my data is at the mercy of Windows on a so called "unrecoverable" NTFS partition. I boot the Ubuntu Live CD and first try to mount the NTFS partition and move the files from Live CD. But it gives me a "Could not mount volume, bad superblock, bad sector" error. So I then try to reinstall Ubuntu, but Windows is so effed at this point that the Ubuntu install botches. Now I'm left with one option..and that's to figure out a way to fix this from the Live CD. So after Googling for awhile I ran across a program called "TestDisk". I install it using the LiveCD and run it, and it sees the drive and all the files on it. I had hope at that point. The only issue I ran into was that it wanted to copy all the data to the LiveCD..which won't work since it's running off of RAM basically. So I check another option, which was use "TestDisk" to rewrite the NTFS boot sector. I tried that, and it appeared to go successfully. So I checked Gparted and Gparted showed no errors! I quit the LiveCD and popped the recovery console CD back in, and ran chkdsk /r and that time it worked! So about 2 hours after I thought I had lost everything, I got it back..and all is well.

TL;DR: So for those of you who want to give up on Linux: don't. Linux is an invaluable tool to have. It only breaks when you do something to break it. This experience reminded me why I hated Windows in the first place. Because it manages to break itself doing simple tasks. If I can find a way to use Linux for my online assignments, I'm deleting Windows and going straight Ubuntu. When my new laptop gets here, I'm going to dual boot and run Ubuntu as much as possibile. So there you go..my 4 months of Linux usage and frustrations in learning it all paid off in an hour of saving all of my data from the horrible thing knows as Windows.

I love Linux. <3 I'm not going to say just Ubuntu because I used a mixture of the Ubuntu Live CD, the System Rescue Live CD, and the Gparted Live CD..haha.

---

### Post by marx2k on 2007-08-31
NTFS can be an ugly, fragmentary,  unworkable beast a lot of the time.  My suggestion for you in the future is to run Linux with XP in a VMWare/Virtualbox sandbox.  That's why I do for school and it's no problem.  Even when I go to school, all they have are XP boxes.  I have Ubuntu on a 160GB USB drive, plug it into the computer at school and boot from the USB drive directly into Fiesty.  Then  if I do need XP for any reason (.NET dev environment, IIS, IE5/6 testing) I just run it in VMWare in a window just like another application.  There's no reason to dualboot.  I used to dualboot then decided I really hate it because I have to shut down Linux, bring up XP for a very limited task, shut down XP, bring Linux back up... it's a hassle and I am forced to do the thing I hate most, which is shut down Linux.

---

### Post by durrell on 2007-08-31
I actually have never considered that. I could type up the document inside of Ubuntu, save it to the Storage drive I have and then upload it from Windows. That's actually a really, really good idea. :)

But that's the thing that worried me about a Virtual box..since it isn't a physical drive, how could I move the file from Ubuntu to the Virtual install to upload it?

I'm still probably going to try to e-mail the sys admin at the school and find out if he can somehow enable uploading from Linux. The problem is that the uploader looks for a filepath that starts with a drive letter, so a Linux filepath that starts with /home/ isn't recognized.

---

### Post by wolfen69 on 2007-08-31
> **durrell said:**
> So I've been using Ubuntu since the beginning of May off and on, I've tried Gentoo for awhile too, among other distros, but Ubuntu is by far my favorite. Well starting this semester I've had some online classes at school that have required me to use WIndows (sad, I know). So I was running Windows, Feisty, and Gutsy Tribe 5 with no apparent issues, but last night I went to delete both Ubuntu installs with plans to reinstall just Feisty. I normally keep all of my important files on a separate partition from any operating system partition. Well I was trying to "clean up" my partitions last night and I moved all of my backups (music, movies, documents, etc.) to the NTFS partition that Windows XP was on. I had not had any issues with it and I figured if I moved it there then I could move it back when I made a new storage partition.

So the deleting commenced, and I do the Windows XP Recovery console normal stuff..fixmbr and fixboot to overwrite GRUB. Go to boot into Windows and what happens? Nothing. Blinking cursor. So I thought.."Ok, it just didn't rewrite the boot sector correctly." I tried it again with the same result. I boot Gparted and see that the Windows partition has errors, so I reboot the Recovery console and try to run chkdsk /r. What does Windows tell me? "One or more unrecoverable errors on the volume." So at this point I go into panic mode, because all of my data is at the mercy of Windows on a so called "unrecoverable" NTFS partition. I boot the Ubuntu Live CD and first try to mount the NTFS partition and move the files from Live CD. But it gives me a "Could not mount volume, bad superblock, bad sector" error. So I then try to reinstall Ubuntu, but Windows is so effed at this point that the Ubuntu install botches. Now I'm left with one option..and that's to figure out a way to fix this from the Live CD. So after Googling for awhile I ran across a program called "TestDisk". I install it using the LiveCD and run it, and it sees the drive and all the files on it. I had hope at that point. The only issue I ran into was that it wanted to copy all the data to the LiveCD..which won't work since it's running off of RAM basically. So I check another option, which was use "TestDisk" to rewrite the NTFS boot sector. I tried that, and it appeared to go successfully. So I checked Gparted and Gparted showed no errors! I quit the LiveCD and popped the recovery console CD back in, and ran chkdsk /r and that time it worked! So about 2 hours after I thought I had lost everything, I got it back..and all is well.

TL;DR: So for those of you who want to give up on Linux: don't. Linux is an invaluable tool to have. It only breaks when you do something to break it. This experience reminded me why I hated Windows in the first place. Because it manages to break itself doing simple tasks. If I can find a way to use Linux for my online assignments, I'm deleting Windows and going straight Ubuntu. When my new laptop gets here, I'm going to dual boot and run Ubuntu as much as possibile. So there you go..my 4 months of Linux usage and frustrations in learning it all paid off in an hour of saving all of my data from the horrible thing knows as Windows.

I love Linux. <3 I'm not going to say just Ubuntu because I used a mixture of the Ubuntu Live CD, the System Rescue Live CD, and the Gparted Live CD..haha.

you could have also done a repair install of xp. it might change some of your personal settings, but programs and files will remain intact.

---

### Post by durrell on 2007-08-31
> **wolfen69 said:**
> you could have also done a repair install of xp. it might change some of your personal settings, but programs and files will remain intact.

I'm not sure if that would have worked in this case or not since Windows thought it was "unrecoverable". Either way, it never should have happened in the first place..

---

