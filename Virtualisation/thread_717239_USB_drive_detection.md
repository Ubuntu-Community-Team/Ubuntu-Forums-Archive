---
title: "USB drive detection"
date: 2008-03-06
forum: Virtualisation
---

### Post by Matt26 on 2008-03-06
i am running VMware Workstation 6.0.2 build-59824 under Ubuntu 7.10, with Windows XP Pro SP2 as the guest OS. when i plug in my USB flash drive Ubuntu automatically recognizes it and mounts the volume- i then unmount the drive from Ubuntu and go into Workstation under VM/Removable Devices/USB Devices and select the flash drive that i want Windows XP to have control over. i get a warning message telling me that the host system has control over the drive first, then i see the removal devices icon in the Windows XP system tray indicating that the USB drive has been detected. when i go into My Computer, it doesn't show up, and i have tried several times to remove and re-add the USB drive with no luck. i have also checked under Device Manager and there are no unrecognized devices. it did work fine the first couple times i plugged it in after installing Workstation, but not since then. any ideas on what might be causing this issue? thanks.

---

### Post by fjgaude on 2008-03-06
Okay, as a test on my system, which I have done before, I am in vmware WinXP. I plug my USB flask drive into the computer's USB port. As soon as I do I get a Ubuntu screen showing the drive's contents.

Then in WinXP I click on VM/Removal Devices/USB Devices and then I click on the name of the flash drive. I then see that Ubuntu has let go of the device and it is now showing in WinXP Explorer as that same device.

Ubuntu let the vm have the drive after it is plugged in.

Let us know what happens with your setup.

---

### Post by Matt26 on 2008-03-06
yes, I have done that and I see the add/remove icon in the system tray but when I open My Computer the drive is not visible... I have tried removing the drivers and reinstalling as well as different USB ports with no luck- i can this same USB stick into another XP system and it works fine, plus i have had the same issue with a different USB flash on this vm (U3 enabled) so this may be either a hardware or config issue in XP.

---

### Post by fjgaude on 2008-03-06
On my system Ubuntu lets the vm take control of the drive.

Yes, something is different, wrong.

I have no suggestions.

---

### Post by Matt26 on 2008-03-07
i am not sure at this point if the issue would be more related to the host OS interaction with the flash drive, or workstation's handling of the drive when it is plugged in... i have turned off the options in Ubuntu that allow the OS to automatically mount and browse the contents of the flash drive so that workstation could take hold of it as soon as it plugged in but i get the same results.  any help would be greatly appreciated.

---

### Post by uberlube on 2008-03-07
I am very hopeful that this question gets answered. I need to use VMware or VirtualBOX to get a winxp desktop to sync with my new LG 800 chocolate as it is not supported in BITPIM. If anyone knows of another way to do it in linux id be much appreciated.

---

### Post by adityakavoor on 2008-03-07
> **fjgaude said:**
> Okay, as a test on my system, which I have done before, I am in vmware WinXP. I plug my USB flask drive into the computer's USB port. As soon as I do I get a Ubuntu screen showing the drive's contents.

Then in WinXP I click on VM/Removal Devices/USB Devices and then I click on the name of the flash drive. I then see that Ubuntu has let go of the device and it is now showing in WinXP Explorer as that same device.

Ubuntu let the vm have the drive after it is plugged in.

Let us know what happens with your setup.


VM/Removable Devices/USB devices shows empty :(

Please help

---

### Post by fjgaude on 2008-03-07
Here's what I did months ago to get USBs to fully work:

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Like so:

    	```

        mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Good to add this line into your guest .vmx file using text editor:

mainMem.useNamedFile=FALSE

Reboot!

You will have full copy, paste from host to and from guest, and USB device handling capability, drives, scanners, printers, etc.

Let us know how you are doing.

---

### Post by adityakavoor on 2008-03-07
> **fjgaude said:**
> 

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Good to add this line into your guest .vmx file using text editor:

mainMem.useNamedFile=FALSE

Reboot!

You will have full copy, paste from host to and from guest, and USB device handling capability, drives, scanners, printers, etc.

Let us know how you are doing.

where to find the fstab file and the guest .vmx file ?

---

### Post by Matt26 on 2008-03-07
fstab file is located under /etc directory... if you look under vm settings in Workstation you should see a section that points to where the .vmx file is being loaded from.

---

### Post by adityakavoor on 2008-03-07
Noooooo , nothing worked . 

VM/Removable Devices/USB is still empty

---

### Post by Matt26 on 2008-03-07
> **adityakavoor said:**
> Noooooo , nothing worked . 

VM/Removable Devices/USB is still empty

have you already applied the fixes suggested by fjgaude?  i only ask because i was planning to do the same the next time i am at my computer to see if it would work :)

---

### Post by adityakavoor on 2008-03-07
> **Matt26 said:**
> have you already applied the fixes suggested by fjgaude?  i only ask because i was planning to do the same the next time i am at my computer to see if it would work :)

yes I did, But didnt work

---

### Post by adityakavoor on 2008-03-07
I resorted the safer way and samba shared the two OS's.

No need of usb now :popcorn:

---

### Post by fjgaude on 2008-03-07
Yes, but USB support for scanners and printers and the like is so needed by so many folks.

Most people have gotten USB to work with the suggested changes made.

Someone needs to write a very detailed HOW-TO, making no assumptions about the readers knowledge, to get us all through the process.

I do believe Hardy Haron, 8.04 in alpha 6 now, has all these fixes already contained within it. I'll check to make sure.

---

### Post by adityakavoor on 2008-03-07
Here it is.. Yippie

I got usb to work also. :) 

step 1: Edit Virtual machine settings

step 2: Select Hardware tab

step 3: See below .. click on Add

step 4: select USB controller

step 5: VM/Removal Devices/USB Devices and then I click on the name of the flash drive.

Enjoy :popcorn:

---

### Post by adityakavoor on 2008-03-07
**fjgaude :**

Can you tell me how to increse the video memory size of guest OS win xp ?

---

### Post by fjgaude on 2008-03-08
I don't know of a way to increase video memory size. VMware uses a software emulation of your video card and likely has no need to increase the memory, it is irrelevant.

---

### Post by Matt26 on 2008-03-10
> **fjgaude said:**
> Here's what I did months ago to get USBs to fully work:

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Like so:

    	```

        mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Good to add this line into your guest .vmx file using text editor:

mainMem.useNamedFile=FALSE

Reboot!

You will have full copy, paste from host to and from guest, and USB device handling capability, drives, scanners, printers, etc.

Let us know how you are doing.

unfortunately this did not work for me either- my windows xp vm will still detect that the USB flash drive was plugged in, but still nothing shows up in My Computer.

---

### Post by fjgaude on 2008-03-10
Did you look in Windows Control under Printers and Faxes?

You did reboot?

---

### Post by Matt26 on 2008-03-10
yes i did a reboot- why would it show up under Printers and Faxes... it is a removal storage device....

---

### Post by djbon2112 on 2008-03-11
> **fjgaude said:**
> <snip the tutorial>
Hey, I've got a Motorola Q Smartphone connected via USB that I'm trying to get working in VMWare. This seems to work, however, when I select the device in the VM -> Removable Devices menu, it connects and then disconnects rapidly (along with the entry in the VM -> Removable Devices menu disappearing then quickly reappearing), and continually repeats this until I disconnect the device or disable the entry in the menu (during the time when it's there). Any suggestions?

On the plus side though, copy + paste to and from the VM now works (it didn't before)

---

### Post by Matt26 on 2008-03-11
> **adityakavoor said:**
> Here it is.. Yippie

I got usb to work also. :) 

step 1: Edit Virtual machine settings

step 2: Select Hardware tab

step 3: See below .. click on Add

step 4: select USB controller

step 5: VM/Removal Devices/USB Devices and then I click on the name of the flash drive.

Enjoy :popcorn:

did you need to turn off your vm to accomplish this?  did you have to remove your existing USB controller first before adding the new one, as i tried adding a new USB controller when the vm was turned off but it was grayed out until i removed the existing controller in the hardware list.

---

### Post by fjgaude on 2008-03-11
> **Matt26 said:**
> yes i did a reboot- why would it show up under Printers and Faxes... it is a removal storage device....

Well, I was thinking the device was a printer or scanner, but it is a drive.

Sorry about that.

---

### Post by djbon2112 on 2008-03-12
Hey sorry to bump, but anyone have any ideas as to my problem? I'm trying to get this solved as soon as I can since this is the only way I can update my phone to fix a DST error!

---

### Post by fjgaude on 2008-03-12
You did put this line in your /etc/fstab file:

```
usbfs /proc/bus/usb usbfs   auto      0       0
```

Seems like this has worked for just about everyone.

---

### Post by djbon2112 on 2008-03-12
Yep. Though, I'm starting to doubt it's my computer. NOTHING to connect this freaking Q to Linux is working. Not SynCE, not WDDrive or whatever it is, it won't connect in VM, a random Bluetooth adapter I bought could neither detect or be detected by it, nothing. It connects perfectly fine to Windows PCs though.

My VM problem though doesn't seem to be a matter of detection: it connects (and the Windows XP inside the VM plays the device connected sound) but it then immediately disconnects. This seems like Ubuntu is constantly trying to take back control of the device. Is there any way to prevent that?

---

### Post by fjgaude on 2008-03-12
Well, I plug my drive into main box, Ubuntu see it, I unmount it; then, go to VM/Removal Devices, click on USB Devices and check the drive. It comes right up and is seen in Win Explorer as another drive.

When I'm ready to leave it, in VM I unclick it. I suppose it shows in WinXP and I should release it there, so the OS thinks it is safe to remove a writeable device.

Let us know when you have your issues fixed.

---

### Post by djbon2112 on 2008-03-12
That might be my problem: Ubuntu doesn't see it at all; it isn't in Computer, and I can't think if where else it might be. Anyone know why it isn't being detected by Ubuntu?

---

### Post by fjgaude on 2008-03-12
If it is a normal USB drive Ubuntu should have no trouble reconginizing it.

You BIOS shows that the USB functions are there?

Have you ever had this drive work in this situation?

---

### Post by Matt26 on 2008-03-12
after reading through other forums i finally found out the cause of the issue- this may work for your issue as well with the Q phone, although it sounds like it differs slightly in that winxp immediately disconnects the device after detection... basically if you have any other hard drive partitions, network drives, or removable devices installed to winxp- in other words, you have other drive letter assignments other than the standard C, D and A, winxp may auto-allocate a newly installed usb device a drive letter that is already taken, instead of the next drive letter that is actually available.  i have 2 network drives and a second HD partition on my winxp system- when i plugged in my USB flash drive xp was assigning the drive letter belonging to my second HD partition to the USB drive (go into Computer Managements console to see if it indeed being assigned a drive letter) so i changed the drive letter associated to the USB drive and BAM- xp recognized it immediately and it showed up in my computer seconds later...

hope this helps others in this situation...

---

### Post by djbon2112 on 2008-03-12
> **fjgaude said:**
> If it is a normal USB drive Ubuntu should have no trouble reconginizing it.

You BIOS shows that the USB functions are there?

Have you ever had this drive work in this situation?

Yep everything USB is working. I reinstalled Windows XP SP2 today just to test all this, and it detects and connects to it perfectly fine. That means my laptop's hardware and the Q itself are fine. :confused: There's gotta be something wrong with Gutsy. Maybe upgrading to Hardy Alpha 5 will help? Anyone have any knowledge of that?

---

### Post by djbon2112 on 2008-03-12
> **Matt26 said:**
> after reading through other forums i finally found out the cause of the issue- this may work for your issue as well with the Q phone, although it sounds like it differs slightly in that winxp immediately disconnects the device after detection... basically if you have any other hard drive partitions, network drives, or removable devices installed to winxp- in other words, you have other drive letter assignments other than the standard C, D and A, winxp may auto-allocate a newly installed usb device a drive letter that is already taken, instead of the next drive letter that is actually available.  i have 2 network drives and a second HD partition on my winxp system- when i plugged in my USB flash drive xp was assigning the drive letter belonging to my second HD partition to the USB drive (go into Computer Managements console to see if it indeed being assigned a drive letter) so i changed the drive letter associated to the USB drive and BAM- xp recognized it immediately and it showed up in my computer seconds later...

hope this helps others in this situation...

No dice; even with only the C: drive, it was still doing this.

It's gotta be something with Ubuntu doing this; there's no other explanation. Somehow it's taking control back from Windows; there's nothing else to explain it connecting and then disconnecting. First things first, is there an easy way to get meaningful statistics on what's plugged in at a given time, like actual device information so I can see what Gutsy's treating my phone as? And then, is there any way to tell Ubuntu just to ignore the device or give control of it to the VM?

If it's any help, when the device cycles the "charging" indicator on the phone keeps changing as well (going from charging to just on then back as the device connects and disconnects).

P.S.: I also tried, just for laughs, trying to reconfigure SynCE again today. It couldn't see the device either. Coincidence? I think not.

---

### Post by fjgaude on 2008-03-12
I wish I had something to suggest... I wouldn't go with Hardy now... wait until the release... as we get updates the OS runs into issues, and at present is far from complete.

I do believe from what I've gone through over the years is that Gutsy is the least stable of any Ubuntu release. Feisty was, is much better.

---

### Post by Matt26 on 2008-03-12
have you already tried going into System/Preferences/Removable Devices and Media and unchecking the first 3 options under the Removable Storage section to make sure that Ubuntu isn't taking control of any USB devices?  i know your phone wouldn't technically be considered a removable drive but it's worth a try..

---

### Post by djbon2112 on 2008-03-13
Yea, I've pretty much given up. I'm backing up my install then doing a clean install of Gutsy (and changing a few other things to make it better, i.e. seperate partition for /home, etc.) and hopefully it works. Thanks for the help guys!

---

### Post by adityakavoor on 2008-03-17
> **Matt26 said:**
> did you need to turn off your vm to accomplish this?  did you have to remove your existing USB controller first before adding the new one, as i tried adding a new USB controller when the vm was turned off but it was grayed out until i removed the existing controller in the hardware list.

I didnt have a USB controller. So I needed to add one.

---

