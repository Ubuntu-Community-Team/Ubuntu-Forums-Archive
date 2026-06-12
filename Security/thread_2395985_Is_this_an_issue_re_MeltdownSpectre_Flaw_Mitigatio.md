---
title: "Is this an issue re Meltdown/Spectre Flaw Mitigations?"
date: 2018-07-09
forum: Security
---

### Post by Geoffrey_Arndt on 2018-07-09
Did I miss an update?


grep "" /sys/devices/system/cpu/vulnerabilities/*
/sys/devices/system/cpu/vulnerabilities/meltdown:Mitigation: PTI
/sys/devices/system/cpu/vulnerabilities/spec_store_bypass:_**Vulnerable**_
/sys/devices/system/cpu/vulnerabilities/spectre_v1:Mitigation: __user pointer sanitization
/sys/devices/system/cpu/vulnerabilities/spectre_v2:Mitigation: Full generic retpoline, IBPB (Intel v4)

---

### Post by deadflowr on 2018-07-09
The vuln requires updated microcode which hasn't updated for Ubuntu yet.
Ubuntu bug: [lpbug]1780399[/lpbug]

So no, you did not miss an update.

---

