---
title: "Usb automount problem on ubuntu server"
date: 2011-08-01
forum: Server Platforms
---

### Post by an2110 on 2011-08-01
Hello everybody. I am new to ubuntu. And I have a problem with my Ubuntu Server. When I plug a media card(Compact Flash, Secure digital etc) into usb multicard reader it doesn't automount on /media/usb. I installed usbmount package but it not solved my problem. 
But usb thumb drives automounting is ok. Can anybody help me?

P.S. Sorry for my english. I am from Russia :)

---

### Post by volkswagner on 2011-08-01
Does it mount if you first insert CF card into reader, then attach the USB cord to the server?

Some card readers are better than others.  You may find a different brand reader works for your needs.

Does the card reader automount with the desktop version?

Run in a terminal:

```
tail -f /var/log/messages
```

Then insert the card reader to see the output.

---

### Post by an2110 on 2011-08-02
Thank you for your reply. I have another multicard reader - external usb. And i test it today. So it works - when i insert CF to external card reader its automounts. Here is /var/log/messages after automount CF:

```

Aug  2 17:31:36 Home-Server kernel: [ 7802.140058] usb 1-5: new high speed USB device using ehci_hcd and address 4
Aug  2 17:31:36 Home-Server kernel: [ 7802.299804] scsi6 : usb-storage 1-5:1.0
Aug  2 17:31:37 Home-Server kernel: [ 7803.500579] scsi 6:0:0:0: Direct-Access     Generic                CF 1.6E PQ: 0 ANSI: 0 CCS
Aug  2 17:31:37 Home-Server kernel: [ 7803.501927] scsi 6:0:0:1: Direct-Access     Generic                MS 1.6E PQ: 0 ANSI: 0 CCS
Aug  2 17:31:37 Home-Server kernel: [ 7803.503300] scsi 6:0:0:2: Direct-Access     Generic            MMC/SD 1.6E PQ: 0 ANSI: 0 CCS
Aug  2 17:31:37 Home-Server kernel: [ 7803.504675] scsi 6:0:0:3: Direct-Access     Generic                SM 1.6E PQ: 0 ANSI: 0 CCS
Aug  2 17:31:37 Home-Server kernel: [ 7803.505461] sd 6:0:0:0: Attached scsi generic sg6 type 0
Aug  2 17:31:37 Home-Server kernel: [ 7803.505732] sd 6:0:0:1: Attached scsi generic sg7 type 0
Aug  2 17:31:37 Home-Server kernel: [ 7803.505989] sd 6:0:0:2: Attached scsi generic sg8 type 0
Aug  2 17:31:37 Home-Server kernel: [ 7803.506239] sd 6:0:0:3: Attached scsi generic sg9 type 0
Aug  2 17:31:37 Home-Server kernel: [ 7803.541682] sd 6:0:0:1: [sdg] Attached SCSI removable disk
Aug  2 17:31:37 Home-Server kernel: [ 7803.542568] sd 6:0:0:2: [sdh] Attached SCSI removable disk
Aug  2 17:31:37 Home-Server kernel: [ 7803.543947] sd 6:0:0:3: [sdi] Attached SCSI removable disk
Aug  2 17:31:37 Home-Server kernel: [ 7803.544453] sd 6:0:0:0: [sdf] 1000944 512-byte logical blocks: (512 MB/488 MiB)
Aug  2 17:31:37 Home-Server kernel: [ 7803.545556] sd 6:0:0:0: [sdf] Write Protect is off
Aug  2 17:31:37 Home-Server kernel: [ 7803.550984]  sdf: sdf1
Aug  2 17:31:37 Home-Server kernel: [ 7803.556118] sd 6:0:0:0: [sdf] Attached SCSI removable disk
Aug  2 17:31:37 Home-Server usbmount[4373]: /dev/sdf does not contain a filesystem or disklabel
Aug  2 17:31:38 Home-Server usbmount[4401]: executing command: mount -tvfat -osync,noexec,nodev,noatime,nodiratime /dev/sdf1 /media/usb0
Aug  2 17:31:38 Home-Server usbmount[4401]: executing command: run-parts /etc/usbmount/mount.d
```

But problem with internal cardreader. /var/log/messages when i insert card into internal cardreader:

```
Aug  2 17:40:53 Home-Server kernel: [   29.280034] sis190 0000:00:04.0: eth0: mii ext = 0000
Aug  2 17:40:53 Home-Server kernel: [   29.340016] sis190 0000:00:04.0: eth0: mii lpa=45e1 adv=01e1 exp=0001
Aug  2 17:40:53 Home-Server kernel: [   29.340022] sis190 0000:00:04.0: eth0: link on 100 Mbps Full Duplex mode
Aug  2 17:40:53 Home-Server kernel: [   29.340066] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug  2 17:41:49 Home-Server kernel: [   85.790167] Marking TSC unstable due to cpufreq changes
Aug  2 17:41:49 Home-Server kernel: [   85.790244] Switching to clocksource acpi_pm
Aug  2 17:43:22 Home-Server kernel: [  178.425102] Intel AES-NI instructions are not detected.
Aug  2 17:43:22 Home-Server kernel: [  178.445517] padlock: VIA PadLock not detected.
Aug  2 17:43:40 Home-Server sudo: pam_sm_authenticate: Called
Aug  2 17:43:40 Home-Server sudo: pam_sm_authenticate: username = [andrey]
Aug  2 17:43:40 Home-Server sudo: pam_sm_authenticate: /home/andrey is already mounted
```

As I can see from log, kernel cant figure out what card is inserted into internal cardreader. Simpliest  way to fix this situation is to use other cardreader. But its internal and I cant replace it with another. May be there is the way to tune software instead of changing hardware parts?

---

