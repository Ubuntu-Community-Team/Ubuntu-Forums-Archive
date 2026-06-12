---
title: "getty causing extreme CPU load"
date: 2014-07-07
forum: Server Platforms
---

### Post by sean50 on 2014-07-07
Hi *,

I run a headless server with Ubuntu 12.04. The other day, I did a kernel upgrade to the latest 3.2.0-65 release, along with some other packages (libvirt for example). After rebooting, the server was unresponsive, meaning that I could ping it, establish a SSH connection but could not login (ssh -vv showed that my key was accepted but it would hang on "starting interactive session").

After a lot of fiddling with a network-booted rescue system I found that plymouthd was causing extreme CPU load, and that slowed the server down so much that I couldn't even log in anymore. After disabling plymouthd and rebooting rsyslogd was now the culprit, again no way to log in. After turning that off as well it seems getty was the problem all along. So what helped was disabling all tty-entries in /etc/init/ (I have no console access anyway to that machine, so that's not a problem). So for now everything's working, but I don't feel comfortable not knowing what the problem really is.

Checking kern.log, I see a flood of these messages (about 1.5GB in a matter of minutes!):

```
tty_release_dev: tty4: read/write wait queue active!
tty_release_dev: tty4: read/write wait queue active!
tty_release_dev: tty4: read/write wait queue active!
```

... with all kinds of different numbered ttys (even tty7, which I didn't have before and never had). So it seems that plymouthd tried to send some console stuff, which failed for some reason, which caused logging to rsyslog, which also tries to send certain log messages to the console by default, which causes even more logging, an endless loop eating up all CPU.

Question is: What is the problem here? This machine has been running perfectly for years, so this is a completely new issue. Unfortunately, I can't at the moment reboot it with the old kernel to see if this is something that was introduced with the kernel update or if it's caused by a different package update... I might have a chance next weekend when nobody's using it.

Right where all that "queue active"-logging starts I can see a getty stack trace in the log:
```

Jul  6 10:56:18 srv02 kernel: [   14.808539] Pid: 1536, comm: getty Tainted: G         C   3.2.0-65-generic #99-Ubuntu System manufacturer System Product Name/P8H67-M PRO
Jul  6 10:56:18 srv02 kernel: [   14.808542] RIP: 0010:[<ffffffff813d6457>]  [<ffffffff813d6457>] csi_J+0x107/0x290
Jul  6 10:56:18 srv02 kernel: [   14.808545] RSP: 0018:ffff8804225d7c88  EFLAGS: 00010246
Jul  6 10:56:18 srv02 kernel: [   14.808547] RAX: 0000000100000010 RBX: 000000010000000e RCX: 0000000100000010
Jul  6 10:56:18 srv02 kernel: [   14.808548] RDX: 0000000000000720 RSI: 0000000000000000 RDI: ffff88042485f400
Jul  6 10:56:18 srv02 kernel: [   14.808550] RBP: ffff8804225d7ca8 R08: 0000000000000000 R09: ffff88042f010400
Jul  6 10:56:18 srv02 kernel: [   14.808551] R10: 00007fff51e5aa90 R11: 0000000000000246 R12: ffff88042485f400
Jul  6 10:56:18 srv02 kernel: [   14.808553] R13: 0000000000000000 R14: 0000000000000009 R15: 00000000ffffffff
Jul  6 10:56:18 srv02 kernel: [   14.808555] FS:  00007f747f7b6700(0000) GS:ffff88043fa00000(0000) knlGS:0000000000000000
Jul  6 10:56:18 srv02 kernel: [   14.808556] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul  6 10:56:18 srv02 kernel: [   14.808558] CR2: 000000010000000e CR3: 000000041c61a000 CR4: 00000000000406f0
Jul  6 10:56:18 srv02 kernel: [   14.808559] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul  6 10:56:18 srv02 kernel: [   14.808561] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul  6 10:56:18 srv02 kernel: [   14.808563] Process getty (pid: 1536, threadinfo ffff8804225d6000, task ffff88041c531700)
Jul  6 10:56:18 srv02 kernel: [   14.808564] Stack:
Jul  6 10:56:18 srv02 kernel: [   14.808565]  ffff8804225d7c98 ffff88042485f400 ffff88042484e000 000000000000004a
Jul  6 10:56:18 srv02 kernel: [   14.808568]  ffff8804225d7cf8 ffffffff813d936d ffff8804225d7ce8 ffff88042485f400
Jul  6 10:56:18 srv02 kernel: [   14.808570]  0000000000000000 000000000000004a 0000000000000009 0000000086f80567
Jul  6 10:56:18 srv02 kernel: [   14.808573] Call Trace:
Jul  6 10:56:18 srv02 kernel: [   14.808576]  [<ffffffff813d936d>] do_con_trol+0xc7d/0xe50
Jul  6 10:56:18 srv02 kernel: [   14.808579]  [<ffffffff813d970e>] do_con_write.part.22+0x1ce/0x9a0
Jul  6 10:56:18 srv02 kernel: [   14.808582]  [<ffffffff813c5f7a>] ? copy_termios+0x6a/0x80
Jul  6 10:56:18 srv02 kernel: [   14.808585]  [<ffffffff813d9f57>] con_write+0x37/0x50
Jul  6 10:56:18 srv02 kernel: [   14.808587]  [<ffffffff813c2add>] process_output_block+0xad/0x1c0
Jul  6 10:56:18 srv02 kernel: [   14.808589]  [<ffffffff813c36a0>] n_tty_write+0x160/0x310
Jul  6 10:56:18 srv02 kernel: [   14.808593]  [<ffffffff81060ad0>] ? try_to_wake_up+0x200/0x200
Jul  6 10:56:18 srv02 kernel: [   14.808596]  [<ffffffff813c00ad>] tty_write+0x15d/0x2c0
Jul  6 10:56:18 srv02 kernel: [   14.808600]  [<ffffffff812dc258>] ? apparmor_file_permission+0x18/0x20
Jul  6 10:56:18 srv02 kernel: [   14.808602]  [<ffffffff813c3540>] ? process_echoes+0x30/0x30
Jul  6 10:56:18 srv02 kernel: [   14.808605]  [<ffffffff8117b273>] vfs_write+0xb3/0x180
Jul  6 10:56:18 srv02 kernel: [   14.808607]  [<ffffffff8117b59a>] sys_write+0x4a/0x90
Jul  6 10:56:18 srv02 kernel: [   14.808611]  [<ffffffff8166bc82>] system_call_fastpath+0x16/0x1b
Jul  6 10:56:18 srv02 kernel: [   14.808612] Code: 00 00 00 00 41 81 e5 ff ff ff 7f 41 0f b7 94 24 68 01 00 00 74 1d 48 8d 43 02 41 83 ed 01 4a 8d 0c 68 eb 04 48 83 c0 02 48 39 c8 <66> 89 13 48 89 c3 75 f1 41 80 a4 24 ea 01 00 00 7f 48 83 c4 08
Jul  6 10:56:18 srv02 kernel: [   14.808629] RIP  [<ffffffff813d6457>] csi_J+0x107/0x290
Jul  6 10:56:18 srv02 kernel: [   14.808631]  RSP <ffff8804225d7c88>
Jul  6 10:56:18 srv02 kernel: [   14.808632] CR2: 000000010000000e
Jul  6 10:56:18 srv02 kernel: [   14.808634] ---[ end trace 9ac2ffa22ff9b185 ]---

```

Has anyone ever seen this? I googled a lot, and found a few people with the same problem, but noone had an answer as to what is the problem or how one can reliably fix it. Most of these posts were also several years old (some over a decade), so no idea how relevant anything there could be anymore.

Greetings,
Sean

---

### Post by alexey8 on 2014-08-04
Hello dear ubuntus : )

I have the same problem and not resolve it yet.
Prehistory - my server work pretty fine about a year or more... but yesterday Hetzner DC19 had power failure. And "tada" we don't boot anymore.
What I have?

I can login via resue system (like liveCD) and mount / chroot my system.
All files read ok I can change any config, but right now I don't find a conclusion.

---

### Post by buzz_lightyear2 on 2014-08-05
> **alexey8 said:**
> Hello dear ubuntus : )

I have the same problem and not resolve it yet.
Prehistory - my server work pretty fine about a year or more... but yesterday Hetzner DC19 had power failure. And "tada" we don't boot anymore.
What I have?

I can login via resue system (like liveCD) and mount / chroot my system.
All files read ok I can change any config, but right now I don't find a conclusion.

Hi guys,
today after apt-get update/upgrade i have rebooted my 12.04 server (hetzner DC13) and i have the same problem.
Trying to fix it since couple of hours, but nothing helps.

Did you have any progress with this problem?

thanx
Buzz

---

### Post by g-info-8 on 2014-08-07
Hi

I had the same problem and came up with a solution:

Boot into the live/recovery system and chroot into your current system (for hetzner see here: [http://wiki.hetzner.de/index.php/Hetzner_Rescue-System](http://wiki.hetzner.de/index.php/Hetzner_Rescue-System)) and run:

```
apt-get install ngetty
```


ngetty replaces the default getty, after that, everthing worked fine.

Hope it will help you too.

---

### Post by buzz_lightyear2 on 2014-08-07
Hi g-info,
thanx a lot, but after playing with it for 2 days, i found out easier (ehm) to do a clean install and restore data from backup.
That took about 1 hour.

Unfortunately, as my server is up and running again, i am not able to confirm, if it would help me, to install ngetty.

Many thanxs for help anyway. I believe, it will help some other people.
take care
buzz

---

