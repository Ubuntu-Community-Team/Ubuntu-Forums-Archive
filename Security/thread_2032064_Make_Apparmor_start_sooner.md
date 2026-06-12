---
title: "Make Apparmor start sooner?"
date: 2012-07-23
forum: Security
---

### Post by Hungry Man on 2012-07-23
I want to confine dnscrypt-proxy in apparmor but as you can see it starts first.

Can I make apparmor start first?

edit: Maybe I can confine an already running process without restarting it (restarting is an issue for this) with:
sudo sh -c "echo 'setprofile /path/to/bin' > /proc/pid/attr/current"


but it doesn't seem to work... I get an error
sh: 1: cannot create /proc/pid/attr/current: Directory nonexistent

edit: ended up being a stupid typo

---

