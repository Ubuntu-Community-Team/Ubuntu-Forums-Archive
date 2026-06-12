---
title: "ACPI Exception: Could not find/resolve named package element: LNKA (20170728/dspkgini"
date: 2018-03-18
forum: Ubuntu Development Version
---

### Post by kilzzz on 2018-03-18
A new error after the last update, right at startup. Not sure where to report it.

ACPI Exception: Could not find/resolve named package element: LNKA (20170728/dspkginit-381)

There are also LNKB LNKC and LNKD lines that look the same.

---

### Post by cruzer001 on 2018-03-18
What kernel are you running?

```
uname -r
```

---

### Post by cruzer001 on 2018-03-18
I'm going offline so here is a launchpad how to:

This looks like a kernel bug.
[https://www.google.com/search?client=ubuntu&channel=fs&q=ACPI+Exception%3A+Could+not+find%2Fresolve+named+package+element%3A+LNKA&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=ACPI+Exception%3A+Could+not+find%2Fresolve+named+package+element%3A+LNKA&ie=utf-8&oe=utf-8)

You need a launchpad account to report a bug.
[https://help.launchpad.net/YourAccount/NewAccount](https://help.launchpad.net/YourAccount/NewAccount)

Then in terminal enter:
```
ubuntu-bug linux
```

And that  will automate a kernel bug report to:
[https://bugs.launchpad.net/bugs/bugtrackers/linux-kernel-bugs](https://bugs.launchpad.net/bugs/bugtrackers/linux-kernel-bugs)

NOTE:
You need to be on kernel 4.15.0-12 or you will probably be creating a invalid bug report.

---

### Post by Yellow Pasque on 2018-03-18
[https://bugzilla.kernel.org/show_bug.cgi?id=198167](https://bugzilla.kernel.org/show_bug.cgi?id=198167)

It sounds like "annoying but harmless" errors. Hopefully, it will be fixed in 4.16

---

### Post by kilzzz on 2018-03-19
Thanks, and I hope they do fix it. If they don't every new user will be posting questions about it.

---

### Post by muemarco on 2018-10-10
> **kilzzz said:**
> Thanks, and I hope they do fix it. If they don't every new user will be posting questions about it.

I have the same problem. Need to enter ctrl-D after each reboot because of this bug.

---

