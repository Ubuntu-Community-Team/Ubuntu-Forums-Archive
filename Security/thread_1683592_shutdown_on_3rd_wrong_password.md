---
title: "shutdown on 3rd wrong password"
date: 2011-02-07
forum: Security
---

### Post by jlparsons on 2011-02-07
Is there a way to have the system shut down automatically after a set number of wrong user password entries?  Am using ubuntu and kubuntu on two different machines.  Am thinking it would make sense to have this feature on an encrypted laptop system in case someone were to take it whilst it's on suspend, screenlock, hibernate or login screen and hence the disk is vulnerable.

---

### Post by sisco311 on 2011-02-07
Check out pam_tally: 

[http://www.cyberciti.biz/tips/lock-unlock-set-number-of-login-attempts.html](http://www.cyberciti.biz/tips/lock-unlock-set-number-of-login-attempts.html)
and
```
man pam_tally
man pam
```

EDIT: Check out [thread=1024263]this[/thread] as well. ;)

---

### Post by jlparsons on 2011-02-07
> **sisco311 said:**
> Check out pam_tally: 

[http://www.cyberciti.biz/tips/lock-unlock-set-number-of-login-attempts.html](http://www.cyberciti.biz/tips/lock-unlock-set-number-of-login-attempts.html)
and
```
man pam_tally
man pam
```

Thanks for that.  To keep encrypted data safe it would need to shutdown the system and force the user to re-enter the encryption passphrase/smartcard, any idea if it can be configured to do so?  I couldn't see how...

---

### Post by Joeb454 on 2011-02-07
*Thread moved to **Security Discussions**.*

---

### Post by Dave_L on 2011-02-08
> **jlparsons said:**
> Is there a way to have the system shut down automatically after a set number of wrong user password entries?...

Would that really be useful?

If the password is a strong one, it wouldn't matter how many retries are made.

And a resourceful person could reboot from a Live CD, or remove the hard drive and connect it to another machine as a secondary (non-boot) drive. In either of those cases, any automatic shutdown feature would be circumvented.

---

### Post by HermanAB on 2011-02-08
It will slow an attacker down, so it is useful.

---

### Post by jlparsons on 2011-02-08
> **Dave_L said:**
> Would that really be useful?

If the password is a strong one, it wouldn't matter how many retries are made.

And a resourceful person could reboot from a Live CD, or remove the hard drive and connect it to another machine as a secondary (non-boot) drive. In either of those cases, any automatic shutdown feature would be circumvented.

Remember I'm talking about an encrypted install - the issue is not with the system password but with the underlying disc encryption passphrase.  If the system is stolen whilst powered-up or suspended the encryption key has already been entered and the filesystem is vulnerable.  If a 3rd strike system forces the system to shutdown or even restart then the encryption key is lost from ram and the hard drive encryption is secure (assuming the theif doesn't have access to the passcode in which case they have complete access via the methods you mentioned).

---

