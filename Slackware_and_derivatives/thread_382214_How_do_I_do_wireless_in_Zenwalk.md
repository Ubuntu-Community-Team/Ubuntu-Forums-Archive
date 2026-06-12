---
title: "How do I do wireless in Zenwalk?"
date: 2007-03-11
forum: Slackware and derivatives
---

### Post by thomasmallen on 2007-03-11
I installed the latest release of Zenwalk, 4.4.1,  and installed it (clean) on my T41 IBM Thinkpad. lspci detects the card (Atheros AR5212) but I have no idea where to go from here...!

Everything I find out there is vague (find a driver?) and I need a step-by-step way to configure my wireless. I'm very frustrated here, and had the same problem when I got started with Ubuntu (no resources answer the simple question: How does the OS expect me to do this?) until I installed KNetworkManager which got me on my way.

---

### Post by johndudley on 2007-03-17
Hi Thomas

I am not familiar with your chip but your situation may be similar to mine.

I have a Broadcom 4306 chip and successfully installed the firmware and got it working.  Problem was that I couldn't get on with the wifi radar program.  No matter what combination of entries I put in the fields it wouldn't connect and there appears to be little documentation.

In the end I installed network manager.  To do this I had to install quite a bit of Gnome bits and pieces from Zeqadious' server (see the Zenwalk forums).  Obviously I had to hook up with an ethernet cable to do this.

With network manager installed it worked perfectly.

John

---

### Post by ahaslam on 2007-04-25
I hope you've figured it out by now, but incase anyone else is struggling I found this to be a perfect guide for Atheros chipsets: [http://support.zenwalk.org/index.php/topic,5189.0.html](http://support.zenwalk.org/index.php/topic,5189.0.html)

;)

---

