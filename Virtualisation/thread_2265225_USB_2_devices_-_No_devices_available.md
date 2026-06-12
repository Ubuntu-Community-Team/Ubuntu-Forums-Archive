---
title: "USB 2 devices - No devices available"
date: 2015-02-13
forum: Virtualisation
---

### Post by bizres on 2015-02-13
Hi,

I've got an Ubuntu 14.04 PC with VirtualBox 4.3.10 installed and running OK.
In there I have a Windows 7 guest OS running OK.

However, the issue is that USB devices cannot be seen by VirtualBox.
I have successfully installed the necessary extension pack and even enabled USB 2 for the Win 7 guest OS, but USB just says "No devices available". The same USB devices like flash disks work perfectly OK in the Ubuntu host OS.
I also have guest additions installed OK.

Would really appreiate some help on this, pls.

---

### Post by Jonners59 on 2015-02-20
I have the same problem hosting Windows 7.
I have VBox running the same install config on two machines.  One has worked for years perfectly fine, but the new configuration on the second machine does not pick up the USB ports even though Guest Additions has been installed.

System details:

[HTML]p { margin-bottom: 0.25cm; line-height: 120%; }   Ubuntu 10.04 trusty
 

 baronipc@baronipc:~$ head /proc/version 
 Linux version 3.13.0-45-generic (buildd@phianna) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 
 

 baronipc@baronipc:~$ head /proc/meminfo 
 MemTotal:       16415508 kB   15.7GB 
 MemFree:         5527532 kB 
 Buffers:         1026680 kB 
 Cached:          3796324 kB 
 SwapCached:            0 kB 
 Active:          7927100 kB 
 Inactive:        1834100 kB 
 Active(anon):    4958508 kB 
 Inactive(anon):    71948 kB 
 Active(file):    2968592 kB 
 

 baronipc@baronipc:~$ head /proc/cpuinfo 
 processor	: 0 
 vendor_id	: GenuineIntel 
 cpu family	: 6 
 model		: 42 
 model name	: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz 
 stepping	: 7 
 microcode	: 0x14 
 cpu MHz		: 2200.000 
 cache size	: 6144 KB 
 physical id	: 0 
 

 baronipc@baronipc:~$ sudo dmidecode -t 2 
 [sudo] password for baronipc:  
 # dmidecode 2.12 
 SMBIOS 2.6 present. 
  Handle 0x0002, DMI type 2, 15 bytes 
 Base Board Information 
 	Manufacturer: ASUSTeK Computer INC. 
 	Product Name: P8P67-M PRO 
 	Version: Rev X.0X 
 	Serial Number: MT7014018601056 
 	Asset Tag: To be filled by O.E.M. 
 	Features: 
 		Board is a hosting board 
 		Board is replaceable 
 	Location In Chassis: To be filled by O.E.M. 
 	Chassis Handle: 0x0003 
 	Type: Motherboard 
 	Contained Object Handles: 0 

[/HTML]

---

### Post by TheFu on 2015-02-20
USB passthru has a trick.  Only 1 OS can access these devices at a time. If the hostOS grabs access to the USB device, then that must be freed before any guestOS can receive the "pass through".

In windows, there's a global menu in the top/center of the virtual machine with devices that can grab any non-used USB device from the hostOS (Windows). Don't know how this works for a Linux host.  For devices you only want available to the guest, reserve it [http://askubuntu.com/questions/481693/virtualbox-usb-add-device-filter-does-not-work-under-14-04](http://askubuntu.com/questions/481693/virtualbox-usb-add-device-filter-does-not-work-under-14-04)
[http://www.virtualbox.org/manual/ch03.html#idp93064144](http://www.virtualbox.org/manual/ch03.html#idp93064144) has more details.

---

### Post by Jonners59 on 2015-02-20
> **TheFu said:**
> 
In windows, there's a global menu in the top/center of the virtual machine with devices that can grab any non-used USB device from the hostOS (Windows). Don't know how this works for a Linux host.  For devices you only want available to the guest, reserve it [http://askubuntu.com/questions/481693/virtualbox-usb-add-device-filter-does-not-work-under-14-04](http://askubuntu.com/questions/481693/virtualbox-usb-add-device-filter-does-not-work-under-14-04)
[http://www.virtualbox.org/manual/ch03.html#idp93064144](http://www.virtualbox.org/manual/ch03.html#idp93064144) has more details.

Thank you
Looked at the link.  Have added the fstab line and have also tried the user group, but the vbox group does not exist :confused:

---

### Post by TheFu on 2015-02-20
Didn't notice that before ... are you really running 10.04 still?  Only a few more months of support for 10.04 Server - desktop support ended about 2 yrs ago.

Did you see this:
**sudo usermod -a -G vboxusers $USER**, log off, on and try again.

there isn't any "vbox" group that is useful. We need to be exactly, correct, for this stuff to work.  **3.10.2. Implementation notes for Windows and Linux hosts** in the 2nd link explains.

---

### Post by Jonners59 on 2015-02-21
> **TheFu said:**
> Didn't notice that before ... are you really running 10.04 still?  Only a few more months of support for 10.04 Server - desktop support ended about 2 yrs ago.

Sorry that was a typo...  It is 14.10

> **TheFu said:**
> Did you see this:
**sudo usermod -a -G vboxusers $USER**, log off, on and try again.
Tried that but there is no vboxusers group.

> **TheFu said:**
> there isn't any "vbox" group that is useful. We need to be exactly, correct, for this stuff to work.  **3.10.2. Implementation notes for Windows and Linux hosts** in the 2nd link explains.
Yes saw those babies too, but justy a tad complicated for me.

---

### Post by TheFu on 2015-02-21
If there isn't a group that is required, did you make it and add yourself to it?

Usually the required group should be created by the virtualbox installation process.
[http://ubuntuforums.org/showthread.php?t=2247263](http://ubuntuforums.org/showthread.php?t=2247263) talks about installing virtualbox using a PPA. That is how I'd do it - to future updates are automatic with your weekly apt-get update/upgrade process.

After you get the PPA setup, do a --reinstall. That should re-setup anything missing.

---

### Post by Jonners59 on 2015-02-22
> **TheFu said:**
> If there isn't a group that is required, did you make it and add yourself to it?

Usually the required group should be created by the virtualbox installation process.
[http://ubuntuforums.org/showthread.php?t=2247263](http://ubuntuforums.org/showthread.php?t=2247263) talks about installing virtualbox using a PPA. That is how I'd do it - to future updates are automatic with your weekly apt-get update/upgrade process.

After you get the PPA setup, do a --reinstall. That should re-setup anything missing.


OK, I managed to get the list of devices working and selected my USB device (Samsung S3 phone) OK, but now having trouble with drivers...  Another story not for this thread.

I managed to make it work by adding the source from the Oracle website, and using Synaptic Package manager to add all that I thought appropriate and uninstalling the "old" VB from Ubuntu Software Centre.... and then adding the ```
[FONT=Ubuntu Mono]sudo usermod -a -G vboxusers $USER[/FONT]
```....  I could then select it and other devices from the list in USB devices.

---

### Post by TheFu on 2015-02-22
Excellent work!
I hope you installed via a PPA, not by downloading a .deb file.  You won't get updates with the .deb install, which has security implications.

The basic issue was the group, I believe. OTOH, the PPA install should have created the group. Did you happen to check that before running the cmd? It would help others.

---

### Post by Jonners59 on 2015-02-22
> **TheFu said:**
> Excellent work!
I hope you installed via a PPA, not by downloading a .deb file.  You won't get updates with the .deb install, which has security implications.

The basic issue was the group, I believe. OTOH, the PPA install should have created the group. Did you happen to check that before running the cmd? It would help others.

Yes to the first question
Yes, I agree, it probably was and maybe the Add-on may not have been working properly, either way a fresh install seemed to do the trick followed by the cmd to add me to the group.

In answer to your last question, no.  Sorry.

Thanks for standing by though.  I can't close this thread (Solved) as I do not won it.

---

