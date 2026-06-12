---
title: "USB could not detect in VirtualBox for Ubuntu 16.04 LTS"
date: 2016-07-02
forum: Virtualisation
---

### Post by myusic on 2016-07-02
I can't seems to connect the USB to VirtualBox for Ubuntu 16.04 LTS. However, when i plug my iPhone USB it is able to detect but when i plug in the bladeRF it is able to detect but is empty as shown by the screenshot.


I have also installed the Extension Pack from Oracle VirtualBox, I also enabled USB 2.0 from settings of my VM. I also filter the Naund USB shown below

Below is the device could not detect in Linux

Below is the device can be detected on Windows using the bladeRF CLI

Would appreciate if anyone could help me :)

---

### Post by howefield on 2016-07-02
Thread moved to the "*Virtualisation*" forum for a better fit,

---

### Post by &amp;KyT$0P# on 2016-07-02
Does this help? [http://ubuntuforums.org/showthread.php?t=2328142](http://ubuntuforums.org/showthread.php?t=2328142)

---

### Post by myusic on 2016-07-02
> **halogen2 said:**
> Does this help? [http://ubuntuforums.org/showthread.php?t=2328142](http://ubuntuforums.org/showthread.php?t=2328142)

Hi thanks for your reply i tried to type this code on the terminal 
  
[COLOR=#000000][FONT=&amp]sudo adduser <yourusername> vboxusers[/FONT][/COLOR]

as [COLOR=#000000][FONT=&amp]sudo adduser bingxun vboxusers[/FONT][/COLOR]

but i got a error saying adduser: The group 'vboxusers' does not exist

---

### Post by &amp;KyT$0P# on 2016-07-02
Sorry, I didn't see there were screenshots in the OP and missed that your host is Windows.  That other thread does not apply to you.

In those menus on the top of the running virtual machine, under Devices > USB, is the USB device actually selected to be connected?  If it's grayed out and not selected, disconnect the USB device and make sure to reconnect it while the virtual machine is running and you're logged in the virtual machine.

---

### Post by myusic on 2016-07-03
> **halogen2 said:**
> Sorry, I didn't see there were screenshots in the OP and missed that your host is Windows.  That other thread does not apply to you.

In those menus on the top of the running virtual machine, under Devices > USB, is the USB device actually selected to be connected?  If it's grayed out and not selected, disconnect the USB device and make sure to reconnect it while the virtual machine is running and you're logged in the virtual machine.


thanks for your reply. i've check the USB in the VM but is still not working.. i have attached the screenshot here

the device does appear in the Ubuntu Desktop but however the device cannot be detected

---

### Post by MAFoElffen on 2016-07-03
Remind me--
What version of Windows and VirtualBox?
Doy have the Oracle VirtualBox Extension Pack installed? Guest Additions?

---

### Post by myusic on 2016-07-03
> **MAFoElffen said:**
> Remind me--
What version of Windows and VirtualBox?
Doy have the Oracle VirtualBox Extension Pack installed? Guest Additions?

I'm using windows 10 , VirtualBox version is: Version 5.0.22 r108108

Extension pack is installed as my iPhone can be detected in the VirtualBox shown in my first post.
Guest additions is also installed i can do a full screen on the VirtualBox (Ubuntu 16.04 LTS)

---

### Post by MAFoElffen on 2016-07-03
Seeing your iPhone, does not explain why your option for "Enable USB Controller" option and all it's sub options are grayed out. Logically, if that option is grayed out... or if was not grayed out and just not selected, then your iphone should not have shown up in your guest... meaning it is usually all shown or none... (Unless you have mixed 3,0 and 2.0 USB ports)

Assuming that your Windows 10 version is 64 bit and that you have Hardware Virtualization (vt-x & vt-d) turned on in your Host BIOS:

I see two direction of fixes (that tied to each other) when this problem occurs on a Windows host.
- First method involves uninstalling/installing  the extension pack from within the VirtualBox Manager.
- Second involves going to your gust settings, removing the USB contoller (as hardware) > Apply ... Add Hardware > USB Passthrough Controller

If You are running Win10 32 bit and/or do not have hardware virtualization turned on, then you will not see those, because then it should not be able to pass through as hardware virtualized.

This is a curious kind of problem. It shuld either work or not, Not usually "partially."

---

### Post by &amp;KyT$0P# on 2016-07-03
Being grayed out in that specific way usually just means the VM is running.

Also, expanding on what MAFoElffen said, it doesn't work if you plug a USB 3.0 device in a physical USB 3.0 port on the host while giving the guest USB 2.0.
(Is USB 2.0 extension cord enough to "downgrade" the port or is an actual USB USB 2.0 hub needed?)

---

### Post by myusic on 2016-07-03
> **MAFoElffen said:**
> Seeing your iPhone, does not explain why your option for "Enable USB Controller" option and all it's sub options are grayed out. Logically, if that option is grayed out... or if was not grayed out and just not selected, then your iphone should not have shown up in your guest... meaning it is usually all shown or none... (Unless you have mixed 3,0 and 2.0 USB ports)

Assuming that your Windows 10 version is 64 bit and that you have Hardware Virtualization (vt-x & vt-d) turned on in your Host BIOS:

I see two direction of fixes (that tied to each other) when this problem occurs on a Windows host.
- First method involves uninstalling/installing  the extension pack from within the VirtualBox Manager.
- Second involves going to your gust settings, removing the USB contoller (as hardware) > Apply ... Add Hardware > USB Passthrough Controller

If You are running Win10 32 bit and/or do not have hardware virtualization turned on, then you will not see those, because then it should not be able to pass through as hardware virtualized.

This is a curious kind of problem. It shuld either work or not, Not usually "partially."

The first method uninstall/install the extension pack is in the Linux (Ubuntu) in the virtualbox itself? not download in windows and install it through windows?
The second method for guest settings is the settings to do in the VirtualBox?

> **halogen2 said:**
> Being grayed out in that specific way usually just means the VM is running.

Also, thanks MAFoElffen for the reminder that it doesn't work if you plug a USB 3.0 device in a physical USB 3.0 port on the host while giving the guest USB 2.0.  Is USB 2.0 extension cord enough to "downgrade" the port or is an actual USB USB 2.0 hub needed?

Yes, i plug the USB device on the USB 2.0. The device still could not be detected as shown from the screenshot of my previous post

---

### Post by &amp;KyT$0P# on 2016-07-03
> **myusic said:**
> The first method uninstall/install the extension pack is in the Linux (Ubuntu) in the virtualbox itself? not download in windows and install it through windows?
First method you would do in Windows exactly like you said, with no virtual machines running.

---

### Post by myusic on 2016-07-03
> **halogen2 said:**
> First method you would do in Windows exactly like you said, with no virtual machines running.

will it works if i uninstall and install again? what is the rational reason behind ?

---

### Post by &amp;KyT$0P# on 2016-07-03
> **myusic said:**
> will it works if i uninstall and install again?
Whether or not that has a chance of working depends if your Windows 10 host meets the criteria specified by MAFoElffen - 
> your Windows 10 version is 64 bit and that you have Hardware Virtualization (vt-x & vt-d) turned on in your Host BIOS
So, are you running 64-bit Windows 10 on your host?

You can determine whether you have Hardware Virtualization enabled or not by shutting down the VM (if it's running), then once it's powered off look if anything is disabled/grayed out under Settings > System.  If Hardware Virtualization is enabled then nothing should be grayed out.

> what is the rational reason behind ?
I think there are several reasons.  Note that Extension Pack is what contains the USB 2.0 & 3.0 support in VirtualBox.. uninstall/reinstall can get rid of potential corruption in install of the Extension Pack and also will make sure that your Extension pack version matches your VirtualBox version, which is required for stability.
[Get Extension Pack Version 5.0.22 r108108 from this link]("https://www.virtualbox.org/wiki/Download_Old_Builds_5_0")

---

### Post by MAFoElffen on 2016-07-03
Clarification... the Op is running Win10 host, VirtualBox on Win10. Ubuntu is just a VM Guest.

For both those, 

first would be that would be Virtualbox is running, vm guest is not. "Installed from within VirtualBox," does impliy that you install it from inside VirtualBox, with Virtual Box running and no gusts running. The exension pack is a VirtualBox application file and has to be openned by VirtualBox to install as a plug-in extension to the program (itself). That it a method unlike the additionals Iso, that installed to a VM Guest. That adds the VT-x and vt-d capalbilities to  the VirtualBox Manager, which USB pci-passthrough is one of those capabilities.

Does that clear things up on that?

---

### Post by myusic on 2016-07-03
> **halogen2 said:**
> Whether or not that has a chance of working depends if your Windows 10 host meets the criteria specified by MAFoElffen - 

So, are you running 64-bit Windows 10 on your host?


You can determine whether you have Hardware Virtualization enabled or not by shutting down the VM (if it's running), then once it's powered off look if anything is disabled/grayed out under Settings > System.  If Hardware Virtualization is enabled then nothing should be grayed out.

I think there are several reasons.  Note that Extension Pack is what contains the USB 2.0 & 3.0 support in VirtualBox.. uninstall/reinstall can get rid of potential corruption in install of the Extension Pack and also will make sure that your Extension pack version matches your VirtualBox version, which is required for stability.
[Get Extension Pack Version 5.0.22 r108108 from this link]("https://www.virtualbox.org/wiki/Download_Old_Builds_5_0")

Yes, i have check, my PC is able to support virtualization shown by the screen shot

Yes, i went into BIOS settings on my laptop it is enabled as shown by the screen shot

Yes, i have re-download and re-install (download) the extension pack version 5.0.22 but it still not working shown in the screen shot

---

### Post by MAFoElffen on 2016-07-04
But you did not uninstall the old extension pack before you tried to install the new one did you(?) It shows that your tried to update over tthe old, which Oracle support says, is not recommened. They recommend an uninstall the version / Install the new version.

Let's approach this from another direction.

Open a Windows cmd prompt.
```

VBoxManage list extpacks

```
Will list the installed extension packs. First line will say how many extension packs are installed. Second line will say for the extension pack number, starting with 0, what the name is for that pack. Then the version of that pack. Then the revision for that pack. Then, if there are more than one installed, it will repeat for each pack. Simil;ar to this
```

$ VBoxManage list extpacks
Extension Packs: 1
Pack no. 0:   Oracle VM VirtualBox Extension Pack
Version:      4.1.12
Revision:     77218

```
Notice that by that output in that, it may be possible that more than one ext pack could be installed at the same time... Which has "happened" ... and causes a conflict between each other... That is why Oracle Support recommends that you uninstall the extension packs, before installing a new one. So using the name from the above output, the command to uninstall an extension pack would be:
```

$ VBoxManage extpack uninstall "Oracle VM VirtualBox Extension Pack"

```
Even though that is another way to do the same thing, does that make more sense of the why you need to "uninstall" an old version of that, before installing their newer? Is that explanation enough to understand the reasoning behind that? I figured you might appreciate an explanation of what we are asking you to do, instead of just blindly following. You had thought you were doing the same, but there was a detail there (the uninstall) that you skipped... 

Just trying to get you going again.

---

### Post by myusic on 2016-07-04
> **MAFoElffen said:**
> But you did not uninstall the old extension pack before you tried to install the new one did you(?) It shows that your tried to update over tthe old, which Oracle support says, is not recommened. They recommend an uninstall the version / Install the new version.

Let's approach this from another direction.

Open a Windows cmd prompt.
```

VBoxManage list extpacks

```
Will list the installed extension packs. First line will say how many extension packs are installed. Second line will say for the extension pack number, starting with 0, what the name is for that pack. Then the version of that pack. Then the revision for that pack. Then, if there are more than one installed, it will repeat for each pack. Simil;ar to this
```

$ VBoxManage list extpacks
Extension Packs: 1
Pack no. 0:   Oracle VM VirtualBox Extension Pack
Version:      4.1.12
Revision:     77218

```
Notice that by that output in that, it may be possible that more than one ext pack could be installed at the same time... Which has "happened" ... and causes a conflict between each other... That is why Oracle Support recommends that you uninstall the extension packs, before installing a new one. So using the name from the above output, the command to uninstall an extension pack would be:
```

$ VBoxManage extpack uninstall "Oracle VM VirtualBox Extension Pack"

```
Even though that is another way to do the same thing, does that make more sense of the why you need to "uninstall" an old version of that, before installing their newer? Is that explanation enough to understand the reasoning behind that? I figured you might appreciate an explanation of what we are asking you to do, instead of just blindly following. You had thought you were doing the same, but there was a detail there (the uninstall) that you skipped... 

Just trying to get you going again.

Thank you for your advice.

I have tried the method you taught and downloaded [Extension Pack Version 5.0.22 r108108 from this link]("https://www.virtualbox.org/wiki/Download_Old_Builds_5_0") advice from [COLOR=#000000]halogen2 and reinstall again is still not working as shown on the screenshot.[/COLOR]

---

### Post by &amp;KyT$0P# on 2016-07-04
Wait, so you have VirtualBox installed in the guest as well as the host?

Those commands need to be run on the **host** (Windows 10) in a Command Prompt, and you will want to shut down any running virtual machines before running them / messing with Extension Packs.

---

### Post by myusic on 2016-07-04
> **halogen2 said:**
> Wait, so you have VirtualBox installed in the guest as well as the host?

Those commands need to be run on the **host** (Windows 10) in a Command Prompt, and you will want to shut down any running virtual machines before running them / messing with Extension Packs.

nope the VirtualBox only install on the host (Windows 10) i could not run the command  VBoxManage list extpacks on Windows command prompt it prompt the error 'VBoxManage' is not recognized as an internal or external command,operable program or batch file. shown on the attached screen shot

---

### Post by &amp;KyT$0P# on 2016-07-04
That means Windows doesn't know where to find VBoxManage.  If I'm remembering correctly, in Windows the easiest way is to manually find the VBoxManage.exe in Windows Explorer, and drag&drop it from the Windows Explorer into the Command Prompt, instead of typing "VBoxManage".

---

### Post by myusic on 2016-07-05
> **halogen2 said:**
> That means Windows doesn't know where to find VBoxManage.  If I'm remembering correctly, in Windows the easiest way is to manually find the VBoxManage.exe in Windows Explorer, and drag&drop it from the Windows Explorer into the Command Prompt, instead of typing "VBoxManage".

I tried but after i drag in the VBoxManage i cannot proceed any further shown in the screen shot

---

### Post by &amp;KyT$0P# on 2016-07-05
Oops, didn't realize Command Prompt now just runs dragged executables...

Ok let's try a different way.  Type "cd " (that's cd followed by one space) then drag the folder containing VBoxManage.exe into the command prompt, hit Enter if it doesn't just run the command for you.  If it worked, where it says C:\Users\<you> in your screenshot, it will show the path to the directory.
Then you should be able to run VBoxManage if you type it as VBoxManage.exe

---

### Post by myusic on 2016-07-05
> **halogen2 said:**
> Oops, didn't realize Command Prompt now just runs dragged executables...

Ok let's try a different way.  Type "cd " (that's cd followed by one space) then drag the folder containing VBoxManage.exe into the command prompt, hit Enter if it doesn't just run the command for you.  If it worked, where it says C:\Users\<you> in your screenshot, it will show the path to the directory.
Then you should be able to run VBoxManage if you type it as VBoxManage.exe

i have tried to manually reinstall the virtualbox and reinstall the virtualbox of version 5.0.22 and installed the extension pack of 5.0.22 and reinstall Linux Ubuntu. However it is still the same..

---

### Post by &amp;KyT$0P# on 2016-07-10
Maybe you could try, when this USB device is plugged in the Ubuntu VM, use that "bladeRF CLI" application on your host.  Does it see your USB device?

Also, did we compare the output of [FONT=Courier New]lsusb[/FONT] in the guest with the device plugged in vs without it?  I'm not clear whether that unnamed entry in your lsusb output screenshots is there when the device is not plugged in.

Does anything change if you give the VM USB 3.0 instead of 2.0? (Power off the VM and take a snapshot first, so that if it doesn't help you can easily revert.)
Particularly note lsusb output

---

### Post by myusic on 2016-07-13
> **halogen2 said:**
> Maybe you could try, when this USB device is plugged in the Ubuntu VM, use that "bladeRF CLI" application on your host. Does it see your USB device?


Also, did we compare the output of lsusb in the guest with the device plugged in vs without it? I'm not clear whether that unnamed entry in your lsusb output screenshots is there when the device is not plugged in.


Does anything change if you give the VM USB 3.0 instead of 2.0? (Power off the VM and take a snapshot first, so that if it doesn't help you can easily revert.)
Particularly note lsusb output


Nope, my host could not detect because the Ubuntu VM is using the USB.


the lsusb on my guest (Ubuntu) is plugged in but has unnamed entry in the output


I plugged the device to USB 3.0 i got an error from the VM, but for USB 2.0 it can be detected.


Update:


I found a troubleshooting page for the bladeRF, i guess is the permission that cause it. however the instruction i don't quite get it and do not know how to create rules and CMake..?


> 
In order to access the bladeRF, Linux users must ensure:
The 88-nuand.rules file has been installed to /etc/udev/rules.d/
When building from source, the CMake option INSTALL_UDEV_RULES defaults to ON
The user is in the group specified by the CMake variable BLADERF_GROUP
BLADERF_GROUP defaults to plugdev, because Debian/Ubuntu users are typically in this group when allowed to access removable USB storage devices. You may wish to change this to conform to your security policies or distribution.
The udev rules have been reloaded since the installation of the aforementioned rules file
This can be done via sudo udevadm control &#8212;reload-rules and then re-plugging the device.
If you have verified the above items and still cannot see the device:
Confirm that you see the device in the output of lsusb -v
Look for any information about the device's connection in the output of dmesg


PyBOMBS


Because PyBOMBS allows users to perform installations as non-root users, it uses -DINSTALL_UDEV_RULES=OFF when configuring the bladeRF project with CMake. (Copying a file to/etc/udev/rules.d/ requires root access, which a PyBOMBS user may not have.)
Therefore, if you've installed bladeRF support via PyBOMBS you will need to manually install the udev rules:
Copy this file to a 88-nuand.rules file.
In 88-nuand.rules, replace @BLADERF_GROUP@ with the name of a group your user is in.
Copy this file to the udev rules directory: sudo cp 88-nuand.rules /etc/udev/rules.d/ && sudo chmod 644 /etc/udev/rules.d/88-nuand.rules
Reload rules: sudo udevadm control &#8212;reload-rules
Replug the device.



Hope someone can help and enlighten me. The website of troubleshooting i got it from this link: [https://github.com/Nuand/bladeRF/wiki/Troubleshooting#Virtual_Machines](https://github.com/Nuand/bladeRF/wiki/Troubleshooting#Virtual_Machines) 


Thank you

---

### Post by &amp;KyT$0P# on 2016-07-13
So, checking [this]("https://github.com/Nuand/bladeRF/wiki/Troubleshooting#failing-to-see-or-connect-to-the-device") step by step:
> The 88-nuand.rules file has been installed to /etc/udev/rules.d/
Please post the output of running this command in the Linux VM:
```
ls -la /etc/udev/rules.d
```

> The user is in the group specified by the CMake variable BLADERF_GROUP
BLADERF_GROUP defaults to plugdev, because Debian/Ubuntu users are typically in this group when allowed to access removable USB storage devices. You may wish to change this to conform to your security policies or distribution.
And these commands too:
```
id
```

```
cat /etc/udev/rules.d/88-nuand.rules || sudo cat /etc/udev/rules.d/88-nuand.rules
```

---

### Post by myusic on 2016-07-14
> **halogen2 said:**
> So, checking [this]("https://github.com/Nuand/bladeRF/wiki/Troubleshooting#failing-to-see-or-connect-to-the-device") step by step:

Please post the output of running this command in the Linux VM:
```
ls -la /etc/udev/rules.d
```


And these commands too:
```
id
```

```
cat /etc/udev/rules.d/88-nuand.rules || sudo cat /etc/udev/rules.d/88-nuand.rules
```

The attached image is the output run in linux VM

---

### Post by &amp;KyT$0P# on 2016-07-14
Why there is also a 88.nuand.rules file?  Can you also post the output of this command?
```
cat /etc/udev/rules.d/88.nuand.rules
```

Likely the problem is that your BladeRF udev rules doesn't specify an existing group on your system.  Try moving 88.nuand.rules (the one with the dot) somewhere other than /etc/udev/rules.d, then edit /etc/udev/rules.d/88-nuand.rules to replace "@bladerf@" with "plugdev", then maybe reboot your VM.

This command should perform the needed find-and-replace
```
sudo sed --in-place -e 's/@bladerf@/plugdev/g' /etc/udev/rules.d/88-nuand.rules
```

---

### Post by myusic on 2016-07-14
> **halogen2 said:**
> Why there is also a 88.nuand.rules file?  Can you also post the output of this command?
```
cat /etc/udev/rules.d/88.nuand.rules
```



Likely the problem is that your BladeRF udev rules doesn't specify an existing group on your system.  Try moving 88.nuand.rules (the one with the dot) somewhere other than /etc/udev/rules.d, then edit /etc/udev/rules.d/88-nuand.rules to replace "@bladerf@" with "plugdev", then maybe reboot your VM.

This command should perform the needed find-and-replace
```
sudo sed --in-place -e 's/@bladerf@/plugdev/g' /etc/udev/rules.d/88-nuand.rules
```

because i tried to create the nuand rules file searching on the internet but no to no avail. attached is the output of the command.

done with the command as you instructed.

---

### Post by &amp;KyT$0P# on 2016-07-14
Thanks, looks like that file doesn't refer an existing group either.  So you should be able to just delete /etc/udev/rules.d/88.nuand.rules

---

### Post by myusic on 2016-07-15
> **halogen2 said:**
> Why there is also a 88.nuand.rules file?  Can you also post the output of this command?
```
cat /etc/udev/rules.d/88.nuand.rules
```

Likely the problem is that your BladeRF udev rules doesn't specify an existing group on your system.  Try moving 88.nuand.rules (the one with the dot) somewhere other than /etc/udev/rules.d, then edit /etc/udev/rules.d/88-nuand.rules to replace "@bladerf@" with "plugdev", then maybe reboot your VM.

This command should perform the needed find-and-replace
```
sudo sed --in-place -e 's/@bladerf@/plugdev/g' /etc/udev/rules.d/88-nuand.rules
```

Sorry but the problem still not solved yet :(

---

### Post by MAFoElffen on 2016-07-16
As I come back to this, like I implied, your lsusb output sees a blank as your device, but your lsusb results also does not have any results for a USB 3.0 hub...Since it does not have a USB 3.0 hub, and the Nuand BladeRF is a USB 3.0 device, is is not going to be able to ID that device until it gets a USB 3.0 hub.

I found this over on the VirtualBox forum, which has the same as the OP: [https://forums.virtualbox.org/viewtopic.php?f=3&t=78467](https://forums.virtualbox.org/viewtopic.php?f=3&t=78467)

Going through that post, one thing they talked about first was to ensure that in the VM settings for the guest, that the xHCI controller setting was turned to enabled... even though they had to use a sort of strange workaround, it may show that virtualbox still has some quirks in recogniszing USB 3.0. They ended up noticing that that physical machiee, when they connected a USB 3.0 hub, to their USB 3.0 port on that laptop, then the VirtualBox VM Guest would then see a USB Hub.

This tells me that VirtualBox sees some USB 3.0 Hubs, but not all vendor's USB 3.0 hubs. But that also if a hub that is can see is plugged in further down the chain, that it might see that hub.

Liek I said, your guest needs to see a USB 3.0 hub, before it can have that capability... before you can worry about seeing a USB 3.0 device. Sort of having a pony before the cart kind of affair... right?

---

### Post by myusic on 2016-07-16
> **MAFoElffen said:**
> As I come back to this, like I implied, your lsusb output sees a blank as your device, but your lsusb results also does not have any results for a USB 3.0 hub...Since it does not have a USB 3.0 hub, and the Nuand BladeRF is a USB 3.0 device, is is not going to be able to ID that device until it gets a USB 3.0 hub.

I found this over on the VirtualBox forum, which has the same as the OP: [https://forums.virtualbox.org/viewtopic.php?f=3&t=78467](https://forums.virtualbox.org/viewtopic.php?f=3&t=78467)

Going through that post, one thing they talked about first was to ensure that in the VM settings for the guest, that the xHCI controller setting was turned to enabled... even though they had to use a sort of strange workaround, it may show that virtualbox still has some quirks in recogniszing USB 3.0. They ended up noticing that that physical machiee, when they connected a USB 3.0 hub, to their USB 3.0 port on that laptop, then the VirtualBox VM Guest would then see a USB Hub.

This tells me that VirtualBox sees some USB 3.0 Hubs, but not all vendor's USB 3.0 hubs. But that also if a hub that is can see is plugged in further down the chain, that it might see that hub.

Liek I said, your guest needs to see a USB 3.0 hub, before it can have that capability... before you can worry about seeing a USB 3.0 device. Sort of having a pony before the cart kind of affair... right?

thank you for your information.. so basically i need to buy a USB 3.0 Hub to plug into my laptop and use my bladeRF to plug into the hub and try is that what you meant if i interpret correctly?

---

### Post by MAFoElffen on 2016-07-16
No 100% guaranty, but a possible maybe. It's still a guess. Do you know anyone who you could borrow one for a few minutes to test that? 

Maybe even if you talked to whatever salesman ... and explained that you need to check if you need to buy it before you buy it, if you could try it there? (if a portable device) Or be able to return it if you didn't need it? (If a desktop)

---

### Post by myusic on 2016-07-24
> **MAFoElffen said:**
> No 100% guaranty, but a possible maybe. It's still a guess. Do you know anyone who you could borrow one for a few minutes to test that? 

Maybe even if you talked to whatever salesman ... and explained that you need to check if you need to buy it before you buy it, if you could try it there? (if a portable device) Or be able to return it if you didn't need it? (If a desktop)

Hi, i've listen to your advice to use a USB 3.0 hub to try to plug into my bladeRF. Unfortunately the name does not appear in the Terminal of the VM. I have attached a screenshot. 

Thank you

---

### Post by MAFoElffen on 2016-07-26
What I see in the attached from post #7 is that there is a USB 3 type hub. That is great news... before, there was no USB 3.0 hub showing through from the host to the guest...

Now, why is the device not showing in the guest. It was connected to that external USB 3.0 Hub right?

---

### Post by myusic on 2016-07-27
> **MAFoElffen said:**
> What I see in the attached from post #7 is that there is a USB 3 type hub. That is great news... before, there was no USB 3.0 hub showing through from the host to the guest...

Now, why is the device not showing in the guest. It was connected to that external USB 3.0 Hub right?

yes it is connected to the external usb 3.0 hub

Hi guys,

i have found another source of solution.. i guess this guy has the exact same problem as me shown in this link [http://nuand.com/forums/viewtopic.php?t=3875&p=7103](http://nuand.com/forums/viewtopic.php?t=3875&p=7103) 

> 
=====
wget [http://www.astro.caltech.edu/~mcs/tecla ... 6.3.tar.gz]("http://www.astro.caltech.edu/~mcs/tecla/libtecla-1.6.3.tar.gz")
tar zxvf libtecla-1.6.3.tar.gz
cd libtecla
./configure
make && sudo make install
====

The other thing I did was adding the option "-DBLADERF_GROUP=bladerf"
to
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local
-DINSTALL_UDEV_RULES=ON ../

FInally, I did this as well:
cat "/usr/local/lib64" > /etc/ld.so.conf.d/libbladeRF.conf
sudo ldconfig


I have tried to follow the code up till here 

> 
wget [http://www.astro.caltech.edu/~mcs/tecla ... 6.3.tar.gz]("http://www.astro.caltech.edu/~mcs/tecla/libtecla-1.6.3.tar.gz")
tar zxvf libtecla-1.6.3.tar.gz
cd libtecla
./configure
make && sudo make install


But However i could not understand what he meant by this paragraph

The other thing I did was adding the option "-DBLADERF_GROUP=bladerf"
to
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local
-DINSTALL_UDEV_RULES=ON ../

FInally, I did this as well:
cat "/usr/local/lib64" > /etc/ld.so.conf.d/libbladeRF.conf
sudo ldconfig


Please advice

Thank you

---

### Post by MAFoElffen on 2016-07-27
So now, I see by that thread on the vendors community board, that you are seeing your USB 3.0 hub... so far, so good on that... but that there is a problem with their device driver, that is not letting it be seen.

Hmmm: That challenge exists with their driver. You have to manually build their driver and mod it to work?

---

### Post by myusic on 2016-07-27
> **MAFoElffen said:**
> So now, I see by that thread on the vendors community board, that you are seeing your USB 3.0 hub... so far, so good on that... but that there is a problem with their device driver, that is not letting it be seen.

Hmmm: That challenge exists with their driver. You have to manually build their driver and mod it to work?

erm im not quite sure about it but could anyone help me out on this? so maybe i could try to see if is working

> 
[COLOR=#333333]The other thing I did was adding the option "-DBLADERF_GROUP=bladerf"[/COLOR]
[COLOR=#333333]to[/COLOR]
[COLOR=#333333]cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local[/COLOR]
[COLOR=#333333]-DINSTALL_UDEV_RULES=ON ../[/COLOR]

[COLOR=#333333]FInally, I did this as well:[/COLOR]
[COLOR=#333333]cat "/usr/local/lib64" > /etc/ld.so.conf.d/libbladeRF.conf[/COLOR]
[COLOR=#333333]sudo ldconfig[/COLOR]


---

### Post by myusic on 2016-07-31
Hi

could anyone help me out with my previous post?

Thank you

---

