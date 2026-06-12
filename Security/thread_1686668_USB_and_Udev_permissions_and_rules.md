---
title: "USB and Udev permissions and rules"
date: 2011-02-12
forum: Security
---

### Post by linuxonbute on 2011-02-12
Not sure if this is the correct forum to post this to but here goes.
I have been trying to use my DS2490 USB to serial device with a Maxim 
DG1921G thermocron with owfs. It is supposed to give me access to a virtual file system for the thermocrom without needing to launch owfs as root.

```
/var/log/messages gives:
Feb  8 16:22:45 norman-HP-G56-Notebook-PC kernel: [  236.140141] usb 5-1: new full speed USB device using ohci_hcd and address 2
Feb  8 16:22:45 norman-HP-G56-Notebook-PC kernel: [  236.384467] Driver for 1-wire Dallas network protocol.
Feb  8 16:22:45 norman-HP-G56-Notebook-PC kernel: [  236.399624] usbcore: registered new interface driver DS9490R
Feb  8 16:22:47 norman-HP-G56-Notebook-PC kernel: [  237.945655] w1_master_driver w1 bus master: Family 81 for 81.0000002b58fc.ea is not registered.
Feb  8 16:22:48 norman-HP-G56-Notebook-PC kernel: [  239.497947] w1_master_driver w1 bus master: Family 21 for 21.00000022fbb5.9f is not registered.

when it is plugged in.

running:
 /opt/owfs/bin/owfs -C -u -m /home/norman/1-wire --foreground
--error_level=9 2>ow.log
with the ds2490 module loaded or not gives the following:

norman@norman-laptop:~$ cat ow.log
CONNECT: owfs.c:main(123) fuse mount point: /home/norman/1-wire
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(75) Avahi support:
libavahi-client loaded successfully
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(77) Avahi library function
found: avahi_client_errno
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(7) Avahi library function
found: avahi_client_free
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(79) Avahi library function
found: avahi_client_new
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(80) Avahi library function
found: avahi_client_get_domain_name
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(81) Avahi library function
found: avahi_entry_group_add_service
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(82) Avahi library function
found: avahi_entry_group_commit
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(83) Avahi library function
found: avahi_entry_group_is_empty
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(84) Avahi library function
found: avahi_entry_group_new
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(85) Avahi library function
found: avahi_entry_group_reset
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(87) Avahi library function
found: avahi_service_resolver_free
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(8) Avahi library function
found: avahi_service_resolver_new
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(89) Avahi library function
found: avahi_service_browser_free
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(90) Avahi library function
found: avahi_service_browser_new
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(102) Avahi support:
libavahi-common loaded successfully.
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(104) Avahi library function
found: avahi_simple_poll_free
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(105) Avahi library function
found: avahi_simple_poll_get
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(106) Avahi library function
found: avahi_simple_poll_loop
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(107) Avahi library function
found: avahi_simple_poll_new
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(10 Avahi library function
found: avahi_simple_poll_quit
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(109) Avahi library function
found: avahi_strerror
   CALL: ow_parsename.c:FS_ParsedName_anywhere(91) path=[]
  DEBUG: owlib.c:SetupTemperatureLimits(79) Globals temp limits 0C 100C (for
simulated adapters)
CONNECT: ow_usb_cycle.c:USB_next(6) Bus master found: 3:2
CONNECT: ow_usb_msg.c DS9490_open(269) Failed to set configuration on USB
DS9490 bus master at 3:2.
  DEBUG: ow_usb_msg.c DS9490_open(290) Did not successfully open DS9490 3:2
DEFAULT: owlib.c:SetupSingleInboundConnection(196) Cannot open USB bus
master
DEFAULT: owlib.c:LibStart(54) No valid 1-wire buses found
  DEBUG: owfs.c ow_exit(31) owfs: ow_exit(1)
```

but if ds2490 module is loaded it works when run sudo
It seems from this that it is a lack of permissions to USB but I have tried all the methods on at [http://owfs.org/index.php?page=udev](http://owfs.org/index.php?page=udev) etc. to overcome this and a few others but none work.
I am running Ubuntu 10.10 kernel 2.6.35-22-generic #33-Ubuntu SMP

Any suggestions as to what I can try?

Thanks,
Norman

---

### Post by linuxonbute on 2011-02-13
It seems it was simply the case that my udev rule needed to be different to the various suggested ones I have seen - which may be due to more changes in udev - and also it's name needed to start with a higher number than suggested.

In case anyone is interested this is what I ended up with:

cat /etc/udev/rules.d/90-ds2490.rules

SYSFS{idVendor}=="04fa", SYSFS{idProduct}=="2490", GROUP="ow", MODE="0664"

---

