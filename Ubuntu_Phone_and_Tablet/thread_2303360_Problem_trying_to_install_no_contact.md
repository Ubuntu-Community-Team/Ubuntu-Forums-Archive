---
title: "Problem trying to install: no contact"
date: 2015-11-18
forum: Ubuntu Phone and Tablet
---

### Post by mringer on 2015-11-18
I am trying to install UB on a tablet. Currently running Android 4.4.2.
Using instructions from

[https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install)

These say (in part, my inserts in square brackets):

Here, you enable Developer Mode on your device.

    Navigate to Settings &#8594; About phone | About tablet | about. Select the option available on your device. Tip: Some earlier Android versions may not require this step.
    Tap Build number seven times.

A pop-up informs you that you have succeeded.

[ It says: "no need you are already a developer" ]

Enable USB Debugging

Here, you enable USB Debugging. This is required for a USB terminal connection from your Desktop to your device. After enabling Developer Mode, the Developer options item is exposed in the Settings page.

    Navigate to Settings &#8594; Developer options

[ 

A large menu appears. At top  "Developer options    ON "
I cant give the whole menu, the ticked options are:

USB debugging; allow mock locations; verify apps over USB

]

    Enable USB Debugging. When a device is connected, you will be prompted in Android to authorize it.

3. Physically connect your enabled device to your Ubuntu Desktop over USB.

4. On Android, accept the prompt to Allow USB debugging for the specified computer.

[ no such prompt appears ]

5. To verify the connection, use adb to display currently connected devices:

$ adb devices
List of devices attached
025d138e2f521413 device

[ The list is blank ]

Tip: If the device does not display, try running adb kill-server first. Now, the
device is fully connected to your Ubuntu Desktop for development/installation
operations.

[ 

$ adb kill-server
$ adb devices
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
List of devices attached 
[blank]

]



Please any advice? Thankyou

---

### Post by mringer on 2015-11-27
BUMP. please any advice?

---

### Post by krusty8 on 2015-11-30
Upon plugging in the USB cable, what do you see happening here
```
tail -f /var/log/syslog

```

---

### Post by mringer on 2015-12-03
> **krusty8 said:**
> Upon plugging in the USB cable, what do you see happening here
```
tail -f /var/log/syslog

```

Thank you for your reply. The thing has mysteriously started to work. I must have
done something but I dont know what. I will give the syslog extract below, but I 
doubt if it is of any interest. My comments in sq brackets:



```

[ Start: tablet on, unlocked, showing home screen, disconnected]


root@sns:/# tail -f /var/log/syslog
Dec  3 21:20:46 sns kernel: [12781.749031] usb 2-3: New USB device found, idVendor=1f3a, idProduct=1002
Dec  3 21:20:46 sns kernel: [12781.749043] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
Dec  3 21:20:46 sns kernel: [12781.749051] usb 2-3: Product: Android
Dec  3 21:20:46 sns kernel: [12781.749057] usb 2-3: Manufacturer: USB Developer
Dec  3 21:20:46 sns kernel: [12781.749065] usb 2-3: SerialNumber: 032c1817e71500000000
Dec  3 21:20:46 sns kernel: [12781.758645] usb-storage 2-3:1.0: USB Mass Storage device detected
Dec  3 21:20:46 sns kernel: [12781.758963] scsi6 : usb-storage 2-3:1.0
Dec  3 21:20:46 sns kernel: [12781.759738] usb 2-3: USB disconnect, device number 9
Dec  3 21:20:46 sns kernel: [12781.762958] systemd-udevd[11792]: Failed to apply ACL on /dev/bus/usb/002/009: No such file or directory
Dec  3 21:20:46 sns kernel: [12781.762994] systemd-udevd[11792]: Failed to apply ACL on /dev/bus/usb/002/009: No such file or directory

[I think the above was from when I disconnected the tablet the previous time]



[Tablet plugged in]

Dec  3 21:21:48 sns kernel: [12843.088111] usb 2-3: new high-speed USB device number 10 using ehci-pci
Dec  3 21:21:48 sns kernel: [12843.221112] usb 2-3: New USB device found, idVendor=1f3a, idProduct=1002
Dec  3 21:21:48 sns kernel: [12843.221124] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
Dec  3 21:21:48 sns kernel: [12843.221132] usb 2-3: Product: Android
Dec  3 21:21:48 sns kernel: [12843.221139] usb 2-3: Manufacturer: USB Developer
Dec  3 21:21:48 sns kernel: [12843.221146] usb 2-3: SerialNumber: 032c1817e71500000000
Dec  3 21:21:53 sns kernel: [12848.220782] usb-storage 2-3:1.0: USB Mass Storage device detected
Dec  3 21:21:53 sns kernel: [12848.220941] scsi7 : usb-storage 2-3:1.0
Dec  3 21:21:53 sns mtp-probe: checking bus 2, device 10: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3"
Dec  3 21:21:53 sns mtp-probe: bus: 2, device: 10 was not an MTP device
Dec  3 21:21:54 sns kernel: [12849.221171] scsi 7:0:0:0: Direct-Access     USB 2.0  USB Flash Driver 0100 PQ: 0 ANSI: 2
Dec  3 21:21:54 sns kernel: [12849.221773] scsi 7:0:0:1: Direct-Access     USB 2.0  USB Flash Driver 0100 PQ: 0 ANSI: 2
Dec  3 21:21:54 sns kernel: [12849.222396] scsi 7:0:0:2: Direct-Access     USB 2.0  USB Flash Driver 0100 PQ: 0 ANSI: 2
Dec  3 21:21:54 sns kernel: [12849.223143] sd 7:0:0:0: Attached scsi generic sg2 type 0
Dec  3 21:21:54 sns kernel: [12849.223680] sd 7:0:0:1: Attached scsi generic sg3 type 0
Dec  3 21:21:54 sns kernel: [12849.224265] sd 7:0:0:2: Attached scsi generic sg4 type 0
Dec  3 21:21:54 sns kernel: [12849.240838] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Dec  3 21:21:54 sns kernel: [12849.241587] sd 7:0:0:1: [sdc] Attached SCSI removable disk
Dec  3 21:21:54 sns kernel: [12849.242596] sd 7:0:0:2: [sdd] Attached SCSI removable disk

[Exit from tail command]

```

I think I should mark this as solved, but I dont know what the solution was.
Thank you anyway.

---

