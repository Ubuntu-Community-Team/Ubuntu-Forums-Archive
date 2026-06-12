---
title: "Pangolin doesn't recognize microSD plus adapter"
date: 2009-08-24
forum: System76 Support
---

### Post by marshmallow1304 on 2009-08-24
Just picked up an 8 GB microSD card for my phone.  It came with one of those adapters that is the same size/shape as the regular SD card.  I know the card itself is fine because it works in the phone, and I know the Pangolin's card reader is fine because it works with a regular SD card I have.

Ubuntu doesn't seem to want to mount it, acknowledge it, or do anything useful with it.


Edit: Just tried it with my printer, which also has an SD card slot.  It gives "Card access error."  This makes me think it's an issue with the adapter.

---

### Post by lswb on 2009-08-24
Have you checked the card and adapter together in another system to make sure it is not the adaptor causing the trouble?

---

### Post by marshmallow1304 on 2009-08-24
> **lswb said:**
> Have you checked the card and adapter together in another system to make sure it is not the adaptor causing the trouble?

No. Only the printer.  I unfortunately don't have another system with an SD reader.

---

### Post by thomasaaron on 2009-08-25
It also might be a problem with how the phone has formatted the card. That could be why neither Ubuntu or your printer like it.

Try opening a terminal and running...

tail -f /var/log/syslog

Then insert your card. See what messages pop up. I'm betting there will be something indicating an un-supported filesystem.

---

### Post by marshmallow1304 on 2009-08-25
```
benn@system76-pc:~$ tail -f /var/log/syslog
[bunch of stuff about wireless beacon loss]
Aug 25 11:44:29 system76-pc kernel: [ 1872.883288] mmc0: error -84 whilst initialising SD card
```

It works OK when I put it in the phone and connect via data cable or bluetooth, so this isn't a huge deal.

---

### Post by thomasaaron on 2009-08-25
OK, so it *sees* the card. It just can't initialize it. Since we know your card works, the problem most likely is either the filesystem or the formatting provided by the phone.

And you don't want to try to reformat the card so that it works with Ubuntu. That will most likely cause it to cease working with the phone.

---

