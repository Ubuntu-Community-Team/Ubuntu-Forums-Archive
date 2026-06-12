---
title: "Apparmor'ing eggdrop - /etc/passwd - that can't be sane can it?"
date: 2012-01-13
forum: Security
---

### Post by cryptotheslow on 2012-01-13
Hi,

First time configuring an apparmor profile - in this case for eggdrop.

Eggdrop v1.6.21 source downloaded from eggheads.org and compiled then installed into home directory by an unprivileged user "eggie" on Ubuntu Server 10.04.3 LTS.

So having added a basic restrictive apparmor profile for it I've spent the last hour or so tailing /var/log/messages and adding stuff being complained about to the profile. Pretty much as expected - some network capability, tcl, some libs - fair enough.

However one apparmor message has me a little concerned:

```
Jan 13 09:17:26 ubuserver kernel: [ 9263.089688] type=1503 audit(1326446246.225:260):  operation="open" pid=2756 parent=2755 profile="/home/eggie/eggdrop/eggdrop-1.6.21" requested_mask="::r" denied_mask="::r" fsuid=3001 ouid=0 name="/etc/passwd"
```It seems eggdrop is wanting to read /etc/passwd.

Is it normal for a user application to want or need to read that?

I've left it denied for now and it seems to run fine.

:confused: crypto :confused:

---

### Post by cryptotheslow on 2012-01-13
Having had more caffeine and done some reading it's perfectly sane for an application to read /etc/passwd - my caffeine deprived mind had somehow disconnected the grey cells that once held the memory that it's been a very long time since passwords were actually held in there :D

Move along - nothing to see here :)

---

