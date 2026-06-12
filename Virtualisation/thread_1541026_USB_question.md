---
title: "USB question"
date: 2010-07-28
forum: Virtualisation
---

### Post by Meow27 on 2010-07-28
Hi, i recently opened up my FlyFusion Pentop pen, its a USB device that basically records what i write on proprietary notebooks. anyhow i wanted to try it out on my XP-guest, but when i connect the pen, i have no idea whether the guest OS is recognizing it.(it doesn't seem to)

im not exactly sure how USB mode of virtualbox works. i have never actually seen it in action so i dont know the proper questions to ask aside for a guide.

here are the specs

VBOX 3.2.6
guest -windows XP sp3
guest additions - 3.2.6
host- Ubuntu 10.4 lynx


thanks in advance

---

### Post by fjgaude on 2010-07-28
Do you have an Install disk for the pen? Likely does as a Windows program. I don't use VBox but there should be some menu for Removeable Devices that permits attachment of the USB. After that you would load the device software that comes with the pen.

---

### Post by Meow27 on 2010-07-28
yeah i have the driver and everything. 

on the guest side, everything should be functioning normally but its not. i think im doing something wrong on the guests end... but i just don't know.

edit-------
to be more precise, if i plug in my flash drive, it isn't recognized as a separate drive on the guest machine.

---

### Post by Ginsu543 on 2010-07-29
Sorry if this is a stupid question, but have you made sure you have your pen selected under Devices --> USB Devices? If not, your Windows guest won't recognize it.

---

### Post by Meow27 on 2010-07-29
> **Ginsu543 said:**
> Sorry if this is a stupid question, but have you made sure you have your pen selected under Devices --> USB Devices? If not, your Windows guest won't recognize it.

everything is grayed out (you can see some of the grayed out things on your screenie as well.)

both of the general usb settings are checked (by defualt)

remember. i have a usb flash drive on board, and i cant even get THAT to work (not the objective but its something universal.)

it was not a stupid question :)

---

### Post by JKyleOKC on 2010-07-29
Are you using the VirtualBox OSE from the repositories, or VirtualBox PUEL from Oracle's VBox web site? The OSE (Open Source Edition) does not support USB, while the PUEL version (which is also free) does. Since you report that all the devices are grayed out, I suspect you have the OSE.

You can replace it with the PUEL version without losing your virtual machines. Just shut them all down or save their state, then go to [http://www.virtualbox.org/](http://www.virtualbox.org/) and find the linux-downloads page. There, you'll find the files and also instructions on adding their site to your repository list so that you'll be notified of updates.

After downloading the appropriate file, double-click it to install. It will ask you for permission to delete the installed version first; tell it "yes." Your VMs won't be harmed. Once the PUEL version is installed, start your VMs again. Go to the "Devices" menu and choose the item to install guest additions. You should then be able to use USB devices with no problem.

Hope this helps!

---

### Post by Meow27 on 2010-07-29
> **JKyleOKC said:**
> Are you using the VirtualBox OSE from the repositories, or VirtualBox PUEL from Oracle's VBox web site? The OSE (Open Source Edition) does not support USB, while the PUEL version (which is also free) does. Since you report that all the devices are grayed out, I suspect you have the OSE.

You can replace it with the PUEL version without losing your virtual machines. Just shut them all down or save their state, then go to [http://www.virtualbox.org/](http://www.virtualbox.org/) and find the linux-downloads page. There, you'll find the files and also instructions on adding their site to your repository list so that you'll be notified of updates.

After downloading the appropriate file, double-click it to install. It will ask you for permission to delete the installed version first; tell it "yes." Your VMs won't be harmed. Once the PUEL version is installed, start your VMs again. Go to the "Devices" menu and choose the item to install guest additions. You should then be able to use USB devices with no problem.

Hope this helps!
i thought it was clear i was using the PUEL version when i stated the version number :/

anyhow im sure im doing something wrong but i just dont know..

---

### Post by JKyleOKC on 2010-07-29
Have you created any USB filters in the VBox "Settings" area? I have one VM that I never created any filter for, and it doesn't show anything at all for the Devices->USB menu choice. Those that do have a filter set up work as expected, so if you don't have a filter that might be the problem.

The VM has to be powered down before you can create the filter. Then open the Settings menu in VBox, select USB Devices, and click the "Add filter" button. Leave all the fields empty, so that the filter will match any device at all, then close out of the settings area and start the VM again to see if that makes a difference.

Sorry I missed the version reference in your initial message!

---

### Post by Meow27 on 2010-07-29
> **JKyleOKC said:**
> Have you created any USB filters in the VBox "Settings" area? I have one VM that I never created any filter for, and it doesn't show anything at all for the Devices->USB menu choice. Those that do have a filter set up work as expected, so if you don't have a filter that might be the problem.

The VM has to be powered down before you can create the filter. Then open the Settings menu in VBox, select USB Devices, and click the "Add filter" button. Leave all the fields empty, so that the filter will match any device at all, then close out of the settings area and start the VM again to see if that makes a difference.

Sorry I missed the version reference in your initial message!

tried doing specific filters, tried doing what you just suggested. both don't work

ill try making a desktop video illustrating my setup. (would be nice to know what video formats i can use and where i can dump em :) )


i dont know if this makes a difference, but im doing this on my laptop

the VM image is running from my external harddrive. 
everything else is running from a usb hub (since i have only have two ports)

so here is the illustration

USB1 --> external HD

           - mouse
USB2 - HUB - flash memory
           - Fly fusion pentop pen

yes i tried connecting the pen directly before and still had the same results.

---

### Post by Meow27 on 2010-07-29
ah i finally found the solution here!

[http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)


thanks to everyone that attempted to solve my problem :3

---

### Post by primetime34 on 2010-07-29
I am having the same problem, but even though I used the solution in the above post, it didn't fix the problem for me.  My two usb devices are still greyed out.  Any help?

---

### Post by Meow27 on 2010-07-30
i dont mean to sound like a nimrod, but did you reboot?

---

