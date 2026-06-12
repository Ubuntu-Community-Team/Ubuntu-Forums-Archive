---
title: "Cannot add a local USB Zebra printer"
date: 2011-12-14
forum: System76 Support
---

### Post by doubledown11 on 2011-12-14
Running Ubuntu 11.10 with Gnome-Shell, trying to setup a Zebra 2844 label printer.

CUPS Admin tool (the browser-based one) does not see it (expect it to appear as a local printer).

Standard Printer Setup tool under System Settings reports "FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall."

The system-config-printer utility doesn't see it either.

lsusb reports the device is connected "Bus 007 Device 007: ID 0a5f:0009 Zebra LP2844 Printer"

The printer is tested and working good on a Windows box.

Any suggestions on how to complete this setup?

---

### Post by isantop on 2011-12-14
Can you take a screen shot of the Printer setup dialog from System Settings? It sounds like it thinks your printer is a network printer instead of a local one.

---

### Post by doubledown11 on 2011-12-14
Here are screens from the System Setting > Printers utility as well as from the "Find New Printers" in the CUPS tool.  Seems like I should be able to add this by its URI but I can't figure out what that is.  Others have claimed that I should be able to connect to it at:

```
usb://Zebra%20/TLP2844
```

... but I get the following from system-config-printer when I try that:

```
No ID match for device usb://Zebra%20/TLP2844
```

---

### Post by isantop on 2011-12-15
You might try:
[code]usb://Zebra/TLP2844[/usb]

Also, would it be possible to try this from Unity? I'm only familiar with Ubuntu's Printer config tool, and it looks like Gnome Shell uses a different one. Just log in to Unity, Then click on the device menu (In the far upper right corner) and then click printers.

---

### Post by doubledown11 on 2011-12-15
> **isantop said:**
> You might try:
[code]usb://Zebra/TLP2844[/usb][/QUUOTE]

Good idea... tried both /Zebra%20/ and /Zebra/ to no avail.

[QUOTE]Also, would it be possible to try this from Unity? I'm only familiar with Ubuntu's Printer config tool, and it looks like Gnome Shell uses a different one. Just log in to Unity, Then click on the device menu (In the far upper right corner) and then click printers.

Fresh screenshot attached from Unity.

---

### Post by isantop on 2011-12-15
can you send me the output of this command:
```
ls /dev | grep usb
```

This will help me find the proper URI.

---

### Post by doubledown11 on 2011-12-15
> **isantop said:**
> can you send me the output of this command:
```
ls /dev | grep usb
```

This will help me find the proper URI.

Here are the results:

```
tj@tj-Gazelle-Ultra:~$ ls /dev | grep usb
usb
usbmon0
usbmon1
usbmon2
usbmon3
usbmon4
usbmon5
usbmon6
usbmon7
usbmon8
vboxusb

```

I tried each of these as the prefix for the URI with no luck (i.e. usbmon0://Zebra%20/TLP2844).

Also ran lpinfo -v and got the following.  Not sure why USB is not showing up here.

```
tj@tj-Gazelle-Ultra:~$ lpinfo -v
network socket
file cups-pdf:/
network ipp
network smb
network lpd
network http
network beh
direct hpfax
direct hp
```

---

