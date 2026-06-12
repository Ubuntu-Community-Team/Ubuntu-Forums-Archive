---
title: "1104x64::USB scanner over network"
date: 2011-05-04
forum: Server Platforms
---

### Post by xerman on 2011-05-04
Hello there,

In the last days I've been reconfiguring every machine on the network setting up a server, and pluggin all common in-out devices to that server so every desktop could share resources.

I have an old USB scanner, AGFA Snapscan 1212U, plugged to the server.

I tried to set up the server so every desktop could use the scanner and followed what is stated in here:
[https://help.ubuntu.com/community/ScanningHowTo]("https://help.ubuntu.com/community/ScanningHowTo")
and here:
[http://penguin-breeder.org/sane/saned/]("http://penguin-breeder.org/sane/saned/")

With no success. 

The scanner can be used on the server directly. So can use the server to scan any document, but desktops don't detect the scanner even after setting the config files.

**scanimage -L** gives the following result on the server:
```
device `snapscan:libusb:002:002' is a AGFA SNAPSCAN 1212U flatbed scanner
```

**scanimage -L** gives the following result on the desktop:
```
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

**sane-find-scanner** gives the following on the server
```
found USB scanner (vendor=0x06bd [AGFA], product=0x0001 [SNAPSCAN 1212U]) at libusb:002:002
```

**sane-find-scanner** gives the following on the desktop:
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```
it does not matter running sane-find-scanner as root or not, no scanners found on the desktop.

So from desktops there is no way to see the scanner on the server, so no way to scan.

Funny is that from desktop can telnet the scanner. Scanner listens to port 6566 so i get same result from Server and from Desktop:
```
telnet 192.168.0.1 6566
Trying 192.168.0.1...
Connected to 192.168.0.1.
Escape character is '^]'.

```

Also it does not matter having xinetd installed or not. Scanner does not appear listed. Always get Xsane saying "no devices found".

Any help would be appreciated.
Thanks and regards,
Xermán


I have been researching for more than 3 weeks with no result and then finally got the answer today, after posting this thread. Just set "RunAsUser=" to "root" instead of "saned" in /etc/default/saned and it works from any desktop on the network. No need for inetd/xinetd as stated in the UbuntuScanningHowto.

Hope it helps

---

