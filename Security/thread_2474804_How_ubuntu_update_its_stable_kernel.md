---
title: "How ubuntu update its stable kernel?"
date: 2022-05-08
forum: Security
---

### Post by davesun1991 on 2022-05-08
I found there's difference between ubuntu latest kernel version and upstream kernel version(from kernel.org stable version), I know ubuntu would apply security update soon after CVE be public, but there are lots of stable commit which is relevant to small bug fix not security issue and do not have CVE number.

I wonder know what strategy ubuntu has to apply those non-CVE stable kernel commit to ubuntu kernel? Does any official docs talking about it?

---

### Post by deadflowr on 2022-05-08
See: [https://wiki.ubuntu.com/Kernel/StableReleaseCadence]("https://wiki.ubuntu.com/Kernel/StableReleaseCadence")

---

### Post by davesun1991 on 2022-05-08
Have got information I want to know from that wiki page, thanks a lot! : )

---

### Post by davesun1991 on 2022-05-08
Learning from that wiki page, Ubuntu generally divided security (CVE) patch into critical CVE and non-critical CVE. But as I know, the CVSSv3 score of most Linux Kernel CVEs lead to Local Privilege Escalation is 7.8 (High) which is non-critical CVE. Will those Non-embargoed High Priority CVEs (Linux LPE Vulnerability) be [COLOR=#333333][FONT=&quot]handled the same as Non-embargoed Critical CVEs or will be handled on a case-by-case basis?[/FONT][/COLOR]

---

