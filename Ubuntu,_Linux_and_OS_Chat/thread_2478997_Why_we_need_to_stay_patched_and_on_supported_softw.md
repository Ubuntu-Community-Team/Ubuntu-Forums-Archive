---
title: "Why we need to stay patched and on supported software"
date: 2022-09-11
forum: Ubuntu, Linux and OS Chat
---

### Post by TheFu on 2022-09-11
> Shikitega exploits two critical escalation of privileges vulnerabilities that give full root access. One bug, tracked as CVE-2021-4034 and colloquially known as PwnKit, lurked in the Linux kernel for 12 years until it was discovered early this year. The other vulnerability is tracked as CVE-2021-3493 and came to light in April 2021. While both vulnerabilities have received patches, the fixes may not be widely installed, particularly on IoT devices. 

 > The main dropper is tiny—an executable file of just 376 bytes.
....
The ultimate objective of the malware isn't clear. It drops the XMRig software for mining the Monero cryptocurrency, so stealthy cryptojacking is one possibility. 

[https://arstechnica.com/information-technology/2022/09/new-linux-malware-combines-unusual-stealth-with-a-full-suite-of-capabilities/](https://arstechnica.com/information-technology/2022/09/new-linux-malware-combines-unusual-stealth-with-a-full-suite-of-capabilities/)

Stay patched.
Have a number of versioned backups.
Look for odd behaviors, like high CPU use.  The best way to do this is to have system performance monitoring always enabled. Looking in real-time isn't likely to show the issue, since crypto-mining doesn't appear to be the primary goal.

This attack scales from IoT devices up to huge servers and works on everything inbetween - including our home servers, laptops and desktops.

---

