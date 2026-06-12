---
title: "upgrading ubuntu to xenial from trusty"
date: 2015-12-09
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-12-09
Got all these erros. Now time to reboot.
```
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libsane-common_1.0.25+git20150528-1ubuntu2_all.deb
Error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of the setuid helper is not correct
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'libkf5akonadisearch-bin'
W: Ignoring Provides line with DepCompareOp for package php-psr-http-message-implementation
W: Ignoring Provides line with DepCompareOp for package php-psr-log-implementation
W: Ignoring Provides line with DepCompareOp for package php-math-biginteger
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical:~$ 

```

---

### Post by zika on 2015-12-09
If we knew steps leading to this partial log, if we knew, lots of stuff, not hard to provide, these lines might be usefull.
This way, only conclusion is that &#8222;Deban-way&#8220; (so called, not litteraly) rules... ;)

---

### Post by ventrical on 2015-12-09
I am downloading the xenial daily version of lubuntu. I tried Mate but it wants at least 6.4 GBs of ssd space. Only have 4 GBs. It worked with trusty so I will try with lubuntu 32bit xenial and see if I will get same problems.

---

### Post by ventrical on 2015-12-09
> **zika said:**
> I we knew steps leading to this partial log, if we knew, lots of stuff, not hard to provide, these lines might be usefull.
This way, only conclusion is that „Deban-way“ (so called, not litteraly) rules... ;)

I suspected same..

I don't think totally 'debian way' is at fault.  Ventrical too hasty :) is at fault.

Regards..

---

### Post by ventrical on 2015-12-09
lubuntu xenial daily 32bit works just fine while booting from live USB but will not install becasue Ubiquity requires 4.6 GB and my EeePC only has 4GB.

 I'll look for alternate ISO.

Regards..

---

### Post by zika on 2015-12-09
> **ventrical said:**
> I suspected same..

I don't think totally 'debian way' is at fault.  Ventrical too hasty :) is at fault.

Regards..One „f“ was missing in my post so... Corrected above...
I do not see that You've used „Debian way“ so it can not be at fault... ;)

---

### Post by ventrical on 2015-12-09
hehehaha ... first .. I did not see a word that was there .. now I see the word and I forget what it was..but whatever it was.... all the code was there but I overwrote with lubuntu alternate (and that failed) so I have ssd upgrade and will try reinstall.

 regards..

---

