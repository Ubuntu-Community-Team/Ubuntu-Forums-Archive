---
title: "after USG setup, login does not check for Yubikey anymore"
date: 2024-07-05
forum: Security
---

### Post by vbgf3 on 2024-07-05
Hi Everyone,

I just installed USG.   [https://ubuntu.com/security/certifications/docs/usg](https://ubuntu.com/security/certifications/docs/usg)  and did the CIS workstation level 2  Fix. After that my login does not check for my YubiKey anymore.   The pam module settings as instructed by Yubi were not modified by USG.  And the required packages for Yubikey were not un-installed.  I even removed and re-installed.  Still no joy. So I don't know why Yubikey doesn't work now. 

Any clues ?

Thanks

---

### Post by currentshaft on 2024-07-05
It is annoying how Canonical has made it impossible to find the actual rules being applied.

You would think they would be linked in this guide, but no.

One might even search the web and find [https://github.com/canonical/ubuntu-security-guide/](https://github.com/canonical/ubuntu-security-guide/) but no, apparently we don't store them there, either.

Even went to the official CIS website but the spammers want contact information to see content.

Why are they so well hidden? I don't know.

Though I will say this based on my experience as a security professional: CIS benchmarks are all about compliance, which is different than actual security. Unless you are mandated to meet a certain set of qualifications by an auditor, I would not use this "USG" project and find better, more meaningful ways to harden your system. And while we're on the topic, a Yubikey for physical logins is practically security theater, since an adversary with physical access can always defeat such mitigations.

---

### Post by 0f4d0335 on 2024-07-05
Have your /etc/pam.d/ files change? In CIS 2 your PAM module will be set to use complex passwords, so likely the USG script disabled whatever configuration you have (especially default) and prioritized the complex requirements in the CIS guideline.

[https://www.redhat.com/sysadmin/pluggable-authentication-modules-pam](https://www.redhat.com/sysadmin/pluggable-authentication-modules-pam)

USG might fix the changes however, so you'll need to tailor the changes by disabling the PAM modification rules. You'd need to download the CIS guide for 24.04 to identify which ones modify the PAM.

---

