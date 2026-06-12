---
title: "Kernel Panic"
date: 2009-03-27
forum: Server Platforms
---

### Post by will136 on 2009-03-27
Hi All,

I'm running a number of Ubuntu 7.10 (VMware) VM's on CentOS hosts.  I had a recent kernel panic on an Ububtu VM that I've not been able to diagnose and would appreciate any help.
Ubuntu host was responding slowly prior to panic though load via uptime was <1 and processes were normal.  I did note that iostat yielded a high iowait time (20%) so I'm wondering if the disk subsystem is having a problem.
The kernel panic wrote the following to console:
RIP [ffffffff880eff3c] :mptbase:mpt_interrupt+0x10c/0x4a0
RSP <ffffffff8063aef8>
CR2: ffff8101bc58650e
Kernel Panic - not syncing: Aiee, killing interrupt handler!
See attached jpeg for full details.

System has been running normally. Uptime was 45 days since last scheduled shutdown. Host has been up for 130 days  Please also find dmesg and dmesg.0 attached.  There have been no recent changes.
Appreciate your comments.

---

### Post by will136 on 2009-04-07
Should have mentioned that this is Ubuntu 64 and should probably have posted in the 64 bit forum.  Most of the kernel panics there seem to be related to install on new systems though.  Any comments on how to interpret the panic info?  Most of the threads on how to interpret the contents of the panic seem to be OSX specific.

Thanks

---

### Post by knowmad on 2009-04-17
Hi Will,

I'm having a very similar problem with a 64-bit host that is running 32-bit guests. So far, you're the first person I've found who is reporting the same issue I'm seeing. Here's my specs:

[LIST]
[*]VMware Server v1.0.9
[*]Host - Ubuntu 8.04 (64-bit)
[*]Guests - 4 x Ubuntu 8.04 (32-bit)
[/LIST]

The server is slightly underpowered CPU-wise but there's plenty of RAM for the running guests. My suspicion is a disk subsystem as well as the kernel panics usual occur when heavy disk activity occurs (such as nightly backups). My kernel message is slightly different (see attached image) but the same general area. I was seeing this on 7.10 as well (hoping the upgrade to 8.04 would fix it but no luck).

I'm continuing to search for a solution. Please post back to this thread if you find anything.

EDIT: I found this link ([http://lkml.indiana.edu/hypermail/linux/kernel/0604.3/0848.html](http://lkml.indiana.edu/hypermail/linux/kernel/0604.3/0848.html)) and want to check my version of the kernel code against the proposed patch.

EDIT: I've reviewed mptbase.c in 2.6.24-23 and the edits in the url above have been made.
I'm considering self-compiling a kernel to see if that makes any difference.


William

---

### Post by knowmad on 2009-05-28
I have resolved this problem. By applying several performance tweaks found around the web, I've not seen this issue in over 3 weeks. Here's what I did:

1. Use tmpfs on tmp – see [http://cyborgworkshop.org/2008/06/12/using-tmpfs-in-linux-with-vmware-server/](http://cyborgworkshop.org/2008/06/12/using-tmpfs-in-linux-with-vmware-server/)

2. Add the following lines to the .vmx of each VM while they are not running:

# Performance improvements
MemTrimRate=0
sched.mem.pshare.enable = "FALSE"
mainMem.useNamedFile = "FALSE"

3. If powersaving is enabled in the OS and/or the BIOS you should disable it.

4. Do not use virtual ide controllers for your guests.

5. Enable write-caching - see [http://sanmelody.blogspot.com/2008/07/write-cache-mode-performance-difference.html](http://sanmelody.blogspot.com/2008/07/write-cache-mode-performance-difference.html)

---

