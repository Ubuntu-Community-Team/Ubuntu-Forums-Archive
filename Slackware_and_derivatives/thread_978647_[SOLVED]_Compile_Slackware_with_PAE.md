---
title: "[SOLVED] Compile Slackware with PAE"
date: 2008-11-11
forum: Slackware and derivatives
---

### Post by Vince4Amy on 2008-11-11
I would like to compile the Slackware Kernel to make use of PAE because I have 4GB RAM and I would like to be able to make use of the whole lot. 

I have no idea where to start on compiling the Kernel so how would I compile the Slackware 12.1 Kernel to support PAE?

---

### Post by ilrudie on 2008-11-11
[URL="http://www.slackbook.org/html/system-configuration-kernel.html"]slack book system configuration - kernel
[/URL]

---

### Post by Vince4Amy on 2008-11-11
Well that seems easy. Would I also be able to use the newest Kernel using this method or will that break stuff?

---

### Post by ilrudie on 2008-11-11
You can certainly try using it.  I don't know if it will break anything.

---

### Post by Vince4Amy on 2008-11-12
Okay I'll give it a try, thanks for the link BTW. I've also disabled a lot of stuff when I tried this in a VM and it seems to be running a little faster then it already was.

---

### Post by Vince4Amy on 2008-11-18
Sorted and working on the actual hardware.

[http://www.slackbasics.org/html/kernel.html](http://www.slackbasics.org/html/kernel.html)

Found this as well. 

I disabled cpufreq and then enabled PAE. Took a while to compile but all seems to be running fine now. Just about to install the ATI Drivers hopefully the custom kernel will be fine with them.

---

