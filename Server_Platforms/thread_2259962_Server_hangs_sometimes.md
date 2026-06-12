---
title: "Server hangs sometimes"
date: 2015-01-08
forum: Server Platforms
---

### Post by Vasy_Malyshev on 2015-01-08
Ubuntu 14.04 server, hangs with:

```
Jan  8 16:49:17 freedom1 kernel: BUG: unable to handle kernel paging request at 0000000000002ba1
Jan  8 16:49:17 freedom1 kernel: IP: [<ffffffff811a2bc0>] kmem_cache_alloc_trace+0x80/0x1f0
Jan  8 16:49:17 freedom1 kernel: PGD 84e1d6067 PUD 84e09c067 PMD 0
Jan  8 16:49:17 freedom1 kernel: Oops: 0000 [#1] SMP
Jan  8 16:49:17 freedom1 kernel: Modules linked in: ipt_MASQUERADE iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat xt_TEE nf
Jan  8 16:49:17 freedom1 kernel:  ptp libahci linear pps_core
Jan  8 16:49:17 freedom1 kernel: CPU: 0 PID: 1131 Comm: systemd-logind Tainted: G        W     3.13.0-40-generic #69-Ubuntu
Jan  8 16:49:17 freedom1 kernel: Hardware name: Supermicro X9SRD-F/X9SRD-F, BIOS 3.00 08/06/2013
Jan  8 16:49:17 freedom1 kernel: task: ffff88084d3ac800 ti: ffff880851584000 task.ti: ffff880851584000
Jan  8 16:49:17 freedom1 kernel: RIP: 0010:[<ffffffff811a2bc0>]  [<ffffffff811a2bc0>] kmem_cache_alloc_trace+0x80/0x1f0
Jan  8 16:49:17 freedom1 kernel: RSP: 0018:ffff880851585e30  EFLAGS: 00010282
Jan  8 16:49:17 freedom1 kernel: RAX: 0000000000000000 RBX: ffff88085f010430 RCX: 0000000029382947
Jan  8 16:49:17 freedom1 kernel: RDX: 0000000029382946 RSI: 00000000000080d0 RDI: ffff88085f003c00
Jan  8 16:49:17 freedom1 kernel: RBP: ffff880851585e68 R08: 0000000000017200 R09: ffff88085f003c00
Jan  8 16:49:17 freedom1 kernel: R10: ffffffff813137ab R11: 0000000000000206 R12: 0000000000002ba1
Jan  8 16:49:17 freedom1 kernel: R13: 00000000000080d0 R14: 0000000000000018 R15: ffff88085f003c00
Jan  8 16:49:17 freedom1 kernel: FS:  00007f41c69378c0(0000) GS:ffff88087fc00000(0000) knlGS:0000000000000000
Jan  8 16:49:17 freedom1 kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jan  8 16:49:17 freedom1 kernel: CR2: 0000000000002ba1 CR3: 000000084d3f7000 CR4: 00000000001427f0
Jan  8 16:49:17 freedom1 kernel: Stack:
Jan  8 16:49:17 freedom1 kernel:  ffff88085f003c00 ffffffff813137ab ffff88085f010430 ffff88084f83e000
Jan  8 16:49:17 freedom1 kernel:  0000000000000003 ffffffff8189bb80 00000000ffffffff ffff880851585e90
Jan  8 16:49:17 freedom1 kernel:  ffffffff813137ab 0000000000000000 ffff88084f83e000 ffff880850968e40
Jan  8 16:49:17 freedom1 kernel: Call Trace:
Jan  8 16:49:17 freedom1 kernel:  [<ffffffff813137ab>] ? apparmor_file_alloc_security+0x5b/0x180
Jan  8 16:49:17 freedom1 kernel:  [<ffffffff813137ab>] apparmor_file_alloc_security+0x5b/0x180
Jan  8 16:49:17 freedom1 kernel:  [<ffffffff812d5df6>] security_file_alloc+0x16/0x20
Jan  8 16:49:17 freedom1 kernel:  [<ffffffff811bf7a0>] get_empty_filp+0x90/0x180
Jan  8 16:49:17 freedom1 kernel:  [<ffffffff811bf8ae>] alloc_file+0x1e/0xf0
Jan  8 16:49:17 freedom1 kernel:  [<ffffffff81607b9c>] sock_alloc_file+0x9c/0x130
```

Is it hardware problem or kernel bug?

---

### Post by Doug S on 2015-01-08
Hi and welcome to Ubuntu forums,

> **Vasy_Malyshev said:**
> Is it hardware problem or kernel bug?Do not know, yet.> **Vasy_Malyshev said:**
> Jan  8 16:49:17 freedom1 kernel: CPU: 0 PID: 1131 Comm: systemd-logind Tainted: G        W     [COLOR=#ff0000]3.13.0-40-generic #69-Ubuntu[/COLOR]Your system is not up to date. The first step should be that you update everything and see how things go from there.```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Vasy_Malyshev on 2015-01-08
> **Doug S said:**
> Hi and welcome to Ubuntu forums,

Do not know, yet.Your system is not up to date. The first step should be that you update everything and see how things go from there.```
sudo apt-get update
sudo apt-get dist-upgrade
```

I always thought that LTS versions are rock solid, but you are recommending upgrade it :confused:

---

### Post by Doug S on 2015-01-08
> **Vasy_Malyshev said:**
> I always thought that LTS versions are rock solid, but you are recommending upgrade it :confused:No, I'm just saying that your 14.04 is out of date. So you should at least start by bringing it up to date as the first step. It will still be 14.04 afterwards.

---

### Post by kpatz on 2015-01-08
Memory issues can cause these.  Boot a live CD/USB and run Memtest for a while, and see if it shows any errors.

---

### Post by MAFoElffen on 2015-01-09
> **Vasy_Malyshev said:**
> I always thought that LTS versions are rock solid, but you are recommending upgrade it :confused:
dist-upgrade is not do-release-upgrade... it is just a safer way of doing
```

sudo apt-get upgrade

```
If you have not applied in-version upgrades to your system, like it looks like you have not, then that may be your problem.

LTS is basically solid, if keep up with your in-version upgrades. Have you ever heard something along the lines of "This version is released, the contained bugs are included free of cost..." A Release is a snap-shot in time. During the Version test cycle, the people involved with U+1 testing try to test as much as we can, on as much varied hardwre as we can. Then the dev's roll back to what was the most stable combination of things for that release date. 

That is not to say that it is bullet proof for all combonations of hardware at that time, but as close to that as we can see at that date. Later, at Launchpad, there are other problems that arise and resolved. Security issues are resolved. (Bleeding Heart, Bash, etc.) Upstream patches are applied. Sometimes, an upstream update of packages, breaks things... Etc. Even with the Instalation ISO's, you usually come with a version .1, .2, ... 

This is not as much a factor with Server Edition as it is with Desktop Edition, but it is still an ongoing process. And yes, a server is not something you can just reboot at any time. But as Sys Admin's we plan for maintenance. We try to prevent problems... and recovery from unforeseen problems.

In an LTS, all those things are applied and improved behind the scenes through updates, to keep that LTS stable. If you have not keep up with those maintenance and security updates... then yes, the system needs to get those patches and fixes applied to get the system up to date within that version. Just doing that "may" resolve your issues. That is a start.

Disclaimer-- Not saying this is the thing to do in all circumstances. Sometimes, "some" issues need to be resolved before someone can proceed.

---

