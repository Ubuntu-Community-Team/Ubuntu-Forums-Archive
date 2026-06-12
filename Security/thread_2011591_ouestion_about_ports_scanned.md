---
title: "ouestion about ports scanned"
date: 2012-06-27
forum: Security
---

### Post by boregard on 2012-06-27
Hello, I was going through my att 2wire firewall logs and found several instances of blocked inbound connections most originating from places in china. I saw Port Scan Detected in the logs.  when i do a whois search using Network Tools, 58.218.199.227  in particular returns an error,see scree s. below. not too worried about them as they are being blocked. I am new to all this,and curious & trying to learn what is going. Any help understanding this will be greatly appreciated.    Best Regards

---

### Post by cariboo on 2012-06-27
Since finding a bug in gnome-network-tools 3 years ago, I've stopped using it. The bug fix was finally released for 12.04 about 6 weeks ago, but I haven't tried it yet.

I'd suggest using **whois** in a terminal, as you get more information, than from gui based tools.

---

### Post by boregard on 2012-06-27
thanks cariboo907, it worked great using terminal. but why would they be doing a port scan? Regards

---

### Post by CharlesA on 2012-06-27
Bots are doing port scans all around the internet.

If the firewall blocked the scan/access attempt, you are fine.

---

### Post by boregard on 2012-06-28
thanks, to you both that explained what i wanted to know.

---

