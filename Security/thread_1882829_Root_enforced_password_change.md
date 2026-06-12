---
title: "Root enforced password change"
date: 2011-11-18
forum: Security
---

### Post by DrJohn999 on 2011-11-18
This is a 10.04 LTS VM using KVM / libvirt under a 10.04 LTS physical server. This evening I attempted to log onto this VM and received a message at login to the effect that I must change my expired password. Strange, I thought, because there is no expiration on the password. This happened both in an ssh session or console tty0 via virt-manager, and persisted after a reboot. I changed the password accordingly, and received the message "the passwords must be different." The new p/w *was* different, but only by one character. However, to my knowledge similarity checking is not enforced. I changed the p/w again and then did:
```
sudo chage -l <username>
Last password change					: Nov 18, 2011
Password expires					: never
Password inactive					: never
Account expires						: never
Minimum number of days between password change		: 0
Maximum number of days between password change		: 99999
Number of days of warning before password expires	: 7

```
As I thought. The system time was running 15 minutes slow (fixed that) but that should have nothing to do with it here. So, why then did login ask to change the password? Logging out and back in worked. Then I changed the password again just for my own reasons.

This is a web/mail server. In the interim where the password change was being requested, it did not respond to incoming IMAP requests. After password change, IMAP etc. is OK.

I've been running 10.04 VMs since the LTS came out, always configured the same with regard to passwords, and I've never seen this before.

---

