---
title: "sudo apt update Failing in 18.04 - Intermittent and Random"
date: 2018-06-11
forum: Server Platforms
---

### Post by m-dw on 2018-06-11
Hi all

I've been running 18.04 as a general purpose server since early May. It's a fresh install on a new system disk replacing a 16.04 system. Some specific server application configs were restored from backups, butthe base configuration is more-or-less default.

Since I've installed I have intermittently got the following error when manually running apt update, apt-get update or aptitude.

```

sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu bionic InRelease
Get:3 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                          
0% [1 InRelease gpgv 242 kB] [3 InRelease 51.2 kB/74.6 kB 69%]terminate called after throwing an instance of 'std::runtime_error'
  what():  random_device::__x86_rdrand(void)
Aborted

```

The point at which the "terminate" error message is received varies. Previously I've resolved the issue by:
[LIST]
[*]rebooting
[*]rebooting without backup disk attached
[*]restarting urbackup service
[/LIST]

Today none of these actions has made a difference. Is this something that others have encountered?

---

### Post by m-dw on 2018-06-11
That's interesting. I have disabled the  "Execute Disable Bit" in the server BIOS and apt update works. Don't know if  this is a permanent or temporary solution.

---

