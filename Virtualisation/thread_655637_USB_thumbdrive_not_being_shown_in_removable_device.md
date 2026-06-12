---
title: "USB thumbdrive not being shown in removable devices in VMware Server."
date: 2008-01-01
forum: Virtualisation
---

### Post by diablo75 on 2008-01-01
I have a USB thumb drive that appears to be recongnized ok within Ubuntu, and I can read and write to it, but I can't get the device to show up within the Removable Devices menu within VMware Server.  Any ideas why?

Edit:  Something of note (this could be a clue).  This drive was once behaving as if it were read only.  It once contained a lot of files that could not be deleted unless done with a sudo rm -d * command.  And couldn't write any files to the drive unless **sudo nautilus **was run.

I'm wondering if there is something about permissions going on with this drive acting like it is.

---

### Post by fjgaude on 2008-01-01
Yes, you have to uncomment four lines:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Starting at line #45 make these four look like this:

```
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

You may wish to add this line to fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Such has aided in adding USB drives to the list.

Reboot and see if you can access the USB devices. If not, let us know.

---

### Post by Tuxi on 2008-01-03
This suggestion seems to work, but I can only mount USB disks that were unmounted when VMWare was started.  If I remove the disk, I have to shutdown and restart VMWare-server.

BTW, I just did "sudo /etc/init.d/mountdevsubfs.sh start".  This also fixed a usbview problem I had.

Thanks!

---

### Post by fjgaude on 2008-01-03
Well, a USB mounted in Ubuntu host may not be able to be mounted in the guest. I'll have to look into that. Is this your only issue?

---

### Post by Tuxi on 2008-01-03
The USB drive *must* be unmounted in the host.  It's always been that way for me.  

The issue now is that I can't remove it from the Windows VM and then reuse it without shutting down and restarting VMWare-server

---

### Post by fjgaude on 2008-01-03
You mean if you unclick it in the Devices menu of guest it cannot be remounted again without restarting the VMware?

---

### Post by Tuxi on 2008-01-03
That is correct.

---

### Post by fjgaude on 2008-01-03
Have you checked what the permissions and owership of the USB drvie is? What filesystem is the drive?

---

### Post by Tuxi on 2008-01-04
The filesystem is VFAT, the owner is my normal user, the group is root, and it's rwxr-xr-x (755) in Ubuntu.  

I successfully saved a file to the stick in VMWare and removed the stick using the VM/Removable Devices/USB Devices menu.  Upon reinsertion of the stick, the menu item was empty.

---

### Post by fjgaude on 2008-01-04
Okay, looks like a bug in vmware... the only thing I'd try is to make the group the user. Can't think of anything else.

---

### Post by Tuxi on 2008-01-04
It may have been user error.

I reRTFM ;-) and noticed that the proper procedure to remove the device is
1. use Wiindows safely remove hardware feature
2. use VM/Removable Devices/USB Devices menu to disconnect the device from the VM

When I followed these steps just now, I was able to remove the USB stick, plug it back in, ensure Ubuntu had not mounted the disk, and connect to the VM :-)

After reading theVMWare-server manual on USB devices, I realized that the key is to set up /proc/bus/usb/devices, which is what the edit and starting of /etc/init.d/mountdevsubfs.sh does.

TYVM

---

### Post by fjgaude on 2008-01-04
Congrats... I tried the things you wished to do on my system without any problems. In fact right now I'm connected to the USB Flash drive both in Ubuntu and in WinXP without issue. Go figure. Anyway, Ubunut rules, eh?

---

### Post by Tuxi on 2008-01-04
Nice to hear that you can access the drive on both OSes at once.

I also notice that you are another of the Dell 1505N laptop owners.  I run VMWare on my Dell 1505N :-)

---

### Post by fjgaude on 2008-01-04
Yes, yes... I'm a Dell 1505n owner. I have blown out the original install and have Gutsy 64-bit with VMware and the three Windows progams I use.

The only thing that doesn't work is Suspend and Recover, other than that it does a really good job. Not as fast as my main box but nice to have on the road.

I didn't try to write to the Flash Drive when it was recognized by WinXP and Ubuntu. Now why would I ever want to do that? <smile>

I wish VMware would update to handle USB 2.2, but it is a small issue. My printers and scanner don't know the difference.

---

### Post by Tuxi on 2008-01-05
I've done some more USB testing.  

USB 2 thumbdrives aren't working properly although they seem to be.  If the USB 2 device is connected but not mounted when VMWare is started up, it shows on the VM/Remvable Devices/USB Devices menu.  When selected, Windows has the message about it being faster on  a USB 2 port, and the Safely Remove Hardware icon appears.  If I try to go to the disk in Windows Explorer or in a command prompt, I get the message to insert a disk (GUI) or drive is not ready (CLI).  If I safely remove the drive and use the VM menu to remove it from the VM, it does not show up in the VM menu.  :-(

I also tried to use WebUpdater with a Garmin GPS.  If the device is on when VMWare is started, I see the device in the VM menu and it is attached to the Windows session.  WebUpdater appears to disconnect the device during its updating process (between steps), and VMWare no longer sees it.  I say it appears to disconnect because I had a usbview window opened and the gps highlighter; during the update, the hightlight moved from the gps to the root of the usb tree.

I guess I need to spend more time in the VMWare forums.

---

### Post by fjgaude on 2008-01-05
Thanks for the update... I don't have any real issues with USB situation in VMware server, other than what I said.

Do please keep us updated if you find anything new from the VMware Forums.

---

### Post by Tuxi on 2008-03-06
I gave up on looking at the VMware user forums.

I've now switched to Innoteck's Virtualbox which has USB 2 support.  I've gotten all the USB devices working, but I've still had some issues with Windows (or the VM) dropping a Garmin GPS during an update.

---

### Post by sum][one on 2008-05-07
Hey there,

I have exactly the same problem.. but with my Nokia n95 8gb... 
the interesting thing is that I didnt had this problem with 7.10 Gutsy.. I have the problem only since I upgraded to 8.04 Hardy.

the whole scenario is:

vmware Workstation 6.0.0 build-45731
problem is that the virtual machine doesnt update USB devices when the machine is on.. it NEEDS to be reset to update USB devices.. (NOT reboot, that doesnt fix, hence is not Windows related, its vmware machine related)
therefore.. when I tyr to update my Nokia N95 firmware which, like the GPS update, gets disconnected and reconnected by the updater .. but the virtual machine doesnt update the USB devices.. making the update impossibile as it gets stuck and complain about device not connected (cause is actually not re-connected).

As I said everything was fine with same vmware version on Gutsy .. so maybe the problem is in the compiled kernel modules that handles the USB devices?...

any help is REALLY appreciated.

cheers.

---

### Post by SlonUA on 2008-11-14
> **fjgaude said:**
> Yes, you have to uncomment four lines:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Starting at line #45 make these four look like this:

```
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```


[COLOR="Red"]Not working in Intrepid. Removed[/COLOR].

> 

You may wish to add this line to fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Such has aided in adding USB drives to the list.

Reboot and see if you can access the USB devices. If not, let us know.



Perfectly work in ALL distros and for ALL virtualization, BUT u must resolve security access for it OR just run job as SUDO =)

---

