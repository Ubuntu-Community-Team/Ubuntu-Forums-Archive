---
title: "lsusb does not see my printer"
date: 2009-12-03
forum: Server Platforms
---

### Post by supremedalek on 2009-12-03
Stupid/Newbie usb question: I bought a Brother HL-2140 usb laserprinter and am trying to add to my ubuntu 9.10 server. So, the first step is to physically connect it to one of the usb ports and use lsusb to see if the printer is being seen:

```
raub@keg:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
raub@keg:~$
```

As you can see, lsusb does not recognize it no matter which usb port I use. That does confuse me since everything else I connect to this computer's usb ports shows up when I type lsusb. As an example, let me slap a MN510 wireless device to a randomly picked usb port:

```
raub@keg:~$ lsusb 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 006: ID 045e:006e Microsoft Corp. MN510 802.11b Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
raub@keg:~$
```

Interestingly enough, dmesg seems to report a printer there:

```
[45141.016030] usb 5-2: new full speed USB device using uhci_hcd and address 3
[45141.188491] usb 5-2: configuration #1 chosen from 1 choice
[45141.196484] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid
0x04F9 pid 0x0033
```

So, I tried the same printer in my laptop, which runs ubuntu 9.04 desktop, and it sees the printer fine (and even tries to add it):

```
raub@monaco:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 04f9:0033 Brother Industries, Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
raub@monaco:~$ 
```

So, I do not think I can blame the printer itself... or printer drives since all I am trying to do right now is to see the stupid printer as a usb device in the usb chain. Am I missing something here?

---

### Post by kuadra on 2009-12-18
I can confirm the same symptoms here with a Brother DCP-115C printer/scanner on Kubuntu 9.10. On my Kubuntu 9.04 system the device is properly identified by *lsusb*.

Concerning the printer part, I have installed *brother-lpr-drivers-extra* and *brother-cups-wrapper-extra* (they both depend on each other) as suggested [here]("http://ubuntuforums.org/showpost.php?p=8218001&postcount=271"). Nice to see that Ubuntu now ships these drivers themselves.
Interesting to mention is that the printer functionality can be used even if *lsusb* doesn't even find the device.

The scanner part seems to be a bit tricky, and I must admit that I'm still trying to figure out how **udev** and **hal** are used to access these devices. In many old howtos udev is used to set the permissions of a scanner. This method seems to be considered obsolete because it is based on the usual file system permissions. In the past we had an extra group for printers and a scanner group for scanners. But with multifunctional devices this method to determine permissions is not good enough. Not long ago I've read somewhere on Launchpad that now hal is used to handle permissions on such devices. I've recently posted a small howto from the info I've found so far [here]("http://ubuntuforums.org/showpost.php?p=7762427&postcount=2").

But surprisingly such an extra hal policy doesn't work for my DCP-115C in Kubuntu 9.10 any more. Every scanning application (xsane, skanlite, etc.) doesn't find my device, and instead selects my notebook webcan as an input device for scanning.
Looking at the [official Brother support sites]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10"), they instruct you to add another udev rule, but not directly to handle permissions ([as opposed]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9") [to frequent howtos]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#9") [from the past]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#10")).

So I've extended */lib/udev/rules.d/40-libsane.rules* with
```
# Brother DCP-115C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="018c", ENV{libsane_matched}="yes"
```
and then issued
```
# udevadm trigger
```
and voila. The device is now properly found even by lsusb, and what is more interesting for practical reasons, skanlite now also finds this device and gives me the option to use it for scanning.

But I don't understand why this works now, and what surprises me more, the extra hal policy doesn't seem to be needed anymore. Even without it, I can now use the device as a scanner.

I hope this info helps a bit, but AFAICT your device is a printer and not a printer/scanner combination so I'm not sure if telling *libsane* via udev rules to be interested in your device would be the proper way to handle the problem...

---

### Post by narcisgarcia on 2010-03-19
With Ubuntu GNU/Linux 9.10 (Karmic Koala) the **Brother MFC-7320** printer functionality works installing the "brother" packages available in the repositories, rebooting and then selecting the **MFC7220** driver.

But the XSane doesn't detect the scanner, and the "lsusb" command the same: no Brother devices listed.

Adding any of these lines to the file **/lib/udev/rules.d/40-libsane.rules** (only one at the same time):
```

SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01eb", ENV{libsane_matched}="yes"
ATTRS{idVendor}=="04f9", SYSFS{idProduct}=="01eb", ENV{libsane_matched}="yes"
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```
...and after adding the line restart the system, makes "lsusb" to show the USB device:
> 
Bus 002 Device 002: ID 04f9:01eb Brother Industries, Ltd

...but XSane still doesn't detect the scanner.

---

### Post by narcisgarcia on 2010-03-19
Done!
Only inserting these lines in /lib/udev/rules.d/40-libsane.rules
```

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```
And after installing the **brscan3** driver provided in [Brother's site]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html") for this model.

---

