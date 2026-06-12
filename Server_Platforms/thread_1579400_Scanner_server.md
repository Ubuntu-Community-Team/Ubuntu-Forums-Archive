---
title: "Scanner server"
date: 2010-09-21
forum: Server Platforms
---

### Post by Paretje on 2010-09-21
I want to scan over the network, but the problems starts already on the sever. The HP all-in-one just works (I can print), is found, except by scanimage:
```
SANE_DEBUG_NET=128 scanimage -L
[sanei_debug] Setting debug level of net to 128.
[net] sane_init: authorize = 0x804d780, version_code = 0xbf9b36cc
[net] sane_init: SANE net backend version 1.0.14 (AF-indep+IPv6) from sane-backends 1.0.20
[net] sane_init: Client has little endian byte order
[net] sane_init: searching for config file
[net] sane_init: done reading config
[net] sane_init: evaluating environment variable SANE_NET_HOSTS
[net] sane_init: evaluating environment variable SANE_NET_TIMEOUT
[net] sane_init: done
[net] sane_get_devices: local_only = 0
[net] sane_get_devices: finished (0 devices)

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
[net] sane_exit: exiting
[net] net_avahi_cleanup: stopping thread
[net] net_avahi_cleanup: done
[net] sane_exit: finished.

```

lsusb:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 2304:0236 Pinnacle Systems, Inc. [hex] 
Bus 001 Device 002: ID 03f0:5c11 Hewlett-Packard PhotoSmart C4200 Printer series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

sane-find-scanner
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x2304, product=0x0236) at libusb:001:003
found USB scanner (vendor=0x03f0, product=0x5c11) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

sudo sane-find-scanner:
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x2304 [LITEON], product=0x0236 [Pinnacle 72e]) at libusb:001:003
found USB scanner (vendor=0x03f0 [HP], product=0x5c11 [Photosmart C4200 series]) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

I've install sane-utils.

---

### Post by Paretje on 2010-09-21
May be deleted, the drivers weren't installed.

---

