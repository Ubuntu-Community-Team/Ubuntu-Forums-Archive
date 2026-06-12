---
title: "What is the surest way to know if an intruder had attacked my computer?"
date: 2011-08-02
forum: Security
---

### Post by arroy_0209 on 2011-08-02
How does one know if an intruder had secretly accessed one's system? Does system log help? It seems it does but I am yet to figure out how to understand those files. Can anybody please help?   Or are there other ways to confirm that. It may happen that the intruder had accessed some vital information but so far had not done anything malicious. So it is likely to be tricky to decide. What suggestions would you give? I am using Ubuntu 10.04 LTS.

---

### Post by Lars Noodén on 2011-08-02
> **arroy_0209 said:**
> How does one know if an intruder had secretly accessed one's system?

If it's secret, then it's secret. ;)

Begin reading about Intrusion Detection Systems (IDS).  Really they're usually a pain to deploy and monitor.  They are not worth it if you don't actively monitor the results and follow up on discrepancies.  

The system logs can help a bit.  Familiarization with how the logs are supposed to be is a pre-requisite in any case.

---

### Post by bodhi.zazen on 2011-08-02
Intruders can be difficult or impossible to detect and it comes down to your knowledge vs the intruder.

Personally I like tools such as snort and OSSEC.

From there you would need to do what is called penetration testing.

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1)

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2)

---

