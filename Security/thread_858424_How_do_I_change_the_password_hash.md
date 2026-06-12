---
title: "How do I change the password hash"
date: 2008-07-13
forum: Security
---

### Post by aetherh4cker on 2008-07-13
Is it possible to change the hashing algorithm that Ubuntu uses to save user passwords?

What is the default algorithm, anyway?  MD5?  If so, I would prefer something that requires more CPU cycles to compute (thinking that I would prefer Whirlpool) and something that isn't known to have collisions.

---

### Post by Gamma746 on 2008-07-13
The version of PAM that ships whith ubuntu doesn't have support for sha256 or sha512.  See [https://bugs.launchpad.net/ubuntu/+source/pam/+bug/245786](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/245786).  If it did, you would edit /etc/pam.d/common-password.

Read ```
man pam_unix
``` for more information.  If you do decide to make changes, **be extremely careful**, as you could lock yourself out of your system if you make a mistake.

---

