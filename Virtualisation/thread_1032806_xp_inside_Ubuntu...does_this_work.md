---
title: "xp inside Ubuntu...does this work?"
date: 2009-01-06
forum: Virtualisation
---

### Post by ibexslam on 2009-01-06
I've got these two new HP Pavilion a6650f desktops here for my business.  We have a small network of computers running xp.  The new machines have that darned vista on them, which we don't want.  For the time being, we can get xp.  OK.  But I'm told that xp drivers for these computers don't exist.  Great.

I am in no way a fan of xp, but we need it.  I do intend to also have Ubuntu in some form on these machines.

Which leads me to my question.  Would it be possible to run xp virtually inside Ubuntu on these machines, using Ubuntu's drivers to interact with the hardware?  Would something like this help, or would it just make everything more complicated?

I'll be the first to admit I'm quite ignorant on this topic.

I.

---

### Post by albinootje on 2009-01-06
> **ibexslam said:**
>  Which leads me to my question.  Would it be possible to run xp virtually inside Ubuntu on these machines, using Ubuntu's drivers to interact with the hardware?  Would something like this help, or would it just make everything more complicated?


It's fairly easy with VirtualBox.
[http://www.virtualbox.org](http://www.virtualbox.org)

The open source version is included in the Ubuntu repositories.
Make sure you install the Guest Additions in your XP Virtual Machine to have the full screen option, and the mouse intregration.

---

### Post by TheUnabeefer on 2009-01-06
I have Ubuntu (Kubuntu to be exact) on both my desktop and my laptop... and XP running in both of those.

VirtualBox.  Install "virtualbox-ose"  It works like a charm.

Then I suggest, once WinXP is set up (quite easy to do, oddly), download the iso for the guest additions and install those.  (The menu in the virtual machine has a "install guest additions" menu option, it will also tell you where it wants you to put the iso, I think it's /var/share/virtualbox, but I am probably wrong)  This will allow you more freedom with your machine.

Ask questions if you have any, it's a commonly used program.... and open source, afaik.

---

### Post by albinootje on 2009-01-06
> **TheUnabeefer said:**
>  Then I suggest, once WinXP is set up (quite easy to do, oddly), download the iso for the guest additions and install those.  (The menu in the virtual machine has a "install guest additions" menu option, it will also tell you where it wants you to put the iso, 
I thought the guest additions iso image was included. Not in the OSE version ?

FYI. In the PUEL version of VirtualBox it's here :
/usr/share/virtualbox/VBoxGuestAdditions.iso

Here's a howto with screenshots :
[http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/)

---

### Post by dcstar on 2009-01-07
> **ibexslam said:**
> 
........
Which leads me to my question.  Would it be possible to run xp virtually inside Ubuntu on these machines, using Ubuntu's drivers to interact with the hardware?  Would something like this help, or would it just make everything more complicated?


The (free) VMWare server product will allow you to run XP (or whatever) inside VMs on a Ubuntu platform, and you can also use their free utility to convert existing Windows setups into VMs so you don't need to reinstall Windows or set up anything again.

I run my 32-bit XP Home on a VMWare Server 64-bit Ubuntu platform (along with various other VMs).

There are posts with detailed instructions in the forums and on the 'net on how to do this sort of thing.

---

### Post by ibexslam on 2009-01-07
Sounds like we're definitely on to something.  Thanks for your assistance, folks!

I.

---

### Post by wizard10000 on 2009-01-07
Here's a picture of a desktop cube running Gutsy, Hardy, XP and Vista.  Took two computers and a KVM switch to pull it off, though.

I have entirely too much time on my hands sometimes  :)

[IMG]http://ebassist.com/pix/desktop-virtualbox-both.jpg[/IMG]

---

### Post by NumPy on 2009-01-07
As everyone else said, it is possible and works great. I have a tutorial posted for it as well. 

[http://numpys.blogspot.com/2009/01/virtualization-and-rest-of-us-part-2.html]("http://numpys.blogspot.com/2009/01/virtualization-and-rest-of-us-part-2.html")

take care.

---

### Post by thomasr on 2009-01-07
Be aware that you will have to activate/reactivate windows in the vmware or virtual box install.

---

