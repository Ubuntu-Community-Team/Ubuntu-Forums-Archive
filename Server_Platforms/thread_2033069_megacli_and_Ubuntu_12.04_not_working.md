---
title: "megacli and Ubuntu 12.04 not working"
date: 2012-07-25
forum: Server Platforms
---

### Post by naviathan on 2012-07-25
Recently I upgraded my file server to 12.04 from 11.10.  The upgrade went smoothly and I haven't had any issues but one.  The megacli program doesn't see my raid adapter anymore.  The program megasasctl and megaraidsas-status both work, but they really provide very limited functionality compared the megacli.  What am I missing?  Has anyone else had this issues after the upgrade?
Any help is greatly appreciated.

---

### Post by naviathan on 2012-08-14
Nothing?  Nobody has anything on this problem?

---

### Post by fleish on 2012-10-16
I solved this on my system by downloading the latest version of MegaCli from LSI's website, here's the link to what I searched for: [http://www.lsi.com/support/Pages/Download-Results.aspx?keyword=megacli]("http://www.lsi.com/support/Pages/Download-Results.aspx?keyword=megacli")

The actual version I ended up with was: MegaCLI SAS RAID Management Tool  Ver 8.04.52 Aug 29, 2012

And viola:
~/megacli/MegaCLI-8.04.52/MegaCLI_Linux/Linux-64# ./MegaCli64 -adpCount
                                     

Controller Count: 1.

Exit Code: 0x01

---

### Post by naviathan on 2012-10-31
> **fleish said:**
> I solved this on my system by downloading the latest version of MegaCli from LSI's website, here's the link to what I searched for: [http://www.lsi.com/support/Pages/Download-Results.aspx?keyword=megacli]("http://www.lsi.com/support/Pages/Download-Results.aspx?keyword=megacli")

The actual version I ended up with was: MegaCLI SAS RAID Management Tool  Ver 8.04.52 Aug 29, 2012

And viola:
~/megacli/MegaCLI-8.04.52/MegaCLI_Linux/Linux-64# ./MegaCli64 -adpCount
                                     

Controller Count: 1.

Exit Code: 0x01

And we have a winner!  That worked perfectly, thank you!

---

### Post by abiel on 2013-05-05
I am ubu newbee.

> **fleish said:**
> I solved this on my system by downloading the latest version of MegaCli from LSI's website, here's the link to what I searched for: [http://www.lsi.com/support/Pages/Download-Results.aspx?keyword=megacli]("http://www.lsi.com/support/Pages/Download-Results.aspx?keyword=megacli")

The actual version I ended up with was: MegaCLI SAS RAID Management Tool  Ver 8.04.52 Aug 29, 2012

And viola:
~/megacli/MegaCLI-8.04.52/MegaCLI_Linux/Linux-64# ./MegaCli64 -adpCount
                                     

Controller Count: 1.

Exit Code: 0x01

My raid1 LSI controller card is LSI Logic / Symbios Logic SAS2004 PCI-Express Fusion-MPT SAS-2
The LSI controller card works properly, as I can mount and work on raid driven by this card.

Using the above I installed megacli on my Ubuntu 12.04. starting from download the file MegaCLI Patch1 - 8.04.53.zip.
The megacli seems not to see the LSI raid controller:
...~# /opt/MegaRAID/MegaCli/MegaCli64 -AdpCount


Controller Count: 0.

Exit Code: 0x00

How can I make MegaCli64 "seeing" the controller card?

---

