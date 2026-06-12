---
title: "LXLE (Dual Boot Windows 10) - Soft lockup causes long/infinite boot time"
date: 2022-12-18
forum: Ubuntu/Debian BASED
---

### Post by pgslmatias on 2022-12-18
When booting my computer yesterday, it took about 5 minutes to boot which was unusually long. There were some error messages I ignored and after some time the computer booted normally and everything was fine, it had an uptime
of a few hours and no problem happened. I shut it down, and today when booting the computer, the same thing happened: long boot time with error messages. I took pictures of the output and this is the result of a scan of one of the pictures. It is mostly accurate: some timestamps are a few miliseconds off, but I read through it and it seems ok.

```
[0.978425] integrity: Problem X.509 [56.448381] watchdog: BUG: soft lockup CPU#4 stuck for 22s! [systemd-udevd:210]

[96.500983) watchdog: BUG: soft lockup - CPU#4 stuck for 22s! [systemd-udevd:210]

[105.467429] rcu: INFO: rcu_sched detected stalls on CPUs/tasks:

[105.467464] rcu: $4-....: (118 ticks this GP) idle=b06/1/0x4000000000000000 softirq=136/136 fqs=543

[132.568604] watchdog: BUG: soft lockup CPU#4 stuck for 22s! [systemd-udevd:210]

[152.606178] watchdog: BUG: soft lockup CPU#1 stuck for 23s! [setfont:269]

[160.621207] watchdog: BUG: soft lockup CPU#4 stuck for 22s! [systemd-udevd:210]

[159.119444] NMI watchdog: Watchdog detected hard LOCKUP on cpu 3

[180.658783] watchdog: BUG: soft lockup CPU#1 stuck for 23s [setfont:269]

[188.673810] watchdog: BUG: soft lockup CPU#4 stuck for 22s!  [systemd-udevd:210]

[188.673893] watchdog: BUG: soft lockup CPU#3 stuck for 26s! [swapper/3:0]

[208.711384] watchdog: BUG: soft lockup CPU#1 stuck for 23s! [setfont:269]

[216.726411] watchdog: BUG: soft lockup CPU#4 stuck for 22s! [systemd-udevd:210]

[228.749026] [drm:atom_op_jump [amdgpu]] *ERROR* atombios stuck in loop for more than 10secs aborting

[228.749094] [drm: amdgpu_atom_execute_table_locked [amdgpu]] *ERROR* atombios stuck executing A4DE (len 84, HS 0, PS 0) @ 0xA514

[228.749160] [drm: amdgpu_atom_execute_table_locked [amdgpu]] *ERROR* atombios stuck executing D078 (len 525, WS 0, PS 0) @ OXD0E9

[244.779015] watchdog: BUG: soft lockup CPU#4 stuck for 22s! [systemd-udevd: 210]

[268.824100] watchdog: BUG: soft lockup CPU#1 stuck for 22s! [setfont:269]

[272.831622] watchdog: BUG: soft lockup CPU#4 stuck for 23s! [systemd-udevd:210]

[285.418582] rcu: INFO: rcu_sched self-detected stall on CPU

[285.418582] rcu: $4-... (480 ticks this GP) idle-b06/1/0x4000000000000002 soft irq-136/136 fqs=756

[312.405830] watchdog: BUG: soft lockup - CPU#4 stuck for 21s! [systemd-udevd:210]

[340.458441] watchdog: BUG: soft lockup CPU#4 stuck for 23s! [systemd-udevd:210]

[dev/nvme0n1p5: clean, 232418/6537216 files, 3640527/26133248 blocks

[368.511037] watchdog: BUG: soft lockup CPU#4 stuck for 23s! [systemd-udevd: 210]

[396.563646] watchdog: BUG: soft lockup CPU#4 stuck for 23s! [systemd-udevd:210]

[424.616240] watchdog: BUG: soft lockup CPU#4 stuck for 22s! [systemd-udevd: 210]

[452.668842] watchdog: BUG: soft lockup CPU#4 stuck for 22s! [systemd-udevd: 210]

[465.697255] rcu: INFO: rcu_sched self-detected stall on CPU

[465.697255] rcu: $4-....: (843 ticks this GP) idle-b06/1/0x4000000000000002 soft irq=136/136 fqs=1116

[484.729160] INFO: task kworker/3:1:75 blocked for more than 120 seconds.

[484.729193]           Tainted: G                    L      5.4.0-113-generic #127-Ubuntu

[484.729220] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

[492.744149] watchdog: BUG: soft lockup CPU#4 stuck for 22s! [systemd-udevd:210]

[520.796595] watchdog: BUG: soft lockup CPU#4 stuck for 23s! [systemd-udevd: 210]

[548.849336] watchdog: BUG: soft lockup CPU#4 stuck for 23s! [systemd-udevd:210]

[576.400982] watchdog: BUG: soft lockup CPU#4 stuck for 22s! [systemd-udevd: 210]

[604.453462] watchdog: BUG: soft lockup CPU#4 stuck for 22s! [systemd-udevd:210]

[605.455471] INFO: task kworker/3:1:75 blocked for more than 241 seconds.

[605.455528]          Tainted: G                     L      5.4.0-113-generic #127-Ubuntu

[605.455581] "echo 0> /proc/sys/kernel/hung_task_timeout_secs" disables this message.

[632.506063] watchdog: BUG: soft lockup CPU#4 stuck for 23s! [systemd-udevd:210]

[646.035424] rcu: INFO: rcu_sched self-detected stall on CPU

[646.532368] rcu: $4-....: (1209 ticks this GP) idle=b06/1/0x4000000000000002 softirq=136/136 fqs=1369
```

This is a link to the picture I took: [0] [https://imgur.com/a/E7WBjAh](https://imgur.com/a/E7WBjAh)

These error messages kept popping up: I waited for about 15 minutes and today the computer wouldn't boot. I shut off the machine.

I googled around in another device and found a few people with the same behaviour. It seems like every case is different but this is a low level bug, which might be caused by the kernel version, graphics drivers, low swap memory... 
A lot of people seem to have this bug while using their computer, but for me it only happened these 2 times and it was from a cold start.

From [https://unix.stackexchange.com/questions/668232/watchdog-bug-soft-lockup-cpu0-stuck-when-booting-arch-linux-on-minisforum](https://unix.stackexchange.com/questions/668232/watchdog-bug-soft-lockup-cpu0-stuck-when-booting-arch-linux-on-minisforum) [2] I turned on the computer, GRUB minimal terminal appeared (see [1]) and I pressed CTRL+ALT+Del. I then booted as usual
and this time it was super fast. Now I'm using that computer and it seems to be working fine, and notoriously the Task Manager says the CPU usage is very low, 0 to 5%.

Still following that same post, LXLE uses Ubuntu LTS so my kernel might not be updated. I'm not sure if I should update it. 
The accepted answer I'm also not sure if I should follow: I have no idea why they did what they did and it seems like a weird hack, to circumvent the fact that it only happens on cold boot they are doing a reboot. I don't know if my bug happens only on cold boot
as I have not done a reboot.

In this post: [https://askubuntu.com/questions/1264859/watchdog-bug-soft-lockup-cpu6-stuck-for-23s](https://askubuntu.com/questions/1264859/watchdog-bug-soft-lockup-cpu6-stuck-for-23s) it was a swap problem. I will now include the debugging information asked for in that post:

```
free -h
              total        used        free      shared  buff/cache   available
Mem:          5,7Gi       1,2Gi       3,5Gi        38Mi       1,1Gi       4,3Gi
Swap:         2,0Gi          0B       2,0Gi

```

```
sysctl vm.swappiness
vm.swappiness = 50

```

```
uname -a
Linux pedro-IdeaPad-3-15ADA05 5.4.0-113-generic #127-Ubuntu SMP Wed May 18 14:30:56 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

```
sudo lshw -C memory
  *-memory                  
       description: System Memory
       physical id: 1
       slot: System board or motherboard
       size: 8GiB
     *-bank:0
          description: Row of chips DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0,4 ns)
          product: M471A5244CB0-CWE
          vendor: Samsung
          physical id: 0
          serial: 40994951
          slot: DIMM 0
          size: 4GiB
          width: 64 bits
          clock: 2400MHz (0.4ns)
     *-bank:1
          description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0,4 ns)
          product: 4ATF51264HZ-2G6E1
          vendor: Micron Technology
          physical id: 1
          serial: 00000000
          slot: DIMM 0
          size: 4GiB
          width: 64 bits
          clock: 2400MHz (0.4ns)
  *-cache:0
       description: L1 cache
       physical id: 3
       slot: L1 - Cache
       size: 384KiB
       capacity: 384KiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=1
  *-cache:1
       description: L2 cache
       physical id: 4
       slot: L2 - Cache
       size: 2MiB
       capacity: 2MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=2
  *-cache:2
       description: L3 cache
       physical id: 5
       slot: L3 - Cache
       size: 4MiB
       capacity: 4MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=3
  *-firmware
       description: BIOS
       vendor: LENOVO
       physical id: d
       version: E8CN34WW
       date: 04/28/2022
       size: 128KiB
       capacity: 8MiB
       capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification netboot uefi


```

```
grep -i swap /etc/fstab
/swapfile                                 none            swap    sw              0       0

```

This other post seems to be related to NVidia graphics cards: [https://superuser.com/questions/1442828/how-to-fix-watchdog-soft-lockup-cpu-error-while-installing-ubuntu](https://superuser.com/questions/1442828/how-to-fix-watchdog-soft-lockup-cpu-error-while-installing-ubuntu)

My computer doesn't have that. It is a Lenovo Ideapad 3 15ADA05 81W1. 

I'll add that this machine is dual booted with Windows and there are some boot problems with it that I haven't gotten around to fix, and may or may not be related: [https://ubuntuforums.org/showthread.php?t=2481759](https://ubuntuforums.org/showthread.php?t=2481759)

I'm not sure what to do with all this information, or if the bug is different from these 3 versions I presented.

[0] [https://imgur.com/a/E7WBjAh](https://imgur.com/a/E7WBjAh) picture of boot time log
[1] [https://ubuntuforums.org/showthread.php?t=2481759](https://ubuntuforums.org/showthread.php?t=2481759) My problems with GRUB
[2] [https://unix.stackexchange.com/questions/668232/watchdog-bug-soft-lockup-cpu0-stuck-when-booting-arch-linux-on-minisforum](https://unix.stackexchange.com/questions/668232/watchdog-bug-soft-lockup-cpu0-stuck-when-booting-arch-linux-on-minisforum) log in hack that worked
[3] [https://askubuntu.com/questions/1264859/watchdog-bug-soft-lockup-cpu6-stuck-for-23s](https://askubuntu.com/questions/1264859/watchdog-bug-soft-lockup-cpu6-stuck-for-23s) same kernel bug, was a memory swap issue
[4] [https://superuser.com/questions/1442828/how-to-fix-watchdog-soft-lockup-cpu-error-while-installing-ubuntu](https://superuser.com/questions/1442828/how-to-fix-watchdog-soft-lockup-cpu-error-while-installing-ubuntu) same kernel bug, was a drivers issue

---

