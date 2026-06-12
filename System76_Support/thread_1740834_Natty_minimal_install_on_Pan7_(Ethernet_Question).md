---
title: "Natty minimal install on Pan7 (Ethernet Question)"
date: 2011-04-27
forum: System76 Support
---

### Post by ArielSonique on 2011-04-27
Hi, I want to be able to do a minimal install using the minimal or the alternate CD on my pan7. However, early in the install the minimal and the alternate CD don't recognize the ethernet connection and I have no choice but to abort the installation (because it won't go anywhere without a functioning ethernet). [The bug was reported in launchpad here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/400297?comments=all"). The bug still persists in 10.10. 

If this ethernet detection trouble is still not fixed in the Natty minimal/alternate iso tomorrow, could anyone suggest a way I could integrate the JMicron ethernet driver into the minimal/alternate natty iso? I found the driver for the JMicron MC250 PCI Express Gigabit Ethernet Controller (rev 05) here -> jme-1.0.7.1.tbz2 at [ftp://driver.jmicron.com.tw/Ethernet/Linux/](ftp://driver.jmicron.com.tw/Ethernet/Linux/)	

If I somehow manage to complete this integration, do you think the minimal install would then work? Has anyone had any experiences doing a minimal/command line install on the Pangolin Pan7 system?

---

### Post by ArielSonique on 2011-04-28
I tried out the Natty Minimal 64bit iso and it still doesn't recognize my ethernet while booting. Any ideas on how to integrate the JMicron driver into the minimal iso? Thanks!

---

### Post by ArielSonique on 2011-04-30
Hi, I already [posted in the System76 forum]("http://ubuntuforums.org/showthread.php?t=1740834") about my problems installing a minimal ubuntu system but have not received any input.  Since I am using your guide, I hope you won't mind if I repost my question in your thread. 

My System76 Pangolin has an ethernet card from JMicron: MC250 PCI Express Gigabit Ethernet Controller (rev 05) The driver for this is jme-1.0.7.1.tbz2 at [ftp://driver.jmicron.com.tw/Ethernet/Linux/](ftp://driver.jmicron.com.tw/Ethernet/Linux/)	

This driver is not in the minimal CD so it always chokes on installation and I can't get past the bad archive error. Could anyone please help me make the minimal install recognize my ethernet? Thanks for your time!

---

