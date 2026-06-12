---
title: "Please someone help me reinstall Windows"
date: 2016-11-10
forum: Windows
---

### Post by blacktophat33 on 2016-11-10
I'm having trouble reinstalling windows after switching to Ubuntu 16.04. I really like Ubuntu but the learning curve is way more intense than I thought it would be and I just cant hack it. 

I tried mounting the Windows 10 iso to a usb and booting it from the boot menu but Ubuntu wouldn't read it. I tried remounting with different usb drives and nothing worked. 

I read that it might be because Ubuntu removed the windows BIOs files so I would need to mount a windows recovery iso and boot from there. When I tried that Ubuntu wouldn't recognize the drive at all. 

I desperately need to go back to windows. 

I would really really appreciate any help. 

Thanks

---

### Post by QIII on 2016-11-10
Hello!

You should not be trying to run anything from Ubuntu.  That won't work.

You need to boot your machine with the install media in place and make sure your BIOS/UEFI is set with that media as the first to try booting from.

Ubuntu did not remove any BIOS settings or files.  It will have changed the boot sequence, but Windows will change that when installed anyway.

---

### Post by yancek on 2016-11-10
> I tried mounting the Windows 10 iso to a usb and booting it from the boot menu but Ubuntu wouldn't read it. 

I don't know if the above is just a terminology question, but mounting a windows iso isn't going to do it.  If you have an actual valid windows iso, you need to loop mount it and then copy all the folders files to the usb drive you want to boot from.  It needs to be an ntfs formatted partition on the usb.

You say "Ubuntu won't read it", what is it?  Did you manually create a menuentry for the windows on the usb drive?  If so, post it.  The entry below is a sample menuentry which worked to boot a usb with windows 10 extractedfiles on it.  You would need to change the uuid to the correct one for your usb drive which you can get with the command:  sudo blkid

> menuentry "Start Windows Installation" {
 insmod ntfs
 search --no-floppy --fs-uuid 459532DE5D8D5C3A --set root 
 chainloader +1 
 boot
}

If you continue to have problems, post back and I can post a link to a site with more details on how to do this.

---

### Post by blacktophat33 on 2016-11-10
Thanks for the replys. I'm not sure what a menuentry is. 

I'm currently trying to follow this guide [http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html?m=1](http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html?m=1)

I have formatted the usb but I'm stuck on this command sudo grub-install --target=i386-pc --boot-directory="/media/ken/DC24-E9C1/boot" /dev/sdX 

Can someone tell me whats wrong with it? I am very noob to linux and this is all very frustrating. 

I really appreciate the help.

Is there really not an easy way to do this??? I cant believe this is so complicated.

I'm trying to follow this one as well. [http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

How in the heck did he get the windows recovery CD to boot up??

---

### Post by QIII on 2016-11-10
OK.  I misread you.

---

### Post by blacktophat33 on 2016-11-10
yes exactly. thats what i read to do anyways. im open to other strategies because i cant get it to work

---

### Post by yancek on 2016-11-10
What is the result of the command you posted above?  Do you get any warning or error messages?

> Thanks for the replys. I'm not sure what a menuentry is.

I posted a sample menuentry in my last post and indicated what you needed to change to get it to boot.  You can use that menuentry modified to suit your system in the grub.cfg file of the installed Ubuntu.  The problem with that is if your windows install fails, you will probably have overwritten that file in your attempt.  If the install works, you won't need it any longer.

>                           Is there really not an easy way to do this??? I cant believe this is so complicated.         


Well that's silly.  You're asking at an Ubuntu/Linux forum how to install windows.  The forum is for dealing with problems with Ubuntu/Linux.
The link you posted is about as simple as it gets for trying to boot the proprietary windows commercial system with Ubuntu/Linux.  
With Ubuntu or any Linux, you have the option to try it using a Live DVD or flash drive until you are familiar with it.  Looks like you installed before you understood the system.  This is one of the major reasons people either dual-boot or use virtual software first.

---

### Post by Bucky Ball on 2016-11-10
> **yancek said:**
> You're asking at an Ubuntu/Linux forum how to install windows.  The forum is for dealing with problems with Ubuntu/Linux.

That it is. At least the 'Ubuntu Specialised Support Forums' are. 

*Thread moved to **Windows**.*

You have a licensed copy of Windows? You can't set BIOS to boot from that disk? Windows will wipe whatever is on there if you can boot that disk and install.

If you do not have a licenced copy of Windows, of course, all bets are off. :)

Nothing to do with *buntu at this point. You need a legit Win disk and to boot from that. That is all.

---

### Post by mörgæs on 2016-11-11
You have not mentioned which problems you had in Ubuntu. Maybe they are not problems after all if you ask here ('here' meaning in a new thread in another forum, as this one is about Windows).

---

