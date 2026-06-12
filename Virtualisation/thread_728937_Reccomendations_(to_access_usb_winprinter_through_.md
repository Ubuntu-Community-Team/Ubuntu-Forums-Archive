---
title: "Reccomendations? (to access usb winprinter through guest os)"
date: 2008-03-19
forum: Virtualisation
---

### Post by stairwayoflight on 2008-03-19
Hi all!

I have a Lexmark 3-in1 printer (x3350) that so far is not playing nice with linux or my wife's macbook.

I would like to, if possible, use an xp professional guest vm to access the usb printer, then share it using samba to our lappies.

I installed qemulator/qemu from synaptic and checked the usb checkbox on the hardware tab, but xp doesn't get my flash drive or the printer.

I have used vmware before but it seemed a little intrusive/hard to pare  out compared to, say, qemu.

Given the above, can anyone reccomend a good strategy here? 

(Also supposedly I need to include an arg in the qemu command to add a usb device with its bus address.

dmesg gives me:
[33421.139476] hiddev96: USB HID v1.00 Device [Lexmark   3300 Series] on usb-0000:00:1f.2-2

but I'm not sure exactly which part I need to pass to qemu.)

---

### Post by ruibernardo on 2008-03-19
Hi stairwayoflight,

if you just installed QEMU (or VirtualBox or VMware) and want to use USB with the guests in Ubuntu, you can't. All of them access host USB devices using /proc/bus/usb/, a (to be?) deprecated mode to access the hardware USB devices and not supported by Ubuntu. Ubuntu uses /dev/usb/. To (re-)activate /proc/bus/usb/ you'll have to do what's in this page: Bug **[#156085 in qemu (Ubuntu)]("https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085/comments/5")**. If you don't do this, no USB joy.

Now QEMU. I don't use qemulator, just qemu, but to enable qemu to access the USB hardware, you have to enable the option "-usb". Fore example:

```
qemu -m 256 disk.img -usb
```With "-usb" on the qemu launch command, you can list the available USB devices to the guest OS accessing the QEMU console with the keys Alt+Ctrl+2 (it's 2, not F2!). On the console type:

```
(qemu) info usb_host
  Device 1.2, speed 480 Mb/s
    Class 00: USB device 1234:5678, USB DISK
```One device. Add it to the guest:

```
(qemu) usb_add host:1234:5678
```Now the USB device is accessible to the guest OS.

To make a device always accessible to the guest without all this, start qemu with:

```
qemu -m 256 disk.img -usb -usbdevice host:1234:5678
```Good luck!

---

### Post by stairwayoflight on 2008-03-21
Thanks for the reply.

Actually I edited the script you mentioned.. but no love. I got the xp guest to recognize the printer on virtualbox, but it couldn't print. But I/O seemed kind of "chunky" to me, like a connection with a poor QoS. Mouse input, gui drawing would freeze for a few minutes, then all poop out at once.

Well, I probably learned not to put an XP vm on a linux machine with only a pentium 3 and 1/4 gig of ram!

Regards,
Timothy

---

### Post by ruibernardo on 2008-03-21
> **stairwayoflight said:**
> I got the xp guest to recognize the printer on virtualbox, but it couldn't print. But I/O seemed kind of "chunky" to me, like a connection with a poor QoS. Mouse input, gui drawing would freeze for a few minutes, then all poop out at once.

Did you start your windows guest machine and select "Install guest additions" from the VirtualBox menu? This improves the performance of the guest and enables seamless integration with the host. It can help.

---

### Post by stairwayoflight on 2008-03-27
> **epimeteo said:**
> Did you start your windows guest machine and select "Install guest additions" from the VirtualBox menu? This improves the performance of the guest and enables seamless integration with the host. It can help.

No, I didn't try it.

Well the dirty deed is done. I have migrated my gutsy fileserverto xp pro, all data (~150g of movies mostly) has been restored. Unfortunately this also revealed xp accessed from ubuntu/samba seems to lack the performance of scp between ubuntu machines (though I just let nautilus copy with a drag'n'drop). Other than that, we now have a printer.

---

