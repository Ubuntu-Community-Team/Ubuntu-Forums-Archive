---
title: "Who or what is Splago?"
date: 2006-10-03
forum: Server Platforms
---

### Post by alba6- on 2006-10-03
Everytime I login, firestarter logs these outbound tcp packets:

Time:Oct  3 15:08:44 Direction: Unknown In:eth2 Out: Port:55470 Source:206.51.237.8 Destination:192.168.1.12 Length:638 TOS:0x00 Protocol:TCP Service:Unknown
Time:Oct  3 15:08:47 Direction: Unknown In:eth2 Out: Port:42456 Source:72.36.195.180 Destination:192.168.1.12 Length:142 TOS:0x00 Protocol:TCP Service:Unknown

When I browse to 206.51.237.8 I get a login page named "Splago". Anybody know
who or what this is?

How do I find the process that is sending these packets?

---

### Post by dddouglas on 2006-10-03
I am not an expert on this but the IP you mentions shows up on proxy dot org as an onion router, NOC4Hosts listed as ISP. Not sure how to stop it? Maybe you are somehow set up for anonymous web surfing?

---

### Post by alba6- on 2006-10-03
I am indeed running tor; that must be the reason. Thanks for your reply and resolving this.

---

