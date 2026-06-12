---
title: "drbd not available in ubuntu 10.10?"
date: 2010-10-15
forum: Server Platforms
---

### Post by artooro on 2010-10-15
Hey folks,

It seems to be drbd is not available in ubuntu 10.10 at all.

I just installed the drbd8-utils package thinking the kernel module would already be built-in. But I guess not, because here is the error I get:

```
# drbdadm syncer r0
Could not stat("/proc/drbd"): No such file or directory
do you need to load the module?
try: modprobe drbd
Command 'drbdsetup 1 syncer --set-defaults --create-device' terminated with exit code 20
drbdadm syncer r0: exited with code 20
```


So what's up with that? I see that in ubuntu 10.04 there is a drbd8-source package which according to the DRBD manual:
[http://www.drbd.org/docs/install/](http://www.drbd.org/docs/install/)
If I run these commands:
```
apt-get install drbd8-utils drbd8-module-source \
  build-essential module-assistant
module-assistant auto-install drbd8
```
it would work. But of course the package is not there in 10.10 maverick.

Can I download the package for lucid and install it on maverick? This seems quite odd.

I want to use 10.10 instead of 10.04 because of the new EC2 features such as pvgrub.

---

### Post by rnldpj on 2011-08-13
Check this step by step guide to configure DRBD in Ubuntu 10.10. 

[http://jackal777.wordpress.com/2011/08/13/setup-drbd-in-ubuntu-10-10/](http://jackal777.wordpress.com/2011/08/13/setup-drbd-in-ubuntu-10-10/)

---

