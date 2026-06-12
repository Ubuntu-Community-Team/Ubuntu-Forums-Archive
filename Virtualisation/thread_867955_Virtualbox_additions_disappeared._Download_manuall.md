---
title: "Virtualbox additions disappeared. Download manually?"
date: 2008-07-23
forum: Virtualisation
---

### Post by kramer65 on 2008-07-23
Hello,


I have virtualbox installed with windows xp in it. The problem is that it doesn't capture my mouse. It says I need to install the additions.

So I clicked on Devices > Install Guest Additions and accepted to download it. After that, I followed [this tutorial]("http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/") and did as followes:


```
cd /media/cdrom
sudo bash ./VBoxLinux*
```

but I got some error. I think it said that it didn't exist or something.

I was pretty tired, went to bed, and thought I would try it later again. Today I wanted to do it again and tried again to clicked Devices > Install Guest Additions, but nothing happens. Not after waiting for quite a while (now more than 15 minutes). Also, when I run the second command again it says it is not there.

Does anybody know where I can maybe download that iso manually? Or is there another way of solving this?

---

### Post by gbold on 2008-07-23
On the settings page for the virtual machine, under CD/DVD-ROM select mount cd/dvd->iso image file-> VBoxGuestAdditions.iso... then start the machine and it should appear for the cd drive...
Greg

---

### Post by kramer65 on 2008-07-23
I then get:

FATAL: No bootable medium found! System halted.

---

### Post by kramer65 on 2008-07-23
Any more ideas?

---

### Post by gbold on 2008-07-23
Do you have the 1st boot device to be the hard drive?  If XP is set up in a virtual box, it shouldn't give you that error...
Greg

---

### Post by kramer65 on 2008-07-25
I now have moved the hard drive up to be the first boot device, and on the settings page for the virtual machine, under CD/DVD-ROM I selected mount cd/dvd->iso image file-> VBoxGuestAdditions.iso like you suggested.

I now started up the virtual machine. XP simply starts up, but my mouse is still not captured and when I mouse-over over the mouse image on the bottom right of the screen, the message still says: "Note that themouse integration feature requires Guest Additions to be installed in the guest OS."

I thought I could get rid of xp on my harddrive (as a real partition) and only boot it up within ubuntu when I desparately needed one thing. Everything seems to work perfect, except for this simple mouse thing, which turns out to be quite essential.

Do you (or anybody else) know any other way of getting this to work?

---

### Post by robertchahine on 2008-07-25
when i had this problem with the mouse, i press right Ctrl, and everything worked.
But if it stills don't work, try to install the vboxguestaddons with your keyboard,i don't think it's hard.

---

### Post by kramer65 on 2008-07-25
I clicked the right control a couple times but that just captures the keyboard, and not the mouse.

I would love to install the additions with the keyboard. But how can I?

Also, I already clicked Devices > Install Guest Additions about a million times. After the first time when it actually downloaded and seemed to install, clicking that menu option doesn't do anything anymore now..

Is it correct by the way that the additions are only 5.05MB?

---

### Post by sbs9 on 2008-08-05
> **kramer65 said:**
> I now have moved the hard drive up to be the first boot device, and on the settings page for the virtual machine, under CD/DVD-ROM I selected mount cd/dvd->iso image file-> VBoxGuestAdditions.iso like you suggested.

I now started up the virtual machine. XP simply starts up, but my mouse is still not captured and when I mouse-over over the mouse image on the bottom right of the screen, the message still says: "Note that themouse integration feature requires Guest Additions to be installed in the guest OS."


Simply mounting the drive doesn't install the software.  Open the drive in My Computer and autorun will install the additions.

I'm pretty sure that clicking the menu item used to download and install the additions, so this is something that has changed recently in VBox.

---

### Post by kramer65 on 2008-08-06
Allright, that was it indeed! It took me a while to understand what mounting meant..

I guess it is just a thing of understanding what I am doing. Nowadays also people like me are drawn to Linux you know. You might see this as a blessing, or as a curse.. ;)

Thanks anyway!!

---

### Post by mathew42 on 2008-11-14
I found that the download option didn't work for me, so I had to
[LIST=1]
[*]visit this url: [http://download.virtualbox.org/virtualbox/2.0.4/](http://download.virtualbox.org/virtualbox/2.0.4/)
[*]download VBoxGuestAdditions_2.0.4.iso file
[*]copy file to /usr/share/virtualbox
[*]rename the file to VBoxGuestAdditions.iso
[/LIST]
Hopefully this will save someone else some frustration.

---

### Post by Shazaam on 2008-11-14
For those reading this thread...
Guest additions still comes with VirtualBox; no need to download it. The problem is when you try to set GuestAdditions to mount in the vm settings window. Vbox used to auto-fill in the location but no longer. You have to use the folder icon to the right of the box to locate it. It is at...

/usr/share/virtualbox/VBoxGuestAdditions.iso

---

### Post by mathew42 on 2008-11-17
Guest additions didn't come with VirtualBox in a fresh install of Ubuntu 8.10 for me and at least one other person. I checked /usr/share/virtualbox and the other directory that was suggested.

---

### Post by Parksy on 2008-12-13
matthew42, thanks for posting the link to the ISO file.  I couldn't find it in 8.10 either and I was wondering if I had lost my mind. :-)

---

### Post by ShivamSemwal on 2008-12-23
> **mathew42 said:**
> I found that the download option didn't work for me, so I had to
[LIST=1]
[*]visit this url: [http://download.virtualbox.org/virtualbox/2.0.4/](http://download.virtualbox.org/virtualbox/2.0.4/)
[*]download VBoxGuestAdditions_2.0.4.iso file
[*]copy file to /usr/share/virtualbox
[*]rename the file to VBoxGuestAdditions.iso
[/LIST]
Hopefully this will save someone else some frustration.
Hi I am new to ubuntu, i tried to download VBoxGuestAdditions_2.0.4.iso but do to some error "source file not found" the download was stopped ;this happened not just once but every time (once at 90 %) ,can you please send me the file by mail or any other source...............

---

### Post by VirtualEdgar on 2008-12-27
Me too! I can't seem to download on the link mentioned. Is there another source?

---

### Post by chmac on 2010-06-04
I just installed virtualbox 3.2.0 on 10.04 Lucid and I'm missing VBoxGuestAdditions.iso. I found what I believe to be the correct file here:
[http://download.virtualbox.org/virtualbox/3.2.0/](http://download.virtualbox.org/virtualbox/3.2.0/)

If you're looking for a different version, check this url and choose your version:
[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

---

