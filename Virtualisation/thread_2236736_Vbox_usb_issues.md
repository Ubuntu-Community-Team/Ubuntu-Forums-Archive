---
title: "Vbox usb issues"
date: 2014-07-28
forum: Virtualisation
---

### Post by toneykg on 2014-07-28
Greetings
Installed VBOX and XP (free download from MS go figure, as are other including WIN 8)
Vbox works fine as does XP
but i can not get the usb ports working

$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 10f1:1a43 Importek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ VBoxManage list extpacks
Extension Packs: 1
Pack no. 0:   Oracle VM VirtualBox Extension Pack
Version:      4.3.14
Revision:     95030
Edition:      
Description:  USB 2.0 Host Controller, Host Webcam, VirtualBox RDP, PXE ROM with E1000 support.
VRDE Module:  VBoxVRDP
Usable:       true 
Why unusable: 

$ VBoxManage list usbhost |more
Host USB Devices:

UUID:               6b3e7a28-0df8-4d5b-97d3-6714ee8c76ba
VendorId:           0x10f1 (10F1)
ProductId:          0x1a43 (1A43)
Revision:           18.18 (1818)
Port:               2
USB version/speed:  2/2
Manufacturer:       Importek
Product:            TOSHIBA Web Camera - HD
Address:            sysfs:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3//d
evice:/dev/vboxusb/001/003
Current State:      Busy

So it appears via term output i have the required 2.0 ports, yet it only sees the toshiba webcam
Yes i used the PUEL ver of VBOX and installed the usb support ext
I added myself to VBOXUSERS
still i am not offered a usb port for selection via VBOX settings USB filters
My ports are blue indicating they are ver3.0 usb ports, which currently are not supported. have i misread the lsusb output? which shows both 2 and 3 available
Am i chasing my tail here?  Like Vbox but i need USB connection to work, i understand this is a non issue in VM.
So is my solution ditch Vbox and load VM or did i overlook something that will get Vbox working with USB 

TIA

---

### Post by dave131 on 2014-07-28
OOOPPPPSSS - my original reply here was not on the right track since you have already done those suggestions.

linux will show the ports it knows, but that doesn't mean VirtualBox can support them.  I see many threads on the net about USB 3 support lacking in VirtualBox.  Some are from he VirtualBox forums.  I currently don't know if the latest version from Oracle supports USB 3 or not. 

Do ANY ports show in VirtualBox or are you just not seeing the USB3 ports?

Connect a device to a USB 2 port and see if VirtualBox finds it.

Here's another question: are ALL of your USB ports USB 3(blue)?  If so, then the USB 2 port is actually just internal and used for the webcam only (assuming it's an internal web cam).  With that in mind, I would think that with the lack of USB 3 support in VirtualBox that you would not see your USB ports.  You might see your webcam - but even that might require a driver in your guest (XP) operating system.

Also - remember that by default the networking will be bridged (I think that's the correct term) so your internet connection will be live in XP.  Since XP is off support, I would DEFINETLY TURNOFF networking to your guest.  Not doing so leaves your XP vm wide open to the new attacks, not to mention I don't believe that Microsoft actually supports Microsoft Update on XP anymore, so you would not have ANY of the security updates since the version of XP you downloaded was created.

BTW - you can download things like Win 7 and Win 8 from Microsoft, but they still require a license key.  The Win 7 download will only run for "x" days and then disable itself.  I haven't tried the Windows 8 download, but I suspect it probably won't even install without the key.  If it does install, it will still be limited to "x" days.

---

### Post by ajgreeny on 2014-07-28
Make sure you are a member of the vboxusers group in your host, and then in the settings for your VM go to the USB settings and make sure USB are enabled in that.

All work fine in my system; I use it to update my TomTom satnav which does not work in Linux.

I have to go online to do that but I have a good snapshot of XP so should it become infected I will just use the snapshot; it's a great advantage of VMs.

---

### Post by dave131 on 2014-07-28
ajreeny - are you using USB 3?  I'd be curious to know that myself since all new hardward seems to ship with those.

Thanks!

---

### Post by ajgreeny on 2014-07-29
> **dave131 said:**
> ajreeny - are you using USB 3?  I'd be curious to know that myself since all new hardward seems to ship with those.

Thanks!
No sorry I am not, but I do have some USB3 ports so will try it out and report back asap.

---

### Post by toneykg on 2014-07-29
Dave131
No key required for WIN download, sure they die after 30 days. However once you have downloaded file just reinstall, some even have reloads that give you 90 days total
But as i only need windows for updating a couple of my items, i run ubuntu exclusively
All
Vbox settings only shows webcam, zero usb ports
guess i,m loading VW as it supports 3.0 usb

---

### Post by ajgreeny on 2014-07-29
OK, I have just tried with a USB external hard disk attached to a USB 3 port.

I had a notification bottom right of XP that it had been found and was ready and available but there was no way that I could find it in the file-manager of XP, so you may be correct.  I am baffled, however, that it was found by the XP system, but then not by me.

Any thoughts?

---

### Post by dave131 on 2014-07-29
I would look in the system details in XP and see what it shows for USB - see if it shows the controllers, etc..  It will say which type in the details for each controller.

> **toneykg said:**
> Dave131
No key required for WIN download, sure they die after 30 days. However once you have downloaded file just reinstall, some even have reloads that give you 90 days total
But as i only need windows for updating a couple of my items, i run ubuntu exclusively
All
Vbox settings only shows webcam, zero usb ports
guess i,m loading VW as it supports 3.0 usb

Yep - that's what I said - you need the key to keep them active.  You can download and install, but they will die.

---

### Post by ajgreeny on 2014-07-29
> **dave131 said:**
> I would look in the system details in XP and see what it shows for USB - see if it shows the controllers, etc..  It will say which type in the details for each controller.
Remind me how to do that, will you please.  It is so long since I have really used Windows that I have forgotten everything that used to come without a second thought, and the whole business of dealing with the system setup now baffles me so much.  I must admit, however, that it had never occurred to me that perhaps XP itself can not deal with USB3, though the icon showing new hardware found at bottom right suggests that XP can indeed see USB3 ports, and as it can see the port, why can it not also see the disk plugged into the USB3 port?

I feel just like a lot of people who have just started using Linux must feel; completely lost at many points, with nothing feeling as simple in Windows as it is in Ubuntu.

That's what happens after 9 years of Ubuntu use and no Windows, I suppose.

---

### Post by dave131 on 2014-07-29
click on start, look to the right - you should see an entry "My Computer" - right-click on that and select "Properties" (I *hope* I'm remembering correctly).  If it's not there, look for Control Panel.  Open it, select and rihgt-click on "My Computer" or "system" and select "Properties.  If the classic view is not showing -e.g. you're not seeing all the icons but instead just some groupings of text - like security, etc. - the look on the left side of the screen you should see an option for classic view.

i *think* that's it - I currently don't have a Windows installation - but I think that was it.  If nothing else perhaps it will "ring some bells" and you'll get there!

Sorry I can't give you exact instructions ;)

EDIT:  I just remembered:  you're looking for the device manager.  Under my computer/properties you made to select something like hardware and then the device manager - I really don't remember enough ;)

---

### Post by ajgreeny on 2014-07-30
Seems we're the blind leading the blind; thanks anyway.  I look into it next time I boot the VM of XP and report back again re the USB3 ports, and whether or not your suggestion leads me anywhere.

---

### Post by ajgreeny on 2014-07-30
I got no further with the XP Hardware device manager other than seeing the USB hard disk plugged in to a USB3 port reported as a mass storage device.  It is still not available in the XP file-manager however, so there is no way I can use it when plugged in to that port, only when in a USB2 port.

---

### Post by dave131 on 2014-07-31
Yeah - I'm sure it would require a USB3 driver at a minimum.  That's why I think the OP isn't finding anything - I think all of their USB ports are USB3.

Have a good one, and thanks!

---

### Post by Paul_Ezust on 2014-08-01
I have a similar problem with my trusty setup. I apologize for the length of my reply but I think it might save time in the long run.
Host System: kubuntu 14.04 (trusty)
Virtualbox version: 4.3.10_Ubuntur93012  (3/26/2014)
Virtualbox GuestAdditions: 4.3.10.0
Extension Pack:4.3.14r-95030
Guest OS: Windows7with latest updates
My host user is inthe vboxusers group.




From the menu bar above the vbox window:
    VirtualboxDevices-->USB Devices  lists four devices.
   Two are checked: Hewlett Packard USB2 Scanner [0100]
                        and  Seagate Expansion Disk [0100]
   Two are unchecked:  Logitech USB Receiver [2400]  
                                          (for my wireless mouse &#8211; which works fine)
                          and:   Generic USB2.0 CRW [8197]
 
My problem:  The two checked USB devices above cannot be accessed by the Guest system.
The Seagate drive can be accessed by the host system. I have not tried accessing the scanner from the Host system because it requires specialized software that only runs under Windows.
I've tried all possible combinations of reinstalling the components and rebooting both the host and guest. Nothing seems to make any difference. When I plug in the Seagate drive I see a message that says &#8220;USB device not recognized&#8221; and, of course, the drive does not show up in Windows Explorer. I keep the scanner plugged in all the time and when I try to scan something I get an error message that tells me that the USB cable is not connected.


Here is an interesting symptom: Today, after I reinstalled all of the vbox items listed above, I booted up Windows7 and plugged in the Seagate drive.After seeing the usual &#8220;USB device not recognized&#8221; message, I pulled down the Vbox Devices-->USB Devices menu and put an 'x' in the box next to Logitech USB Receiver. My mouse instantly froze on the screen and I had to shut down Windows7 before I could use my mouse again.


Prior to upgrading from Kubuntu 13.10 to 14.04, both USB devices worked reliably.
I've poked around inthe various forums and tried several of the suggested fixes and tweaks and have had no luck.
I've run out of ideas. 
Can anyone suggest something else for me to try?

---

### Post by Paul_Ezust on 2014-08-01
Sorry to reply to my own post but I solved my problem by removing the Ubuntu pkgs for virtualbox and virtualbox-guest-additions and, instead, used the virtualbox-4.3 pkg from from virtualbox.org.
To do that I had to add the line:   debhttp://download.virtualbox.org/virtualbox/debian trusty contrib    to   etc/apt/sources.list
I could not find  a direct-from-virtualbox.com  guest-additions pkg using apt-cache search.I also failed to find one on the virtualbox.com site.
But, when I ran the fresh version of vbox and booted up Windows7, there seemed to be a guest-additions pkg already installed and, best of all, both of my USB devices were accessible.
So, I am now a happy (but very tired) camper.

---

### Post by dave131 on 2014-08-02
Basically, you should just use the ones from Oracle.  I don't know - maybe that's where the virtualbox.org points to, but I seem to remember just going to the Oracle site and just downloading both.  I've never had a problem doing that way. I've never installed virtualbox from the repositories, nor from virtualbox.org.  I used to just go to the Sun site, but since they were bought by Oracle you now just go to the Oracle site.

I don't know others' experiences - just mine from the past.  i always went that way and didn't have problems.

---

### Post by ajgreeny on 2014-08-02
> **dave131 said:**
> Basically, you should just use the ones from Oracle.  I don't know - maybe that's where the virtualbox.org points to, but I seem to remember just going to the Oracle site and just downloading both.  I've never had a problem doing that way. I've never installed virtualbox from the repositories, nor from virtualbox.org.  I used to just go to the Sun site, but since they were bought by Oracle you now just go to the Oracle site.

I don't know others' experiences - just mine from the past.  i always went that way and didn't have problems.
Same here.

There was a time when the version from the repos was very crippled compared to the Oracle PUEL version, and that is still the case with the guest additions package, I believe.  However getting both direct from Oracle seems to solve many problems.

Unfortunately it does not solve the WinXP and USB3 difficulty, though it is not something that worries me as I still have many USB2 ports available.

---

