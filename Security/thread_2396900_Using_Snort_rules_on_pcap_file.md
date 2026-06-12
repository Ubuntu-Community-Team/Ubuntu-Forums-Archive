---
title: "Using Snort rules on pcap file"
date: 2018-07-22
forum: Security
---

### Post by at2657 on 2018-07-22
I am using Snort for the first time and I am quite stuck with using my Snort local.rules on a pcap file I have downloaded. 
  I've created the below rule to bring up a message for all TCP traffic:
  > alert tcp any any -> 80 (msg:"Web traffic"; content: "login"; sid:100)
  I also have the below rule to show basically any IP packet:
  > alert ip any any -> any any (msg: "IP Packet detected")
  However, when I run Snort against my pcap file by typing:
  > snort -r attack-trace.pcap 
  I don't get a single alert message on there. The image below shows what I can see:

[https://imgur.com/a/cbmRZXX](https://imgur.com/a/cbmRZXX)
[[IMG]https://imgur.com/a/cbmRZXX[/IMG]]("https://i.stack.imgur.com/F4fw8.png")

  Can anybody see where I am going wrong?


  Thanks all!

---

