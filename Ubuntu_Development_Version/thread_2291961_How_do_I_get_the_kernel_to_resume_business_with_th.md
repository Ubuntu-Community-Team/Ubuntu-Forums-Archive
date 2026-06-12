---
title: "How do I get the kernel to resume business with the Bluetooth card again?"
date: 2015-08-24
forum: Ubuntu Development Version
---

### Post by Smask on 2015-08-24
When the Bluetooth card goes to sleep, the kernel drops any handle it got to the card and it takes minutes for it to reconnect again. There are an old bug report from 2007 that's marked "Won't fix" for some reason. And the mentioned workaround don't work because card share ID with WiFi NIC.

```
Aug 24 07:35:03 lappy2 anacron[14853]: Job `cron.daily' terminated
Aug 24 07:35:03 lappy2 anacron[14853]: Normal exit (1 job run)
Aug 24 08:17:01 lappy2 CRON[16712]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 24 09:17:01 lappy2 CRON[18904]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 24 09:24:30 lappy2 kernel: [340081.138147] Bluetooth: hci0 ACL packet for unknown connection handle 5
Aug 24 09:24:54 lappy2 kernel: [340105.430341] Bluetooth: hci0 ACL packet for unknown connection handle 6
Aug 24 09:26:01 lappy2 kernel: [340172.883775] Bluetooth: hci0 ACL packet for unknown connection handle 7
Aug 24 09:26:17 lappy2 kernel: [340188.283809] Bluetooth: hci0 ACL packet for unknown connection handle 8
Aug 24 09:26:32 lappy2 kernel: [340203.670174] Bluetooth: hci0 ACL packet for unknown connection handle 9
Aug 24 09:26:47 lappy2 kernel: [340218.931445] Bluetooth: hci0 ACL packet for unknown connection handle 10
Aug 24 09:27:03 lappy2 kernel: [340234.367743] Bluetooth: hci0 ACL packet for unknown connection handle 11
Aug 24 09:27:18 lappy2 kernel: [340249.627736] Bluetooth: hci0 ACL packet for unknown connection handle 12
Aug 24 09:27:33 lappy2 kernel: [340264.875245] Bluetooth: hci0 ACL packet for unknown connection handle 1
Aug 24 09:27:49 lappy2 kernel: [340280.417074] hid-generic 0005:046D:B008.0004: unknown main item tag 0x0
Aug 24 09:27:49 lappy2 kernel: [340280.417310] input: Bluetooth Laser Travel Mouse as /devices/pci0000:00/0000:00:13.0/usb4/4-1/4-1.3/4-1.3:1.0/bluetooth/hci0/hci0:2/0005:046D:B008.0004/input/input15
Aug 24 09:27:49 lappy2 kernel: [340280.417717] hid-generic 0005:046D:B008.0004: input,hidraw2: BLUETOOTH HID v3.13 Mouse [Bluetooth Laser Travel Mouse] on 10:08:b1:08:07:f0

```

The computer is a Lenovo laptop with a Realtek Bluetooth/WiFi combo hardcoded to the bios (I've tried to switch NIC to a Intel 7260. It will not pass POST). The machine runs Xenial with devel-proposed enabled.

---

### Post by kansasnoob on 2015-08-24
I've never had any bluetooth in-house to test with but a new version of bluez was recently uploaded:

> bluez (5.33-0ubuntu4) wily; urgency=medium

  * Really have bluez Conflict/Replace bluez-alsa this time.

 -- Mathieu Trudel-Lapierre <mathieu-tl@ubuntu.com>  Sat, 15 Aug 2015 10:07:31 -0400

bluez (5.33-0ubuntu3) wily; urgency=medium

  * debian/control: add Conflicts/Replaces for bluez-alsa, ALSA support was
    dropped in BlueZ 5.

 -- Mathieu Trudel-Lapierre <mathieu-tl@ubuntu.com>  Fri, 14 Aug 2015 10:34:46 -0400

bluez (5.33-0ubuntu2) wily; urgency=medium

  * debian/tests/bluez_response:
    - Stop setting up private D-BUS. An autopkgtest must test what's
      installed, including the real system bus.
    - Stop calling bluetoothd (which hangs in 5.x, as it doesn't fork), and
      just call "service bluetooth start" to actually test our packaged
      startup scripts.
  * debian/tests/control: Drop unused Python 2 and GI dependencies.
  * debian/tests/control: Add "isolation-container", this shouldn't be
    attempted in a schroot.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Fri, 14 Aug 2015 11:10:42 +0200

bluez (5.33-0ubuntu1) wily; urgency=medium

  * New upstream version, drop patch included in the update

 -- Sebastien Bacher <seb128@ubuntu.com>  Wed, 12 Aug 2015 15:26:11 +0200


And Ubuntu GNOME's lead dev put out a call for testing:

[https://lists.launchpad.net/ubuntugnome-qa/msg00807.html](https://lists.launchpad.net/ubuntugnome-qa/msg00807.html)

From looking at this PPA:

[https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/transitions/](https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/transitions/)

I think there are still some pieces regarding bluetooth support left to be uploaded to the Wily repos ???????

I wish I could be more helpful but since I lack the hardware I'm more than a bit clueless :redface:

---

### Post by tista on 2015-08-24
Greetings,

```
systemctl suspend
``` could make any difference with your DE's suspend hook?

Regards.

---

### Post by Smask on 2015-12-29
> **tista said:**
> Greetings,

```
systemctl suspend
``` could make any difference with your DE's suspend hook?

Regards.

Suspending and bringing it back immediately keeps the bluetooth device alive. Suspend and leave the computer for a while makes the bluetooth go Zzzzzz and me shaking the mouse for about 150 seconds for reconnection.

---

