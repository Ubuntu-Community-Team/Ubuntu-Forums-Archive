---
title: "Common VirtualBox error but I am already in the dialout group"
date: 2022-10-29
forum: Virtualisation
---

### Post by scottbomb on 2022-10-29
New install of 22.04. Check this out...
```
user@laptop:~$ ll /dev/ttyS0
crw-rw---- 1 root dialout 4, 68 Oct 29 12:51 /dev/ttyS0
user@laptop:~$ groups
user adm tty dialout cdrom sudo dip plugdev lpadmin lxd sambashare vboxusers
user@laptop:~$ 

```
I'm a member of dialout but still get this error when trying to launch a VM. BTW, the extension pack is installed as well as guest additions on the target VM:

```
Failed to open host device '/dev/ttyS0' (VERR_DEV_IO_ERROR).
Result Code:
NS_ERROR_FAILURE (0X80004005)
Component:
ConsoleWrap
Interface:
IConsole {6ac83d89-6ee7-4e33-8ae6-b257b2e81be8}

```

```
user@laptop:~$ ll /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 Oct 29 12:51 /dev/ttyS0

```

Any ideas on what could be wrong here?

---

### Post by scottbomb on 2022-10-29
I think I found the problem. The VM came from may main PC which has a serial port  but this laptop does not. Virtualbox was trying to talk to a serial port that doesn't exist.

---

