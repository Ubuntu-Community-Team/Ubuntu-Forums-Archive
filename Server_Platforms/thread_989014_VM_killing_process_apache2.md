---
title: "VM: killing process apache2"
date: 2008-11-21
forum: Server Platforms
---

### Post by adieb on 2008-11-21
Hi,

I am using a webserver in a virtual maschine, which is based on JEOS, running on a 8.04 64BIT Server.
The Webserver hosts Typo3 (PHP, MYSQL). Actually there are no "visible" errors, the Site is running fine.

The virtualization is done by VirtualBox CSE.

But in /var/log/syslog I can read this error almost everyday:
```
Nov 21 00:17:52 VMwebserver kernel: [1307868.061128] Bad pte = 00000060, process = apache2, vm_flags = 100073, vaddr = 853a001
Nov 21 00:17:52 VMwebserver kernel: [1307868.067770] Pid: 3398, comm: apache2 Not tainted 2.6.24-19-virtual #1
Nov 21 00:17:52 VMwebserver kernel: [1307868.067956]  [handle_mm_fault+0x650/0x730] handle_mm_fault+0x650/0x730
Nov 21 00:17:52 VMwebserver kernel: [1307868.068020]  [do_page_fault+0x13f/0x730] do_page_fault+0x13f/0x730
Nov 21 00:17:52 VMwebserver kernel: [1307868.068055]  [do_page_fault+0x0/0x730] do_page_fault+0x0/0x730
Nov 21 00:17:52 VMwebserver kernel: [1307868.068076]  [error_code+0x72/0x80] error_code+0x72/0x80
Nov 21 00:17:52 VMwebserver kernel: [1307868.068099]  [__copy_user_intel+0x69/0xb0] __copy_user_intel+0x69/0xb0
Nov 21 00:17:52 VMwebserver kernel: [1307868.068129]  [memcpy_toiovec+0x37/0x60] memcpy_toiovec+0x37/0x60
Nov 21 00:17:52 VMwebserver kernel: [1307868.068160]  [ipv6:skb_copy_datagram_iovec+0xaf/0x210] skb_copy_datagram_iovec+0xaf/0x210
Nov 21 00:17:52 VMwebserver kernel: [1307868.068183]  [ipv6:_spin_lock_bh+0x8/0x20] _spin_lock_bh+0x8/0x20
Nov 21 00:17:52 VMwebserver kernel: [1307868.068210]  [ipv6:tcp_recvmsg+0xa57/0xb80] tcp_recvmsg+0xa57/0xb80
Nov 21 00:17:52 VMwebserver kernel: [1307868.068242]  [ipv6:sock_common_recvmsg+0x47/0x70] sock_common_recvmsg+0x47/0x70
Nov 21 00:17:52 VMwebserver kernel: [1307868.068266]  [sock_aio_read+0x120/0x130] sock_aio_read+0x120/0x130
Nov 21 00:17:52 VMwebserver kernel: [1307868.068292]  [ext3:do_sync_read+0xd5/0xba0] do_sync_read+0xd5/0x120
Nov 21 00:17:52 VMwebserver kernel: [1307868.068320]  [<c01408e0>] autoremove_wake_function+0x0/0x40
Nov 21 00:17:52 VMwebserver kernel: [1307868.068352]  [lp:schedule+0x1e2/0x630] schedule+0x1e2/0x5e0
Nov 21 00:17:52 VMwebserver kernel: [1307868.068376]  [vfs_read+0x15f/0x170] vfs_read+0x15f/0x170
Nov 21 00:17:52 VMwebserver kernel: [1307868.068398]  [sys_read+0x41/0x70] sys_read+0x41/0x70
Nov 21 00:17:52 VMwebserver kernel: [1307868.068419]  [syscall_call+0x7/0x0b] syscall_call+0x7/0xb
Nov 21 00:17:52 VMwebserver kernel: [1307868.068449]  =======================
Nov 21 00:17:52 VMwebserver kernel: [1307868.068469] VM: killing process apache2
Nov 21 00:17:53 VMwebserver kernel: [1307868.081335] Bad pte = 00000060, process = apache2, vm_flags = 100073, vaddr = 853a001
Nov 21 00:17:53 VMwebserver kernel: [1307868.082067] Pid: 3398, comm: apache2 Not tainted 2.6.24-19-virtual #1
Nov 21 00:17:53 VMwebserver kernel: [1307868.082100]  [handle_mm_fault+0x650/0x730] handle_mm_fault+0x650/0x730
Nov 21 00:17:53 VMwebserver kernel: [1307868.082137]  [do_page_fault+0x13f/0x730] do_page_fault+0x13f/0x730
Nov 21 00:17:53 VMwebserver kernel: [1307868.082165]  [do_page_fault+0x0/0x730] do_page_fault+0x0/0x730
Nov 21 00:17:53 VMwebserver kernel: [1307868.082187]  [error_code+0x72/0x80] error_code+0x72/0x80
Nov 21 00:17:53 VMwebserver kernel: [1307868.082210]  [__copy_user_intel+0x69/0xb0] __copy_user_intel+0x69/0xb0
Nov 21 00:17:53 VMwebserver kernel: [1307868.082234]  [memcpy_toiovec+0x37/0x60] memcpy_toiovec+0x37/0x60
Nov 21 00:17:53 VMwebserver kernel: [1307868.082259]  [ipv6:skb_copy_datagram_iovec+0xaf/0x210] skb_copy_datagram_iovec+0xaf/0x210
Nov 21 00:17:53 VMwebserver kernel: [1307868.082285]  [tcp_v4_rcv+0x7bd/0x9a0] tcp_v4_rcv+0x7bd/0x9a0
Nov 21 00:17:53 VMwebserver kernel: [1307868.082307]  [ipv6:_spin_lock_bh+0x8/0x20] _spin_lock_bh+0x8/0x20
Nov 21 00:17:53 VMwebserver kernel: [1307868.082355]  [ipv6:tcp_recvmsg+0xa57/0xb80] tcp_recvmsg+0xa57/0xb80
Nov 21 00:17:53 VMwebserver kernel: [1307868.082379]  [ip_local_deliver_finish+0xf9/0x210] ip_local_deliver_finish+0xf9/0x210
Nov 21 00:17:53 VMwebserver kernel: [1307868.082407]  [ipv6:sock_common_recvmsg+0x47/0x70] sock_common_recvmsg+0x47/0x70
Nov 21 00:17:53 VMwebserver kernel: [1307868.082454]  [sock_aio_read+0x120/0x130] sock_aio_read+0x120/0x130
Nov 21 00:17:53 VMwebserver kernel: [1307868.082481]  [ext3:do_sync_read+0xd5/0xba0] do_sync_read+0xd5/0x120
Nov 21 00:17:53 VMwebserver kernel: [1307868.082508]  [<c01408e0>] autoremove_wake_function+0x0/0x40
Nov 21 00:17:53 VMwebserver kernel: [1307868.082535]  [finish_task_switch+0x2e/0x80] finish_task_switch+0x2e/0x80
Nov 21 00:17:53 VMwebserver kernel: [1307868.082566]  [vfs_read+0x15f/0x170] vfs_read+0x15f/0x170
Nov 21 00:17:53 VMwebserver kernel: [1307868.082589]  [sys_read+0x41/0x70] sys_read+0x41/0x70
Nov 21 00:17:53 VMwebserver kernel: [1307868.082612]  [syscall_call+0x7/0x0b] syscall_call+0x7/0xb
Nov 21 00:17:53 VMwebserver kernel: [1307868.082637]  =======================
Nov 21 00:17:53 VMwebserver kernel: [1307868.082650] VM: killing process apache2
Nov 21 00:17:53 VMwebserver kernel: [1307868.281830] Bad pte = 00000060, process = apache2, vm_flags = 100073, vaddr = 853a000
Nov 21 00:17:53 VMwebserver kernel: [1307868.282789] Pid: 3398, comm: apache2 Not tainted 2.6.24-19-virtual #1
Nov 21 00:17:53 VMwebserver kernel: [1307868.282828]  [handle_mm_fault+0x650/0x730] handle_mm_fault+0x650/0x730
Nov 21 00:17:53 VMwebserver kernel: [1307868.282872]  [do_page_fault+0x13f/0x730] do_page_fault+0x13f/0x730
Nov 21 00:17:53 VMwebserver kernel: [1307868.282905]  [do_page_fault+0x0/0x730] do_page_fault+0x0/0x730
Nov 21 00:17:53 VMwebserver kernel: [1307868.282933]  [error_code+0x72/0x80] error_code+0x72/0x80
Nov 21 00:17:53 VMwebserver kernel: [1307868.282966]  =======================
Nov 21 00:17:53 VMwebserver kernel: [1307868.282982] VM: killing process apache2

```


What is going on there? Is it harmful? How can I stop that?

Any Ideas?


Thanks a lot!

---

### Post by adieb on 2009-02-09
bump...

I am sorry to bump this thread... But even after a couple of month this problem / error persists...

Does anybody experience similar problems?

I just found a post with:
```
[11926.720530] Bad pte = 4800000010ba1842, process = hald-addon-keyb, vm_flags 
= 100073, vaddr = 2b1ced112ea0
```

here: [http://lkml.org/lkml/2006/9/27/146](http://lkml.org/lkml/2006/9/27/146)


No idea what it´s about...

---

