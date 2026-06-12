---
title: "Virtual box error: FATAL no bootable medium found mean in a virtual box ?"
date: 2016-11-26
forum: Virtualisation
---

### Post by flex567 on 2016-11-26
I am using Oracle VMVirtual box and created a new Ubunut virtual box, when I try to run it I get:
> 
 FATAL no bootable medium found mean in a virtual box. System halted 

How can I fix this ?

---

### Post by howefield on 2016-11-26
Moved to the "*Virtualisation*" forum for a better fit.

---

### Post by &amp;KyT$0P# on 2016-11-26
Put the Ubuntu ISO image in the VM's virtual optical drive.

If you're not sure how to do that, [this thread]("https://ubuntuforums.org/showthread.php?t=2343126") might help you.

---

### Post by flex567 on 2016-11-26
I need an ISO image?

---

### Post by kpatz on 2016-11-26
When you create a VM it's like a brand new computer with an empty hard drive.  It won't boot until you install an OS on it,  usually from an ISO image which is an image of an installation CD/DVD.  You can download the Ubuntu ISO from here: [https://www.ubuntu.com/download](https://www.ubuntu.com/download)  Attach the image to the VM's optical drive (the virtual equivalent of sticking a CD in the drive in a physical machine), then start the VM and it will boot from the image.  From there you can install Ubuntu to the virtual hard drive.

---

### Post by flex567 on 2016-11-26
I had a look at the link and I think I should click the disk icon in Virtual Box interface - I right clicked Ubuntu and clicked Setting>Storage and clicked Ubuntu.vdi and everything is greyed out. So I cannot reference the path to Ubuntu iso.

[[img]https://s13.postimg.org/ne2k7izhf/temp.jpg[/img]](https://postimg.org/image/ne2k7izhf/)

---

### Post by &amp;KyT$0P# on 2016-11-26
That VM is in "Saved" state.  Since it has no OS, and therefore you've nothing to lose on it, try powering it off.  Close the VM using the window's close button, and you'll get a prompt allowing you to power it off.

Now, let's take another look at the screenshot I posted in the other thread.  Here it is again.
[ATTACH=CONFIG]272394[/ATTACH]
You were editing your VM's hard drive settings.  It's the **optical drive** you want to edit here - where it says "Host Drive TSSTcorp CDDVDW ..." in your screenshot.

---

### Post by flex567 on 2016-11-26
I tried to referencu Ubuntu iso but I get this error?

[ATTACH=CONFIG]272398[/ATTACH]

---

### Post by &amp;KyT$0P# on 2016-11-26
You are still trying to modify your VM's hard drive.  As you have discovered, that won't help here.

You need to modify your VM's optical drive.  The one with the CD icon.  The one you have under "Controller: IDE".

---

### Post by flex567 on 2016-11-26
aha, thanx now it works

---

### Post by &amp;KyT$0P# on 2016-11-26
You're welcome. :KS

---

