---
title: "How to upgrade when HD is encrypted"
date: 2010-08-09
forum: Security
---

### Post by PaganImmolator on 2010-08-09
I have a 9.04 system encrypted from installation using the standard Ubuntu FS encryption. 

My question is what consequences are there to upgrading to 9.10 and beyond?

Does it happen seemlessly or are the potential for security leaks and or data loss?

---

### Post by bodhi.zazen on 2010-08-09
> **PaganImmolator said:**
> I have a 9.04 system encrypted from installation using the standard Ubuntu FS encryption. 

My question is what consequences are there to upgrading to 9.10 and beyond?

Does it happen seemlessly or are the potential for security leaks and or data loss?

You upgrade an encrypted system the same way as an unencrypted system. It is no more or less problematic then an unencrypted partition.

The only differences I can think of would be:

1. Encryption makes data recovery difficult to impossible, so back up before you upgrade, but you should be doing this already, so not much different.

2. There are a handful of packages unique to LUKS / ecryptfs or whatever you are using for encryption. I have not had bugs with any of these packages in terms of upgrades, YMMV.

---

### Post by OpSecShellshock on 2010-08-09
I would think that since you're in an active session when upgrading, the relevant files would not be encrypted during the process. Just keep the passphrase you were given at the time you initially installed and encrypted handy, and back up the data in case of any issues. I wouldn't expect a problem due to it taking place during an active session and the login password staying the same before and after the OS upgrade.

---

