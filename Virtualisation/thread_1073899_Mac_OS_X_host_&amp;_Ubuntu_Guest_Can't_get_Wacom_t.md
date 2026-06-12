---
title: "Mac OS X host &amp; Ubuntu Guest: Can't get Wacom tablet to work"
date: 2009-02-18
forum: Virtualisation
---

### Post by Ryupower on 2009-02-18
Hi
I've searched numerous pages in google and yahoo search engines numerous times on this, with no avail. 
I am using Virtualbox ( propriety version ) to run kubuntu on OSX. Now, I have done all the steps in gettig the ubuntu drivers for the wacom to work, including editing xorg.conf. The drivers are also installed on OSX.

Here's the problem: on the external usb devices, the tablet is grayed out. I can't click it to mount it. I applied a filter to get it to work, still won't. So when I use KUBUNTU I can't use the tablet because of this.

Any suggestions?

---

### Post by Favux on 2009-02-18
Hi Ryupower,

Assuming it is not a Virtualbox problem (and we can pretend it is a standard tablet install) then you need to post a few things.

Which external graphics tablet (model)?  From what you're saying it is usb.  Is it a Wacom or another type?  If it is a Wacom tablet how did you install the linuxwacom drivers?  What version of the linuxwacom drivers did you install?  What version of Kubuntu?  You also need to post your xorg.conf.

With that information someone should be able to help you.

If it is a Virtualbox problem, with a hotplug usb device not being recognized, some of this information might still be relevant.

---

### Post by Ryupower on 2009-02-20
> **Favux said:**
> Hi Ryupower,

Assuming it is not a Virtualbox problem (and we can pretend it is a standard tablet install) then you need to post a few things.

Which external graphics tablet (model)?  From what you're saying it is usb.  Is it a Wacom or another type?  If it is a Wacom tablet how did you install the linuxwacom drivers?  What version of the linuxwacom drivers did you install?  What version of Kubuntu?  You also need to post your xorg.conf.

With that information someone should be able to help you.

If it is a Virtualbox problem, with a hotplug usb device not being recognized, some of this information might still be relevant.

-I'm using a Wacom Intuos 3 which is USB. 
-I downloaded with Ubuntu guest's synaptic "wacom-tools" and edited xorg.conf as instructed in the documentation.
-wacom-tools 1:0.8.1.4
xserver-xorg-input-wacom 1:0.8.1.4

- linux headers 2.6.27-12
- Kubuntu 8.10

-xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
#  Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

# Uncomment the following section if you you have a TabletPC that supports touch
# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "touch"
#  Option        "Device"        "/dev/ttyS0"       # SERIAL ONLY
#  Option        "Device"        "/dev/input/wacom" # USB ONLY
#  Option        "Type"          "touch"
#  Option        "ForceDevice"   "ISDV4"            # Serial Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
# EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
  InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
# InputDevice   "touch"   "SendCoreEvents" # Only a few TabletPCs support this type
EndSection

```

---

### Post by Favux on 2009-02-20
Hi Ryupower,

Everything looks ok so it's not clear why it isn't working for you, other than the obvious that you're on Virtualbox.

One thing you could try is updating the linuxwacom drivers and tools to 0.8.1-6 at Loic2's wiki:

[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")

just install the debs he has for you.  You could also post on his associated thread, or neko18's thread.

The only other possibility I see is that for some reason the symlink "wacom" in:
```
  Option        "Device"        "/dev/input/wacom"
```
isn't working for you.  Maybe because of virtual box.  On my tablet pc it doesn't work either.  I have to do a by-path pci input.  Please see appendix 1 here:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

Try using:
```
dmesg | grep [Ww]acom
```
or
```
sudo dmesg | grep [Ww]acom
```

Hopefully some of this is helpful.

---

### Post by Ryupower on 2009-02-20
Updated drivers, still not working. And:

```
dmesg | grep [Ww]acom
```
gives me:
```
[   69.696897] usbcore: registered new interface driver wacom
[   69.709873] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
```

do you mean I should change the "wacom" part in the path in xorg.conf?

---

### Post by Favux on 2009-02-21
Hi Ryupower,

Yes, with that command, after a fresh boot, my output is:
```
[   30.913216] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input11
[   30.957435] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.1/input/input12
[   31.017488] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
```
which goes in my xorg.conf for "stylus" and "eraser" like so:
```
	Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse"
```
and the other path goes in the "touch" section, since I have a tablet pc with touch.  The symlink seems to work with most external tablets.  Did you try the sudo version?  Nothing on it either?

You might also want to consider commenting out all the Wacom sections and the Wacom stuff in ServerLayout and trying again.  After a reboot or restarting X.

---

