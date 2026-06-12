---
title: "Kernel panic when under cpu + network load"
date: 2008-10-21
forum: Server Platforms
---

### Post by GoBieN on 2008-10-21
Hey everyone, i hope you can help me out with this.

I'm running Ubuntu 8.04.1 server as a virtual machine on XenServer 5.0 Express (free version of the commercial Xen Hypervisor solution from Citrix, formerly XenSource).

After the third kernel panic (and forced reboot) i went to see what triggers this error.

This is what i have come up with, t**he kernel panic happens when there is a huge amount of network traffic, combined with some CPU load.**

**I have just now triggered this panic like this:**
I ran WinSCP on a windows VM (on the same physical server), from WinSCP i logged in on the Ubuntu VM and copied a 5GB file to /mnt/public on the linux . After this started i went to my already open SSH connection to the Ubuntu VM and typed in:
> stress --cpu 2 --io 4 --vm 2 --vm-bytes 128M --timeout 60s
Right after this stresstest started i got a kernel panic.

**Now my questions:**
1) Does anyone know how I can resolve this ?
2) Can i somehow force reboot on kernel panic ?

Ouput on console from panic:
```
[74056.154355] BUG: unable to handle kernel paging request at virtual address 10d81284
[74056.154371] printing eip: c0161083
[74056.154378] 292fb000 -> *pde = 00000001:11910027
[74056.154381] 1e447000 -> *pme = 00000000:00000000
[74056.154386] Oops: 0000 [#1] SMP 
[74056.154391] Modules linked in: nfnetlink_queue nfnetlink nf_conntrack_ipv4 ipt_REJECT xt_mark xt_tcpudp ipt_iprange xt_state nf_conntrack xt_NFQUEUE iptable_filter ip_tables x_tables parport_pc lp parport loop ipv6 evdev 8250 serial_core ext3 jbd mbcache dm_mirror dm_snapshot dm_mod fuse
[74056.154429] 
[74056.154433] Pid: 10510, comm: stress Not tainted (2.6.24-21-xen #1)
[74056.154438] EIP: 0061:[<c0161083>] EFLAGS: 00010003 CPU: 1
[74056.154452] EIP is at move_freepages+0x93/0xd0
[74056.154455] EAX: 10d81280 EBX: c03fdc94 ECX: c1b6fd38 EDX: 00000010
[74056.154459] ESI: c1d4e9f4 EDI: c1b6fd20 EBP: c1b75fe0 ESP: e9175d28
[74056.154462]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0069
[74056.154466] Process stress (pid: 10510, ti=e9174000 task=ec400750 task.ti=e9174000)
[74056.154471] Stack: 00000010 c03fd800 00000005 c03fd800 c1b6e000 c1b75000 c1b6e000 c016112c 
[74056.154485]        00000002 00000002 00000002 c1b75000 00000000 c03fd800 c016196c c03fddb8 
[74056.154497]        c03fddb8 c03356a0 000005b4 00000010 00000001 00000007 00000000 c1cc7ff8 
[74056.154509] Call Trace:
[74056.154516]  [<c016112c>] move_freepages_block+0x6c/0x90
[74056.154523]  [<c016196c>] __rmqueue+0xec/0x1f0
[74056.154530]  [<c0161aa5>] rmqueue_bulk+0x35/0x70
[74056.154536]  [<c0162bac>] get_page_from_freelist+0x3fc/0x4b0
[74056.154544]  [<c0162d50>] __alloc_pages+0x60/0x390
[74056.154550]  [<c01787cd>] anon_vma_prepare+0x1d/0xe0
[74056.154558]  [<c01659aa>] __pagevec_lru_add_active+0xda/0x100
[74056.154564]  [<c017121c>] handle_mm_fault+0x89c/0x1350
[74056.154570]  [<c012bfb2>] __do_softirq+0x92/0x130
[74056.154576]  [<c0107110>] do_IRQ+0x40/0x70
[74056.154585]  [<c0329356>] do_page_fault+0x366/0xe90
[74056.154592]  [<c0325e0f>] schedule+0x26f/0x640
[74056.154601]  [<c0328ff0>] do_page_fault+0x0/0xe90
[74056.154606]  [<c0327c95>] error_code+0x35/0x40
[74056.154612]  [<c0320000>] vcc_getsockopt+0xb0/0x170
[74056.154618]  =======================
[74056.154620] Code: 74 f0 8d 4f 18 8b 77 0c 8b 57 18 8b 41 04 89 42 04 89 10 6b c6 2c c7 47 18 00 01 10 00 8b 14 24 8d 84 10 80 04 00 00 03 44 24 04 <8b> 50 04 8d 58 04 89 4a 04 89 57 18 89 59 04 89 48 04 89 f1 b8 
[74056.154678] EIP: [<c0161083>] move_freepages+0x93/0xd0 SS:ESP 0069:e9175d28
[74056.154687] ---[ end trace e7683d4a49761ce4 ]---
```

Thanks for your help !

---

### Post by promodus on 2008-10-21
Some hardware details, if you mind. motherboard, chipset, network card...

---

### Post by GoBieN on 2008-10-22
Another one, this one happend without me trying to trigger it:
```
[20001.141696] BUG: unable to handle kernel paging request at virtual address 0a05857c
[20001.141709] printing eip: c0161083
[20001.141713] 1e841000 -> *pde = 00000000:bf01d027
[20001.141716] 1fe74000 -> *pme = 00000000:00000000
[20001.141721] Oops: 0000 [#1] SMP 
[20001.141726] Modules linked in: nfnetlink_queue nfnetlink nf_conntrack_ipv4 ipt_REJECT xt_mark xt_tcpudp ipt_iprange xt_state nf_conntrack xt_NFQUEUE iptable_filter ip_tables x_tables parport_pc lp parport loop ipv6 evdev 8250 serial_core ext3 jbd mbcache dm_mirror dm_snapshot dm_mod fuse
[20001.141784] 
[20001.141792] Pid: 14532, comm: xe-update-guest Not tainted (2.6.24-21-xen #1)
[20001.141802] EIP: 0061:[<c0161083>] EFLAGS: 00010007 CPU: 1
[20001.141815] EIP is at move_freepages+0x93/0xd0
[20001.141823] EAX: 0a058578 EBX: c03fdcb8 ECX: c1ad5398 EDX: 00000008
[20001.141827] ESI: c1ad3834 EDI: c1ad5380 EBP: c1adafe0 ESP: ddde9dfc
[20001.141836]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0069
[20001.141845] Process xe-update-guest (pid: 14532, ti=ddde8000 task=deaa2610 task.ti=ddde8000)
[20001.141855] Stack: 00000008 c03fd800 0000000c c03fd800 c1ad3000 c1ad3900 c1ad3000 c016112c 
[20001.141880]        00000001 00000001 00000001 c1ad3900 00000000 c03fd800 c016196c c03fdcb0 
[20001.141898]        c03fdcb0 c0335690 000004ac 00000008 00000001 00000001 00000000 c1afd0b8 
[20001.141911] Call Trace:
[20001.141923]  [<c016112c>] move_freepages_block+0x6c/0x90
[20001.141935]  [<c016196c>] __rmqueue+0xec/0x1f0
[20001.141947]  [<c0161aa5>] rmqueue_bulk+0x35/0x70
[20001.141957]  [<c0162bac>] get_page_from_freelist+0x3fc/0x4b0
[20001.141975]  [<c0162d50>] __alloc_pages+0x60/0x390
[20001.141986]  [<c01630b7>] __get_free_pages+0x37/0x50
[20001.141994]  [<c01c0989>] proc_file_read+0x79/0x2d0
[20001.142006]  [<c01c0910>] proc_file_read+0x0/0x2d0
[20001.142015]  [<c01bc473>] proc_reg_read+0x63/0xa0
[20001.142027]  [<c01bc410>] proc_reg_read+0x0/0xa0
[20001.142038]  [<c0185cd7>] vfs_read+0xb7/0x170
[20001.142049]  [<c0186231>] sys_read+0x41/0x70
[20001.142060]  [<c0105832>] syscall_call+0x7/0xb
[20001.142066]  =======================
[20001.142069] Code: 74 f0 8d 4f 18 8b 77 0c 8b 57 18 8b 41 04 89 42 04 89 10 6b c6 2c c7 47 18 00 01 10 00 8b 14 24 8d 84 10 80 04 00 00 03 44 24 04 <8b> 50 04 8d 58 04 89 4a 04 89 57 18 89 59 04 89 48 04 89 f1 b8 
[20001.142131] EIP: [<c0161083>] move_freepages+0x93/0xd0 SS:ESP 0069:ddde9dfc
[20001.142140] ---[ end trace 2f32b21274d4c500 ]---
```

Hardware of the Ubuntu VM, is virtual hardware:
**Intel(R) Core(TM)2 Quad CPU Q9300 @ 2.50GHz**
**Kernel Version	2.6.24-21-xen (SMP)**
[B]/	ext3	/dev/mapper/hercules-root	
/boot	ext3	/dev/xvda1[/B]
The rest is al standard Xen hardware, i don't know how to tell you more.

The VM is running in PV (not HVM) virtualisation mode.

The real physical XenServer hardware is:
Asus P5Q -> Intel P45, Intel ICH10R
Intel Core 2 Quad Q9300
4GB DDR2-800 Kingston ValueRam
750 GB SATA-2 HD @ RAID 1
LSI SCSI controller: Ultrium1 + DAT40 tape drive.

Hope this is enough information. Btw, the other windows 2003 VM is running stable as a rock.

---

### Post by Robstarusa on 2008-10-22
If you boot off the ubuntu CD and do a memtest for 24 hours, does it pass?

I had an OpenBSD router a while ago that had a pentium pro-200 in it with 128M 72 pin simms and it would kernel panic ~ once every 1-2 months.  I eventually got a second box & replaced it.

The original ppro box I then ran memtest on it and it found a single bit error in one of the simms.  I replaced it, put it back in production and haven't had a problem since.

---

### Post by GoBieN on 2008-10-24
This is a Virtual Machine, surely the other VM's would crash to ?

---

### Post by linuxpenguin on 2008-10-24
I may not be digging deep enough. . . but I think your problem is right there on the first line:
```
BUG: unable to handle kernel paging request at virtual address 10d81284

```
I'm pretty sure that means it tried to page that address and couldn't do it for whatever reason.  My guess would be either that the VM (or something else) is somehow not letting the kernel have access to memory it wants, or your swap partitions aren't set up right (or aren't set up at all) and the kernel is trying to swap.

Could be bad memory too like the other guy said.  If it's only bad in certain spots, then it might not affect anything else at all.

---

### Post by GoBieN on 2008-10-26
Hmm i will try the memory tests, if someone knows about one that can run live, that would be great ;)

Ps: Here some more panics, from this week:
```
[186569.824336] BUG: soft lockup - CPU#0 stuck for 11s! [kswapd0:103]
[186603.539724] BUG: soft lockup - CPU#1 stuck for 11s! [rm:23344]
[186581.638242] BUG: soft lockup - CPU#0 stuck for 11s! [kswapd0:103]
[186615.353704] BUG: soft lockup - CPU#1 stuck for 11s! [rm:23344]
[186593.452259] BUG: soft lockup - CPU#0 stuck for 11s! [kswapd0:103]
[186627.163722] BUG: soft lockup - CPU#1 stuck for 11s! [rm:23344]
[186605.262264] BUG: soft lockup - CPU#0 stuck for 11s! [kswapd0:103]
[186638.977822] BUG: soft lockup - CPU#1 stuck for 11s! [rm:23344]
[186617.076274] BUG: soft lockup - CPU#0 stuck for 11s! [kswapd0:103]
[186650.788002] BUG: soft lockup - CPU#1 stuck for 11s! [rm:23344]
[186628.885542] BUG: soft lockup - CPU#0 stuck for 11s! [kswapd0:103]

``````

[147995.683778] BUG: soft lockup - CPU#1 stuck for 11s! [pis|Bot.botchk:17437]
[147995.683787] 
[147995.683790] Pid: 17437, comm: pis|Bot.botchk Tainted: G      D (2.6.24-21-xen #1)
[147995.683795] EIP: 0061:[<c03277ba>] EFLAGS: 00000282 CPU: 1
[147995.683802] EIP is at _spin_lock+0xa/0x10
[147995.683805] EAX: c1afff2c EBX: 00000000 ECX: 1fe79000 EDX: 00000000
[147995.683813] ESI: be338067 EDI: c1afff2c EBP: dfe79dd8 ESP: df6bde44
[147995.683817]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0069
[147995.683825] CR0: 8005003b CR2: b7dbb6fc CR3: 1e9a9000 CR4: 00002620
[147995.683834] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[147995.683839] DR6: ffff0ff0 DR7: 00000400
[147995.683846]  [<c0170c81>] handle_mm_fault+0x301/0x1350
[147995.683869]  [<c0107ec5>] local_clock+0x55/0xa0
[147995.683881]  [<c0329356>] do_page_fault+0x366/0xe90
[147995.683898]  [<c0121de5>] finish_task_switch+0x75/0xa0
[147995.683910]  [<c0325e0f>] schedule+0x26f/0x640
[147995.683922]  [<c0210830>] copy_to_user+0x30/0x60
[147995.683935]  [<c0103226>] sys_clone+0x36/0x40
[147995.683945]  [<c0328ff0>] do_page_fault+0x0/0xe90
[147995.683956]  [<c0327c95>] error_code+0x35/0x40
[147995.683967]  [<c0320000>] vcc_getsockopt+0xb0/0x170
[147995.683978]  =======================
```

---

### Post by GoBieN on 2008-10-26
Can i have some more information on SWAP.
Should i be able to see the SWAP when i list all mounted devices with the command "mount" ?

If i use mount i see this:
```

/dev/mapper/hercules-root on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/xvda1 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)

```
My root and swap are on LVM partitions.
But when i look in phpsysinfo i see this:
```
Memory Usage
Type	Usage	Free	Used	Size
**Physical Memory **  47%	266.7 MB	239.01 MB	505.71 MB
- Kernel + applications	 23%		118.43 MB	
- Buffers	 5%		25.26 MB	
- Cached	 19%		95.32 MB	
**Disk Swap** 0%	1.51 GB	0 KB	1.51 GB
```
Thanks for helping me to solve this.
I really want to stay with Ubuntu as I have for all these years so far even tough it's not officially supported on XenServer.
Only Debian, Centos and Redhat are. But since Ubuntu is debian based i tought i wouldn't be a problem.

---

### Post by linuxpenguin on 2008-10-26
I'm sorry I can't be a whole ton of help since I've no experience with virtual machines. . . but on a regular physical setup, yes, the swap partition does show up when you use the "mount" command.

It'll look something like this:
```
/dev/sdb3 on swap
```
where /dev/sdb3 is your swap partition.

If you have a swap partition formatted already, you can make it mount at boot by adding it to your /etc/fstab file (just put "swap" as the mountpoint instead of an actual directory name).

If you don't have one you should set it up just in case your system ever does need it.  You do that just like you'd create any other partition - "Linux swap" is its own partition type.

---

### Post by GoBieN on 2008-10-27
```
[12717.128901] BUG: unable to handle kernel paging request at virtual address 0a3aa704
[12717.128914] printing eip: c0161083
[12717.128919] 13e5d000 -> *pde = 00000001:0eeee027
[12717.128922] 14169000 -> *pme = 00000000:00000000
[12717.128927] Oops: 0000 [#1] SMP 
[12717.128931] Modules linked in: nfnetlink_queue nfnetlink nf_conntrack_ipv4 ipt_REJECT xt_mark xt_tcpudp ipt_iprange xt_state nf_conntrack xt_NFQUEUE iptable_filter ip_tables x_tables parport_pc lp parport loop ipv6 evdev 8250 serial_core ext3 jbd mbcache dm_mirror dm_snapshot dm_mod fuse
[12717.128969] 
[12717.128971] Pid: 10391, comm: xe-update-guest Not tainted (2.6.24-21-xen #1)
[12717.128976] EIP: 0061:[<c0161083>] EFLAGS: 00010007 CPU: 0
[12717.128984] EIP is at move_freepages+0x93/0xd0
[12717.128987] EAX: 0a3aa700 EBX: c03fdc94 ECX: c196e9d8 EDX: 00000010
[12717.128991] ESI: c1ae6d54 EDI: c196e9c0 EBP: c1972fe0 ESP: d36a5cc4
[12717.128994]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0069
[12717.128998] Process xe-update-guest (pid: 10391, ti=d36a4000 task=d37297f0 task.ti=d36a4000)
[12717.129002] Stack: 00000010 c03fd800 00000058 c03fd800 c196b000 c1971800 c196b000 c016112c 
[12717.129014]        00000002 00000002 00000002 c1971800 00000000 c03fd800 c016196c c03fdd60 
[12717.129026]        c03fdd60 c03356a0 0000055c 00000000 00000000 00000005 00000000 c03fd88c 
[12717.129039] Call Trace:
[12717.129044]  [<c016112c>] move_freepages_block+0x6c/0x90
[12717.129051]  [<c016196c>] __rmqueue+0xec/0x1f0
[12717.129057]  [<c0161aa5>] rmqueue_bulk+0x35/0x70
[12717.129063]  [<c0162bac>] get_page_from_freelist+0x3fc/0x4b0
[12717.129070]  [<c0162d50>] __alloc_pages+0x60/0x390
[12717.129076]  [<c01787cd>] anon_vma_prepare+0x1d/0xe0
[12717.129083]  [<c016bfdf>] do_wp_page+0xbf/0x9f0
[12717.129090]  [<c017151a>] handle_mm_fault+0xb9a/0x1350
[12717.129099]  [<c0329356>] do_page_fault+0x366/0xe90
[12717.129107]  [<c0185bce>] vfs_write+0x11e/0x170
[12717.129113]  [<c01862a1>] sys_write+0x41/0x70
[12717.129118]  [<c0328ff0>] do_page_fault+
```
And another panic, i added an option to reboot on panic to systcvl.conf (or something like that) but it didn't reboot !

Also here is my fstab:
```
root@hercules:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/hercules-root
UUID=cc4044e8-792a-4e16-8d11-1cf93209bcdb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=94218f37-e132-4445-bbfb-f53427529b62 /boot           ext3    relatime        0       2
# /dev/mapper/hercules-swap_1
UUID=5822ede5-3920-4d89-b546-321df402c5cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//w2003r2/torrentflux/mnt/torrentflux cifs defaults,rw,noauto,username=share,password=sharedelen,uid=1000,gid=100 0 0
root@hercules:~# 
```

So my fstab looks normal ?

---

### Post by GoBieN on 2008-10-27
Maybe this is useful information.

Even since i started with FreeBSD 6 years ago, i liked **aee**as my console text editor. In Ubuntu i alwaus use it to, next to nano sometimes.

Now on this VM i have trouble using aee, i get this error almost every time.
> root@hercules:~# aee /path/to/some/file
**Segmentation fault**

Does anyone know why this happens, is this related ?

edit: I just now discovered that when this happens, i get this information in /var/log/messages
> Oct 27 22:51:34 hercules kernel: [ 7802.492489] aee[8183]: segfault at 00000000 eip 080673da esp bfc934d0 error 6
Oct 27 22:54:04 hercules kernel: [ 7952.664853] aee[8281]: segfault at 00000000 eip 080673da esp bfab92f0 error 6

I think this adds up to theory of faulty memory, am I right ?

Going to do overnight memtesting.

---

### Post by linuxpenguin on 2008-10-27
I think you meant /etc/sysctl.conf. . . that file should have already been there with quite a bit in it (although most of it's commented out).

Memory definitely seems quite possible but did you confirm that your swap partition is getting mounted?  Also the swapon/swapoff commands tell your computer to either use swap or not.  You might need to use swapon to tell the system to use swap.

Also. . . has this been happening ever since you set it up or is this something where it's been running fine for a few weeks and just broke?  If it's been doing it, maybe it's a glitch in a module or something.  If you haven't touched it and it just started happening though. . . probably the memory.

---

### Post by promodus on 2008-10-28
[http://www.google.ca/search?q=xen+BUG:+soft+lockup+-+CPU%230+stuck+for&start=10&sa=N](http://www.google.ca/search?q=xen+BUG:+soft+lockup+-+CPU%230+stuck+for&start=10&sa=N)

You're not the only one with that error. 

I would suggest going with ECC memory for server applications where uptime is a priority. One [bit flip]("http://h20271.www2.hp.com/SMB-AP/cache/301687-0-0-155-121.html") is all it takes...

---

### Post by GoBieN on 2008-10-28
Last night I ran an 8-hour memory test, and the test was completely clean ! So i think it's safe to rule out memory.
ECC memory is not an option, the board doesn't support it, this is just consumer hardware because this server is a home-server, not a business server.

This problem is happening ever since i installed Ubuntu in this VM and converted to PV (instead of HVM).

As i posted few posts back, in my /etc/fstab swap is present but not visible. Here another prove.
```
root@hercules:~# cat /etc/fstab | grep swap
# /dev/mapper/hercules-swap_1
UUID=5822ede5-3920-4d89-b546-321df402c5cd none            swap    sw              0       0
root@hercules:~# mount | grep swap
root@hercules:~#

```
I tried with swap-on:
```
root@hercules:~# swapon /dev/mapper/hercules-swap_1
swapon: /dev/mapper/hercules-swap_1: Device or resource busy

```
So my guess, swap is already active, but not shown in mount. Maybe because it's on LVM it is not shown.

Thanks for the link promodus, i will continu reading, but so far it seems the links describe panics on Dom0 (that is the hypervisor itself) i'm having panics on DomU (that is the guest (or VM)).

Any further brainstorming is highly appreciated.

---

### Post by GoBieN on 2008-10-28
After some reading, i decied to change the number of virtual CPU's for this VM guest to 1 instead of 2. So far i have not been able to reproduce the panic. Hoping for the best. I will report back if i still get a panic.

---

