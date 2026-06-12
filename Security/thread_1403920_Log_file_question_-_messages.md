---
title: "Log file question - messages"
date: 2010-02-10
forum: Security
---

### Post by tiger.woods on 2010-02-10
I'm seeing this repeat a lot in my message log does anyone know how to interpret what's going and a possible fix?

Thanks,

Feb 10 08:07:09 dns1 kernel: [84867.522714] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:ca:73:c8:08:00 SRC=192.168.1.150 DST=255.255.255.255 LEN=139 TOS=0x00 PREC=0x00 TTL=128 ID=2600 PROTO=UDP SPT=17500 DPT=17500 LEN=119 
Feb 10 08:07:09 dns1 kernel: [84867.524406] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:ca:73:c8:08:00 SRC=192.168.1.150 DST=192.168.1.255 LEN=139 TOS=0x00 PREC=0x00 TTL=128 ID=2601 PROTO=UDP SPT=17500 DPT=17500 LEN=119 
Feb 10 08:07:22 dns1 kernel: [84880.353150] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:ca:73:c8:08:00 SRC=192.168.1.150 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=2666 PROTO=UDP SPT=138 DPT=138 LEN=220 
Feb 10 08:07:39 dns1 kernel: [84897.500747] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:ca:73:c8:08:00 SRC=192.168.1.150 DST=255.255.255.255 LEN=139 TOS=0x00 PREC=0x00 TTL=128 ID=2741 PROTO=UDP SPT=17500 DPT=17500 LEN=119 
Feb 10 08:07:39 dns1 kernel: [84897.501561] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:ca:73:c8:08:00 SRC=192.168.1.150 DST=192.168.1.255 LEN=139 TOS=0x00 PREC=0x00 TTL=128 ID=2742 PROTO=UDP SPT=17500 DPT=17500 LEN=119 
Feb 10 08:08:09 dns1 kernel: [84927.476269] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:ca:73:c8:08:00 SRC=192.168.1.150 DST=255.255.255.255 LEN=139 TOS=0x00 PREC=0x00 TTL=128 ID=2878 PROTO=UDP SPT=17500 DPT=17500 LEN=119 
Feb 10 08:08:09 dns1 kernel: [84927.476890] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:ca:73:c8:08:00 SRC=192.168.1.150 DST=192.168.1.255 LEN=139 TOS=0x00 PREC=0x00 TTL=128 ID=2879 PROTO=UDP SPT=17500 DPT=17500 LEN=119 
Feb 10 08:08:39 dns1 kernel: [84957.451823] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:ca:73:c8:08:00 SRC=192.168.1.150 DST=255.255.255.255 LEN=139 TOS=0x00 PREC=0x00 TTL=128 ID=3021 PROTO=UDP SPT=17500 DPT=17500 LEN=119 
Feb 10 08:08:39 dns1 kernel: [84957.452560] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:ca:73:c8:08:00 SRC=192.168.1.150 DST=192.168.1.255 LEN=139 TOS=0x00 PREC=0x00 TTL=128 ID=3022 PROTO=UDP SPT=17500 DPT=17500 LEN=119 
Feb 10 08:09:09 dns1 kernel: [84987.427449] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:ca:73:c8:08:00 SRC=192.168.1.150 DST=255.255.255.255 LEN=139 TOS=0x00 PREC=0x00 TTL=128 ID=3230 PROTO=UDP SPT=17500 DPT=17500 LEN=119

---

### Post by cariboo on 2010-02-11
Who is 192.168.1.150?

---

### Post by unspawn on 2010-02-11
This is UDP broadcast traffic for your subnet (192.168.1.255) and for the "everything else" network (255.255.255.255). No malicious activity is recorded for UDP/17500 (TCP/17500 crazzynet trojan) and about the only link matching logs is [http://forum.pfsense.org/index.php?topic=21760.0](http://forum.pfsense.org/index.php?topic=21760.0).

---

### Post by tiger.woods on 2010-02-11
Thanks for the reply's.

So does that mean that UDP/17500 was being scanned from inside or outside or neither???

This just showed up the day before last so it stuck out like a sore thumb.

Thanks,

---

### Post by Jliax on 2010-03-21
Look at this thread:

[http://ubuntuforums.org/showthread.php?t=544027](http://ubuntuforums.org/showthread.php?t=544027)

I had this problem too, iptables (set by firestarter) was just logging like crazy.

---

### Post by Kinstonian on 2010-03-21
Does 192.168.1.150 use DropBox.com?

> Dropbox [https://www.dropbox.com/](https://www.dropbox.com/) broadcasts on port 17500 every 30 seconds 24 hours per day for unknown reasons. This behavior is documented on their web site, but when we removed Dropbox from a Windows system, the broadcasts stopped.

[http://isc.sans.org/port.html?port=17500](http://isc.sans.org/port.html?port=17500)

---

### Post by Kinstonian on 2010-03-21
> **tiger.woods said:**
> Thanks for the reply's.

So does that mean that UDP/17500 was being scanned from inside or outside or neither???

This just showed up the day before last so it stuck out like a sore thumb.

Thanks,

Neither... it's not a port scan.  You can tell it's internal traffic by the looking at the IP address, and that it's probably a Windows box by looking at the TTL.

---

### Post by Jeruvy on 2010-12-22
Sorry for the late response, but very likely this is Dropbox.  I see similar entries on some of my non-dropbox machines.

This is used to detect LANSync on your network.  If you wish to disable simply go to dropbox select 'preferences' and disable 'Enable LAN sync'.

Cheers.

---

