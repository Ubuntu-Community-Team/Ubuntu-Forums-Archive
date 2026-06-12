---
title: "Ubuntu 9.10 &amp; Linksys WUSB54GC"
date: 2010-01-23
forum: Ubuntu Moblin Remix
---

### Post by Hondo2009 on 2010-01-23
Ubuntu 9.10 & Linksys WUSB54GC
 
I am new to Ubuntu... I have loaded Ubuntu to run from a SanDisk Ultra II SDHC Card (transfer rate of 15mb/sec) and running the OS on a Acer Aspire Netbook (AOD250-1365). It seems to run quite well BUT I am unsure how to get the USB NIC to work.
 
The netbook has a built in NIC (Broadcom) but I use the netbook in my shop, a ways from the router and the signal is weak. My plan to is make the Linksys USB NIC more directional by using a USB extension cord and a reflector behind the NIC. I've read that it will project and collect the routers signal more efficiently.
 
I have NO clue how to do this in Ubuntu. Setting up the Broadcom NIC was simple as I basically selected one of two drivers (included in Ubuntu).
 
Some postings suggest using a script, others say they have not been able to get this NIC working at all. I know my way around a Windows machine but not Ubuntu.
 
Can someone please help me get this working?
 
Thank you in advance for your assistance!!!

---

### Post by qwertysockets on 2010-02-17
Hi,

I don't know if you've gotten this fixed yet, but I successfully installed the drivers for the WUSB54GC v.3 on a 32 bit 9.10 install with updated kernel 2.6.31-19-generic.

Here's what I followed:

1. Go to Ralink's website, and download the 3070 driver zip.

2. Open the README file once you've downloaded the file, follow the instructions (sudo if you make && make install).

3. Add to /etc/rc.local

```
/sbin/insmod module_name i.e. /home/user/drivers/RALINK_PACKAGE_NAME/os/linux/ra***sta.ko
```

4. Reboot

More (better documented) info is here:

[http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044)

---

### Post by AFI420 on 2010-02-26
update to newest kernel and configure the adapter. it will work

---

