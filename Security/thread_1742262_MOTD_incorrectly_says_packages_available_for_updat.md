---
title: "MOTD incorrectly says packages available for update"
date: 2011-04-28
forum: Security
---

### Post by box2 on 2011-04-28
When logging into ubuntu-server 10.04 via ssh I see:

17 packages can be updated.
6 updates are security updates.

But apt-get update; apt-get upgrade shows that nothing needs updating.  And indeed I have been keeping up to date, I downloaded the rsync update this morning.

How do I trace this back to what writes those messages?

---

### Post by stlsaint on 2011-04-29
> **box2 said:**
> When logging into ubuntu-server 10.04 via ssh I see:

17 packages can be updated.
6 updates are security updates.

But apt-get update; apt-get upgrade shows that nothing needs updating.  And indeed I have been keeping up to date, I downloaded the rsync update this morning.

How do I trace this back to what writes those messages?

try:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by box2 on 2011-04-29
dist-upgrade does not fix it either :(

---

### Post by tgm4883 on 2011-04-29
Are you experiencing this 

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827)

---

### Post by CharlesA on 2011-04-29
> **tgm4883 said:**
> Are you experiencing this 

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827)
Yep, that's the bug.

Check this file:

```
cat /etc/motd.tail
```

I had the same thing happen on my 10.04 desktop.

[http://ubuntuforums.org/showthread.php?t=1222909](http://ubuntuforums.org/showthread.php?t=1222909)

---

### Post by box2 on 2011-04-30
Yes, this was the problem exactly.  I removed /etc/motd.tail and it seems to be generating the correct information for motd again.  Thank you very much for the input!

---

