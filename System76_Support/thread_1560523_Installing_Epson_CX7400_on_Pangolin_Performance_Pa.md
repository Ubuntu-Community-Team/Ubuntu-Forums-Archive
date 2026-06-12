---
title: "Installing Epson CX7400 on Pangolin Performance PanP7"
date: 2010-08-25
forum: System76 Support
---

### Post by fusionex on 2010-08-25
I hope this might help someone. Otherwise, this isn't a bad place for my own possible future reference. I'm using Ubuntu 10.04 Lucid Lynx.

I installed the XSane Image Scanner from Applications->Ubuntu Software Center.

I ran the following from a terminal:

```
sudo apt-get install sane sane-utils xsane libsane-extras
```

I ran the following to obtain my scanner information: ```
sudo sane-find-scanner
```

Here's what sane-find-scanner outputted:

```


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0838) at libusb:002:010
found USB scanner (vendor=0x147e [TouchStrip        ], product=0x1000 [Fingerprint Sensor   ]) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

I read /etc/sane.d/epson.conf and /etc/sane.d/epson2.conf so that I could modify them appropriately. Since my Epson CX7400 is connected through usb, I followed the info from sane-find-scanner where it shows vendor=0x04b8 and product=0x0838. I get the following for each of the files:

```
# epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
scsi EPSON
# for the GT-6500:
scsi "EPSON SC"
#
# Parallel port scanner:
#pio 0x278
#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend. 
usb 0x04b8 0x0838
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0
```

```
# epson2.conf
#
# here are some examples for how to configure the EPSON2 backend

# SCSI
scsi EPSON
# for the GT-6500:
#scsi "EPSON SC"

# Parallel port
#pio 0x278
#pio 0x378
#pio 0x3BC

# USB
usb 0x04b8 0x0838

# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110

# Network
# 
# net 192.168.1.123
net autodiscovery
```

The main modification for both epson.conf and epson2.conf was to change the line that read

```
usb
```

to 

```
usb 0x04b8 0x0838
```

At that point, I was able to run Xsane Image Scanner and it detected my scanner.

This post and its links to other posts were very useful: [http://ubuntuforums.org/showthread.php?t=734591](http://ubuntuforums.org/showthread.php?t=734591).

---

