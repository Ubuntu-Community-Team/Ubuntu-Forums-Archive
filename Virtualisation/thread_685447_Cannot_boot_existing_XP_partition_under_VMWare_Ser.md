---
title: "Cannot boot existing XP partition under VMWare Server in Ubuntu Gutsy"
date: 2008-02-02
forum: Virtualisation
---

### Post by vvvladut on 2008-02-02
Hi All,

I have a classic dual-boot configuration, with Windows XP and Ubuntu Gutsy (as I am a 'classic' case of the XP-to-Ubuntu-convert). I'm trying to virtualize my existing XP partition in Ubuntu. The key word here is *existing*; I don't want to create a new VM and install XP onto that, because I need my existing partition. Also, I really need to be able to still boot into XP, without it being messed up in any way because of virtualizing it - this is for my wife who does not believe in Ubuntu (yet!).

Now, I've tried a few tutorials, following each step carefully (although the tutorials seem to contradict each other on some of the steps). Here is a short list:

[http://blog.gobanquet.com/index.php/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/](http://blog.gobanquet.com/index.php/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/)
[http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/)
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)
[http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu)
[http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

What I have achieved so far is:

- Installed VMWare Server in Ubuntu; it works flawlessly with a number of other images (all sorts of Linux and BSD flavours)
- Made a VMWare hardware profile in XP and installed the drivers (although, once installed the drivers appear for both the VMWare profile and the standard profile - what is the point of hardware profiles anyway?)
- Created a XP virtual machine which reads from the existing physical partition
- Started it and got to Grub
- Selected XP and got past Grub, and apparently, got past the infamous 'inaccessible boot device' problem (code 07 or somethig like that); this, I hear, happens when the incorrect disk drivers are installed in XP
- Selected the VMWare hardware profile
- Then I got stuck on the splash screen with the Win logo and the blue progress bar; it does seem to load up for about 5 seconds, then the progress bar stops and nothing happens for about 30 seconds; then I get an error message (in VMWare, not XP) saying : "Operation on file /dev/sda failed (input/output error)", and the machine stops.

I have read hundreds of posts and threads on VMWare issues, but never have I read of this error message. This is why I'm turning to you for help.

This is my second post ever asking for help with Ubuntu; the first one was a bug report in Launchpad, which I got no response for. I'm still waiting to benefit from the great community support that Ubuntu, and Open Source in general is supposed to have. Can anyone help me with this? What am I doing wrong?

Many thanks!

---

### Post by vvvladut on 2008-02-05
...so much for the "great community support"...

---

### Post by e_james on 2008-02-05
Just a comment from a passerby. I suspect your problem is too unusual. It hasn't been noticed yet by someone with the appropriate knowledge. I stumbled across it because I am looking for information about a grub configuration bug - on some machines ubuntu configures grub in such a way that it can't start unbuntu.

---

### Post by noogen on 2008-02-05
I don't think this is a ubuntu issue but a vmware issue.  In your case, it is better for you to install windows xp to vmware yourself.  Your partition and dual boot makes the conversion more complicated.  I think the issue is that vmware had a hard time reading the converted image so it threw the io exception.  

Many things could happen with the conversion such as a bad parition where it cannot read a certain file at a certain location.  Even though you created a new hardware profile, your Windows could still be looking for the old driver and it took a long time to do it?  You can blame Windows for that.

---

### Post by vvvladut on 2008-02-05
Thank you for replying. I didn't say this was Ubuntu's fault, as a matter of fact every other Linux distro and BSD OS that I've tried to virtualize worked unexpectedly well. I suspect this is one of the myriad of problems Windows has. 

I was just hoping that someone else encountered the same problem, someone who is more tech savvy than I am. Still hoping...

---

### Post by ponartur on 2008-02-29
hi,

you just saved me 2-3 hours of frustrations - I have the same problem - Ubuntu and XP, on Ubuntu I installed vmware tried to access XP. I got message XP OS not found. From what I understand - vmware asks to istall XP AFTER their application install? does it make any sense? i do not know, I do not know how to solve this issue without reistalling XP

Kind Regards,

---

### Post by vvvladut on 2008-02-29
I don't think it's the same, mine can find the OS very well, it just freezes up mid-boot...

---

### Post by popch on 2008-02-29
It appears that you are using not a partition of a disk to run XP from, but the whole disk. In that case, Windows XP might be trying to write to the disk and Linux protects the disk by preventing that.

Try and run Windows in your virtual machine from a partition (such as /dev/hda1).

---

### Post by vvvladut on 2008-02-29
popch - What do you mean? What should I do to make sure I only use the XP partition? How can I be using the entire disk?

Thanks

---

### Post by popch on 2008-02-29
> **vvvladut said:**
> popch - What do you mean? What should I do to make sure I only use the XP partition? How can I be using the entire disk?

Thanks

In your first post, you mention  > then I get an error message (in VMWare, not XP) saying : "Operation on file /dev/sda failed (input/output error)"

Your message mentions /dev/sda which is all of your disk. I suggested you use /dev/sda1 which is the first partition on that disk.

Got to the place where you attached /dev/sda to you virtual machine and change that to /dev/sda1, then try again.

---

