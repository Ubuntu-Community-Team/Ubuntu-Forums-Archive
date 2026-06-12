---
title: "tcpdump &amp; mysql"
date: 2010-08-04
forum: Security
---

### Post by sinamorawej on 2010-08-04
Hey all

I have an interesting problem which could be the first case of PC haunting or my stupidity has reached a new level. 

I started to capture mysql communication with joomla on my local machine:

 -- tcpdump -i any -s 0 -vv port 3306

this worked fine and I could see stuff happening. I then started to use wireshark and created a filter which was similar to the above and again, I could see packets. However, after running wireshark for a while everything stopped i.e. no traffic was captured on port 3306. Switching back to shell it's the same result - the only traffic I capture on this port is when I telnet to it which brings back:

localhost.52767 > localhost.mysql: Flags [.], cksum 0xc720 (correct), seq 6, ack 100, win 257, options [nop,nop,TS val 211247 ecr 211247], length 0
17:44:23.145302 IP (tos 0x8, ttl 64, id 59628, offset 0, flags [DF], proto TCP (6), length 52)

localhost.mysql > localhost.52767: Flags [F.], cksum 0xc720 (correct), seq 100, ack 6, win 256, options [nop,nop,TS val 211247 ecr 211247], length 0
17:44:23.145318 IP (tos 0x8, ttl 64, id 59629, offset 0, flags [DF], proto TCP (6), length 52)




Anyone seen this before??

~sina

---

### Post by anomie on 2010-08-06
If telnet testing is captured by tcpdump / wireshark, then the filter is not your problem. 

Is it possible your content is simply being cached server or (more likely in your case) client/browser side? Dump your web browser cache and try again.

---

