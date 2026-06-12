---
title: "USB in VirtualBox: HOWTO"
date: 2008-12-19
forum: Virtualisation
---

### Post by HotShotDJ on 2008-12-19
**[COLOR="Red"]THIS HOWTO IS NOW OBSOLETE![/COLOR]**

As of VirtualBox version 2.1.4, USB support works properly "Out-of-the-Box"  I strongly recommend following the following HowTo for installing VirtualBox 2.1.4 (PUEL): [http://ubuntuforums.org/showthread.php?t=1074160](http://ubuntuforums.org/showthread.php?t=1074160)

[COLOR="Blue"]**Below are the original instructions for version 2.0 through 2.1.2.  Be warned, this howto is no longer maintained.**[/COLOR]

----------------------------------------------------------------

This is an expanded version of my howto that is included in the [USB Devices section]("http://ubuntuforums.org/showpost.php?p=6122145&postcount=4") of the [Virtualization Mega-Thread.]("http://ubuntuforums.org/showthread.php?t=973756") NOTE!  The [Community Documentation]("https://help.ubuntu.com/community") for [VirtualBox on Ubuntu]("https://help.ubuntu.com/community/VirtualBox#USB") describes an obsolete method that may or may not work with current (Hardy and Intrepid) versions of Ubuntu running VirtualBox 2.*.  If you have attempted to enable USB support by following any other method, you must reverse any changes that you made before continuing.

IF YOU ARE RUNNING A VERSION OF UBUNTU OLDER THAN 8.04, IT IS STRONGLY RECOMMENDED THAT YOU UPGRADE TO AT LEAST VERSION 8.04 LTS.  I have only validated these instructions against Ubuntu 8.04 LTS and Ubuntu 8.10.  They may not work with earlier version!

_Note to KDE/Kubuntu users_: These instructions are Gnome-centric, however they will work, with some modifications, in Kubuntu (and probably other Ubuntu derivatives).  Some examples include:[LIST][*]To access software sources & software installation in KDE, see [Repositories/Kubuntu]("https://help.ubuntu.com/community/Repositories/Kubuntu").
[*]Replace "gksudo gedit" with "kdesudo kate."
[*]K-menu --> System Settings --> Users and Groups is used to access user and group information.[/LIST]


**[CENTER]Getting USB support working in VirtualBox 2.*[/CENTER]**

First of all, you will need the Personal Use End License (PUEL) version of VirtualBox.  The Open Source Edition (OSE) version that is included in the  Ubuntu Universe repository does NOT support USB.

**I.  Getting VirtualBox 2.1 PUEL edition**

If you've previously installed the OSE version of VirtualBox, you'll need to completely remove it.  Use System &#8594; Administration &#8594; Synaptic Package Manager and search for "virtualbox" and completely remove any virtualbox related packages.  Right click on the package you want to remove and select "Mark for Complete Removal."  Simply using "Mark for Removal" may leave files behind that could block the installation of the PUEL version.  Click on "Apply" then confirm the changes and click apply again.  When done, go ahead and close Synaptic Package Manager.

Go to System &#8594; Administration &#8594; Software Sources.  Click on the &#8220;Third-Party Software&#8221; tab.  Now, click on the &#8220;Add&#8221; button near the bottom of the window.  Paste the following into the &#8220;APT line&#8221; box:```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```If you are running Hardy (8.04 LTS) replace &#8220;intrepid&#8221; with "hardy". At the time of this writing, packages for later versions are not available. If you are using a version older than hardy, DO NOT USE THIS HOWTO.  Since versions prior to hardy are either no longer supported or will soon reach their [end-of-life]("https://wiki.ubuntu.com/Releases"), this would be a good time to upgrade to at least hardy (8.04 LTS).

Click &#8220;Add Source&#8221;  Do not close Software Sources yet..

Save the attached file (sun_vbox.txt) as sun_vbox.asc to your home directory or desktop. In Software Sources, click on the Authentication tab and then click on  &#8220;Import Key File...&#8221;   Browse to the location of sun_vbox.asc.  Click on the file and then press OK.  Notice that  a key has been added to Trusted software providers for Sun Microsystems, Inc. (xVM VirtualBox archive signing key).  Now you can close Software Sources.

NOTE:  If you prefer, you can get the signing key directly from Sun at [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc)

**II.  Install VirtualBox 2.1**

Open System &#8594; Administration &#8594; Synaptic Package Manager.  Click on the Reload button.  Now search for virtualbox (the Quick search box sometimes does not work with third-party repositories, so use the Search button instead).  Click on the checkbox next to &#8220;virtualbox-2.1&#8221; (or virtualbox-2.0 if you prefer the older version).  Click &#8220;Apply&#8221; and follow the onscreen instructions.  Once Virtualbox is installed, close Synaptic Package Manager.

You will now have to add all users who will be using Virtualbox to the &#8220;vboxusers&#8221; group.  We'll take care of that below.

**III.  Getting USB working**

Go to System &#8594; Administration &#8594; Users & Groups.  Unlock  "Users Settings" using the "Unlock" button near the lower right of the box (next to the close button) then click on &#8220;Manage Groups&#8221;

Scroll through the list of group names until you find &#8220;vboxusers&#8221; then click on it to highlight and click on the &#8220;Properties&#8221; button.  You'll see a list of users on your system.  Check off the users who you will want to give access to Virtualbox.  Do NOT check off &#8220;root&#8221;

Before you close this window, you have a decision to make.  Do you want all users of Virtualbox to have USB access or just SOME users of Virtualbox?  If you want all users of Virtualbox to be able to use USB devices within Virtualbox, WRITE DOWN the Group ID number (on my system, the number is 126 &#8211; it may be the same or different on your system).  You may now close out of Users & Groups and skip to &#8220;Edit /etc/fstab&#8221;

If you want only SOME users of Virtualbox to be able to use USB devices within Virtualbox, do the following:[LIST=1]
[*]Click on "+ Add Group"
[*]In the "Group Name" text box, type "usbuser"
[*]Write down the Group ID number on a piece of paper
[*]Click on your user name in the "Group Members" table -- a check mark will appear in front of the user name.  Do this for each user you wish to allow USB access in VirtualBox
[*]Click OK, and then Close, then Close again.
[/LIST]

**Edit /etc/fstab**

Open Applications -> Accessories -> Terminal and type "gksudo gedit /etc/fstab" (without the quotes).  Add following lines to the end of the file:```
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=**####**,devmode=664	0	0
```
***IMPORTANT***: Replace **####** with the Group ID number that you wrote down earlier.  Save the edited file (File -> Save) and then exit gedit.

Reboot your system.

**IV.  Enable USB Controller in VirtualBox**

This part of the HOWTO assumes that you have already created a Virtual Machine.  Instructions on how to create a VM and install an operating system can be found [elsewhere]("https://help.ubuntu.com/community/VirtualBox#Using%20Virtual%20Box") and is outside the scope of this HOWTO.  *While not required, you will enjoy a much better user experience with your VirtualBox guest operating systems if you install the guest additions.  For a Windows guest, start your guest OS. After it is booted up and ready to use, make sure you are in windowed mode (as opposed to full screen), open "Devices" from the menu bar, and select "Install Guest Additions..." Normally, it will start up automatically, but if it doesn't, just open the Windows "start" menu, go to "My Computer" (or "Computer" in Vista) and double click on the CD labeled "VirtualBox Guest Additions."*

Now you are ready to enable the USB controller for your guest OS.  Open Applications &#8594; System Tools &#8594; Sun xVM VirtualBox.  Click to highlight your Virtual Machine then click &#8220;Settings&#8221; -- In the left panel, click on USB.  You'll see the USB options appear on the right.  Check off &#8220;Enable USB Controller&#8221; and, if desired, &#8220;Enable USB 2.0 (EHCI) Controller.  For now, don't worry about device filters.  Click OK.  Do this for each VM in which you wish to have USB access.

Start you guest OS.  You can activate your USB devices using either the USB icon in the bottom-right icon bar of your virtual machine window or from Devices --> USB Devices in the menu bar across the top of your virtual machine window.

Remember, just as with operating systems installed normally, you may need to install drivers for your device(s) (such as USB printers, U3 enabled flash drives, etc.) on your guest OS before you will be able to successfully use your device with the guest OS.  Follow your  hardware manufacturer's or guest OS's instructions to install the appropriate drivers in the guest OS.

**V.  TROUBLESHOOTING**

***My USB keyboard and/or USB mouse is not working or is behaving erratically***.  DO NOT activate these devices for your virtual machines.  VirtualBox uses virtual drivers for these devices.  Activating them in your virtual machine may cause erratic behavior in both the guest and host OS.

***I can activate my USB Hard Drive and/or Flash Drive, but it is not working in the guest OS ***.  You'll need to create a device filter. Before opening VirtualBox, plug in your flash drive and/or your USB hard drive. Open VirtualBox and select your guest OS. Do NOT start the guest, just highlight it. Click on "Settings" in the toolbar and select USB in the left pane. Notice a large white area just below the heading "Device Filters." Right click anywhere in that large white area and select "Add filter from device." Now select your USB hard drive or Flash drive. Notice that the name of the device will now appear in the large white area with a checked box next to it. Repeat for other USB hard drives or flash drives as desired.  In some cases, you'll need to unmount the device from your Ubuntu desktop before starting the guest OS.  Once the guest OS has been started and is ready to use, plug in the USB hard drive or flash drive.  The guest OS should recognize and mount it properly now.

***When I activate a USB device in my guest OS, I can no longer use it from my host OS***.  This is normal.  When you enable a USB device, it will be inaccessible to your host OS until you release it from your guest OS.

***I cannot burn CD's or DVD's with my USB CDRW/DVDRW drive***.  You're actually better off using tools such as Brasero or K3B in Ubuntu to burn CD's or DVD's ... but if you must use your guest OS, it can be done very easily.  Plug your USB CDRW/DVDRW drive. Open VirtualBox and select your guest OS.  Do not start it yet.  Open "Settings" and select "CD/DVD-ROM" from the left panel.  In the right panel, check off "Mount CD/DVD Drive" and then select the "Host CD/DVD Drive radio button.  Select your CDRW/DVDRW drive from the drop down list.  Now, check off "Enable Passthrough."  Click OK.  Start your guest OS.  You should now have full burning support for the drive.  NOTE:  This also works for internal CDRW/DVDRW drives.

***USB Devices are visible under Devices --> USB Devices, but they are greyed out***.  First, double check your work.  Go back to the top of this HowTo and check for any errors that you may have made and be sure that you haven't skipped any steps. (Even the most intelligent people in the world make mistakes. I've found the most mistakes are made by those who angrily insist that they made no errors.) Before posting for help, please do the following (and include your answers and actions in any post for help on this issue)
[LIST=1]
[*]Are all USB device effected or only some USB devices?  If only some, then the USB support is functioning, but there is a problem with support for the particular device (for example, web cams are notoriously buggy under Virtualbox)
[*]Did you edit /etc/init.d/mountkernfs.sh in a previous attempt to enable USB support in VirtualBox?  If yes, please remove or comment out your changes.
[*]Did you edit /etc/init.d/mountdevsubfs.sh in a previous attempt to enable USB support in VirtualBox?  If yes, please remove or comment out your changes.
[*]Did you edit /etc/udev/rules.d/40-permissions or /etc/udev/rules.d/40-basic-permissions-rules in a previous attempt to enable USB support in VirtualBox?  If yes, please remove or comment out your changes.
[*]If you've had to change any of the above files, please reboot your system.  Now, start up VirtualBox and your guest OS.  Does USB work now?  If not, continue...
[*]Make sure that your guest OS is shut down.  Now, select it (but don't start it) and click on Settings and then select USB.  Verify that "Enable USB Controler"  and "Enable USB 2.0" are checked off.  Click OK.  If you had to check either box off, start your guest OS.  Does USB work now?  If not, continue...
[*]Please run the following commands, one line at a time, in a terminal (Applications --> Accessories --> Terminal) and post the output.  DO NOT cover up, block out, or otherwise alter the information from these commands.  There is no information that can be used to hack your computer, and all of the information is relevant to diagnosing the problem.```
mount | grep usb
cat /etc/group | grep vboxusers
cat /etc/fstab
```[/LIST]

---

### Post by bodhi.zazen on 2008-12-19
This information was posted in the virtualization mega thread.

I will add a link to this thread as well, but we are trying to keep the number of stickies to a minimum.

I think it would be best if :

1. It the sticky needs additional information, send me a PM and I will maintain it.

2. If we are going to maintain a sticky, we also need to encourage it's use.

---

### Post by SVWander on 2009-01-17
Thanks for the great howto. Do you know if it would be possible to use MS Streets & Trip within VirtualBox? I have been trying to get VB to "see" the usb GPS but so far nothing seems to work. When I try to active the GPS I get a com port not present or being used by other application error message. I would like to use Ubuntu on this Dell Inspiron 1200 on trips and not have to install my other hard drive.
Tim

---

### Post by HotShotDJ on 2009-01-17
> **SVWander said:**
> I have been trying to get VB to "see" the usb GPS but so far nothing seems to work. When I try to active the GPS I get a com port not present or being used by other application error message.I've done a little research on this issue. After you activate the device via the VirtualBox Devices --> USB Devices menu or the USB icon in the bottom-left VirtualBox window, you should see your GPS hardware in the device manager even though MS Streets & Trips isn't seeing it.  If that is the case, in order to make the GPS unit "visible" to your software, you need to go to the Windows device manager and then disable the GPS device, then re-enable it.

---

### Post by SVWander on 2009-01-18
> **HotShotDJ said:**
> I've done a little research on this issue. After you activate the device via the VirtualBox Devices --> USB Devices menu or the USB icon in the bottom-left VirtualBox window, you should see your GPS hardware in the device manager even though MS Streets & Trips isn't seeing it.  If that is the case, in order to make the GPS unit "visible" to your software, you need to go to the Windows device manager and then disable the GPS device, then re-enable it.

Thanks for the quick answer! I have tried what you suggested and do have the USB device enabled in VirtualBox. Or at least on the menu bar heading Device it shows a Prolific Technology Inc USB Serial Controller D [0300]. However the font is grayed out. When I right click on the USB icon on the lower right side of the screen it will say the same thing. BUT when I hover over the same icon it will say that no USB device is present. Very confusing. In the Device Manager will it show up as a USB device? I have disabled and enabled the Hub and the USB controller but it didn't help. Do you have any ideas what I am doing wrong or even if it is possible to get Street & Trips working in VirtualBox?

---

### Post by HotShotDJ on 2009-01-18
> **SVWander said:**
> Thanks for the quick answer! I have tried what you suggested and do have the USB device enabled in VirtualBox. Or at least on the menu bar heading Device it shows a Prolific Technology Inc USB Serial Controller D [0300]. However the font is grayed out.Ok. Do other USB devices work?  

EDIT:  I just thought of something.  Have you installed the Guest Additions?

If not start up your guest OS in windowed mode (not Full Screen or seamless). After it has completely booted, open the Devices menu in the VirtualBox menu and select "Install Guest Additions." If it doesn't autostart (be patient, it takes time to load), you'll have to go to My Computer in Windows and manually start it by opening it (Guest Additions will appear as a CD). Follow onscreen instructions. When the Guest Additions finish installing, restart your guest OS. 

Is the GPS device still grayed out?

Also, you can set a device filter and see if that helps.  First plug in your GPS device. Highlight the guest OS without starting it, go to settings and select USB (Enable USB Controller and Enable USB 2.0 should both be checked).  You'll see a large white box underneath the heading "USB Device Filters" which should be empty at the moment. Right Click anywhere within that white box and select "Add Filter from Device."  Are you able to select your GPS device from the pop-up menu?  If so, it will now appear in the USB Device Filters box with a check mark next to it.  Click on the OK button in the lower right corner of the USB settings page.  Now you can start your guest OS.

Now try disabling and the re-enabling the device using the Windows device manager (NOT VirtualBox's device menu!).

---

### Post by nirvblakr on 2009-01-18
Hi!  I was able to activate the 4 USB ports in Virtual Box.  One had a USB printer, one had an external HDD, one had a flash drive and the other was unknown.  On the main menu of Virtual Box under USB Device filters, it indicates 4 are active.  

When I turn on the virtual machine to load my XP OS, the printer is identified and I was able to install the drivers for it.  I cannot see the flash drive and the external HDD in My Computer.  Is there something else I should do in order to access the files from these external storage sources?

Thanks in advance.

---

### Post by HotShotDJ on 2009-01-18
> **nirvblakr said:**
> I cannot see the flash drive and the external HDD in My Computer.  Is there something else I should do in order to access the files from these external storage sources?There are two things you can try... either one should work.

1. (EDIT: I've found that this first method is rather "hit or miss" -- you're probably better off with #2) Unmount the drive from the Host OS (Linux).  When you plug in the HDD or the flash drive, they should appear on your Ubuntu desktop (unless you changed your desktop configuration).  Right click on the icon for the drive and select "Unmount Volume."  It should now be available to VirtualBox.

2. Create a device filter.  Plug in your flash drive and/or your HDD. Open VirtualBox and select your guest OS.  Do NOT start the guest, just highlight it.  Click on "Settings" in the toolbar and select USB in the left pane.  Notice a large white area just below the heading "Device Filters."  Right click anywhere in that large white area and select "Add filter from device."  Now select your HDD or Flash drive.  Notice that the name of the device will now appear in the large white area with a checked box next to it.  Repeat for other HDD's or flash drives as desired.  Now when you start up your guest OS, it will automatically take control of the device from the host OS when it is plugged in.

Keep in mind, whether you choose option 1 or option 2, that when you give control of a device to the guest OS, it will NOT be available for use in the host OS until it is released from the guest OS.

---

### Post by nirvblakr on 2009-01-19
Thanks for the response.  I tried the first method of unmounting the flash drive in my Ubuntu OS but I can't still see the drive in my XP Host OS.  

I tried the 2nd method. I placed an x mark on enable usb controller and enable usb 2.0 controller.  The 4 USB device filters are active with names of the printer on one, the flash drive on the 2nd one, the ext HDD on the 3rd and an unknown device on the 4th.  All have x marks on the box before the name of the device.  

I turned on my Host OS again and yet I can't still see the flash drive. 

BTW, do I have to install the guest additions for me to access the external drives?

Hope you can shed light on this.

---

### Post by HotShotDJ on 2009-01-19
> **nirvblakr said:**
> I turned on my Host OS again and yet I can't still see the flash drive. 

BTW, do I have to install the guest additions for me to access the external drives?Before moving forward, can you verify that the other USB devices are working from within the guest OS?  If they are, then we can just focus on the flash drive.  Also, I don't believe that guest additions are required for USB support in VirtualBox, however, it is probably a good idea to install them -- you'll get support for many other features.

EDIT:  Ok, I did some testing on my system with some spare USB hard drives I have.  I ran into a similar issue as you did with one of them.  In my case, when I tried to activate it, Windows tried, and failed, to load the USB Mass Storage Driver.  It was a simple fix.  After setting up the device filter, I unmounted the drive from my Ubuntu desktop and then unplugged it from the computer.  I then started up my guest OS (Windows Vista Home Premium).  Once it was completely booted up and ready to use, I plugged in the problematic USB hard drive.  It was then picked up and worked fine within the guest OS.

---

### Post by SVWander on 2009-01-19
> **HotShotDJ said:**
> Ok. Do other USB devices work?  

EDIT:  I just thought of something.  Have you installed the Guest Additions?

If not start up your guest OS in windowed mode (not Full Screen or seamless). After it has completely booted, open the Devices menu in the VirtualBox menu and select "Install Guest Additions." If it doesn't autostart (be patient, it takes time to load), you'll have to go to My Computer in Windows and manually start it by opening it (Guest Additions will appear as a CD). Follow onscreen instructions. When the Guest Additions finish installing, restart your guest OS. 

Is the GPS device still grayed out?

Also, you can set a device filter and see if that helps.  First plug in your GPS device. Highlight the guest OS without starting it, go to settings and select USB (Enable USB Controller and Enable USB 2.0 should both be checked).  You'll see a large white box underneath the heading "USB Device Filters" which should be empty at the moment. Right Click anywhere within that white box and select "Add Filter from Device."  Are you able to select your GPS device from the pop-up menu?  If so, it will now appear in the USB Device Filters box with a check mark next to it.  Click on the OK button in the lower right corner of the USB settings page.  Now you can start your guest OS.

Now try disabling and the re-enabling the device using the Windows device manager (NOT VirtualBox's device menu!).

I installed Guest Additions.

I enabled both the USB Controller and USB 2.0 and added filter for the GPS. It accurately display the GPS and it is not "grayed out".

I restart XP and still have the same problem. Right clicking on the USB icon shows the GPS. Hovering over the icon shows NO USB connected.

I tried a USB drive. Actually I tried two of them. One a card reader the other a Corsair Flash Drive. Neither showed up with XP running both showed up in the add filter.

I completely reinstalled XP to see if that was the problem but there was no change. I was able to connect to my wireless card which is something I couldn't do in VMware, so I guess I could say I am making progress but I really need to get the GPS working but I don't know what to do now.

thanks for your help!

---

### Post by HotShotDJ on 2009-01-20
> **SVWander said:**
> I enabled both the USB Controller and USB 2.0 and added filter for the GPS. It accurately display the GPS and it is not "grayed out".

I restart XP and still have the same problem. Right clicking on the USB icon shows the GPS. Hovering over the icon shows NO USB connected.

I tried a USB drive. Actually I tried two of them. One a card reader the other a Corsair Flash Drive. Neither showed up with XP running both showed up in the add filter.Since you've reinstalled XP in VirtualBox, I'd like you to remove the filters that you previously added.  Now, go back and add them again for the GPS unit and the Corsair Flash Drive (lets not deal with the card reader right yet.)  After you set up the new device filters but before you start up XP in VirtualBox, unmount and remove the Flash Drive and the GPS.  Now, boot up your Virtual Machine.  Once it has booted up and is ready to use, go ahead and plug in the Flash Drive.  Does it work as expected?  If yes, then go ahead and safely remove the Flash drive in XP and unplug it from your USB port and then try your GPS.

Let me know what happens.

---

### Post by the_pod on 2009-01-20
First off, thanks.  Hard to find great tutorials / "how-to"s and you made one. I appreciate it.  Especially for those of us Linux challenged individuals...

Still relatively new to the Linux world... Want to run Rosetta Stone in a VM (XP) and that's not really a problem.  Just purchased a USB headset in order to record myself in the program.

After following all your directions I got the headset to work (thanks again).  Question if you know anything on this -- sound is choppy.  When running the sound through my regular speakers its great but through the headset / mic?  Not so great.

I'm going to surf around b/c I think I found some mention of this in the last day or so while trying to find a solution but if you have a quick and easy one it'd be appreciated.

Regardless, thanks for the thread.

---

### Post by HotShotDJ on 2009-01-20
> **the_pod said:**
> After following all your directions I got the headset to work (thanks again).  Question if you know anything on this -- sound is choppy.  When running the sound through my regular speakers its great but through the headset / mic?  Not so great.I'm pleased that my HowTo was useful to you.

I don't have any experience with USB headsets, so I did a quick search regarding the issue.  Unfortunately, I found others with a similar problem, but no solutions.  I wonder if a similar fix that we use for USB hard drives and Flash drives might help.  Follow the instructions in the Troubleshooting section of the HowTo entitled "***I can activate my USB Hard Drive and/or Flash Drive, but it is not working in the guest OS***" but use your USB headset rather than a hard drive or flash drive.  Let me know if that helps.

---

### Post by nirvblakr on 2009-01-21
> **HotShotDJ said:**
> Before moving forward, can you verify that the other USB devices are working from within the guest OS?  If they are, then we can just focus on the flash drive.  Also, I don't believe that guest additions are required for USB support in VirtualBox, however, it is probably a good idea to install them -- you'll get support for many other features.

EDIT:  Ok, I did some testing on my system with some spare USB hard drives I have.  I ran into a similar issue as you did with one of them.  In my case, when I tried to activate it, Windows tried, and failed, to load the USB Mass Storage Driver.  It was a simple fix.  After setting up the device filter, I unmounted the drive from my Ubuntu desktop and then unplugged it from the computer.  I then started up my guest OS (Windows Vista Home Premium).  Once it was completely booted up and ready to use, I plugged in the problematic USB hard drive.  It was then picked up and worked fine within the guest OS.

Thanks so much for the response.  Everything is ok already. :D

---

### Post by SVWander on 2009-01-22
> **HotShotDJ said:**
> Since you've reinstalled XP in VirtualBox, I'd like you to remove the filters that you previously added.  Now, go back and add them again for the GPS unit and the Corsair Flash Drive (lets not deal with the card reader right yet.)  After you set up the new device filters but before you start up XP in VirtualBox, unmount and remove the Flash Drive and the GPS.  Now, boot up your Virtual Machine.  Once it has booted up and is ready to use, go ahead and plug in the Flash Drive.  Does it work as expected?  If yes, then go ahead and safely remove the Flash drive in XP and unplug it from your USB port and then try your GPS.

Let me know what happens.

Sorry I didn't get back to you. I had to solder on a new DC power jack. Followed the steps above and got the same results. I have attached a screenshot showing the message I keep getting. I tried to take one of the USB icon showing no USB device attached and being able to right click on the icon and it shows the GPS but grayed out.

Tim

---

### Post by the_pod on 2009-01-22
> **HotShotDJ said:**
> I'm pleased that my HowTo was useful to you.

I don't have any experience with USB headsets, so I did a quick search regarding the issue.  Unfortunately, I found others with a similar problem, but no solutions.  I wonder if a similar fix that we use for USB hard drives and Flash drives might help.  Follow the instructions in the Troubleshooting section of the HowTo entitled "***I can activate my USB Hard Drive and/or Flash Drive, but it is not working in the guest OS***" but use your USB headset rather than a hard drive or flash drive.  Let me know if that helps.

Tried it, but unsuccessful.  Did a lot of searching in the last day or so on this and it seems I'm out of luck.  The VB world is outraged about the lack of support for USB headsets but I can't get a handle on whether or not its in the "fix-it" stage or merely a "heads-up".  Something about sound buffers is what sticks in my head, but my take-away was that I'm SOL.  Ah well, I'll stick with the reboot into a dual-operating system for audio recording work for now and hopefully they'll make an upgrade/update at some point.

-Scott

---

### Post by nirvblakr on 2009-01-24
Even if the guest OS (WinXP) is running, I was able to install the USB flash drive.  This what I did:

When inserting the flash drive, the host OS (Ubuntu) identifies it and opens a window showing its contents.  I then closed this window.

I opened the running guest OS and just clicked Devices (found at the top of the Virtual Box main menu) -->USB then just choose and put an x on the USB device I want to activate.  Then the guest OS will now idenfify the device.  :D

---

### Post by HotShotDJ on 2009-01-24
> **nirvblakr said:**
> 
When inserting the flash drive, the host OS (Ubuntu) identifies it and opens a window showing its contents.  I then closed this window.

I opened the running guest OS and just clicked Devices (found at the top of the Virtual Box main menu) -->USB then just choose and put an x on the USB device I want to activate.  Then the guest OS will now idenfify the device.  :DExcellent!  Thats the way its supposed to work. :)  Some devices are more stubborn, though.

---

### Post by mmendez on 2009-01-24
Thanks for the quicky, couldn't find a fix for that damned greyed out stuff.

---

### Post by SVWander on 2009-01-24
> **HotShotDJ said:**
> Excellent!  Thats the way its supposed to work. :)  Some devices are more stubborn, though.

Finally! I got it working. I had KDE installed on this system. After doing some other research, and I do believe some of what I found might have been your work) I switched to KDE and tried. Fired up XP and there the USB port was!

Lets see I change permissions as per this howto:
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

And edited:
/etc/init.d/mountdevsubfs.sh
/etc/udev/rules.d/40-basic-permissions.rules 
and added myself as having permission:
sudo usermod -G vboxusers -a `whoami`

It was all a shot in the dark but my GPS now works flawlessly! 
Thanks for the good howto and for your help over the last week.

Tim

---

### Post by syntheticz on 2009-01-24
All problems solved :)

---

### Post by Dark_Ronius on 2009-01-25
Hi there

I'm finding all of my USB devices greyed out. I followed your instructions, however had made no attempt to get USB working in Virtualbox before in the files mentioned.

I was working from an image I'd made from Virtual Box OSE, and had attempted USB support in that (as far as ticking the two boxes under "usb support", no fiddling around with files in gedit). I also made sure I got rid of any files to do with virtualbox ose before installing the version in this guide.

Thanks in advance

---

### Post by HotShotDJ on 2009-01-25
> **Dark_Ronius said:**
> Hi there

I'm finding all of my USB devices greyed out. I followed your instructions, however had made no attempt to get USB working in Virtualbox before in the files mentioned.
Please open a terminal (Applications --> Accessories --> Terminal) and then type the following commands one at a time and post the output:
```
mount | grep usb
cat /etc/group | grep vboxusers
cat /etc/fstab

```

---

### Post by Dark_Ronius on 2009-01-26
Hi again

Sorry I'd completely forgotten to do that, I'd read the instructions a few hours before actually posting.

Here's the output:

```
gary@gary-xubuntu-pc:~$ gksudo mousepad /etc/fstab
gary@gary-xubuntu-pc:~$ mount | grep usb
gary@gary-xubuntu-pc:~$ cat /etc/group | grep vboxusers
vboxusers:x:124:gary
gary@gary-xubuntu-pc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b482df9b-f79a-43e7-96f4-925387acc4c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=e79163e0-707f-4c53-9a3b-2590b07b7d3a /boot           ext3    relatime        0       2
# /dev/sda14
UUID=caa9c564-6011-46ea-ad91-a39ccb566199 /home           ext3    relatime        0       2
# /dev/sda5
UUID=5D4A8ECB0581543B /home/gary/windocs ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=D048C1E948C1CE82 /home/gary/windows ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda15
UUID=5dc1e36c-d92c-4cf6-bb81-c318bc93a44b /opt            ext3    relatime        0       2
# /dev/sda12
UUID=a21d8a34-4454-4946-9975-029971942e87 /srv            ext3    relatime        0       2
# /dev/sda9
UUID=e9390944-a47f-4d89-bf1c-d8bbbe9a73d8 /tmp            ext3    relatime        0       2
# /dev/sda10
UUID=24b09da8-2b22-459c-b8b2-744f5a81ed60 /usr            ext3    relatime        0       2
# /dev/sda13
UUID=32b5082c-9fe6-40c1-a3a1-b3c5998627a9 /usr/local      ext3    relatime        0       2
# /dev/sda11
UUID=9bcf900f-3b33-45f1-8f7a-d9cc97da9f01 /var            ext3    relatime        0       2
# /dev/sda7
UUID=e0c1b349-5f02-44b0-a3b2-24cef3d68c9f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=124,devmode=664	0	0
gary@gary-xubuntu-pc:~$ 

```

---

### Post by HotShotDJ on 2009-01-27
> **Dark_Ronius said:**
> ```
gary@gary-xubuntu-pc:~$ mount | grep usb
gary@gary-xubuntu-pc:~$ cat /etc/group | grep vboxusers
vboxusers:x:124:gary
gary@gary-xubuntu-pc:~$ cat /etc/fstab

{deleted a portion that isn't relevant -- HSDJ}

# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=124,devmode=664	0	0

```I'm sorry it took so long for me to get back to you.  Its been very busy at work, and its only Tuesday!!!!

For some reason, the USB file system isn't mounted.  The line added to /etc/fstab looks fine, so it SHOULD be mounted (assuming you've rebooted since adding that line to your fstab). Also, the user "gary" is a member of the vboxusers group, so there shouldn't be a problem with permissions.

Try this sequence of commands (one at a time, of course) and post the outputs:
```
sudo mount /proc/bus/usb
mount | grep usb
```You should end up with something like this:```
$ mount | grep usb
none on /proc/bus/usb type usbfs (rw,devgid=124,devmode=664)
```

---

### Post by wildmanne39 on 2009-02-03
Hi this is what my 40-basic-permissionsrules says,  # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="vboxusers"
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"
My usb devive is seen in virtualbox but grayed out and I am running Kubuntu 8.10 with vista inside virtualbox, Thanks for any help you can give me I really appreciate it. There is no out put for sudo mount /proc/bus/usb.  For mount | grep usb output is 
procbususb on /proc/bus/usb type usbfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)

---

### Post by HotShotDJ on 2009-02-03
> **wildmanne39 said:**
> Hi this is what my 40-basic-permissionsrules says,  # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="vboxusers"
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"Is this a change that you made?  If you did not add those lines yourself, leave them as they are.  Otherwise, you must reverse any changes that you made in previous attempts to enable USB support in VirtualBox before using the HowTo at the beginning of this thread.  Also, what version of VirtualBox do you have installed?> **wildmanne39 said:**
> For mount | grep usb output is 
procbususb on /proc/bus/usb type usbfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)This is interesting.  This line should only be listed once.  Is this a cut & paste error or was it actually listed twice when you ran that command?  I'd also like to see the output of the following two commands:```
cat /etc/group | grep vboxusers
cat /etc/fstab
```

---

### Post by wildmanne39 on 2009-02-03
This is how it reads with that command. I am using virtualbox 2.12 and I did add GROUP="vboxusers" to the commands by copying the one a post told me to put in I deleted the commands that were already there to put the new one in. Is there away to revert back to the original commands just in case the was more different then I remember? I am using kubuntu 8.10 with kde 4.2. I have tried kde forums also but for some reason I can not post a new thread over there I can only post a reply to one already open. Thank both of you for your help and any more help is greatlt appreciated.

larry@larry-laptop:~$ cat /etc/group | grep vboxusers
vboxusers:*:122:larry
larry@larry-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=fc19aea1-abe3-4f9e-a96f-8f4f88dd62a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=5ea8a916-520d-45d1-bf68-580bcc2c65d2 /boot           ext3    relatime        0 2
# /dev/sda3
UUID=6d4070ea-45bb-4a68-a689-447b6d76f9dc /home           ext3    relatime        0 2
# /dev/sda5
UUID=f2f869af-6141-447a-8b8f-f227bcd59bbc none            swap    sw              0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
larry@larry-laptop:~$

---

### Post by HotShotDJ on 2009-02-03
> **wildmanne39 said:**
> I did add GROUP="vboxusers" to the commands by copying the one a post told me to put in I deleted the commands that were already there to put the new one in. Is there away to revert back to the original commands just in case the was more different then I remember? Ok.  The section that you changed originally should have looked like this:```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",		MODE="0664"

```Please make a backup of the current file, and then edit that section so that it looks like the above code, then reboot.

I've just looked at the additional information that you added to your last post.  You forgot to edit your /etc/fstab file when you were working through the HowTo.  Here are the instructions -- I've "Kubuntu-fied" them for you:

Open a terminal and type "kdesudo kate /etc/fstab" (without the quotes).  Add following lines to the end of the file:```
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=122,devmode=664	0	0
```
Save the edited file and then exit kate.

Reboot your system.

---

### Post by wildmanne39 on 2009-02-04
Hi Thank you so much for your help when I changed those commands like you told me to it fixed my usb problem now I am tring to get my printer to work woth virtualbox hopefully that will be easy now.

---

### Post by dargaud on 2009-02-04
I just installed "aptitude install virtualbox" (which is 2.0.4_OSE) and a WinXP in it before seeing your instructions. Does this mean I have no hope of getting my USB device through to XP ? Am I better off wipping the whole thing and restarting with your instructions or will they 'probably' work if I try them ?

The main reason I'm installing a virtual WinXP is to use USB devices that have no or poor support in XP, in particular photo printers and calibration probes. Can a device with no support be passed on to the guest OS ? Should I be able to install a USB printer on the guest OS and then export it via SMB network to the other windows machines on the local network ?

If I reinstall the version you indicate, can I keep my already installed XP ?

Thanks.

---

### Post by HotShotDJ on 2009-02-04
> **dargaud said:**
> If I reinstall the version you indicate, can I keep my already installed XPYes... Absolutely.  Since you have the OSE version installed, you'll have to completely remove it (the instructions for this are in the HowTo).  The removal won't touch your current virtual machines.  If you follow my instructions in the first post of this thread, you should end up with USB enabled with your already installed XP.  Let me know how it works out!

---

### Post by Simpotico on 2009-02-05
Master HotShot DJ,

Your tutorial has been most helpful but it seems that I have hit a wall and need your expertise to get over it...

I have finally got my virtualbox Windows XP guest to recognize and install my USB devices as indicated by the active USB icon in the right hand corner of the taskbar menu. Now the problem arises when I open the "my computer" icon on my desktop to view my C: drive and other organic devices to the computer but cannot view my USB device! What gives? I have included several screen shots to show you exactly what I'm looking at and what I have done on the Windows side to try and resolve this.

I have followed the other advise in your tutorial including, removing filters, mounting and unmounting the USB device several different ways with the machine on and off but nothing seems to work.

I have no doubt that I am missing something here or perhaps when going back and reviewing my work, I keep stupidly making the same mistake without catching it. I don't know. But there it is, that's my problem. USB is mounting, activated, on but I cannot access it from my Windows desktop or "My Computer" icon to use it.

Any help, oh great master, would be appreciated!

---

### Post by albinootje on 2009-02-05
> **Simpotico said:**
>  I have followed the other advise in your tutorial including, removing filters, mounting and unmounting the USB device several different ways with the machine on and off but nothing seems to work.


If using your usb disk inside the MS-Win guest VM is the only thing you need right now, then you can do the following (without usb support even :) ) :
1) use /media with "shared folders" for the MS-Win guest vm
2) map network drive for /media inside the MS-Win guest vm
Done ;-)

---

### Post by Simpotico on 2009-02-05
I wish it was that simple for me... Take a look at the attachment in this reply. As you can see I cannot find my VirtualBox Shared Folders in my Map Network. I don't know if this has something to do with Guest Additions feature in VirtualBox but when I click on Guest Additions to try and play around in there it just ignores me like a high school prom queen. So far, if there's a bug, I've found it... And it's left me stuck up to my neck in mud.:(

---

### Post by albinootje on 2009-02-05
> **Simpotico said:**
> I wish it was that simple for me... 

I've used the /media "shared folder" method successfully on other people's computer several times :)
> 
Take a look at the attachment in this reply. As you can see I cannot find my VirtualBox Shared Folders in my Map Network. 

Indeed. Thanks for posting the screenshot.
> 
I don't know if this has something to do with Guest Additions feature in VirtualBox 

Me neither.
> 
but when I click on Guest Additions to try and play around in there it just ignores me like a high school prom queen.

Here's a somewhat old howto for installing Guest Additions :
[http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/)

---

### Post by Simpotico on 2009-02-05
I got part of it figured out. The VirtualBox edition that I downloaded from the Innotek website did not contain the Guest Additions program. So, I had to download it from here: 

[http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso](http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso)

Once installed it solved my network / file sharing problem with my Ubuntu host and Windows XP guest. The problem with my USB external hard drive appears to be more complex. I found an old 64MB Lexar Jumpdirve that my Windows guest loves but simply rejects my 160GB Lacie and 1TB WD external hard drives. Go figure. But now I have cool wide screen resolution and a free roaming mouse.

---

### Post by albinootje on 2009-02-05
> **Simpotico said:**
> 
Once installed it solved my network / file sharing problem with my Ubuntu host and Windows XP guest. The problem with my USB external hard drive appears to be more complex. I found an old 64MB Lexar Jumpdirve that my Windows guest loves but simply rejects my 160GB Lacie and 1TB WD external hard drives. Go figure. But now I have cool wide screen resolution and a free roaming mouse.

Good! 
But what about the /media as "shared folder" mapped as network drive inside the guest vm ?
That should show all of your external disks if they work fine in Ubuntu.

---

### Post by HotShotDJ on 2009-02-05
> **Simpotico said:**
> I have followed the other advise in your tutorial including, removing filters, mounting and unmounting the USB device several different ways with the machine on and off but nothing seems to work.If I understand the issue correctly, you have no device filters set under VirtualBox's Settings --> USB?  I'd like you to try setting a new device filter for your USB Hard Drive.  After setting up the device filter, but before starting up your Windows XP virtual machine, unmount and unplug the USB Hard Drive, then start XP.  Once XP has booted up and is ready to use, try plugging in the USB Hard Drive.  Does it work now?  If not, I'm wondering if you have formated the USB drive using a file system other than NTFS or FAT?  You can determine the file system on the drive by plugging it in without VirtualBox running.  When the icon for the drive appears on the desktop, right click on the icon, and select "Properties" and then select the "Volume" tab.  You should see a listing for "File System."  Let me know what happens.

---

### Post by HotShotDJ on 2009-02-05
> **Simpotico said:**
> I got part of it figured out. The VirtualBox edition that I downloaded from the Innotek website did not contain the Guest Additions program. So, I had to download it from here: 

[http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso](http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso)This is VERY odd.  I've seen this happen with the OSE version, but never with the PUEL version.  You shouldn't be downloading VirtualBox or the guest additions.  It is best to add the proper repository (see the HowTo at the beginning of this thread) and install VirtualBox using Synaptic Package Manager.  You will enjoy the benefit of having updates appear in the Update Manager, and you will always have the correct version of the Guest Additions at your finger-tips.

Remember, while the "Install Guest Additions" selection from the "Devices" menu will usually automatically start the installation process, it is sometimes necessary to start the installer manually.  After clicking on "Install Guest Additions" and nothing happens, you should go to My Computer in Windows... you should see the Guest Additions mounted as a CD-ROM.  Double click on it to start the installer.

Downloading VirtualBox and Guest Additions can sometimes cause problems, such as unfixed bugs (no notification of updates through Update Manager) and mismatched Guest Additions version.

---

### Post by Simpotico on 2009-02-05
Part I: No go with the USB mounting issue. Followed the steps you provided. It mounts, I get the little icon in the bottom right hand corner of the taskbar tray but no access to the device itself. I've tried mounting my external hard drive with filters and without. Installing, updating, uninstalling and then reinstalling the drivers. Going to the manufacturer's website for support. Oh, and the file system; vfat (FAT32).

Part II: I tied a couple of times to download VB using the synaptic package manager but I was constantly receiving a failure to start message once VB was installed. Then after hours of trouble shooting I ended up at Ubuntu Unleashed VirtualBox installation, followed the instructions and it worked.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

However, the synaptic package manager shows the program is installed and manageable through there. See attached. 

Now, if I could only gain full access through the network drive I have setup. For some reason I only have limited access to my Ubuntu home files. Like I said earlier, if there is a bug out there this program has it. I love my Ubuntu and I'm very excited about VB but it has been quite a headache.

---

### Post by HotShotDJ on 2009-02-05
Version 1.5.6 ????????????????????  That is a VERY old version.  Where did you find it?  You should be using at LEAST version 2.0 -- and preferably 2.1.2.  My HowTo is written for minimally for Ubuntu 8.04 LTS (Hardy) with at least VirtualBox 2.0.  I strongly recommend that you completely remove virtualbox (in Synaptic Package Manager, select "mark for complete removal" and then apply).  Now, start from the beginning of the HowTo.

There were many bugs in the first generation VirtualBox. A large number of them have been fixed in the second generation.

---

### Post by Simpotico on 2009-02-05
Okay Master HotShotDJ,

I'm going to do it. I'm going to remove what I've got and all of the work I've put into it and reinstall the latest version per your guidance... I'll let you know how it turns out.


TO BE CONTINUED...

---

### Post by WasMeHere on 2009-02-06
Thank you, HotShotDJ,
I have been running VBox1.6 in Hardy for 6 months without USB, but now there is a need for it because of a bank's modified internet service software (!). Anyway, your HowTo helped me to install and configure VBox2.1 with USB2.0. I could use the old virtual disk, but not the old (converted) virtual machine. When I created a new machine using the old vdisk, it started to work nicely.

---

### Post by Simpotico on 2009-02-06
:KS Master HotShotDJ,

Success, all I can say is, success. After days of banging my head against a wall, thou, learning a lot, your recommendation has led to total and complete success; USB, shared folders, performance, everything. Windows is now my SLAVE! I will whip it and beat it every day! I will curse it and spit on it and keep it in its little box where it belongs! In a place where it can do no more harm to the rest of the world! A place where the rest of us Linux enlightened beings can stand and point and laugh at all of the Windows lemmings as they trudge along within the confines of DOS to their eventual DOOM, DOOM I TELL YOU! And it's all because of you! HAHAHAHAHAHAAAAAAAAAAAAAAAAAAAAAAAAAAAA!!!!! :twisted:

---

### Post by wildmanne39 on 2009-02-07
Thank you so much adding that line to my /etc/fstab fixed my usb problem, I tried before to add that line but i could not get it to work because i didnt have the command to do it in kubuntu. I was wondering can you tell me what kind of external drive to buy I want to add more space to my laptop. Will it access the data on one connected to my usb port slower then an internal one and can I boot from an external drive connected to my usb port? Thank you for all your help you and everyone like you make it possible for new people to use ubuntu. Also can you tell me when I can learn commands and other necessary stuff. Like is there a book I should buy or a place I can download manuals?

QUOTE=HotShotDJ;6671878]Ok.  The section that you changed originally should have looked like this:```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",		MODE="0664"

```Please make a backup of the current file, and then edit that section so that it looks like the above code, then reboot.

I've just looked at the additional information that you added to your last post.  You forgot to edit your /etc/fstab file when you were working through the HowTo.  Here are the instructions -- I've "Kubuntu-fied" them for you:

Open a terminal and type "kdesudo kate /etc/fstab" (without the quotes).  Add following lines to the end of the file:```
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=122,devmode=664	0	0
```
Save the edited file and then exit kate.

Reboot your system.[/QUOTE]

---

### Post by HotShotDJ on 2009-02-08
> **wildmanne39 said:**
> I was wondering can you tell me what kind of external drive to buy I want to add more space to my laptop. Will it access the data on one connected to my usb port slower then an internal one and can I boot from an external drive connected to my usb port? Thank you for all your help you and everyone like you make it possible for new people to use ubuntu. Also can you tell me when I can learn commands and other necessary stuff. Like is there a book I should buy or a place I can download manuals?Any USB drive should work.  The only problems I've had are with Flash Drives that have U3 installed.  They are a ROYAL PAIN.  But, if you have access to a Windows machine (or a VirtualBox Windows VM with USB support enabled, as you now do) it is trivial to remove the U3 garbage.

The speed of a USB port is slower than the ports used for internal hard drives, so your data access will be slower when using an external hard drive, but the difference will not be all that bad.  You should only really notice it when accessing very large files.

Most modern computers allow booting from a USB device.  You simply need to make sure that the USB device is part of your boot order in the BIOS.  As far as using a USB device to store your Virtual Drives for use in VirtualBox, this is easily accomplished.  When you are ready to try it, post a new thread and somebody will be happy to help you out.

I'm not aware of any books that you could buy (I'm not saying there aren't any, just that I'm not aware of them).  However, I've found the [Official Ubuntu Documentation]("https://help.ubuntu.com/") to be invaluable!  As with most things in the world of Ubuntu, it tends to be Gnome-centric.  But you will often find information for KDE users included as well as a lot of information that is fungible across all desktop environments.

---

### Post by HotShotDJ on 2009-02-08
> **Olle Wiklund said:**
> I could use the old virtual disk, but not the old (converted) virtual machine. When I created a new machine using the old vdisk, it started to work nicely.I'm sure others will also find this information helpful.  Thank you for letting us know how you got things working for you!

---

### Post by Benjammn on 2009-02-11
Is there any info on how to use VirtualBox on a USB with a Windows XP host?

---

### Post by zevans on 2009-02-12
In case this helps anyone out...

This is on an Advent 4211 = MSI Wind but may help anyone struggling with their card reader even if other USB devices may be working.

I started from the PUEL edition under Intrepid and KDE 3.5.

I could see USB devices and add them to the filter OK right from the get-go. I also managed to get ActiveSync working with HTC phone via USB correctly on the first attempt. So, that much of USB works out of the box, WITHOUT needing to make the udev or the /proc changes - interesting.

However getting the multi-card reader working was a bit harder...

1. I thought maybe the generic drivers were the problem, so I installed the specific drivers for the card reader using the copy that shipped on the "real" Windows OEM partition. It's a Realtek device. That got rid of the yellow exclamation mark on the device and showed me a generic volume if I plugged a card in. However I couldn't see the files on the card.

2a. I added the vboxusers group to the udev stuff as described in the Wiki.
2b. I added the /proc mountpoints as described in the Wiki.
Restarted the appropriate services (did NOT need to reboot the host) but rebooted the guest.

That got me a device that looked like a disk but didn't seem to have any way of accessing it - no drive letter. However I've seen this strangeness before with real disks, so I ran Local Storage management in Admin Tools to see what would happen. Sure enough that assigned a drive letter to it - D:.

Still wouldn't work, and then I realised that D: was already mapped over the "network" to the folder that I'd shared with the host - so I used the Storage Mgr to remap the card reader to R: - and it now works!

So the moral of the story is use Admin Tools and make sure you don't have a clash of drive letters anywhere - if you follow the wiki and install the correct driver in Windows, the chances are the reader is working but you just have no drive letter assigned.

---

### Post by marcgh on 2009-02-13
Thanks for the HOW TO.

I followed the instructions and both my 8Gb pendrive and my 120 Gb USD hDD are working perfectly.

Thanks you!

---

### Post by HotShotDJ on 2009-02-18
Good News!  The newest version (as of this writing) of VirtualBox PUEL (version 2.1.4) has USB support working "out-of-the-box."

---

### Post by tabarnackle on 2009-04-11
ok im troubleshooting the "greyed out" problem. i ran the codes and here are the results. whats next? 

david@DforceONE:~$ mount | grep usb
none on /proc/bus/usb type usbfs (rw,devgid=125,devmode=664)
david@DforceONE:~$ cat /etc/group | grep vboxusers
vboxusers:x:125:
david@DforceONE:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9a843a47-b57b-423f-8f75-47ddaf73bc2e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ee4f7bb0-05fe-4785-ac01-11c0e6bc121b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0# For USB access with Virtualbox
none    /proc/bus/usb    usbfs    devgid=125,devmode=664    0  0

---

### Post by albinootje on 2009-04-11
> **tabarnackle said:**
> ok im troubleshooting the "greyed out" problem. i ran the codes and here are the results. whats next? 

Which VirtualBox version are you running ? 1.6.x or 2.0.x or 2.1.x ?
And are you using the PUEL version or the OSE version ?

---

### Post by tabarnackle on 2009-04-11
> **albinootje said:**
> Which VirtualBox version are you running ? 1.6.x or 2.0.x or 2.1.x ?
And are you using the PUEL version or the OSE version ?

solved :) IRC chat saves the day!

---

### Post by bodhi.zazen on 2009-04-11
> **tabarnackle said:**
> solved :) IRC chat saves the day!

It would be helpful to the forums if you posted the solution here as well, although USB should be working out of the box with the PUEL version.

---

### Post by fanum on 2009-05-23
I was having problems with my usb after a fresh install of 9.04. The problem for me was in the Windows install (also fresh) not detecting my iPhone properly. To fix this, start the Windows VM, right click on "my computer", select "manage", then "device manager". Right click on the USB device with the exclamation point on it, and select "update driver". VirtualBox worked all along. As usual the problem was in windows. Big surprise.

---

