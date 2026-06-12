---
title: "CF-953AX adapter(mt7921u) disappeared"
date: 2024-03-21
forum: Virtualisation
---

### Post by hiloves on 2024-03-21
I am from China.Please forgive my English!Sorry!

I created a vm with Ubuntu Server 23.10.
I pluged my CF-953AX adapter(mt7921u),ubuntu shows me some errors,the prompt freezed some seconds,then CF-953AX adapter disappeared from the vm.
Kali and Debian has no problem like this.CF-953AX adapter's wifi worked well on them.

*deleted link*

VM:VMware workstation 17.0.0 build-20800274
System:Linux kali 6.5.0-26-generic #26-Ubuntu SMP PREEMPT_DYNAMIC Tue Mar 5 21:19:28 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
Sorry,my system and username is kali.

---

### Post by ajgreeny on 2024-03-21
Moved to **Virtualisation** which is more appropriate for this problem.

---

### Post by DuckHook on 2024-03-21
Welcome to the forums, hiloves.

As a new member of the forums, it is understandable that you are unfamiliar with our netiquette, but please do not post links to zip files or other downloads. This is not good practice and raises serious issues about security.

I for one would never open a private link or an unknown zip file from a stranger.

Accordingly, I have deleted the link in your original post.

There is no need to post a full video of your problem anyway. In fact, it is very difficult to work with and will discourage people from helping. Linux is designed so that you can capture plain output, either through piping the output to a file or scrolling back through terminal output, then copying and pasting the output directly to your posts on this site. Be sure to enclose your output in [noparse]```

```[/noparse] tags to preserve formatting and readability. There are many videos and instructions teaching how to pipe output. Please do a websearch to learn how.

Troubleshooting should also start by checking your logs. These can tell you a lot of information that is useful for finding the problem.

Last but not least, most people running servers do not run standard releases like 23.10 because they only have 9 months of support. LTS releases like 22.04 which have 5 years of support are the usual choice. Is there a reason that you have chosen 23.10? If not, perhaps 22.04 will solve your problem.

---

### Post by hiloves on 2024-03-21
Sorry,It's my bad.

I chose 23.10 because linux core image of 22.04.4 is too old to drive CF-953AX adapter.I have to upgrade linux-image-6.5.

```
sudo apt install linux-headers-6.5.0-26-generic linux-image-6.5.0-26-generic linux-modules-6.5.0-26-generic linux-modules-extra-6.5.0-26-generic
```

But the problem is still in there.So, I think maybe I do something wrong when I upgrade.

---

### Post by DuckHook on 2024-03-21
According to the following post, you ***can*** run this adapter in 22.04 (which I would recommend over 23.10). Even the 5.19 kernel will work. You do not need anything newer. However, you do need to add the mt7921u driver. Have a look at this user's solution: [https://www.medo64.com/2023/07/running-comfast-cf-953ax-on-ubuntu-22-04/](https://www.medo64.com/2023/07/running-comfast-cf-953ax-on-ubuntu-22-04/)

If this works for you, please mark the thread *solved* for the benefit of the community.

---

### Post by hiloves on 2024-03-21
> **DuckHook said:**
> According to the following post, you ***can*** run this adapter in 22.04 (which I would recommend over 23.10). Even the 5.19 kernel will work. You do not need anything newer. However, you do need to add the mt7921u driver. Have a look at this user's solution: [https://www.medo64.com/2023/07/running-comfast-cf-953ax-on-ubuntu-22-04/](https://www.medo64.com/2023/07/running-comfast-cf-953ax-on-ubuntu-22-04/)

If this works for you, please mark the thread *solved* for the benefit of the community.

Thanks for your help.But my problem isn't like this.I couldn't find CF-953AX in ubuntu.

I reinstalled ubuntu 22.04.4 lts instead of 23.10.I try linux-image-5.15.0-101-generic and linux-image-6.5.0-26-generic.Also,I upgraded vm workstation to 17.5.1 build-23298084.

This is log.
```

kali@kali1981:~$ sudo uname -a
Linux kali1981 5.15.0-101-generic #111-Ubuntu SMP Tue Mar 5 20:16:58 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
kali@kali1981:~$ sudo lsusb -tv
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
    |__ Port 1: Dev 5, If 0, Class=Wireless, Driver=btusb, 5000M
        ID 0e8d:7961 MediaTek Inc. 
    |__ Port 1: Dev 5, If 1, Class=Wireless, Driver=btusb, 5000M
        ID 0e8d:7961 MediaTek Inc. 
    |__ Port 1: Dev 5, If 2, Class=Wireless, Driver=, 5000M
        ID 0e8d:7961 MediaTek Inc. 
    |__ Port 1: Dev 5, If 3, Class=Vendor Specific Class, Driver=, 5000M
        ID 0e8d:7961 MediaTek Inc. 
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        ID 0e0f:0003 VMware, Inc. Virtual Mouse
    |__ Port 3: Dev 3, If 0, Class=Hub, Driver=hub/7p, 12M
        ID 0e0f:0002 VMware, Inc. Virtual USB Hub
    |__ Port 4: Dev 4, If 0, Class=Hub, Driver=hub/7p, 480M
        ID 0e0f:0002 VMware, Inc. Virtual USB Hub
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub


Mar 22 02:39:41 kali1981 kernel: [ 8806.271899] usb 4-1: new SuperSpeed USB device number 5 using xhci_hcd
Mar 22 02:39:41 kali1981 kernel: [ 8806.298309] usb 4-1: New USB device found, idVendor=0e8d, idProduct=7961, bcdDevice= 1.00
Mar 22 02:39:41 kali1981 kernel: [ 8806.298313] usb 4-1: New USB device strings: Mfr=6, Product=7, SerialNumber=8
Mar 22 02:39:41 kali1981 kernel: [ 8806.298315] usb 4-1: Product: Wireless_Device
Mar 22 02:39:41 kali1981 kernel: [ 8806.298317] usb 4-1: Manufacturer: MediaTek Inc.
Mar 22 02:39:41 kali1981 kernel: [ 8806.298319] usb 4-1: SerialNumber: 000000000
Mar 22 02:39:41 kali1981 systemd[1]: Starting Load/Save RF Kill Switch Status...
Mar 22 02:39:41 kali1981 systemd[1]: Reached target Bluetooth Support.
Mar 22 02:39:41 kali1981 systemd[1243]: Reached target Bluetooth.
Mar 22 02:39:41 kali1981 systemd[1]: Started Load/Save RF Kill Switch Status.
Mar 22 02:39:43 kali1981 dbus-daemon[888]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.60' (uid=0 pid=6004 comm="cockpit-bridge --privileged " label="unconfined")
Mar 22 02:39:43 kali1981 systemd[1]: Starting Time & Date Service...
Mar 22 02:39:43 kali1981 dbus-daemon[888]: [system] Successfully activated service 'org.freedesktop.timedate1'
Mar 22 02:39:43 kali1981 systemd[1]: Started Time & Date Service.
Mar 22 02:39:44 kali1981 kernel: [ 8809.500974] Bluetooth: hci0: Device setup in 3116810 usecs
Mar 22 02:39:46 kali1981 systemd[1]: systemd-rfkill.service: Deactivated successfully.
Mar 22 02:39:56 kali1981 kernel: [ 8821.591869] Bluetooth: hci0: Failed to read MSFT supported features (-110)

```

```

kali@kali1981:~$ uname -a
Linux kali1981 6.5.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Mar 12 10:22:43 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
kali@kali1981:~$ sudo lsusb -tv
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        ID 0e0f:0003 VMware, Inc. Virtual Mouse
    |__ Port 3: Dev 3, If 0, Class=Hub, Driver=hub/7p, 12M
        ID 0e0f:0002 VMware, Inc. Virtual USB Hub
    |__ Port 4: Dev 4, If 0, Class=Hub, Driver=hub/7p, 480M
        ID 0e0f:0002 VMware, Inc. Virtual USB Hub
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub


Mar 22 03:23:18 kali1981 kernel: [  138.081546] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
Mar 22 03:23:18 kali1981 kernel: [  138.107235] usb 4-1: New USB device found, idVendor=0e8d, idProduct=7961, bcdDevice= 1.00
Mar 22 03:23:18 kali1981 kernel: [  138.107242] usb 4-1: New USB device strings: Mfr=6, Product=7, SerialNumber=8
Mar 22 03:23:18 kali1981 kernel: [  138.107246] usb 4-1: Product: Wireless_Device
Mar 22 03:23:18 kali1981 kernel: [  138.107249] usb 4-1: Manufacturer: MediaTek Inc.
Mar 22 03:23:18 kali1981 kernel: [  138.107252] usb 4-1: SerialNumber: 000000000
Mar 22 03:23:18 kali1981 kernel: [  138.198031] Bluetooth: Core ver 2.22
Mar 22 03:23:18 kali1981 kernel: [  138.198088] NET: Registered PF_BLUETOOTH protocol family
Mar 22 03:23:18 kali1981 kernel: [  138.198091] Bluetooth: HCI device and connection manager initialized
Mar 22 03:23:18 kali1981 kernel: [  138.198096] Bluetooth: HCI socket layer initialized
Mar 22 03:23:18 kali1981 kernel: [  138.198099] Bluetooth: L2CAP socket layer initialized
Mar 22 03:23:18 kali1981 kernel: [  138.198106] Bluetooth: SCO socket layer initialized
Mar 22 03:23:19 kali1981 kernel: [  138.302183] cfg80211: Loading compiled-in X.509 certificates for regulatory database
Mar 22 03:23:19 kali1981 kernel: [  138.303144] Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
Mar 22 03:23:19 kali1981 kernel: [  138.315177] usbcore: registered new interface driver btusb
Mar 22 03:23:19 kali1981 systemd[1]: Starting Load/Save RF Kill Switch Status...
Mar 22 03:23:19 kali1981 kernel: [  138.520152] Bluetooth: hci0: urb 00000000f0dc524d failed to resubmit (2)
Mar 22 03:23:19 kali1981 kernel: [  138.520840] Bluetooth: hci0: urb 0000000088c09e73 failed to resubmit (2)
Mar 22 03:23:19 kali1981 kernel: [  138.520869] Bluetooth: hci0: urb 00000000df06f040 failed to resubmit (2)
Mar 22 03:23:22 kali1981 kernel: [  141.479925] Bluetooth: hci0: Device setup in 3086788 usecs
Mar 22 03:23:22 kali1981 kernel: [  141.479935] Bluetooth: hci0: HCI Enhanced Setup Synchronous Connection command is advertised, but not supported.
Mar 22 03:23:24 kali1981 kernel: [  143.507288] Bluetooth: hci0: Opcode 0x0c03 failed: -110
Mar 22 03:23:26 kali1981 kernel: [  145.522782] Bluetooth: hci0: Failed to read MSFT supported features (-110)
Mar 22 03:23:28 kali1981 kernel: [  147.537668] Bluetooth: hci0: AOSP get vendor capabilities (-110)
Mar 22 03:23:46 kali1981 kernel: [  165.676648] usb 4-1: USB disconnect, device number 2
Mar 22 03:23:46 kali1981 kernel: [  165.677537] mt7921u: probe of 4-1:1.3 failed with error -5
Mar 22 03:23:46 kali1981 kernel: [  165.677600] usbcore: registered new interface driver mt7921u
Mar 22 03:23:46 kali1981 systemd[1]: Reached target Bluetooth Support.
Mar 22 03:23:46 kali1981 systemd[1]: Started Load/Save RF Kill Switch Status.
Mar 22 03:23:46 kali1981 systemd[2325]: Reached target Bluetooth.
Mar 22 03:23:46 kali1981 systemd[2325]: Stopped target Bluetooth.
Mar 22 03:23:46 kali1981 systemd[1]: Stopped target Bluetooth Support.
Mar 22 03:23:51 kali1981 systemd[1]: systemd-rfkill.service: Deactivated successfully.

```

---

### Post by DuckHook on 2024-03-22
The key log entry is: ```
mt7921u: probe of 4-1:1.3 failed with error -5
```

Websearches returned a number of possible problems:

[LIST]
[*]Are you dual booting this machine with Windows? If so, Windows seems to be one cause of problems, although yours may be a different issue: [https://askubuntu.com/questions/1382918/wireless-adapter-mediatek-mt7921-is-not-working-after-a-reboot-in-ubuntu-21-10](https://askubuntu.com/questions/1382918/wireless-adapter-mediatek-mt7921-is-not-working-after-a-reboot-in-ubuntu-21-10)
[*]Another possibility is a firmware regression: [https://bbs.archlinux.org/viewtopic.php?id=291391](https://bbs.archlinux.org/viewtopic.php?id=291391)
[*]Then there are reports of a workaround — powering off the computer completely instead of just rebooting: [https://github.com/openwrt/mt76/issues/548](https://github.com/openwrt/mt76/issues/548)
[*]
[/LIST]
Overall, I must say that this WIFI unit appears to be problematic for Ubuntu. Do you have another that you can use? Also, as a practical matter, if you experience no problems with other distros, why use Ubuntu? Is there an overriding reason that you must use Ubuntu?

---

### Post by MAFoElffen on 2024-03-22
Install the HWE stack first... Mine on 22.04.4
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsb_release -d
Description:    Ubuntu 22.04.4 LTS
mafoelffen@Mikes-ThinkPad-T520:~$ uname -r
6.5.0-25-generic

```
My questions are,:

what is the host OS that you are running VMware Workstation 17.0.0 on?

How are you passing the USB WiFi Network Adapter to the VM?

Why are you doing a hardware pass-through of a USB WiFi adapter to a VM in the first place? Usually you setup the network connections to the Host, and just use those connections, through the Virt-Switches of the VM Hosting software, to use as a wired connection in the VM... Are you just looking for a challenge to see if you can make it work? Just seems like you are making things harder than they need to be (normally).

Not saying it can't be done. It can. But it all depends what your end-goal really is. There may be an easier way to get there. Does that make sense?

Just curious...

---

### Post by MAFoElffen on 2024-03-23
Also... While that is passed through, post the results of
```

sudo lsusb -vvv

```

---

### Post by hiloves on 2024-03-25
I solved this problem.


This seems to be caused by the CF-953AX adapter not shielding the Bluetooth function on the mt7921u chip very well.


Ubuntu tried to install the Bluetooth driver for the CF-953AX adapter but an error occurred.So, Ubuntu ejected it.


I disable bluetooth driver loading for ubuntu.


```

sudo nano /etc/modprobe.d/blacklist.conf


blacklist btusb

```


This thread should not be placed under "virtualization" because it is not a virtualization issue.

---

