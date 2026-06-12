---
title: "limit login attempts"
date: 2011-01-15
forum: Security
---

### Post by arapaho on 2011-01-15
I'd like to limit login attemts for specific user. I've found information in manpages:
[http://manpages.ubuntu.com/manpages/lucid/man5/limits.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/limits.conf.5.html)
but I'm not sure if this '@' is purposly there, so would be that correct?
```
aparaho        -       maxlogins       4
```
or
```
@aparaho        -       maxlogins       4
```
Maybe '@' is a group syntax? I'm confused.

What happens after 4 failed loggins? Is it enough to restart system to get another login attempts?

Are there any other values that it is reasonable to limit for safety reasons?

---

### Post by CharlesA on 2011-01-15
That only limits how many times a user can be logged in simultaneously. It does nothing for failed login attempts.

---

### Post by Thirtysixway on 2011-01-15
Look at installing fail2ban, it will limit login attempts and temporarily ban the host that's trying to log in too many times.

---

### Post by CharlesA on 2011-01-15
> **Thirtysixway said:**
> Look at installing fail2ban, it will limit login attempts and temporarily ban the host that's trying to log in too many times.
You can also do something similar using iptables.

---

### Post by bodhi.zazen on 2011-01-15
See failog

[http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/](http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/)

---

