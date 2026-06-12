---
title: "systemctl and snap stopped working"
date: 2021-03-01
forum: Virtualisation
---

### Post by ben-barbour on 2021-03-01
I updated my Ubuntu 20.10 this morning, and now any time I try to run `snap`, I get the message:

```

error: cannot preform the following tasks:
- Mount snap "<snap-name>" (Cannot proceed, expected snap "<snap-name>" revision ## to be mounted, but it was not)

```

I've tried multiple snaps.

I tried to restart snapd, but noticed that systemctl no longer gives me any output. None at all, for any command. It always exits 0 and outputs nothing. Examples:

[LIST]
[*]systemctl status snapd 
[*]systemctl restart snapd 
[*]systemctl list-units 
[*]systemctl list-unit-files 
[/LIST]

This is a VM, so I reverted to a snapshot and confirmed that both snapd and systemctl were working (much) earlier. I don't really want to jump back that far because I'll lose other work; and I did try running the update again, and hit the same issue. Any ideas? I don't see anything that looks particularly problematic in journalctl or /var/log/syslog.

---

### Post by slickymaster on 2021-03-02
*Thread moved to **Virtualisation**.*

---

