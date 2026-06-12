---
title: "Live boot media security problem due to missing updates?"
date: 2009-09-22
forum: Security
---

### Post by Peter Frank on 2009-09-22
LiveCD / USB are typically kept for months without getting the latest security patches. They are difficult to update anyway. Does this represent a security risk?

On the more optimistic side, each liveCD session is at most a few hours. The chance of being attacked during this time is small, and the malicious changes to the system will be lost once the computer is rebooted.

However, I guess an attacker who has infiltrated the liveCD system could make malicious changes to the Hard disk, thus doing permanent damage.

What's your opinion?

---

### Post by cdenley on 2009-09-22
The livecd doesn't have any remotely exploitable vulnerabilities as far as I know. However, you can still get compromised by starting connections with vulnerable software such as firefox. In my opinion, it is more secure to use a real install with noscript and security updates, then use the guest account which cannot make any persistent changes to the system unless you change filesystem permissions somewhere.

---

