---
title: "Grub2 Authentication 0-Day"
date: 2015-12-18
forum: Security
---

### Post by slickymaster on 2015-12-18
A vulnerability in Grub2 has been found. Versions from 1.98 (December, 2009) to 2.02 (December, 2015) are affected. The vulnerability can be exploited under certain circumstances, allowing local attackers to bypass any kind of authentication (plain or hashed passwords). And so, the attacker may take control of the computer.

Ref.: [https://security-tracker.debian.org/tracker/CVE-2015-8370](https://security-tracker.debian.org/tracker/CVE-2015-8370), [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-8370](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-8370) and [http://people.canonical.com/~ubuntu-security/cve/2015/CVE-2015-8370.html](http://people.canonical.com/~ubuntu-security/cve/2015/CVE-2015-8370.html)

---

### Post by howefield on 2015-12-18
Not sure I'll worry about that one :)

[https://lists.ubuntu.com/archives/ubuntu-security-announce/2015-December/003218.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2015-December/003218.html)

> The problem can be corrected by updating your system to the following package versions:

Ubuntu 15.10:   grub2-common                    2.02~beta2-29ubuntu0.2
Ubuntu 15.04:   grub2-common                    2.02~beta2-22ubuntu1.4
Ubuntu 14.04 LTS:   grub2-common                    2.02~beta2-9ubuntu1.6
Ubuntu 12.04 LTS:   grub2-common                    1.99-21ubuntu3.19

After a standard system update you need to reboot your computer to make all the necessary changes.

---

### Post by slickymaster on 2015-12-18
Yes, it's already corrected upstream.

For the curious of mind, you can take a look at the patch here: [http://hmarco.org/bugs/patches/0001-Fix-CVE-2015-8370-Grub2-user-pass-vulnerability.patch](http://hmarco.org/bugs/patches/0001-Fix-CVE-2015-8370-Grub2-user-pass-vulnerability.patch)

---

### Post by Habitual on 2015-12-18
> **slickymaster said:**
> allowing local attackers to bypass any kind of authentication (plain or hashed passwords).
There is no Security without Physical Security, this includes the keyboard.

---

