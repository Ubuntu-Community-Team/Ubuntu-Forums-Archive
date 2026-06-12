---
title: "[SOLVED] VBox+Intrepid Ibex Alpha-1, Guest Additions wont compile."
date: 2008-07-02
forum: Virtualisation
---

### Post by Shazaam on 2008-07-02
Ubuntu 7.10, VirtualBox 1.6 (from Sun/Innotek).
Installed Intrepid Alpha-1 on vbox after some fiddling with ACPI. Guest Additions 1.6 error out and wont install. Has anybody had any luck with installing them?
Error message.....
```
(vboxvfs)" -c -o /tmp/vbox.0/.tmp_regops.o /tmp/vbox.0/regops.c
/tmp/vbox.0/regops.c: In function &#8216;sf_reg_nopage&#8217;:
/tmp/vbox.0/regops.c:339: error: &#8216;NOPAGE_SIGBUS&#8217; undeclared (first use
in this function)
/tmp/vbox.0/regops.c:339: error: (Each undeclared identifier is reported
only once
/tmp/vbox.0/regops.c:339: error: for each function it appears in.)
/tmp/vbox.0/regops.c:346: error: &#8216;NOPAGE_OOM&#8217; undeclared (first use in
this function)
/tmp/vbox.0/regops.c: At top level:
/tmp/vbox.0/regops.c:378: error: unknown field &#8216;nopage&#8217; specified in
initializer
/tmp/vbox.0/regops.c:379: warning: initialization from incompatible
pointer type
make[2]: *** [/tmp/vbox.0/regops.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxvfs] Error 2

```
edit=
!d'oh! (smacks head) probably a app version missmatch.

---

### Post by Shazaam on 2008-07-02
Hmmpfff.
Installed Intrepid on VMware Player. Was able to adjust screen resolution/use shared folders without the need for VMware Tools.
For those having trouble running Ibex as a vm try adding these to your kernel line in Ibex's menu.lst.....
```
noalpci acpi=off
```

---

### Post by Shazaam on 2008-07-03
I am going to call this somewhat solved per my edit in the first post but I am still open to suggestions.

---

