---
title: "System freeze after 7.04 -&gt; 7.10 update"
date: 2009-01-27
forum: Server Platforms
---

### Post by Tartagus on 2009-01-27
Hi there,

I hope this is the right forum to post in, as I'm having a strange problem. I updated Ubuntu 7.04 to 7.10 using do-release-upgrade. Everything worked fine and there were no error messages. After the upgrade the system wanted to restart.

When the system starts, it stops with "BIOS data check successful". After that nothing happens till I CTRL-ALT-DEL. I searched Google for about 3 hours now and didn't find a solution.

Maybe one of you could give me a hint, in what direction I have to search... If any further information is needed, please let me know!

regards 

Tarta

---

### Post by starling on 2009-01-28
Is this happening before ubuntu starts booting? sounds like a problem with the boot loader.
Look up reinstalling grub to MBR (often done after installing Windows) and see if that helps.

---

### Post by gtdaqua on 2009-01-28
Its a BIOS level problem. Nothing to do with the boot loader. Looks like a self-test is failing. Get your motherboard manual and see if you can get into the bios and find more information.

---

