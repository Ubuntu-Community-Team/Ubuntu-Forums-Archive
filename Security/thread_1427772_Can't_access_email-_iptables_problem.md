---
title: "Can't access email- iptables problem"
date: 2010-03-11
forum: Security
---

### Post by PDA1 on 2010-03-11
This happened to me before but it was fixed (somehow).  Now it's happening again and i hate it.

To get my Thunderbird email to work and to do FTP to my website I have to use TERMINAL and enter the following code in Root;

iptables -F


At one point weeks ago I got Gufw and I don't remember if that had any effect.

I'm really sick of this problem

Any idea how to fix this?

---

### Post by PDA1 on 2010-03-12
The problem still persists but what I did is uninstall Gufw.

Oddly enough, when I open Firestarter then I can access my email via Thunderbird and FTP to my website works too.

I can QUIT Firestarter and everything still runs fine.

Any ideas so I don't have to open Firestarter every time?

---

### Post by cdenley on 2010-03-12
```

sudo ufw disable

```

---

