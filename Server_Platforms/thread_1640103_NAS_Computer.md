---
title: "NAS Computer"
date: 2010-12-07
forum: Server Platforms
---

### Post by alliance1975 on 2010-12-07
I'm thinking of building a NAS computer for home use that will utilize Free NAS software. I was reading an article that discussed various hardware components. A suggestion for the boot device was to use a Compact Flash. A quote follows:

"The only downside to using a Compact Flash drive is that it doesn't support DMA (without a hardware mod to the flash drive itself), and will therefore adversely affect the performance of the system."

Can someone elaborate on this downside for me? Is the loss of direct memory access on a NAS really that important?

---

### Post by windependence on 2010-12-07
I don't agree. Using something like FreeNAS, the program is so small it loads into RAM anyway and is just as fast as it can be. I have several such boxes and they run on CF cards with no issues at all. The nice thing is you can copy the CF card to another one and have instant config backup, just pop it in and boot it up.
 
-Tim

---

### Post by Fafler on 2010-12-07
CF cards work great for this kind of application. You can get really cheap SATA to CF converters on eBay. Another alternative can be a USB flash drive. It works equally good.

The FreeNAS and similar systems take up very little space and all the system files are easily cached. Don't worry.

---

### Post by dtfinch on 2010-12-07
We have a few servers that boot off sd cards, though not without some worries. My main concern with a flash root (other than newer ssds which have better wear leveling) is logging and anything else that's write-heavy to the same location over and over, so in /etc/fstab I have:```
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log/apt tmpfs defaults,noatime,mode=1777 0 0
```The main downside is that if it crashes you lose the logs from the previous boot.

---

### Post by chrislynch8 on 2010-12-08
We have a NAS box for taking on-site to CLient networks and we run the server from a memory key. I've seen no performance issues.

---

### Post by alliance1975 on 2010-12-08
I thank you all for your replies. I too favor the flash card for the boot device for its simplicity, low power needs, no noise and low heat generation. Thank you dtfinch, I will save your code. My application will consist of two HD in RAID 1 configuration with a CF card linked to the ide connection. Again thank you for your help.

---

