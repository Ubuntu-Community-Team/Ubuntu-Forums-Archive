---
title: "Create bootable ISO from Win10 recovery USB"
date: 2016-07-22
forum: Virtualisation
---

### Post by shawn37 on 2016-07-22
Hello,

I am having a unique problem and cannot find a solution in the forums or Google. Here are the specifics:

December 2015:
- Bought an HP-Stream laptop specifically to load Linux. It came with Windows 10.
- Using Win10 utilities I moved the recovery drives to a USB stick (supposed to be bootable). I reclaimed the recovery partition and loaded Linux.
- I LOVE Linux. I wish I could drop Microsoft altogether.

Today:
- Unfortunately, I have found that I still need Windows for some tasks.
- I installed VirtualBox and setup a Win10 drive.
- I am attempting to install my copy of Win10, but I'm having difficulties:[INDENT]- I created a Win10 ISO from my Win10 USB using dd; because a VirtualBox VM cannot boot from a USB image.
     - I loaded the ISO into the Win10 VM Secondary IDE "CD/DVD" drive, but the VM will not boot into Windows.[/INDENT]

Other considerations:
- I have a Win8.1 laptop at home. I do not wish to use that computer for these tasks as that machine is my gaming laptop.
- I have no other Win10 machines.

Questions:
1. Can I convert the existing Win10 ISO to be bootable?
2. If not, can I create a bootable ISO from the Win10 recovery USB?
3. Can I use my Win8.1 laptop to create a bootable ISO from my Win10 recovery USB?
4. Can I use a different bootable ISO (any OS) to boot the VM, then load Win10? Or must I boot with Win10 to install it?

Any help is greatly appreciated.
Thank you for your time.
Shawn

---

### Post by mook765 on 2016-07-28
Something to read:[http://www.winhelp.us/restore-windows-re.html](http://www.winhelp.us/restore-windows-re.html)

---

### Post by MAFoElffen on 2016-07-30
There is a utility from Microsoft that you can dowload the Windows 10 ISO. The ISO file is bootable. If you read the Win 10 doc's, that is what is says to do. Not sure how last might Upgrade deadline, if it changed anything with those downloads, but, worth a try right?

To boot into Win a install, I know you have to be booted in Win PE... But I do not know if you can boot into Win PE from one image and change to another image and continue, and install from another.

---

