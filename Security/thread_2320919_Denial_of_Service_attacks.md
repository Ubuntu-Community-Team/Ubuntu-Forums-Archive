---
title: "Denial of Service attacks"
date: 2016-04-18
forum: Security
---

### Post by mrusliathome on 2016-04-18
Hi

I am having issues with my Ubuntu (regardless which version of ubuntu)

I keep having DDos on my Dell Lalitude D420 laptop.

I am using a Ubuntu live distro on a USB stick. 

Is there a method which I can stop the DDos and ICMP attacks via ufw?

My Ubuntu keeps on crashing and freezing most of the time!

I cannot seems to get any work done on my computer.

---

### Post by QIII on 2016-04-18
What behavior leads you to believe you are being DDoSed?

Have you examined your logs?

---

### Post by mrusliathome on 2016-04-18
How to read the logs with a live USB Distro. When your computer keeps on freezing and crashing most of the time.

---

### Post by ian-weisser on 2016-04-18
QIII's question is important. 'freezing and crashing' could have many possible causes.
How did you eliminate the numerous more common causes, and determine that you are the victim of a DDOS? 

And if it really is a DDOS, why are you letting the offending packets past your router? Why is your ISP not filtering them?

---

### Post by Habitual on 2016-04-19
> **ian-weisser said:**
> And if it really is a DDOS, why are you letting the offending packets past your router?Easy Test 
Disconnect your internet for 5m, 30m, an hour? and see if the anomalous behavior continues.

"freezing and crashing" sounds like low ram, low disk, or Power Supply related anomaly.
and is a poor description of what froze or what crashed.
 
Thank you.

---

### Post by Thirtysixway on 2016-04-23
Can you use tcpdump or wireshark to get a capture of the alleged attack packets?

It'd be interesting to see what types of ICMP requests you're getting, as that's not a typical choice for DDoS attacks... And as others have said, if it's really enough data to swamp your PC, how would it not be overwhelming any upstream device?

---

