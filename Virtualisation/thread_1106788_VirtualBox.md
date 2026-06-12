---
title: "VirtualBox"
date: 2009-03-26
forum: Virtualisation
---

### Post by lmoreira on 2009-03-26
Hi All,
I have installed VBox and a guest XP OS to run a couple of programs I can not make work using wine. Everything works great, but I hit a small problem. When I insert the installation disk on the CD drive I can see it on the XP environment but when I explore the CD some files are not shown and infact the setup file as changed and I can not install the application. Do I need to change some setting to be able to install applications on the guest OS or do I need to get the installation CD in another format like ISO?
Best Regards
             Luis

---

### Post by lmoreira on 2009-03-26
Hi All,
I have installed VBox and a guest XP OS to run a couple of programs I can not make work using wine. Everything works great, but I hit a small problem. When I insert the installation disk on the CD drive I can see it on the XP environment but when I explore the CD some files are not shown and infact the setup file as changed and I can not install the application. Do I need to change some setting to be able to install applications on the guest OS or do I need to get the installation CD in another format like ISO?
Best Regards
Luis

---

### Post by 3Miro on 2009-03-26
There is nothing special that you need to do to install programs on the guest. If there is a problem, try manually mounting the media. Insert the disk and mount it under Linux (either right click on the desktop icon or just explore it with nautilus). Then start XP from VB and select Device -> Mount cdrom.

Note that you might have couple of different CD-ROMs visible under windows.

---

### Post by tang0delta on 2009-03-26
Luis, 

To my knowledge a CD should work as normal, as though you were actually viewing it in XP. Maybe you need to enable the setting for the guest OS which allows it to directly access the hardware interface  for your CD-ROM/DVD drive? Its just a simple checkbox somewhere in the preferences menu for your guest OS. I'll try and find it now...

Delcan

EDIT: reconsidered, that probably isn't your problem. Maybe you have a bad install disk for the application? have you ever used it in a real windows environment?

---

### Post by overdrank on 2009-03-26
Please do not create multiple threads on the same issue. Threads merged.

---

### Post by kpatz on 2009-03-26
How do you have the CD/DVD drive configured in the settings for the virtual machine?

See my attached screenshot.  You can either have the host machine's CD/DVD drive mounted to the VM, or an ISO image.  If you're trying to install something from an actual disc, make sure you mount the actual drive to the VM.  If you're installing from an ISO, make sure you have the ISO file mounted.

---

### Post by lmoreira on 2009-03-26
Hi Overdrank,
Apologies for the duplication of the topic but I realised that this subforum was the best place for this post after I post it in the general one.

Hi kpatz,
I did mount the CD drive and I can see the CD but not all the files. I already tried to install this application using Wine and it did install is just that it does not work well. I can see all the files fine under Linux, but not all of them in the windows OS.

Hi Delcan,
I have installed from this disk in Windows with no problems, and also using Wine with no installation problems, hence I think the disk is fine. It almost seems some kind of permission issue, the only thing I can see is the datasheets installation but the program itself is not visible on the guest OS. The other interesting thing is that if I start the setup the option of installing the application as disappeared I can only install the datasheets.

Hi 3Miro,
I have tried that.

thank you all for your help.
Best Regards to all,

                    Luis

---

