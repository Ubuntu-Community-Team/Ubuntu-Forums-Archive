---
title: "Why is VMware Player 3 so slow with Ubuntu 10.04 LTS?"
date: 2011-05-18
forum: Virtualisation
---

### Post by AlexanderDGreat on 2011-05-18
Why is VMware Player 3 so slow with Ubuntu 10.04 LTS?

Here's my simple stats:

Host: Ubuntu 10.04 32bit LTS
Intel E7500 C2D
4gb RAM (running Ubuntu PAE)
3 TB harddisks
Nvidia 9500GT
Linux kernel 2.6.32-25-generic-pae #45-Ubuntu SMP i686 GNU/Linux

Guest: Windows XP 32bit
Running with only 1cpu
512mb Ram
Turned off paging file / swap
Fresh install also uses a lot of computer processing!
Installed Vmware tools

Any ideas guys?

---

### Post by fjgaude on 2011-05-19
In your **BIOS** do you have it handle "virtual"?

---

### Post by slooksterpsv on 2011-05-19
Have you enabled VT-x/Virtualization/Hardware Virtualization or that in your BIOS? If not you need to do that in BIOS.

Now this is just my opinion:

I tried VMWare on Ubuntu about 2-3 weeks ago and installed Windows XP Pro with 1024MB RAM and what not. It ran slower than having XP Pro installed on VirtualBox 4.0.6, same specs.

Have you tried or would be willing to try VirtualBox? It's free, open source, supports USB with the extension installed, shared folders, etc.

Not saying VMWare is bad or that, it's just slow for me, my specs are:

AMD Athlon II X2 M300 (2.0GHz)
4GB DDR2 800 RAM
500 GB HDD
Ubuntu 11.04 64-bit

---

### Post by AlexanderDGreat on 2011-06-04
Hi thanks for the responses, I forgot to answer your queries.

> In your BIOS do you have it handle "virtual"? - Yes, I've tried this.

> Have you tried or would be willing to try VirtualBox? It's free, open source, supports USB with the extension installed, shared folders, etc. - I'm a VirtualBox user before, but my USB modem didn't work there for some strange reason, I need it for a fax server. Plus, I like VMware Player, it's also free. It's cool the fact you can just copy paste any file you like from Host to Guest. :)

I've searched online on how to speed it up:

[http://www.fewt.com/2008/06/performance-tuning-vmware-server-on.html]("http://www.fewt.com/2008/06/performance-tuning-vmware-server-on.html")

[http://communities.vmware.com/thread/146002]("http://communities.vmware.com/thread/146002")

I've seen a big difference so far in performance. :)

---

