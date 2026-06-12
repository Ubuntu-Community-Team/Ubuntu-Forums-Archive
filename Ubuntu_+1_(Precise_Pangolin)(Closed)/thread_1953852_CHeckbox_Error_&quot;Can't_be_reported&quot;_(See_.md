---
title: "CHeckbox Error: &quot;Can't be reported&quot; (See screenshot)"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-04-07
Checkbox crashes immediately after launch, but apport refuses to report it.
- Full update/upgrade, added Unity Testing PPA and rebooted
- Apport dialog popped immediately after Checkbox one
- See the screenshot:

[ATTACH]215617[/ATTACH]

/me facepalms.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-04-07
Another three: 
[B]
1) Checkbox ghost-icon in the launcher (see screenshot)[/B]
[ATTACH]215618[/ATTACH]

**2) Impossible to get hardware-profile to Friendly/Launchpad**
My motherboard support everything you can think of. FireWire, SmartCards, etc, but I got nothing of those features in use. I.E. The Motherboard wires to all these are not connected to devices. I don't use a CD-ROM, don't have FireWire devices, PCMCIA (really, on a desktop? New to me) etc. So I have to skip those tests in System-Testing. Therefore, by the end of the tests, it refuses to upload to friendly and I can't put a hardware profile on Launchpad. The xml is saved locally but never uploaded.  

**3) How to safely revert from test Unity to default**
Because ppa-purge surely ain't a good idea.
**EDIT:** Actually, it is safe now, as pointed out by mc4man in the post below.

Regards,
Effenberg

---

### Post by mc4man on 2012-04-07
> **effenberg0x0 said:**
> 

**3) How to safely revert from test Unity to default**
Because ppa-purge surely ain't a good idea.

Regards,
Effenberg
ppa-purge worked out ok here, couple of day old install, attached log
(the 'removed' were not relevant to this, auto installed previously when exploring gimp-2.8 build-deps, ect.

---

### Post by effenberg0x0 on 2012-04-07
Thank you mc4man, I thought it would break deps. So 1 down.

Regards,
Effenberg

---

### Post by dino99 on 2012-04-07
yes now apport refuse to report if the package or one of its dependencies is (are) not a genuine ubuntu package (brian murray try to remove the fake reports)

---

### Post by larrypg on 2012-04-07
The ghost icon changed to the real icon at some point in the test and stayed that way.  I am not sure that it actually submitted the report though as it did not ask me for my email address (I was logged into launchpad though at the time).  I am not sure it is actually the correct version as it is showing 5.8 and was expecting 5.10. Sure hope I did not waste time testing the wrong version.

---

