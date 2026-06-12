---
title: "systemd[1]: ureadahead.service failed"
date: 2015-04-19
forum: Ubuntu Development Version
---

### Post by aljosa2 on 2015-04-19
Hi all,
has anyone else noticed this problem: 

> dmesg
[1.672332] systemd[1]: ureadahead.service: main process exited, code=exited, status=5/NOTINSSTALLED
[1.672612] systemd[1]: Unit ureadahead.service entered failed state.
[1.672643] systemd[1]: ureadahead.service failed.

Here's the output of "*systemctl status -l ureadahead.service*"

> systemctl status -l ureadahead.service
&#9679; ureadahead.service - Read required files in advance
   Loaded: loaded (/lib/systemd/system/ureadahead.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2015-04-19 10:44:50 CEST; 28min ago
  Process: 262 ExecStart=/sbin/ureadahead (code=exited, status=5)
 Main PID: 262 (code=exited, status=5)

Apr 19 10:44:50 blabla ureadahead[262]: ureadahead: Error while tracing: No such file or directory
Apr 19 10:44:50 blabla ureadahead[262]: Counted 8 CPUs
Apr 19 10:45:44 blabla systemd[1]: Stopped Read required files in advance.
Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.

---

### Post by zika on 2015-04-20
Do You have ureadahead installed?

---

### Post by aljosa2 on 2015-04-20
hi zika, thanks for your reply.
i've googled but didn't find a way to see if i have ureadahead installed... 
by the way, my ubuntu is installed onto ssd, but i also have one hdd.

---

### Post by dino99 on 2015-04-20
added my comments on lp:1429098 , vivid package installed indeed

---

### Post by zika on 2015-04-20
> **aljosa2 said:**
> hi zika, thanks for your reply.i've googled but didn't find a way to see if i have ureadahead installed... 
by the way, my ubuntu is installed onto ssd, but i also have one hdd.```
:~$ dpkg -l|grep uread
ii  ureadahead                                            0.100.0-19                                              amd64        Read required files in advance
```If You're using SystemD UReadAhead is not important... ;)

---

### Post by aljosa2 on 2015-04-20
my is the same:
> $ dpkg -l|grep uread
ii  ureadahead                                           0.100.0-19                                 amd64        Read required files in advance

> **zika said:**
> If You're using SystemD UReadAhead is not important... ;)

Sorry, I didn't understand what do you mean by that? Do you maybe want to say that ureadahead error is insignificant? If so, I'm ok with that, but am a little preoccupied because it seems to me that the total number of all this "insignificant" errors here and there is not so small.

---

### Post by zika on 2015-04-20
```
:~$ sudo systemctl status ureadahead.service&#9679; ureadahead.service - Read required files in advance
   Loaded: loaded (/lib/systemd/system/ureadahead.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since &#1087;&#1086;&#1085; 2015-04-20 17:48:23 CEST; 1s ago
  Process: 15186 ExecStart=/sbin/ureadahead (code=exited, status=5)
 Main PID: 15186 (code=exited, status=5)
```
SystemD does not support ureadahead or You could state it the other way around: ureadahead does not support systemd.
In such cases if bothered I do mask susch service so I do not see anymore those warnings... /dev/null rules...
Pick Your own level of suppresing these warnins:```
:~$ sudo systemctl disable ureadahead.service
Removed symlink /etc/systemd/system/default.target.wants/ureadahead.service.
:~$ sudo systemctl mask ureadahead.service
Created symlink from /etc/systemd/system/ureadahead.service to /dev/null.
```It is just an atavism left in default.target.wants ... I'd welcome its revival but...

---

### Post by dino99 on 2015-04-20
> **zika said:**
> 
SystemD does not support ureadahead or You could state it the other way around: ureadahead does not support systemd.


agreed but ubuntu-minimal still force ureadahead to be installed, which is not expected, except if upstart is chosen

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1446283](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1446283)

---

### Post by zika on 2015-04-20
> **9d9 said:**
> agreed but ubuntu-minimal still force ureadahead to be installed, which is not expected, except if upstart is chosen [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1446283](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1446283)It does not make a significant difference so it will be, I suppose, among last to be cleaned as cruft, when/if systemd becomes sole init provider. There are much more important things to get sorted before that (as I call it) atavism (even though I like that idea of readahed, arch has its own way as fedora does, if I remember right). It makes sense to have fallback init provider and that is very wise decision made by Udev's.

---

