---
title: "how good are zif to ide converters?"
date: 2011-03-15
forum: The Cafe
---

### Post by nerdy_kid on 2011-03-15
I have a friend of mine who bought a 25GB zif SSD and a zif to ide converter.  The chip refuses to turn on, even with the ssd and a brand new ZIF cable connected.  Before I have him buy a new converter, I'm just wondering -- how good are these chips in general?  [http://cgi.ebay.com/1-8Inch-TOSHIBA-Hard-Drive-ZIF-2-5-43pin-IDE-Adapter-/330541389052?pt=LH_DefaultDomain_0&hash=item4cf5cd54fc#ht_3205wt_932](http://cgi.ebay.com/1-8Inch-TOSHIBA-Hard-Drive-ZIF-2-5-43pin-IDE-Adapter-/330541389052?pt=LH_DefaultDomain_0&hash=item4cf5cd54fc#ht_3205wt_932)

---

### Post by mips on 2011-03-15
What do you mean the chip refuses to turn on. A converter like that has no logic circuitry for the actual signal path. Only circuitry is usually for power protection.

Do you guys have the orientations correct? It's pretty easy to plug things in the wrong way round on those 2.5" drives, I've done it a few times with my 2.5" to 3.5" adapter.

Looking that adapter from the top with the 2.5" connector in view Pin#1 is on the far left and the power pins 41-44 are on the far right by the LEDs. On a 2.5" ribbon cable Pin#1 is red.
Also make sure you match up pin#1 on the ZIFF socket to Pin#1 on the SSD.

Also try removing that jumper.

---

### Post by nerdy_kid on 2011-03-15
> **mips said:**
> What do you mean the chip refuses to turn on. A converter like that has no logic circuitry for the actual signal path. Only circuitry is usually for power protection.

Do you guys have the orientations correct? It's pretty easy to plug things in the wrong way round on those 2.5" drives, I've done it a few times with my 2.5" to 3.5" adapter.

Looking that adapter from the top with the 2.5" connector in view Pin#1 is on the far left and the power pins 41-44 are on the far right by the LEDs. On a 2.5" ribbon cable Pin#1 is red.
Also make sure you match up pin#1 on the ZIFF socket to Pin#1 on the SSD.

Also try removing that jumper.

The pins are lined up, and the ZIF cable is intact and everything.  But still the green power LED won't even flicker.  No sign of activity at all.  I have the ZIF to IDE converted plugged into a IDE to usb converter, which I know works, and works well at that.  syslog shows 
```


Mar 15 09:25:04 jesse-laptop kernel: [53500.381229] usb 2-1: new high speed USB device using ehci_hcd and address 11
Mar 15 09:25:04 jesse-laptop kernel: [53500.517814] scsi13 : usb-storage 2-1:1.0
Mar 15 09:25:05 jesse-laptop kernel: [53501.517350] scsi 13:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
Mar 15 09:25:05 jesse-laptop kernel: [53501.518911] sd 13:0:0:0: Attached scsi generic sg2 type 0
Mar 15 09:25:05 jesse-laptop kernel: [53501.527559] sd 13:0:0:0: [sdb] Attached SCSI disk

```
when I plug the ZIF to IDE converter in, even if the actual SSD is not there.  sudo cat /dev/sdb returns nothing.  I'm going to take a microscope to the connector pins.

---

### Post by nerdy_kid on 2011-03-15
the pins all look fine.

---

