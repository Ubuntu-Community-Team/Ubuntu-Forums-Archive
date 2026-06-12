---
title: "Alt+Print+k doesn't work anymore"
date: 2012-09-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Bazon on 2012-09-28
Has anybody an idea how to make it work again?

---

### Post by mc4man on 2012-09-28
> **Bazon said:**
> Has anybody an idea how to make it work again?
Use a kernel where it's enabled ??

Here just enable ctrl+alt+backspace in keyboard options for the occasional need..

---

### Post by Bazon on 2012-09-28
This is really implemented in kernel level? Thanks, interesting to know. 
Does anyone know, why it has been disabled? I thought it was so much "cleaner" than just killing X by Ctrl+Alt+Backspace?

---

### Post by kansasnoob on 2012-09-29
I've noticed a lot of the Alt+SysReq+whatever key sequences no longer work. REISUB used to be really cool way to try and save work if something crashed but we seem to be losing that option.

---

### Post by funicorn on 2012-09-29
It can be enabled in the running level, i.e., tuning some value in /proc/sys/kernel/sysrq. The wierd thing is it's not by default disabled in my case.
> **kansasnoob said:**
> I've noticed a lot of the Alt+SysReq+whatever key sequences no longer work. REISUB used to be really cool way to try and save work if something crashed but we seem to be losing that option.

---

### Post by Bazon on 2012-09-29
OK, it works this way:

check state:
```
cat /proc/sys/kernel/sysrq 
```
(echos 1 if activated)

set on for this session:
```
echo 1 | sudo tee /proc/sys/kernel/sysrq 
```

set on permanently:
in /etc/sysctl.conf add
```
kernel.sysrq = 1
```

---

### Post by funicorn on 2012-09-29
It'd better to set here: 10-magic-sysrq.conf 

I checked and found it's set  kernel.sysrq=176

176= 128 + 32 +16

> **Bazon said:**
> OK, it works this way:

check state:
```
cat /proc/sys/kernel/sysrq 
```(echos 1 if activated)

set on for this session:
```
echo 1 | sudo tee /proc/sys/kernel/sysrq 
```set on permanently:
in /etc/sysctl.conf add
```
kernel.sysrq = 1
```

---

### Post by Bazon on 2012-09-29
> **funicorn said:**
> It'd better to set here: 10-magic-sysrq.conf 
Interesting. But why?
And do you mean /etc/sysctl.d/10-magic-sysrq.conf or do you propose to add it in the home directory (as leaving out the path implies.)

> **funicorn said:**
> 
I checked and found it's set  kernel.sysrq=176
176= 128 + 32 +16
Yes, it had the same value for me. But what does this value mean?
At least I can say, if it is set to 1, Alt+Print+k works.

This may be interesting as well:
[https://launchpad.net/ubuntu/+source/procps/1:3.3.3-2ubuntu2](https://launchpad.net/ubuntu/+source/procps/1:3.3.3-2ubuntu2)

> Changelog

procps (1:3.3.3-2ubuntu2) quantal; urgency=low

  * Add debian/sysctl.d/10-magic-sysrq.conf: disable the magic sysrq key
    by default, since it's not needed for the average system, and exposes
    security issues such as memory disclosure and killing arbitrary
    processes including the screen lock. (LP: #194676)
 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>   Thu, 21 Jun 2012 08:19:56 -0400

---

### Post by Bazon on 2012-09-29
Ah, OK:
/etc/sysctl.d/10-magic-sysrq.conf:
> # The magic SysRq key enables certain keyboard combinations to be
# interpreted by the kernel to help with debugging. The kernel will respond
# to these keys regardless of the current running applications.
#
# In general, the magic SysRq key is not needed for the average Ubuntu
# system, and having it enabled by default can lead to security issues on
# the console such as being able to dump memory or to kill arbitrary
# processes including the running screen lock.
#
# Here is the list of possible values:
#   0 - disable sysrq completely
#   1 - enable all functions of sysrq
#  >1 - enable certain functions by adding up the following values:
#          2 - enable control of console logging level
#          4 - enable control of keyboard (SAK, unraw)
#          8 - enable debugging dumps of processes etc.
#         16 - enable sync command
#         32 - enable remount read-only
#         64 - enable signalling of processes (term, kill, oom-kill)
#        128 - allow reboot/poweroff
#        256 - allow nicing of all RT tasks
#
#   For example, to enable both control of console logging level and
#   debugging dumps of processes: kernel.sysrq = 10
#
kernel.sysrq = 176

so the default setting is:
128 - allow reboot/poweroff
16 - enable sync command
32 - enable remount read-only

---

### Post by funicorn on 2012-09-29
# Here is the list of possible values:
#   0 - disable sysrq completely
#   1 - enable all functions of sysrq
#  >1 - enable certain functions by adding up the following values:
#          2 - enable control of console logging level
#          4 - enable control of keyboard (SAK, unraw)
#          8 - enable debugging dumps of processes etc.
#         16 - enable sync command
#         32 - enable remount read-only
#         64 - enable signalling of processes (term, kill, oom-kill)
#        128 - allow reboot/poweroff
#        256 - allow nicing of all RT tasks
#
#   For example, to enable both control of console logging level and
#   debugging dumps of processes: kernel.sysrq = 10

I think it's clear enough. 176 means enable sync command, enable remount read-only and allow reboot/poweroff

---

