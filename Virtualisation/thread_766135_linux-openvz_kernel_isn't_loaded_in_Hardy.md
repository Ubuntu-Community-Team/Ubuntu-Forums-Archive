---
title: "linux-openvz kernel isn't loaded in Hardy"
date: 2008-04-25
forum: Virtualisation
---

### Post by ansi on 2008-04-25
Hello,

 I have 8.04 LTS Kubuntu installation with:

```
linux-image-2.6.24-16-openvz:
  Installed: 2.6.24-16.30
  Candidate: 2.6.24-16.30
```

- LVM + ReiserFS for all partitions (and for / too)

- Quote from /boot/grub/menu.lst:
>         kernel /vmlinuz-2.6.24-16-openvz root=/dev/mapper/sys--vol-root ro

but this kernel doesn't work for me, it shows traceback each N seconds and system isn't loaded:
```
DR0: 0000000 DR1: 0000000 DR2: 0000000 DR3: 0000000
DR6: ffff0ff0 DR7: 0000000
[timestamp] [<c01b820a>] __d_path+0xea/0x1b0
[timestamp] [<c01b83a1>] d_path+0xd1/0x110
[timestamp] [<c01b8d51>] d_root_check+0x11/0x20
[timestamp] [<c01e019a>] proc_fd_info+0x7a/0x170
[timestamp] [<c01e010b>] do_lookup+0x7b/0x1d0
   ...
[timestamp] [<c0320000>] neigh_lookup_cb+0x10/0x80
======
```

OpenVZ's developer said to me it must be fixed in this kernel version in 8.04, but it wasn't.

Could please anybody tell me the solution? May be I do smth. wrong?

Thank you,

---

### Post by ansi on 2008-04-26
Eventually I found an already submitted bug at 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210672](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210672) with solutions of the problem.

So, the problem solved.

---

