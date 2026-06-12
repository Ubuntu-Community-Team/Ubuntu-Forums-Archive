---
title: "Honeypot logs help"
date: 2009-01-19
forum: Security
---

### Post by sherylkayzb on 2009-01-19
I have 2 logs generated and Im not sure If its really a real attack.



Log 1:(aaa.aaaa = site in the web)
[12/27/07 info as hticj] url::anyurl: "http://aaa.aaaa.org/streams"

---

### Post by pdtpatrick on 2009-01-19
Just curious which application did u use for the honeypot? honeyd or tinyhoney or nepenthes or labrea?? I'm sure there are more but those are common ones that could be installed from repo

---

### Post by sherylkayzb on 2009-01-19
Log 1 : honeyd

---

### Post by Kinstonian on 2009-01-20
Is this a homework question?  I ask because the dates are from 12/27/07.  Anyway I believe those are all low interaction honeypots so technically the honeypot will just log attacks, it won't actually be compromised.

The logs are pretty detailed.  In the first log you can tell that someone connected to the honeypot and then the honeypot tried to parse the data it received in order to look for signs of it being an attack.  If an attack string had been found and tried to get the honeypot to download malware, it would have downloaded the malware and then scanned it with ClamAV.  It wouldn't have executed the malware like what would normally happen in a successful attack.

Apparently the "attack string" that was parsed was saved to the following directory:

[12/27/07] 5031 SaveFile - Attack string saved as attacks/from_port_80-tcp_5031_2007-12-27.

---

### Post by sherylkayzb on 2009-01-21
Actually its not a homework, they forgot 1 machine to audit and there it was 2 years old log. thank you for explaining log 1. I hope you have some idea in log 2 and 4, i already figured log 3.
High interaction honeypots are those that can be compromised? I hope you can share more of your thoughts. 
Were can I study or know more about honeypots including understanding logs. I go to some links but they only feature honeypots and how they do not understanding log files.

thank you so much

---

### Post by sherylkayzb on 2009-02-17
please help me with the remaining 2 logs

---

### Post by sherylkayzb on 2009-02-24
Hi everyone....

Please help me interpreting this logs


Log 1  aaa.aaaa = site in the web)
[12/27/07 info cv sdf] url::anyurl: "http://aaa.aaaa.org/sss"

---

