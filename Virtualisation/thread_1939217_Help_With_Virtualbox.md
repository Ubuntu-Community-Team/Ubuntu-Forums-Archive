---
title: "Help With Virtualbox"
date: 2012-03-11
forum: Virtualisation
---

### Post by wisdomlight on 2012-03-11
Hi,
Can any one point me to a good explanation [I am a complete newbee to computers and linux etc]
on how to install microsoft program [zune] on a virtual box ? 
I have downloaded and installed the virtual box 4.1 from the oracle site with the USB capability[as I read somewhere that the VBox from the ubuntu repository is not supporting USB]

But i do not know how to continue.
Any help is appreciated.

Thank you

---

### Post by howefield on 2012-03-11
Neither the repository .deb package nor the download from the virtualbox website support USB out of the box, but both do with the installation of the extension pack which is a separate download from the Virtualbox website.

Installing Windows programs in a VM is just the same as installing them in a native Windows installation. 

Have you created the Virtual Machine yet, ie, installed Windows ?

---

### Post by wisdomlight on 2012-03-11
Thank you for your reply,
Now ,
I downloaded both the Vbox version i.386 and AMD64 and only the first one[i.386] installed the other did not.
Finally I understood that I need to put my Win7 OS disc which I did, it then told me that it failed because of architecture.
It said something like I am attempting to load a 64 bit application however this CPU is not compatible with 64 bit application.

Now this is strange because this is the disc that came together and is installed on my computer
Hmmm
Puzzling words.

Any ideas?

Thank you for your help.

---

### Post by Old_Grey_Wolf on 2012-03-11
It appears the host OS is the 32-bit version of Ubuntu. You need to use the 64-bit version of Ubuntu in order to install the AMD64 version of Vbox and a 64-bit version of Windows 7 as a guest OS.

---

### Post by wisdomlight on 2012-03-11
Cool, just to confirm:
Uninstall my 32 bit version
Install 64 bit version.
Is there a11.10 64bit version or do I need to download an earlier Ubuntu version?
 
Does it mean loosing all my documents etc?
do I need to re partition hard disk
 
 
Thanks for support

---

### Post by Old_Grey_Wolf on 2012-03-11
Backup your documents, etc.

You can install the 64-bit version alongside the 32-bit version if you have enough disk space. You will need to re-partition the drive to add the second OS. Some versions of Ubuntu have an option when you install it to "Install them side by side"; which, does the partitioning for you.

There is a 64-bit version of 11.10.

---

### Post by wisdomlight on 2012-03-11
thank you so much.
you are making my Ubuntu experience very enjoyable.
 
it probably will take me a while before I can implement the suggestions but as soon as I'm back home i will give it a go.
 
Thank you

---

### Post by wisdomlight on 2012-03-13
Hi i have installed ubuntu 64-bit
starting VB and creating a machine which then loads the file,
it then thinks a little and i get the following

 windows boot manager appeared saying

 windows has failed to start and I should do few things and it gives the following announcements
1 insert the disc
2 choose the language
3 click  repair your comptuer

File: \windows\system32\boot\winload.exe
Status 0xc000035a
Info : attempting to load a 64-bit application however this CPU is not compatible with 64-bit mode

no mention of installing win7 on my Virtual Machine

Help

---

### Post by Old_Grey_Wolf on 2012-03-13
Did you install the AMD64 bit version of Virtualbox on your new 64-bit Ubuntu Host? Have you installed the Virtualbox extensions?

---

### Post by wisdomlight on 2012-03-14
the problem was in my Bios , needed to enable virtualization.

Now there is still the question of how do I install Zune on my virtual machine and how do I connect my windows phone 7 to it?

any ideas?

---

### Post by Old_Grey_Wolf on 2012-03-14
Using the Windows VM, download Zune from Zune.net. It should offer to install it for you.

If Zune is on a CD, then you will need to go to the Devices menu in VirtualBox and mount the CD drive.

---

