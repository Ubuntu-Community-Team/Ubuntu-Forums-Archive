---
title: "Upskilling in the security space"
date: 2024-05-23
forum: Security
---

### Post by abasel on 2024-05-23
I am busy using my homelab to do some Cybersecurity training.

I have installed Wazuh and have some machines reporting critical vulnerabilities.

One of them is CVE-2016-1585.

What I am battling with is how one patches these things. The machine in question runs Ubuntu 22.04.4 LTS. I have run the updates using apt-get but that did not help.

Looking at [https://ubuntu.com/security/CVE-2016-1585](https://ubuntu.com/security/CVE-2016-1585) it appears that the patch has not been completed yet.

Do I need to recompile myself to address this or is there something I am missing?

---

### Post by #&amp;thj^% on 2024-05-23
If you have not seen this yet have a look: [https://discourse.ubuntu.com/t/upcoming-apparmor-security-update-for-cve-2016-1585/44268](https://discourse.ubuntu.com/t/upcoming-apparmor-security-update-for-cve-2016-1585/44268)
There is a test going on with "Proposed" on 22.04 20.04, That's the last I heard currently.
It still reads Needed: [https://ubuntu.com/security/CVE-2016-1585](https://ubuntu.com/security/CVE-2016-1585)

---

### Post by abasel on 2024-05-23
Thanks for this.

---

