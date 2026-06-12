---
title: "Cell phone and the Starling"
date: 2009-12-06
forum: System76 Support
---

### Post by ShowMeGrrl on 2009-12-06
Hi - I have a Starling netbook running Jaunty. I want to transfer photos from my Sony Ericsson TM506 cell phone to my Starling. 

I have a USB cable connecting my cell phone to the Starling, but I can't seem to find a way to get the photos off, nor do I see any indication in the file browser or desktop that the cell phone is "mounted." This is in contrast to other USB devices such as my Sony camera and a USB thumb drive. Both of these latter devices show up on the right side of the desktop as soon as I insert them, and I am able to transfer files back and forth with no problem.

The Starling has 3 USB ports. I use one of them for my optical mouse. I inserted the cell phone USB cable into another, and the third USB port has nothing attached to it.

Apparently, the Starling DOES know about the cell phone, because here is what I get when I use the lsusb command:

myname@system76-netbook:~$ lsusb
Bus 003 Device 004: ID 04b3:310c IBM Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 003: ID 064e:a127 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0fce:e0d6 Sony Ericsson Mobile Communications AB 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have tried using the Wammu phone management software to connect my cell phone and the Starling, but it's not working. When I use the wizard and tell it to automatically find the phone, it comes up empty. When I try either the guided or manual setup, I am asked to input an address or name for the USB port. I have tried various addresses such as: 

Bus 002 Device 005: ID 0fce:e0d6 Sony Ericsson Mobile Communications AB 

or 0fce:e0d6

or 002:005:0fce:e0d6

and in all cases I am given the message that "the device doesn't exist."

When I tried the manual setup, I was given a drop-down list with the choice of tty0, tty1, tty2, and tty3 for this USB port device address. I tried all of those and Wammu still didn't work.

When I first hook up the cell phone to the Starling, the cell phone screen gives me choices of: phone mode, media transfer, print, or mass storage. 

I have tried all of these except print. The phone mode got some action but the wrong kind: it brought up a dialogue that wanted to establish a broadband connection with my provider. I didn't want to do that, so I exited out of that option. Media transfer, of course, is what I want to do, but I just can't seem to get it to work -- at least in a way that I understand. Mass storage also brought no results. 

Can anybody figure a way for me to transfer photos off my cell phone onto the Starling?

---

### Post by drewbenn on 2009-12-06
> **ShowMeGrrl said:**
> I am asked to input an address or name for the USB port.

The device you want is probably in /dev/. Go to a terminal before plugging in the phone, and type ```
ls -1 /dev/ttyUSB*
```
Then plug in the phone, and pick the proper mode in the phone, and issue the same command: you should see a new entry, like 'ttyUSB0'.  Give wammu the path to that new device, e.g. /dev/ttyUSB0.  It might be something completely different, though: my old Nokia with a serial->USB cable is /dev/ttyACM0, so you might have to look around a bit (e.g. do an "ls -rtaFl /dev/" after plugging in the phone to see what was most recently added).

Hope that at least gets you moving in the right direction.

---

### Post by ShowMeGrrl on 2009-12-07
OK, I typed in the command you suggested and here is what I got:

```
myname@system76-netbook:~$ ls -1 /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory
myname@system76-netbook:~$ 
```

---

### Post by mick222 on 2009-12-07
I use 2 different sony Erricson phones both connect using the mass storage option set the phone in connections to mass storage connect via the usb the phone might ask to restart you should then be connected and be able to browse to the photos.I can't get wammu to work either.

---

### Post by ShowMeGrrl on 2009-12-07
Mick222 - I hooked up my cell phone via USB cable and set it to "mass storage" setting and also entered this command in the terminal:

```
tail -f /var/log/messages
```

Below is what I got. Clearly the machine knows that the cell phone is there. I just can't figure out how to get access to it. There's no sign of it on my desktop. In the system messages below, the Starling seems to be constantly checking for wireless networks. I don't have wireless in my house but there are several wireless networks in my neighborhood (the "valley" network is one of them) that occasionally fade in and out of my Starling's consciousness. You can ignore that obviously. The interesting messages in the log are the references to the Sony memory stick, USB mass storage, USB device, SCSI hard disk, etc. Unfortunately, I don't know what any of it means.


```
Dec  6 22:43:42 system76-netbook kernel: [ 2995.788104] rtl8187: IPSEnter(): Turn off RF.
Dec  6 22:43:42 system76-netbook kernel: [ 2995.789247] rtl8187: Now Radio OFF!
Dec  6 22:43:51 system76-netbook kernel: [ 3004.834290] rtl8187: ISLeave(): Turn on RF.
Dec  6 22:43:51 system76-netbook kernel: [ 3004.835879] rtl8187: Now Radio ON!
Dec  6 22:43:54 system76-netbook kernel: [ 3007.788109] rtl8187: IPSEnter(): Turn off RF.
Dec  6 22:43:54 system76-netbook kernel: [ 3007.789258] rtl8187: Now Radio OFF!
Dec  6 22:44:02 system76-netbook kernel: [ 3016.134420] rtl8187: ISLeave(): Turn on RF.
Dec  6 22:44:02 system76-netbook kernel: [ 3016.135599] rtl8187: Now Radio ON!
Dec  6 22:44:04 system76-netbook kernel: [ 3017.788103] rtl8187: IPSEnter(): Turn off RF.
Dec  6 22:44:04 system76-netbook kernel: [ 3017.789250] rtl8187: Now Radio OFF!
Dec  6 22:44:13 system76-netbook kernel: [ 3027.032090] usb 2-1: new full speed USB device using uhci_hcd and address 2
Dec  6 22:44:13 system76-netbook kernel: [ 3027.429872] rtl8187: ISLeave(): Turn on RF.
Dec  6 22:44:13 system76-netbook kernel: [ 3027.431012] rtl8187: Now Radio ON!
Dec  6 22:44:14 system76-netbook kernel: [ 3027.684627] usb 2-1: configuration #2 chosen from 1 choice
Dec  6 22:44:14 system76-netbook kernel: [ 3027.866121] Initializing USB Mass Storage driver...
Dec  6 22:44:14 system76-netbook kernel: [ 3027.866783] scsi2 : SCSI emulation for USB Mass Storage devices
Dec  6 22:44:14 system76-netbook kernel: [ 3027.869001] usbcore: registered new interface driver usb-storage
Dec  6 22:44:14 system76-netbook kernel: [ 3027.869022] USB Mass Storage support registered.
Dec  6 22:44:16 system76-netbook kernel: [ 3029.792248] rtl8187: IPSEnter(): Turn off RF.
Dec  6 22:44:16 system76-netbook kernel: [ 3029.793503] rtl8187: Now Radio OFF!
Dec  6 22:44:19 system76-netbook kernel: [ 3032.876932] scsi 2:0:0:0: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Dec  6 22:44:19 system76-netbook kernel: [ 3032.880327] scsi 2:0:0:1: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Dec  6 22:44:19 system76-netbook kernel: [ 3032.889440] sd 2:0:0:0: [sdb] 120093 512-byte hardware sectors: (61.4 MB/58.6 MiB)
Dec  6 22:44:19 system76-netbook kernel: [ 3032.906043] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
Dec  6 22:44:19 system76-netbook kernel: [ 3032.932330] sd 2:0:0:0: [sdb] 120093 512-byte hardware sectors: (61.4 MB/58.6 MiB)
Dec  6 22:44:19 system76-netbook kernel: [ 3032.942559] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
Dec  6 22:44:19 system76-netbook kernel: [ 3032.942609]  sdb: sdb1
Dec  6 22:44:19 system76-netbook kernel: [ 3032.958678] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Dec  6 22:44:19 system76-netbook kernel: [ 3032.959012] sd 2:0:0:0: Attached scsi generic sg1 type 0
Dec  6 22:44:19 system76-netbook kernel: [ 3032.964490] sd 2:0:0:1: [sdc] Attached SCSI removable disk
Dec  6 22:44:19 system76-netbook kernel: [ 3032.964688] sd 2:0:0:1: Attached scsi generic sg2 type 0
Dec  6 22:44:25 system76-netbook kernel: [ 3038.745798] rtl8187: ISLeave(): Turn on RF.
Dec  6 22:44:25 system76-netbook kernel: [ 3038.747380] rtl8187: Now Radio ON!
Dec  6 22:44:28 system76-netbook kernel: [ 3041.792104] rtl8187: IPSEnter(): Turn off RF.
Dec  6 22:44:28 system76-netbook kernel: [ 3041.793253] rtl8187: Now Radio OFF!
Dec  6 22:44:31 system76-netbook kernel: [ 3045.087829] Linking with Valley, channel:11
Dec  6 22:44:31 system76-netbook kernel: [ 3045.088561] rtl8187: ISLeave(): Turn on RF.
Dec  6 22:44:31 system76-netbook kernel: [ 3045.090753] rtl8187: Now Radio ON!
Dec  6 22:44:31 system76-netbook kernel: [ 3045.136691] Linking with Valley, channel:11
Dec  6 22:44:34 system76-netbook kernel: [ 3047.652094] Linking with Valley, channel:11
Dec  6 22:44:36 system76-netbook kernel: [ 3050.164121] Linking with Valley, channel:11
Dec  6 22:44:39 system76-netbook kernel: [ 3052.784099] Linking with Valley, channel:11
Dec  6 22:44:41 system76-netbook kernel: [ 3055.300101] ieee80211_associate_retry_wq():Not find SSID:Valley[ch=11, mode=BSS] in network list scan now
Dec  6 22:44:48 system76-netbook kernel: [ 3061.792088] rtl8187: IPSEnter(): Turn off RF.
Dec  6 22:44:48 system76-netbook kernel: [ 3061.793259] rtl8187: Now Radio OFF!
Dec  6 22:44:50 system76-netbook kernel: [ 3064.112108] usb 2-1: reset full speed USB device using uhci_hcd and address 2
Dec  6 22:44:51 system76-netbook kernel: [ 3064.590709] rtl8187: Setting SW wep key
Dec  6 22:44:51 system76-netbook kernel: [ 3064.603747] rtl8187: ISLeave(): Turn on RF.
Dec  6 22:44:51 system76-netbook kernel: [ 3064.606112] rtl8187: Now Radio ON!
Dec  6 22:44:56 system76-netbook kernel: [ 3069.792223] rtl8187: IPSEnter(): Turn off RF.
Dec  6 22:44:56 system76-netbook kernel: [ 3069.793260] rtl8187: Now Radio OFF!
Dec  6 22:45:21 system76-netbook kernel: [ 3095.112146] usb 2-1: reset full speed USB device using uhci_hcd and address 2
Dec  6 22:45:40 system76-netbook kernel: [ 3113.543551] rtl8187: ISLeave(): Turn on RF.
Dec  6 22:45:40 system76-netbook kernel: [ 3113.544751] rtl8187: Now Radio ON!
Dec  6 22:45:42 system76-netbook kernel: [ 3115.792131] rtl8187: IPSEnter(): Turn off RF.
Dec  6 22:45:42 system76-netbook kernel: [ 3115.793390] rtl8187: Now Radio OFF!
```

---

### Post by drewbenn on 2009-12-07
mick222's suggestion is definitely more promising than using wammu!  The 'sdb' and 'sdc' lines in your dmesg look like the phone has been connected like any other USB storage device.  Go to a Nautilus (File Browser) window: do you have 2 new entries in the Places window? (If it's not already there, turn on Places by enabling View | Sidepane, and then select 'Places' from the dropdown menu at the top of the sidepane.)  If so, try clicking on the entry to mount it.

If there's nothing there, try "sudo fdisk -l" in a terminal, which will list all the partitions.

---

### Post by ShowMeGrrl on 2009-12-07
drewbenn - No, I don't have new entries in my places list. That's what puzzles me. The log messages indicate that the Starling is aware of the Sony Ericsson mass storage in the USB port, but there is no indication of its presence other than the log message.

I did the  fdisk command that you suggested and here is what I got:

```
myname@system76-netbook:~$ sudo fdisk -l
[sudo] password for myname: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b2733

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14648437+  83  Linux
/dev/sda2            1824        1945      966796+  83  Linux
/dev/sda3            1945       19458   140675669+  83  Linux
jhadle@system76-netbook:~$ 

```

---

### Post by drewbenn on 2009-12-07
I'm afraid this is beyond me.  It does remind me a little bit of a problem I had with a Sansa music player, where another program was intercepting the event and preventing the music player from mounting.  I did a little googling and came across [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/318939](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/318939) ... comment #6 might be worth trying.

---

### Post by thomasaaron on 2009-12-07
Could you try the tail -f /var/log/syslog command one more time. The output above gives me some ideas, but it is pretty chaotic. Lot's of wireless junk intermingled in there too.

So unplug the phone from the computer, run...

tail -f /var/log/syslog

...and *then* plug in the phone. 

What is the output?

---

### Post by ShowMeGrrl on 2009-12-07
Thomas Aaron -- I did the syslog command and below is the output:


```
myname@system76-netbook:~$ tail -f /var/log/syslog
Dec  7 11:27:11 system76-netbook NetworkManager: <info>  (wlan1): device state change: 9 -> 3 
Dec  7 11:27:11 system76-netbook NetworkManager: <info>  (wlan1): deactivating device (reason: 0). 
Dec  7 11:27:11 system76-netbook kernel: [  309.931947] rtl8187: Setting SW wep key
Dec  7 11:27:11 system76-netbook NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Dec  7 11:27:11 system76-netbook kernel: [  309.941821] rtl8187: ISLeave(): Turn on RF.
Dec  7 11:27:11 system76-netbook kernel: [  309.942877] rtl8187: Now Radio ON!
Dec  7 11:27:17 system76-netbook kernel: [  315.784106] rtl8187: IPSEnter(): Turn off RF.
Dec  7 11:27:17 system76-netbook kernel: [  315.785275] rtl8187: Now Radio OFF!
Dec  7 11:27:24 system76-netbook anacron[2898]: Job `cron.daily' started
Dec  7 11:27:24 system76-netbook anacron[3567]: Updated timestamp for job `cron.daily' to 2009-12-07
Dec  7 11:28:25 system76-netbook kernel: [  382.993937] rtl8187: ISLeave(): Turn on RF.
Dec  7 11:28:25 system76-netbook kernel: [  382.995050] rtl8187: Now Radio ON!
Dec  7 11:28:27 system76-netbook kernel: [  385.768116] usb 2-1: new full speed USB device using uhci_hcd and address 2
Dec  7 11:28:27 system76-netbook kernel: [  385.784078] rtl8187: IPSEnter(): Turn off RF.
Dec  7 11:28:27 system76-netbook kernel: [  385.785155] rtl8187: Now Radio OFF!
Dec  7 11:28:28 system76-netbook kernel: [  386.354293] usb 2-1: configuration #2 chosen from 1 choice
Dec  7 11:28:28 system76-netbook kernel: [  386.422807] Initializing USB Mass Storage driver...
Dec  7 11:28:28 system76-netbook kernel: [  386.448156] scsi2 : SCSI emulation for USB Mass Storage devices
Dec  7 11:28:28 system76-netbook kernel: [  386.453572] usbcore: registered new interface driver usb-storage
Dec  7 11:28:28 system76-netbook kernel: [  386.453585] USB Mass Storage support registered.
Dec  7 11:28:28 system76-netbook kernel: [  386.454389] usb-storage: device found at 2
Dec  7 11:28:28 system76-netbook kernel: [  386.454397] usb-storage: waiting for device to settle before scanning
Dec  7 11:28:33 system76-netbook kernel: [  391.455375] usb-storage: device scan complete
Dec  7 11:28:33 system76-netbook kernel: [  391.458314] scsi 2:0:0:0: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Dec  7 11:28:33 system76-netbook kernel: [  391.461310] scsi 2:0:0:1: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Dec  7 11:28:33 system76-netbook kernel: [  391.479985] sd 2:0:0:0: [sdb] 120093 512-byte hardware sectors: (61.4 MB/58.6 MiB)
Dec  7 11:28:33 system76-netbook kernel: [  391.488306] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
Dec  7 11:28:33 system76-netbook kernel: [  391.488322] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Dec  7 11:28:33 system76-netbook kernel: [  391.499307] sd 2:0:0:0: [sdb] 120093 512-byte hardware sectors: (61.4 MB/58.6 MiB)
Dec  7 11:28:33 system76-netbook kernel: [  391.507572] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
Dec  7 11:28:33 system76-netbook kernel: [  391.507588] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Dec  7 11:28:33 system76-netbook kernel: [  391.507612]  sdb: sdb1
Dec  7 11:28:33 system76-netbook kernel: [  391.519552] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Dec  7 11:28:33 system76-netbook kernel: [  391.519878] sd 2:0:0:0: Attached scsi generic sg1 type 0
Dec  7 11:28:33 system76-netbook kernel: [  391.527007] sd 2:0:0:1: [sdc] Attached SCSI removable disk
Dec  7 11:28:33 system76-netbook kernel: [  391.527382] sd 2:0:0:1: Attached scsi generic sg2 type 0
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Activation (wlan1) starting connection 'Auto Valley' 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  (wlan1): device state change: 3 -> 4 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  (wlan1): device state change: 4 -> 5 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Activation (wlan1/wireless): connection 'Auto Valley' requires no security.  No secrets needed. 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Config: added 'ssid' value 'Valley' 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  Config: set interface ap_scan to 1 
Dec  7 11:28:36 system76-netbook NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected 
Dec  7 11:28:36 system76-netbook kernel: [  394.040095] rtl8187: ISLeave(): Turn on RF.
```

---

### Post by thomasaaron on 2009-12-08
This seems to be the pertinent output...

```
kernel: [  386.454389] usb-storage: device found at 2
Dec  7 11:28:28 system76-netbook kernel: [  386.454397] usb-storage: waiting for device to settle before scanning
Dec  7 11:28:33 system76-netbook kernel: [  391.455375] usb-storage: device scan complete
Dec  7 11:28:33 system76-netbook kernel: [  391.458314] scsi 2:0:0:0: Direct-Access     **Sony Eri Memory Stick **       0 PQ: 0 ANSI: 0
Dec  7 11:28:33 system76-netbook kernel: [  391.461310] scsi 2:0:0:1: Direct-Access     **Sony Eri Memory Stick**        0 PQ: 0 ANSI: 0
Dec  7 11:28:33 system76-netbook kernel: [  391.479985] sd 2:0:0:0: [sdb] 120093 512-byte hardware sectors: (61.4 MB/58.6 MiB)
Dec  7 11:28:33 system76-netbook kernel: [  391.488306] sd 2:0:0:0: [sdb] **Test WP failed, assume Write Enabled**
Dec  7 11:28:33 system76-netbook kernel: [  391.488322] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Dec  7 11:28:33 system76-netbook kernel: [  391.499307] sd 2:0:0:0: [sdb] 120093 512-byte hardware sectors: (61.4 MB/58.6 MiB)
Dec  7 11:28:33 system76-netbook kernel: [  391.507572] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
Dec  7 11:28:33 system76-netbook kernel: [  391.507588] sd 2:0:0:0: [sdb] Assuming drive cache: write through
```

I'm sort of getting mixed messages about what it all means via Googling. But it looks like Ubuntu just doesn't play nicely with whatever kind of formatting/filesystem your phone uses.

---

### Post by ShowMeGrrl on 2009-12-08
Thomas - Thanks for your efforts.  

I can always e-mail the pictures to myself and get them onto the Starling that way, but I am charged 15 cents for each e-mail, so I prefer not to do it that way.

A hypothetical question: If had another System76 computer such as the Wildebeest and was running Windows XP on it in Virtual Box and installed the cell phone's Windows software, would the cell phone likely work in that case?

---

### Post by thomasaaron on 2009-12-08
Yes.

Make sure you don't install the OSE version of Virtualbox in the repos. It doesn't have USB support.

But you can download the latest version from Sun Microsystems, which does have USB support. Then you should be able to install the software and create a USB filter to link the phone to your VM.

---

