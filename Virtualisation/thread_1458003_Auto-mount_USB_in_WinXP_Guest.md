---
title: "Auto-mount USB in WinXP Guest"
date: 2010-04-19
forum: Virtualisation
---

### Post by psilokan on 2010-04-19
Hi

I have my Ubuntu box set up to automatically launch my XP Guest session when it boots up.  Problem is I can't figure out how to automatically reconnect the USB devices.  I'm not sure but I think this may have to do with Ubuntu automatically mounting them itself.  Before I connect them in XP I always first right click them on the Gnome desktop and unmount them.

I've been googling this and no luck :(

---

### Post by Morbius1 on 2010-04-19
If you truly want to automount then try this method:

> **Morbius1 said:**
> You can access a usb drive from a guest OS in virtual box OSE as long as the host is linux:

_LINUX HOST_
Using the VBox application create a Shared Folder to /media:
Folder Path: /media
Folder Name: hostmedia ( or whatever you choose )

_WinXP GUEST_
Open My Computer

Select Tools
Select Map Network Drive
Drive: Select an available Drive Letter
Folder: Select Browse. You will notice that there is a listing titled VirtualBox Shared Folders. Within that will be the shared folder "hostmedia" you created above.
check Reconnect at login

Every time you boot into the WinXP guest your shared folder created from /media will show up as a drive letter. Within that will be any usb device mounted on the linux host . 

[COLOR=Blue]There's also a side benefit. You'll always know who is in charge of the mounted / unmounted device - it's always the host.[/COLOR]

---

### Post by psilokan on 2010-04-19
Hey, thanks for the reply!

> **Morbius1 said:**
> If you truly want to automount then try this method:

You make it sound like I'm just pretending that I want to auto mount it when really I dont.

> **Morbius1 said:**
> You can access a usb drive from a guest OS in virtual box OSE as long as the host is linux:

You mention this is for VBox OSE, which I found very odd because you can't share USB devices with OSE.  I learned that the hard way.  

Either way this whole method sounds very odd.  It sounds like you're talking about mounting a USB hard drive or something when this is a VOIP phone.  So I don't even want the Host to "be in charge" as it is not Linux compatible.  

Aside from that, I also should have mentioned (didn't think it would be necessary) is that there are actually three of the same device plugged in and three XP Guest OSes.  Each Guest will be assigned one VOIP phone. Since each Guest only is to connect to one device, I would think following this advice would result in each Guest trying to mount all 3 devices at the same time, which would not work.

Is there any other way to do this? I honestly expected a checkbox saying "Auto connect USB device on boot" and was quite surprised no such thing existed.

---

### Post by Morbius1 on 2010-04-19
> You mention this is for VBox OSE, which I found very odd because you can't share USB devices with OSE. I learned that the hard way.You can share a USB device with OSE, this method proves it.

> Either way this whole method sounds very odd. It sounds like you're talking about mounting a USB hard drive or something when this is a VOIP phone. So I don't even want the Host to "be in charge" as it is not Linux compatible.I am talking about a USB Storage device. You never mentioned anything about VOIP in your original post.

You have a nice day.

---

### Post by psilokan on 2010-04-19
I could probably dig up a dozen links that will dispute this fact about USB in OSE.  I went through a lot of frustration with OSE and hosed it in favour of the closed source version.  To me that doesn't sound like sharing USB in OSE, it's simply sharing a folder from Host to Guest.  But that's another topic altogether.

And no I didn't mention that it's VOIP, but I also didn't say it was a hard drive ;)  I have a hard time believe there's no way to do this for USB devices that are not hard drives.

Anyone else have any ideas?

---

### Post by reiki on 2010-04-21
In the USB section of the machine settings, create a filter for your particular USB device. Instructions are in the VBox documentation. Once you have the filter created, any time that particular device is connected, it will be taken by the virtual machine.

I had to do this in a winddows VM (on Ubuntu host) for a universal remote that I use and it is USB programmable. I could connect it using the Devices menu, but when it was being programmed it would reboot (normal) and when it did that, the Ubuntu host would grab it when it came back online and screw up the programming confirmation. So I created a filter and once that was in there, every time that remote was connected and teh VM was running, the VM had control of the remote.

Does that sound like what you need?

---

