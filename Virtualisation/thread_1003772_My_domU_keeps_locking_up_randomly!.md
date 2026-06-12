---
title: "My domU keeps locking up randomly!"
date: 2008-12-06
forum: Virtualisation
---

### Post by tdjb on 2008-12-06
I'm kind of at a loss on this one but it is starting to become quite frustrating. First I'll give you the background:

- Running Ubuntu 8.04 server as the dom0
- Currently using the 2.6.24-19-xen from the ubuntu archives
- domU in question is also Ubuntu 8.04 server using the same kernel

About a week ago, the website that is run on this problem domU wouldn't respond and I couldn't ssh into the domU. I logged into my dom0 and attached myself to the domU console and found this error scrolling over and over:

```

[259458.110263] __find_get_block_slow() failed. block=1360, b_blocknr=32148
[259458.110265] b_state=0x00000029, b_size=4096
[259458.110269] device blocksize: 4096

```

I tried to figure out what the cause was (a reboot was the only fix), but the only thing I could come up with is that it happened around 3am. As an FYI, this happened when I was running the same kernel from this howto: [http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories). 
So I never figured out what the cause was and assumed it was a one off thing. Three days later though I ran into a similar situation (still with this other kernel). The domU wouldn't respond so I logged into the dom0 and attached myself to the domU console again. This time I found this error message:

```

[231747.850967]  =======================
[231759.665823] BUG: soft lockup - CPU#0 stuck for 11s! [apache2:1782]
[231759.665826]
[231759.665828] Pid: 1782, comm: apache2 Tainted: G      D (2.6.24-16-xen #2)
[231759.665831] EIP: 0061:[<c0327dc7>] EFLAGS: 00000286 CPU: 0
[231759.665835] EIP is at _spin_lock+0x7/0x10
[231759.665837] EAX: cf802c18 EBX: cf802bd4 ECX: c1671ec0 EDX: 00000000
[231759.665840] ESI: c1671ec0 EDI: 00000000 EBP: c0f15ddc ESP: c0f15c4c
[231759.665843]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0069
[231759.665846] CR0: 8005003b CR2: b7388e80 CR3: 01741000 CR4: 00000660
[231759.665849] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[231759.665852] DR6: ffff0ff0 DR7: 00000400
[231759.665854]  [<c01a730d>] try_to_free_buffers+0x2d/0x90
[231759.665859]  [<c0167c95>] shrink_page_list+0x4b5/0x5f0
[231759.665864]  [<c01777e3>] page_check_address+0x1d3/0x3d0
[231759.665869]  [<c0166e20>] isolate_lru_pages+0x50/0x1c0
[231759.665874]  [<c0167eeb>] shrink_inactive_list+0x11b/0x3b0
[231759.665879]  [<c0168224>] shrink_zone+0xa4/0x100
[231759.665883]  [<c0168d62>] try_to_free_pages+0x152/0x250
[231759.665888]  [<c016305b>] __alloc_pages+0x12b/0x390
[231759.665893]  [<c0171739>] handle_mm_fault+0x7f9/0x1330
[231759.665899]  [<c0107deb>] local_clock+0x3b/0x80
[231759.665903]  [<c010824b>] sched_clock+0x1b/0x60
[231759.665908]  [<c03299ac>] do_page_fault+0x3bc/0xee0
[231759.665912]  [<c011c6d0>] update_curr+0x70/0x110
[231759.665916]  [<c03263d4>] schedule+0x244/0x600
[231759.665921]  [<c0175824>] do_mmap_pgoff+0x314/0x330
[231759.665925]  [<c0109ef5>] sys_mmap2+0x65/0xd0
[231759.665930]  [<c03295f0>] do_page_fault+0x0/0xee0
[231759.665934]  [<c0328285>] error_code+0x35/0x40
[231759.665940]  =======================

```

Again, looking through the logs I couldn't find anything to set this off, just that it happened between midnight and 4am. So now I think it's possibly the kernel and I update to the 2.6.24-19-xen kernel from the ubuntu repo's. Well, it worked for three days again until this morning I noticed the site was not responding AGAIN. I logged into the console from the dom0 and found this error:

```

[266281.773639] BUG: soft lockup - CPU#0 stuck for 11s! [webalizer:11884]

```

So what is going on here?
I have four other domU's running on this machine that haven't had these issues (yet), but they also get less traffic. Should I file a bug report on this or is there a known fix? Any help would be great as I am really starting to dislike having to reboot this domU every three days.

TIA

---

