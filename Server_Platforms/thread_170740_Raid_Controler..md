---
title: "Raid Controler."
date: 2006-05-05
forum: Server Platforms
---

### Post by jdevora on 2006-05-05
Hi,

I have a 3rd party Server that has a 6300ESB SATA RAID Controller (id 8086:25b0).

Im wondering what kind of support the server version has for it...

If I configure one logical drive as RAID 1 on the controler's setup and I try to install ubuntu server 6.06 beta I see 2 disk (instead the logical volumen that I created) in the "create partitions" step.

 If I create the partitions in one disk. will they be mirrored to the other disk by the controler?

 If not, were can I find some documentation for use the RAID capabilities of that controler?

 Cheers
  JD

---

### Post by jdevora on 2006-05-06
I answer myself ;-)

I came acrosss the page [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

There explains that this   [RAID controler ]("http://linuxmafia.com/faq/Hardware/sata.html#intel-ich5")   is a ["fakeraid"]("http://linuxmafia.com/faq/Hardware/sata.html#fakeraid")  that means that it is a normal controler with a Software RAID implemented in the controler's BIOS.

In that case, they advaice to use the Linux software RAID controler because they say it is quicker and more reliable

---

