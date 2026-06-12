---
title: "password for user bin?"
date: 2013-01-30
forum: Security
---

### Post by hufemj on 2013-01-30
My system got compromised and I'm trying to find out how. The log files show a brute force attack on user bin. Since remote ssh login attempts are spaced 3 seconds apart, I am having difficulty understanding why an attacker would even attempt to login as bin. Since bin is not even a regular user, what password would apply to an ssh attempt? The first administrator's (me)?

I know that the system was compromised at least 10 days before because there's a record of me having logged in from the other side of the world. Since the brute force attack on bin followed later, I wonder ... why?

I suspect that the original compromise was related to Samba and poor patch maintenance on my part.

In summary, what password would apply to system user bin and how is the password established?

Thanks.

---

### Post by linuxtechguy on 2013-01-30
The bin user doesnt have a password associated with it. In /etc/shadow you should see a * in the second field for the bin user meaning logins are distabled.

```

bin:*:13678:0:99999:7:::

```

If you are seeing that a lot of your system accounts have a password hash in the second field you might have a lot more cleanup to do.

---

