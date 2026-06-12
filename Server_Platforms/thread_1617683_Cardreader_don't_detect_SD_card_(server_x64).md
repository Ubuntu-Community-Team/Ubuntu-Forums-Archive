---
title: "Cardreader don't detect SD card (server x64)"
date: 2010-11-09
forum: Server Platforms
---

### Post by Andrew__ on 2010-11-09
I own a ubuntu-server (2.6.35-22-server x64) - a home router / NAS / etc assembled at the mini-itx motherboard with no attached keyboard / display.

The problem is that the system does not detect the occurrence of SD-card in a USB-card reader. Card reader is normally detected and visible in the system.
When I insert SD-card in cardreader, in "dmesg" and, accordingly, "udevadm monitor" does not display any events.
If reboot with connected SD, everything works fine, but, of course, there is no event when removing SD.

On the forum topics if problems arise, it is only with automounting. But it's not. I do not have events from kernel, that he discovered the SD-card.

In the desktop version there is no problem.
I installed the generic kernel; comparing kernels configurations for desktop/server versions, comparing the output "udevadm monitor" at the time when I inserted the SD-card on desktop/server, etc. - useless.

I don't have more ideas. I don't understand something. Probably there is no package. Who can help?

Almost ready to give up, put the desktop version and delete unnecessary.

On desktop versions missing events displayed as follows (the output "udevadm monitor" when inserting SD-card):
```


KERNEL[985153522.094479] change   /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3/block/sdf (block)
KERNEL[985153522.095020] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3/block/sdf/sdf1 (block)
KERNEL[985153522.097269] change   /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3 (scsi)
UDEV  [985153522.139363] change   /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3/block/sdf (block)
UDEV  [985153522.307998] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3/block/sdf/sdf1 (block)
KERNEL[985153522.310726] change   /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3/block/sdf (block)
UDEV  [985153522.310781] change   /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3 (scsi)
UDEV  [985153522.404698] change   /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3/block/sdf (block)



```On the server version, the silence instead of events. Events occur only after the launch sg_map or reattach cardreader.
The problem is not just a cardreader or a card - in ubuntu-desktop everything works fine.

The problem in the settings of the kernel, security, or somewhere else?

Thank you for your help.
And sorry for my English - my text is partially translated by Google.


With best regards,
Andrew.

---

### Post by PapaNerd on 2010-11-10
I wonder if auto-mounting is not enabled in the server edition by design.  One would not expect a server to behave like a desktop.  Perhaps someone on the development crew would know for sure.

As a workaround, try mounting the card from the command line.  Something like: ```
sudo mkdir /mnt/sdb1
sudo mount -t vfat /dev/sdb1 /mnt/sdb1
```

---

### Post by Z.K. on 2010-11-12
> **PapaNerd said:**
> I wonder if auto-mounting is not enabled in the server edition by design.  One would not expect a server to behave like a desktop.  Perhaps someone on the development crew would know for sure.

As a workaround, try mounting the card from the command line.  Something like: ```
sudo mkdir /mnt/sdb1
sudo mount -t vfat /dev/sdb1 /mnt/sdb1
```


Servers tend to be locked down more than a desktop.  The server install does not automatically install auto-mounting, at least not for USB.  I had to install a USB automount package and I don't remember the exact name at the moment. I still have a problem mounting an external USB drive though, but it does work now for flash drives.  The one thing I don't like is if you look in the media folder, there is like 8 different usb folders and I have to go through each one to find my drive.  I am still looking for a solution to this.

---

### Post by Andrew__ on 2010-11-15
> **PapaNerd said:**
> 
As a workaround, try mounting the card from the command line.  Something like: ```
sudo mkdir /mnt/sdb1
sudo mount -t vfat /dev/sdb1 /mnt/sdb1
```

These commands are valid only after the appearance of the device /dev/sdf1.
My problem is that this device is not created when I insert the SD-card. Kernel  does not see any change in status of the device /devices/pci0000:00/0000:00:1 d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3/block/sdf

That's how it looks on the ubuntu-desktop:
KERNEL [985153522.094479] **change** /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3/block/sdf (block)

And only after this event, kernel will be able to create device /dev/sdf1
KERNEL [985153522.095020] **add** /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host4/target4:0:0/4:0:0:3/block/sdf/sdf1 (block)

The problem is not automounting. There is nothing to mount. Device /dev/sdf1 appears only after manual rescan scsi devices with command sg_map or reattach card-reader with inserted SD-card.

---

### Post by Andrew__ on 2010-11-17
Solution:

$ sudo apt-get install udisks

after install run:
$ /usr/lib/udisks/udisks-daemon

And now, when I insert SD-card, udevadm display needed events =)

That's all I needed. Everything else is done via udev-rules.

Thank you for taking the time to my question.

With best regards, Andrew.

---

### Post by jjs on 2011-04-04
I had the same problem while setting up a headless media server and digged into it.

It should be noted, that there is nothing special about the udisks-daemon in this use-case. It simply polls the cardreader device (tries to open e.g. /dev/sdc) and when a card is inserted the kernel generates a udev event for adding /dev/sdc1. (It doesn't do this when no one tries to open /dev/sdc.)

You can try this by hand. Stop udisks-daemon (or even uninstall udisks). Watch out for udev-events with "udevadm --monitor". Insert an SD-Card. Nothing should happen now. Try to open your cardreader-device e.g. "dd if=/dev/sdc count=0" (in polling mode udisks-daemon does nothing more). Now the kernel should generate a udev-event for adding /dev/sdc1.

---

