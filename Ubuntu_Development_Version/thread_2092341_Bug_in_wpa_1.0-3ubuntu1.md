---
title: "Bug in wpa 1.0-3ubuntu1"
date: 2012-12-07
forum: Ubuntu Development Version
---

### Post by Harry33 on 2012-12-07
The newest wpa (1.0-3ubuntu1) contains a bug.
The package wpasupplicant (which is a dependency of network-manager) depends on libreadline5.
Well we have had libreadline6 in use already with Precise Pangolin.

So updating wpasupplicant pulls in libreadline5 too.

---

### Post by dino99 on 2012-12-07
libreadline5 is also already used by some other packages. I suppose that wpa is using 5 for a good reason (but dont ask me which one ;)  )

---

### Post by smartboyhw on 2012-12-08
> **Harry33 said:**
> The newest wpa (1.0-3ubuntu1) contains a bug.
The package wpasupplicant (which is a dependency of network-manager) depends on libreadline5.
Well we have had libreadline6 in use already with Precise Pangolin.

So updating wpasupplicant pulls in libreadline5 too.
Well the developers don't read here. Why don't you report a bug in Launchpad against this package?

---

### Post by zika on 2012-12-08
> **smartboyhw said:**
> Well the developers don't read hereThat's a myth... ;)

---

### Post by mc4man on 2012-12-08
changelog (debian
> * revert to GNU readline for wpa_cli, instead of using the internal readline
    implementation added in wpa 1~. Prefer libreadline-gplv2-dev, because libnl
    is GPL-2 (only) - switching back to the internal readline implementation is
    targeted for wheezy+1 (Closes: #677993, #678077).

libreadline-gplv2-dev uses libreadline5

---

### Post by ventrical on 2012-12-08
> **mc4man said:**
> changelog (debian


libreadline-gplv2-dev uses libreadline5


libreadline5 just installed itself today in updates ?

 I just let it roll in.

No show stoppers.

---

### Post by Harry33 on 2012-12-09
> **ventrical said:**
> libreadline5 just installed itself today in updates ?

 I just let it roll in.

No show stoppers.

True it does not behave like a show stopper.
But I just do not like having both libreadline5 and libreadline6 installed.
Libreadline6 is definitely newer, hence ABI bumb on naming too.

---

### Post by mc4man on 2012-12-09
> **Harry33 said:**
> 
But I just do not like having both libreadline5 and libreadline6 installed.
Libreadline6 is definitely newer, hence ABI bumb on naming too.
wpa didn't/does not use libreadline6, re-quoting snipped
 > instead of using the **internal** readline implementation added in wpa 1~.


---

