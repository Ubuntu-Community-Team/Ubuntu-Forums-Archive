---
title: "server slowdown"
date: 2010-04-03
forum: Server Platforms
---

### Post by waspinator on 2010-04-03
Hi,

I have ubuntu 9.10 server installed to use as a simple home server. All it has is samba file sharing and some other small things running. It worked without any problems since October, but starting about last week it starts to slow down about half an hour after it boots to a crawl. At midday I cannot access any samba shares, and in the evening I can't even SSH to it anymore. If I hook up a screen and keyboard to it, it takes 5 min just to log on. When I run htop though everything looks fine. I have 160 processes, 1 running, no zombies, and my memory and cpu loads look fine. Rebooting it makes it go fast again, but only for a short while. I have no idea how to properly look at log files; I tried to open var/logs/syslog with nano but it couldn't handle 4+ GB worth of log data. (BTW why do my log files get so huge?; My server wouldn't start properly once because it ran out of disk space due to the huge log files!) What's going on with my server?


**Memory**
166 MB used 
112 MB buffers 
192 MB cached 

**CPUS**
1 3 %
2 0 %
3 1 %
4 0 %


Thanks,

Waspinator

---

### Post by CharlesA on 2010-04-03
Does it have a GUI?

160 processes seems a bit excessive.

Is SSH secured properly?

---

### Post by KB1JWQ on 2010-04-03
Set up logrotate. Tail -f the logfile. Report back!

---

### Post by HermanAB on 2010-04-04
Well, the log files are there for you to read to see what is going on.  The best way to read them is with tail, eg:
tail -f /var/log/whatever.log

As mentioned above, use logrotate to truncate the files and create new ones every week.  See /etc/logrotate.conf for details.

---

### Post by waspinator on 2010-04-04
Thanks for the tips on reading log files. I just booted my server and tailed the last 1000 lines of my syslog and it looks like there is a repeating part every 10-20 seconds.

btw I have no X server. I just use byobu, htop and nano, and I log in through ssh.

looks like a problem with my file system. What can I do to fix it? fsck ran when I booted it up but it didn't seem to do much.

In the future is using ext3/2 or something else better?

Thanks,

Waspinator

```

Apr  4 07:55:50 server kernel: [  495.001647] ------------[ cut here ]------------
Apr  4 07:55:50 server kernel: [  495.001658] WARNING: at /build/buildd/linux-2.6.31/fs/quota/dquot.c:964 dquot_claim_space+0x84/0x130()
Apr  4 07:55:50 server kernel: [  495.001666] Hardware name:
Apr  4 07:55:50 server kernel: [  495.001672] Modules linked in: xt_mac xt_MARK xt_mark nf_conntrack_ipv4 nf_defrag_ipv4 xt_CONNMARK nf_conntrack iptable_mangle $
Apr  4 07:55:50 server kernel: [  495.001789] Pid: 46, comm: pdflush Tainted: G        W  2.6.31-14-generic-pae #48-Ubuntu
Apr  4 07:55:50 server kernel: [  495.001797] Call Trace:
Apr  4 07:55:50 server kernel: [  495.001808]  [<c0146a1d>] warn_slowpath_common+0x6d/0xa0
Apr  4 07:55:50 server kernel: [  495.001821]  [<c0228fb4>] ? dquot_claim_space+0x84/0x130
Apr  4 07:55:50 server kernel: [  495.001832]  [<c0228fb4>] ? dquot_claim_space+0x84/0x130
Apr  4 07:55:50 server kernel: [  495.001844]  [<c0146a65>] warn_slowpath_null+0x15/0x20
Apr  4 07:55:50 server kernel: [  495.001855]  [<c0228fb4>] dquot_claim_space+0x84/0x130
Apr  4 07:55:50 server kernel: [  495.001868]  [<c028ee53>] ext4_mb_mark_diskspace_used+0x363/0x3b0
Apr  4 07:55:50 server kernel: [  495.001880]  [<c0288bfe>] ? ext4_mb_use_preallocated+0x21e/0x230
Apr  4 07:55:50 server kernel: [  495.001893]  [<c028f19e>] ext4_mb_new_blocks+0x2fe/0x570
Apr  4 07:55:50 server kernel: [  495.001905]  [<c02851af>] ? ext4_ext_find_extent+0xff/0x280
Apr  4 07:55:50 server kernel: [  495.001917]  [<c02871ba>] ext4_ext_get_blocks+0x44a/0x540
Apr  4 07:55:50 server kernel: [  495.001930]  [<c0268cd6>] ext4_get_blocks+0x1d6/0x200
Apr  4 07:55:50 server kernel: [  495.001943]  [<c0269254>] mpage_da_map_blocks+0x94/0x400
Apr  4 07:55:50 server kernel: [  495.001956]  [<c029c2d3>] ? jbd2_journal_start+0x93/0xd0
Apr  4 07:55:50 server kernel: [  495.001968]  [<c026980e>] ext4_da_writepages+0x24e/0x490
Apr  4 07:55:50 server kernel: [  495.001980]  [<c013bf57>] ? find_busiest_group+0x1b7/0x6e0
Apr  4 07:55:50 server kernel: [  495.001995]  [<c01bc501>] do_writepages+0x21/0x40
Apr  4 07:55:50 server kernel: [  495.002006]  [<c0206bbe>] writeback_single_inode+0x16e/0x3d0
Apr  4 07:55:50 server kernel: [  495.002019]  [<c01407f6>] ? load_balance_newidle+0x96/0x330
Apr  4 07:55:50 server kernel: [  495.002031]  [<c02072bd>] generic_sync_sb_inodes+0x38d/0x4a0
Apr  4 07:55:50 server kernel: [  495.002043]  [<c02074ad>] writeback_inodes+0x4d/0xe0
Apr  4 07:55:50 server kernel: [  495.002055]  [<c01bb3e2>] wb_kupdate+0xa2/0x110
Apr  4 07:55:50 server kernel: [  495.002067]  [<c01bcbd7>] __pdflush+0xf7/0x1f0
Apr  4 07:55:50 server kernel: [  495.002078]  [<c01bccd0>] ? pdflush+0x0/0x40
Apr  4 07:55:50 server kernel: [  495.002090]  [<c01bccd0>] ? pdflush+0x0/0x40
Apr  4 07:55:50 server kernel: [  495.002101]  [<c01bcd09>] pdflush+0x39/0x40
Apr  4 07:55:50 server kernel: [  495.002112]  [<c01bb340>] ? wb_kupdate+0x0/0x110
Apr  4 07:55:50 server kernel: [  495.002124]  [<c015deac>] kthread+0x7c/0x90
Apr  4 07:55:50 server kernel: [  495.002135]  [<c015de30>] ? kthread+0x0/0x90
Apr  4 07:55:50 server kernel: [  495.002147]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  4 07:55:50 server kernel: [  495.002155] ---[ end trace 65676136a26f800f ]---
Apr  4 07:56:00 server kernel: [  505.000110] ------------[ cut here ]------------


```


EDIT:

I found this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442799") and it looks like it's something to due with quotas, but I don't want to mess with anything yet. I'm using eBox to administrate it if that matters.

---

### Post by waspinator on 2010-04-05
anyone have any ideas? I miss my server, and April 29 seems so far away.

Thanks,

Waspinator

---

### Post by Sporkman on 2010-04-06
Does the server nfs-mount (as a client) any external directories? I've noticed that if my laptop nfs-mounts an external directory from a server which is no longer responsive, it tends to just drag along or even hang which it tries to obtain the directory or something.

---

### Post by waspinator on 2010-04-07
No, my server doesn't connect to any other file shares. I get that freezing behavior on my clients as well if my server goes offline. 

I think this all started after a power failure I had. fsck seems to run at startup but doesn't do much. And then I get that message repeating every 10-20 seconds. Is there a more thorough way of checking my file system?

Thanks,

Waspinator

---

### Post by KB1JWQ on 2010-04-07
Assuming that your drives are fine (smart can help with this), I'd talk to the ebox folks.  I have no insight into how various point and click admin tools do things.

---

### Post by ian dobson on 2010-04-07
Hi,

I would try booting in single user mode and run a "fsck -f" for all your file systems. The dmesg looks like a warning from the ext4 file system, it could be corruption.

Regards
Ian Dobson

---

### Post by waspinator on 2010-04-10
I ran a short smartctl  test and it completed without errors.

I can't seem to figure out how to get to single user mode. When I boot my server all I see is a message that says "GRUB is Loading" and then it starst up. I have tried to hit the Esc key and hold down the Shift key during bootup and the "GRUB is Loading" message but it doesn't do anything. I think I'm using Grub 1.97 if that matters (whatever comes with ubuntu 9.10 server).

Thanks,

Waspinator

---

### Post by ian dobson on 2010-04-11
Hi,

When grub loads, it usually displays a count down 3,2,1,0 before it loads the default kernel. You need to press escape during this countdown.

If that doesn't work (maybe the countdown is set to 1 second), you'll have to edit your /boot/grub/menu.lst and increase the timout or if the worst comes to the worst just edit the default kernel boot line to read "ro single"

Something like:-
kernel      /boot/vmlinuz-2.6.31-20-generic root=/dev/md0 ro single

don't change the root=/dev/whatever part, this line is from my server and I boot from a RAID partition.

The timeout options is also in the menu.list file:-
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3


Hope this helps
Regards
Ian Dobson

---

### Post by CharlesA on 2010-04-11
Grub 2 hides the GRUB menu by default. You can hold down left shift (I think) to get it to show the menu.

There is no menu.lst in Grub2.

You could also try booting from LiveCD and doing a fsck from there.

---

### Post by waspinator on 2010-04-11
Since I'm using Grub 2, and there is no menu.lst, how do I change the timeout for grub? I tried holding down shift, but that didn't work. My server does not have an optical drive, so trying to boot off a CD would be a last resort. 

There has to be some easy way of editing GRUB 2, and getting into single user mode. 

Thanks,

Waspinator

---

### Post by waspinator on 2010-04-11
Ok, so I got into 'recovery mode' which I think is single user mode. I'm logged in as 'root'. To get it I changed the grub timeout (GRUB_HIDDEN_TIMEOUT=0 --> GRUB_HIDDEN_TIMEOUT=10; GRUB_HIDDEN_TIMEOUT_QUIET=true
 --> GRUB_HIDDEN_TIMEOUT_QUIET=false) in /etc/default/grub and ran update-grub

When I run fsck it scares me with this message:

WARNING!!! Runing e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Do you really want to contiune(y/n)?


If I try to umount /dev/sda1 it says that the device is busy.

What should I do?

---

### Post by CharlesA on 2010-04-12
The FS is mounted in recovery mode. You need to boot from a livecd or liveusb to run the FSCK.

I'd suggest a liveUSB, since there isn't an optical drive on the server.

Or you can run "touch /forcefsck" then reboot and see what happens.

---

### Post by waspinator on 2010-04-12
Ok, I booted to a livecd version of Ubuntu 9.10 desktop. I ran e2fsck (also tried just fsck but I think they're the same thing) on /dev/sda1 , /dev/sda2. and /dev/sda3, and they all finish in about a second and say that they're 'clean'. 

The exact command I'm running is
```
sudo e2fsck -y /dev/sda1 
```
( -y for automaitic fixing as per the man page)

Am I doing that correctly? Shouldn't it take more than a second to run?

Thanks,

Waspinator

---

### Post by CharlesA on 2010-04-13
Use the -f switch to force a fsck.

Example:

fsck -f /dev/sda1

I use the -C switch so that I can keep an eye on the progress of the fsck.

---

### Post by waspinator on 2010-04-14
Ok I finally got fsck to do something with the -f switch. I tried the -y switch too. It took a bit longer this time, but it didn't look like it found/fixed anything.

I'm still getting the same warning in the syslog every 10-20 seconds.

After a week of fiddling I didn't really do much besides get fsck to work. At this point there is only about 2 weeks left before 10.04, but I still would like to know how to fix these types of problems just in case it happends again in May. But alas this problem is probably to obscure to fix. 

Thanks everyone for all your help.

Waspinator

---

