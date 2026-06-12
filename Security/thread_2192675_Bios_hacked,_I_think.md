---
title: "Bios hacked, I think??"
date: 2013-12-09
forum: Security
---

### Post by bdice1986 on 2013-12-09
I'm writing on this forum for this reason. I have six machines with what I think is  persistant malware. Dmesg log reads, "Starting paravirtualization on  bare hardware". This message appears way before bios searches for OS or  HDD. I think my OS's are running in virtual environment and someone else  is in control. What makes me think this is when I attempt to connect to  any type of net, it wont connect unless I use a virtbridge.There's a  few other odd things I've noticed but i'll keep them to myself for now  for obvious reasons. This same message appears no matter what flavor or  what machine I use. Whether I boot from HDD or live cd/dvd w/no HDD  installed. Tosh. Compaq, Lenovo, HP Pavillion. All the same. Any  bios/mobo gurus out there wanna take a crack at reverse engineering  this, I would be happy to part with one or two of my machines. I'll even  pay the shipping. BTW I tried flashing bios via USB. This stuff somehow  blocks bios from updating. Any help or ideas would be greatly appreciated. I'm a truck driver so go easy on me.

---

### Post by pholden on 2013-12-09
How can dmesg (or anything OS related) even be running before your BIOS has finished it's POST.. :-#

---

### Post by The Cog on 2013-12-09
This is a normal message from recent Linux kernels. Being paravirtualised means that the kernel is prepared to cooperate with the VM if it finds itself running on one. However, "on bare hardware" means that the kernel has decided it is *not* running in a VM after all. As pholden points out, no BIOS is going to write entries into a guest OS log, especially if it's a hack that wants to remain hidden. I suggest you start a new thread detailing your networking problems as normal network problems.
[http://ubuntuforums.org/showthread.php?t=843254](http://ubuntuforums.org/showthread.php?t=843254)

---

### Post by bdice1986 on 2013-12-15
could someone take a look at these logs, produced by checkbox system test. I'm a newb so if you could put my mind at ease and interpret what this means and if I'm being paranoid. The dmesg timeline has big gaps and the [COLOR=#ff0000]red[/COLOR] line  is an example of what I was referring to with the physical interfaces not connecting directly. This time paravirt on bare hardware line is gone. Same machine, same kernel. Totally confused! Your help is appreciated. I know. It's a lot of text.
[TABLE]
[TR]
[TD="class: label"]release[/TD]
[TD]13.10[/TD]
[/TR]
[TR]
[TD="class: label"]description[/TD]
[TD]Ubuntu 13.10[/TD]
[/TR]
[TR]
[TD="class: label"]codename[/TD]
[TD]saucy[/TD]
[/TR]
[TR]
[TD="class: label"]distributor_id[/TD]
[TD]Ubuntu
[/TD]
[/TR]
[/TABLE]
```
P: /devices/software
A: type=1
A: perf_event_mux_interval_ms=0


P: /devices/system/clockevents/broadcast
A: current_device=hpet


P: /devices/system/clockevents/clockevent0
A: current_device=lapic


P: /devices/system/clockevents/clockevent1
A: current_device=


P: /devices/system/clockevents/clockevent2
A: current_device=


P: /devices/system/clockevents/clockevent3
A: current_device=


P: /devices/system/clocksource/clocksource0
A: current_clocksource=tsc
A: available_clocksource=tsc hpet acpi_pm 


P: /devices/system/cpu/cpu0


P: /devices/system/machinecheck/machinecheck0
A: monarch_timeout=0
A: bank0=ffffffffffffffff
A: bank1=ffffffffffffffff
A: bank2=ffffffffffffffff
A: bank3=ffffffffffffffff
A: bank4=ffffffffffffffff
A: bank5=ffffffffffffffff
A: check_interval=300
A: dont_log_ce=0
A: trigger=
A: cmci_disabled=0
A: tolerant=1
A: ignore_ce=0


P: /devices/tracepoint
A: type=2
A: perf_event_mux_interval_ms=0


P: /devices/virtual/bdi/0:24
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=1


P: /devices/virtual/bdi/11:0
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:0
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:1
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:10
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:11
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:12
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:13
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:14
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:15
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:2
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:3
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:4
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:5
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:6
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:7
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:8
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/1:9
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/7:0
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/7:1
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/7:2
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/7:3
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/7:4
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/7:5
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/7:6
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/7:7
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/8:0
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/bdi/default
A: min_ratio=0
A: stable_pages_required=0
A: read_ahead_kb=128
A: max_ratio=100


P: /devices/virtual/block/loop0
A: ro=0
A: size=0
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=256
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=250


P: /devices/virtual/block/loop1
A: ro=0
A: size=0
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=256
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=250


P: /devices/virtual/block/loop2
A: ro=0
A: size=0
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=256
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=250


P: /devices/virtual/block/loop3
A: ro=0
A: size=0
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=256
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=250


P: /devices/virtual/block/loop4
A: ro=0
A: size=0
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=256
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=250


P: /devices/virtual/block/loop5
A: ro=0
A: size=0
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=256
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=250


P: /devices/virtual/block/loop6
A: ro=0
A: size=0
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=256
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=250


P: /devices/virtual/block/loop7
A: ro=0
A: size=0
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=256
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=250


P: /devices/virtual/block/ram0
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram1
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram10
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram11
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram12
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram13
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram14
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram15
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram2
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram3
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram4
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram5
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram6
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram7
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram8
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/block/ram9
A: ro=0
A: size=131072
A: stat=       0        0        0        0        0        0        0        0        0        0        0
A: range=1
A: discard_alignment=0
A: ext_range=1
A: alignment_offset=0
A: inflight=       0        0
A: removable=0
A: capability=30


P: /devices/virtual/dmi/id
A: product_name=Presario CQ56 Notebook PC
A: board_name=1604
A: board_asset_tag=Base Board Asset Tag
A: product_version=058D100002242810010620100
A: chassis_vendor=Hewlett-Packard
A: chassis_version=N/A
A: bios_date=02/15/2011
A: bios_version=F.16
A: sys_vendor=Hewlett-Packard
A: bios_vendor=Hewlett-Packard
A: chassis_asset_tag= 
A: chassis_type=10
A: board_vendor=Hewlett-Packard
A: board_version=88.17


P: /devices/virtual/drm/ttm


P: /devices/virtual/graphics/fbcon
A: cursor_blink=0
A: rotate=0


P: /devices/virtual/hwmon/hwmon0
A: name=acpitz
A: temp1_input=68000


P: /devices/virtual/input/input8
A: name=HP WMI hotkeys
A: phys=wmi/input0
A: uniq=
A: properties=0


P: /devices/virtual/input/input8/event8


P: /devices/virtual/input/mice


P: /devices/virtual/mem/full


P: /devices/virtual/mem/kmsg


P: /devices/virtual/mem/mem


P: /devices/virtual/mem/null


P: /devices/virtual/mem/port


P: /devices/virtual/mem/random


P: /devices/virtual/mem/urandom


P: /devices/virtual/mem/zero


P: /devices/virtual/misc/btrfs-control


P: /devices/virtual/misc/cpu_dma_latency


P: /devices/virtual/misc/device-mapper


P: /devices/virtual/misc/ecryptfs


P: /devices/virtual/misc/fuse


P: /devices/virtual/misc/hpet


P: /devices/virtual/misc/loop-control


P: /devices/virtual/misc/mcelog


P: /devices/virtual/misc/microcode


P: /devices/virtual/misc/network_latency


P: /devices/virtual/misc/network_throughput


P: /devices/virtual/misc/psaux


P: /devices/virtual/misc/rfkill


P: /devices/virtual/misc/snapshot


P: /devices/virtual/misc/tun


P: /devices/virtual/misc/uinput


P: /devices/virtual/misc/vga_arbiter


P: /devices/virtual/misc/watchdog


[COLOR=#ff0000]P: /devices/virtual/net/lo[/COLOR]
A: mtu=65536
A: type=772
A: netdev_group=0
A: flags=0x9
A: dormant=0
A: addr_assign_type=0
A: dev_id=0x0
A: iflink=1
A: addr_len=6
A: address=00:00:00:00:00:00
A: operstate=unknown
A: broadcast=00:00:00:00:00:00
A: tx_queue_len=0
A: ifalias=
A: ifindex=1
A: link_mode=0
A: carrier=1


P: /devices/virtual/ppp/ppp


P: /devices/virtual/sound/seq


P: /devices/virtual/sound/timer


P: /devices/virtual/thermal/cooling_device0
A: type=Processor
A: cur_state=0
A: max_state=10


P: /devices/virtual/thermal/cooling_device1
A: type=LCD
A: cur_state=4
A: max_state=10


P: /devices/virtual/thermal/thermal_zone0
A: mode=enabled
A: temp=68000
A: type=acpitz
A: trip_point_0_temp=100000
A: trip_point_0_type=hot
A: trip_point_1_temp=95000
A: trip_point_1_type=passive
A: policy=step_wise
A: cdev0_trip_point=1


P: /devices/virtual/tty/console
A: active=tty0


P: /devices/virtual/tty/ptmx


P: /devices/virtual/tty/tty


P: /devices/virtual/tty/tty0
A: active=tty7


P: /devices/virtual/tty/tty1


P: /devices/virtual/tty/tty10


P: /devices/virtual/tty/tty11


P: /devices/virtual/tty/tty12


P: /devices/virtual/tty/tty13


P: /devices/virtual/tty/tty14


P: /devices/virtual/tty/tty15


P: /devices/virtual/tty/tty16


P: /devices/virtual/tty/tty17


P: /devices/virtual/tty/tty18


P: /devices/virtual/tty/tty19


P: /devices/virtual/tty/tty2


P: /devices/virtual/tty/tty20


P: /devices/virtual/tty/tty21


P: /devices/virtual/tty/tty22


P: /devices/virtual/tty/tty23


P: /devices/virtual/tty/tty24


P: /devices/virtual/tty/tty25


P: /devices/virtual/tty/tty26


P: /devices/virtual/tty/tty27


P: /devices/virtual/tty/tty28


P: /devices/virtual/tty/tty29


P: /devices/virtual/tty/tty3


P: /devices/virtual/tty/tty30


P: /devices/virtual/tty/tty31


P: /devices/virtual/tty/tty32


P: /devices/virtual/tty/tty33


P: /devices/virtual/tty/tty34


P: /devices/virtual/tty/tty35


P: /devices/virtual/tty/tty36


P: /devices/virtual/tty/tty37


P: /devices/virtual/tty/tty38


P: /devices/virtual/tty/tty39


P: /devices/virtual/tty/tty4


P: /devices/virtual/tty/tty40


P: /devices/virtual/tty/tty41


P: /devices/virtual/tty/tty42


P: /devices/virtual/tty/tty43


P: /devices/virtual/tty/tty44


P: /devices/virtual/tty/tty45


P: /devices/virtual/tty/tty46


P: /devices/virtual/tty/tty47


P: /devices/virtual/tty/tty48


P: /devices/virtual/tty/tty49


P: /devices/virtual/tty/tty5


P: /devices/virtual/tty/tty50


P: /devices/virtual/tty/tty51


P: /devices/virtual/tty/tty52


P: /devices/virtual/tty/tty53


P: /devices/virtual/tty/tty54


P: /devices/virtual/tty/tty55


P: /devices/virtual/tty/tty56


P: /devices/virtual/tty/tty57


P: /devices/virtual/tty/tty58


P: /devices/virtual/tty/tty59


P: /devices/virtual/tty/tty6


P: /devices/virtual/tty/tty60


P: /devices/virtual/tty/tty61


P: /devices/virtual/tty/tty62


P: /devices/virtual/tty/tty63


P: /devices/virtual/tty/tty7


P: /devices/virtual/tty/tty8


P: /devices/virtual/tty/tty9


P: /devices/virtual/tty/ttyprintk


P: /devices/virtual/vc/vcs


P: /devices/virtual/vc/vcs1


P: /devices/virtual/vc/vcs2


P: /devices/virtual/vc/vcs3


P: /devices/virtual/vc/vcs4


P: /devices/virtual/vc/vcs5


P: /devices/virtual/vc/vcs6


P: /devices/virtual/vc/vcs7


P: /devices/virtual/vc/vcsa


P: /devices/virtual/vc/vcsa1


P: /devices/virtual/vc/vcsa2


P: /devices/virtual/vc/vcsa3


P: /devices/virtual/vc/vcsa4


P: /devices/virtual/vc/vcsa5


P: /devices/virtual/vc/vcsa6


P: /devices/virtual/vc/vcsa7


P: /devices/virtual/vtconsole/vtcon0
A: bind=0
A: name=(S) VGA+


P: /devices/virtual/vtconsole/vtcon1
A: bind=1
A: name=(M) frame buffer device


P: /devices/virtual/wmi/05901221-D566-11D1-B2F0-00A0C9062910


P: /devices/virtual/wmi/5FB7F034-2C63-45E9-BE91-3D44E2C707E4


P: /devices/virtual/wmi/95F24279-4D7B-4334-9387-ACCDC67EF61C


P: /devices/virtual/wmi/D0992BD4-A47C-4EFE-B072-324AEC92296C


P: /devices/virtual/workqueue/writeback
A: nice=0
A: numa=1
A: cpumask=0f
A: pool_ids=0:8
A: per_cpu=0
#########################################################
cat /var/log/dmesg | ansi_parser


0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-14-generic (buildd@akateko) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 (Ubuntu 3.11.0-14.21-generic 3.11.7)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000002243ff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000224800-0x00000000002343ff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000234800-0x00000000012243ff] usable
[    0.000000] BIOS-e820: [mem 0x0000000001224800-0x00000000012343ff] usable
[    0.000000] BIOS-e820: [mem 0x0000000001234800-0x000000006e449fff] usable
[    0.000000] BIOS-e820: [mem 0x000000006e44a000-0x000000006e649fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000006e64a000-0x000000006fd3efff] usable
[    0.000000] BIOS-e820: [mem 0x000000006fd3f000-0x000000006fdbefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000006fdbf000-0x000000006febefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000006febf000-0x000000006fef5fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000006fef6000-0x000000006fefffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Hewlett-Packard Presario CQ56 Notebook PC/1604, BIOS F.16 02/15/2011
[    0.000000] .text .data .bss are not marked as E820_RAM!
[    0.000000] e820: remove [mem 0x01000000-0x01d8afff] 
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x6ff00 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFFC0000000 write-back
[    0.000000]   1 base 000040000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 000060000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 00006FEBC000 mask FFFFFFFFF000 uncachable
[    0.000000]   4 base 0000FFE00000 mask FFFFFFE00000 write-protect
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x00223fff]
[    0.000000]  [mem 0x00100000-0x00223fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x00225000-0x00233fff]
[    0.000000]  [mem 0x00225000-0x00233fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x00235000-0x33ffffff]
[    0.000000]  [mem 0x00235000-0x003fffff] page 4k
[    0.000000]  [mem 0x00400000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b39000, 0x01b39fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35992000-0x36cc0fff]
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 6fef5120 0005C (v01 HPQOEM SLIC-MPC 00000003      01000013)
[    0.000000] ACPI: FACP 6fef4000 000F4 (v04 HP     1604     00000003 MSFT 01000013)
[    0.000000] ACPI BIOS Error (bug): 32/64X address mismatch in FADT/Pm2ControlBlock: 0x00000900/0x0000000000000800, using 32 (20130517/tbfadt-462)
[    0.000000] ACPI: DSDT 6fee2000 0E1DE (v01 HP     1604     F0000000 MSFT 01000013)
[    0.000000] ACPI: FACS 6fe9b000 00040
[    0.000000] ACPI: HPET 6fef3000 00038 (v01 HP     1604     00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 6fef2000 00084 (v02 HP     1604     00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 6fef1000 0003C (v01 HP     1604     00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 6fee1000 00028 (v01 HP     1604     00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 6fee0000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 6fedf000 001B7 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 899MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b3a000, 0x01b3afff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x6fefffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x00223fff]
[    0.000000]   node   0: [mem 0x00225000-0x00233fff]
[    0.000000]   node   0: [mem 0x00235000-0x6e449fff]
[    0.000000]   node   0: [mem 0x6e64a000-0x6fd3efff]
[    0.000000]   node   0: [mem 0x6fef6000-0x6fefffff]
[    0.000000] On node 0 totalpages: 457445
[    0.000000] free_area_init_node: node 0, pgdat c1948b40, node_mem_map f6dfe020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1799 pages used for memmap
[    0.000000]   HighMem zone: 229195 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x00224000-0x00224fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00234000-0x00234fff]
[    0.000000] e820: [mem 0x6ff00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f6dbd000 s36288 r0 d21056 u57344
[    0.000000] pcpu-alloc: s36288 r0 d21056 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 455661
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=03adf968-aed5-4b81-8c75-6171f0d3176b ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3667960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0006ff00)
[    0.000000] Memory: 1779584K/1829780K available (6353K kernel code, 607K rwdata, 2640K rodata, 880K init, 908K bss, 50196K reserved, 916780K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1962000 - 0xc1a3e000   ( 880 kB)
[    0.000000]       .data : 0xc1634864 - 0xc1961dc0   (3253 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1634864   (6354 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f5008000 soft=f500a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2294.187 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4588.37 BogoMIPS (lpj=9176748)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000043] Security Framework initialized
[    0.000061] AppArmor: AppArmor initialized
[    0.000062] Yama: becoming mindful.
[    0.000117] Mount-cache hash table entries: 512
[    0.000326] Initializing cgroup subsys memory
[    0.000336] Initializing cgroup subsys devices
[    0.000338] Initializing cgroup subsys freezer
[    0.000340] Initializing cgroup subsys blkio
[    0.000342] Initializing cgroup subsys perf_event
[    0.000345] Initializing cgroup subsys hugetlb
[    0.000370] mce: CPU supports 6 MCE banks
[    0.000376] LVT offset 0 assigned for vector 0xf9
[    0.000381] process: using AMD E400 aware idle routine
[    0.000387] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.000387] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
[    0.000387] tlb_flushall_shift: 4
[    0.009491] ACPI: Core revision 20130517
[    0.018100] ACPI: All ACPI Tables successfully acquired
[    0.019603] ftrace: allocating 27143 entries in 54 pages
[    0.030416] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.030796] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070451] smpboot: CPU0: AMD V140 Processor (fam: 10, model: 06, stepping: 03)
[    0.175753] Performance Events: AMD PMU driver.
[    0.175758] ... version:                0
[    0.175759] ... bit width:              48
[    0.175760] ... generic registers:      4
[    0.175761] ... value mask:             0000ffffffffffff
[    0.175763] ... max period:             00007fffffffffff
[    0.175764] ... fixed-purpose events:   0
[    0.175765] ... event mask:             000000000000000f
[    0.177271] Brought up 1 CPUs
[    0.177275] smpboot: Total of 1 processors activated (4588.37 BogoMIPS)
[    0.177587] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.177691] devtmpfs: initialized
[    0.177843] EVM: security.selinux
[    0.177845] EVM: security.SMACK64
[    0.177846] EVM: security.capability
[    0.177909] PM: Registering ACPI NVS region [mem 0x6e44a000-0x6e649fff] (2097152 bytes)
[    0.177939] PM: Registering ACPI NVS region [mem 0x6fdbf000-0x6febefff] (1048576 bytes)
[    0.179079] regulator-dummy: no parameters
[    0.179142] RTC time: 13:21:35, date: 12/15/13
[    0.179181] NET: Registered protocol family 16
[    0.179296] EISA bus registered
[    0.179301] node 0 link 0: io port [0, ffffff]
[    0.179304] TOM: 0000000080000000 aka 2048M
[    0.179306] Fam 10h mmconf [mem 0xf8000000-0xfbffffff]
[    0.179309] node 0 link 0: mmio [a0000, bffff]
[    0.179312] node 0 link 0: mmio [80000000, 8fffffff]
[    0.179314] node 0 link 0: mmio [90000000, 900fffff]
[    0.179316] node 0 link 0: mmio [90100000, 902fffff]
[    0.179318] node 0 link 0: mmio [90300000, f7ffffff]
[    0.179319] node 0 link 0: mmio [f8000000, fbffffff] ==> none
[    0.179321] node 0 link 0: mmio [fc000000, ffdfffff]
[    0.179324] bus: [bus 00-1f] on node 0 link 0
[    0.179326] bus: 00 [io  0x0000-0xffff]
[    0.179327] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.179329] bus: 00 [mem 0x80000000-0xf7ffffff]
[    0.179330] bus: 00 [mem 0xfc000000-0xfcffffffff]
[    0.179393] ACPI: bus type PCI registered
[    0.179396] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.179456] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.179459] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.179460] PCI: Using MMCONFIG for extended config space
[    0.179462] PCI: Using configuration type 1 for base access
[    0.180319] bio: create slab <bio-0> at 0
[    0.180438] ACPI: Added _OSI(Module Device)
[    0.180439] ACPI: Added _OSI(Processor Device)
[    0.180441] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.180442] ACPI: Added _OSI(Processor Aggregator Device)
[    0.181724] ACPI: EC: Look up EC in DSDT
[    0.183015] ACPI: Executed 1 blocks of module-level executable AML code
[    0.185211] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.185557] process: System has AMD C1E enabled
[    0.185566] process: Switch to broadcast mode on CPU0
[    0.190813] ACPI: Interpreter enabled
[    0.190833] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.190839] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.190860] ACPI: (supports S0 S3 S4 S5)
[    0.190862] ACPI: Using IOAPIC for interrupt routing
[    0.191060] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.191175] ACPI: No dock devices found.
[    0.198166] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.198174] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.198176] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.198872] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cedff])
[    0.198878] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.198972] PCI host bridge to bus 0000:00
[    0.198975] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.198977] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.198979] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.198981] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.198984] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.198986] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.198988] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.198990] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.198992] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.198994] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.198996] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.198998] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.199000] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.199003] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.199005] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.199007] pci_bus 0000:00: root bus resource [mem 0x80000000-0xf7ffffff]
[    0.199009] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfed3ffff]
[    0.199011] pci_bus 0000:00: root bus resource [mem 0xfed45000-0xffffffff]
[    0.199025] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
[    0.199121] pci 0000:00:01.0: [1022:9602] type 01 class 0x060400
[    0.199270] pci 0000:00:05.0: [1022:9605] type 01 class 0x060400
[    0.199306] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.199346] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.199376] pci 0000:00:06.0: [1022:9606] type 01 class 0x060400
[    0.199411] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.199455] pci 0000:00:06.0: System wakeup disabled by ACPI
[    0.199535] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.199554] pci 0000:00:11.0: reg 0x10: [io  0x4038-0x403f]
[    0.199564] pci 0000:00:11.0: reg 0x14: [io  0x404c-0x404f]
[    0.199573] pci 0000:00:11.0: reg 0x18: [io  0x4030-0x4037]
[    0.199583] pci 0000:00:11.0: reg 0x1c: [io  0x4048-0x404b]
[    0.199592] pci 0000:00:11.0: reg 0x20: [io  0x4010-0x401f]
[    0.199602] pci 0000:00:11.0: reg 0x24: [mem 0x90308000-0x903083ff]
[    0.199740] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.199753] pci 0000:00:12.0: reg 0x10: [mem 0x90307000-0x90307fff]
[    0.199836] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.199909] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.200314] pci 0000:00:12.2: reg 0x10: [mem 0x90308600-0x903086ff]
[    0.202632] pci 0000:00:12.2: supports D1 D2
[    0.202634] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.202673] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.202748] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.202761] pci 0000:00:13.0: reg 0x10: [mem 0x90306000-0x90306fff]
[    0.202844] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.202918] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.203311] pci 0000:00:13.2: reg 0x10: [mem 0x90308500-0x903085ff]
[    0.205631] pci 0000:00:13.2: supports D1 D2
[    0.205632] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.205671] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.205744] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.205901] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.205922] pci 0000:00:14.2: reg 0x10: [mem 0x90300000-0x90303fff 64bit]
[    0.205985] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.206048] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.206200] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.206261] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.206291] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.206304] pci 0000:00:14.5: reg 0x10: [mem 0x90305000-0x90305fff]
[    0.206414] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    0.206428] pci 0000:00:16.0: reg 0x10: [mem 0x90304000-0x90304fff]
[    0.206577] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    0.206970] pci 0000:00:16.2: reg 0x10: [mem 0x90308400-0x903084ff]
[    0.209292] pci 0000:00:16.2: supports D1 D2
[    0.209294] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.209332] pci 0000:00:16.2: System wakeup disabled by ACPI
[    0.209404] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.209462] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.209516] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.209569] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.209629] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.209761] pci 0000:01:05.0: [1002:9712] type 00 class 0x030000
[    0.209771] pci 0000:01:05.0: reg 0x10: [mem 0x80000000-0x8fffffff pref]
[    0.209776] pci 0000:01:05.0: reg 0x14: [io  0x3000-0x30ff]
[    0.209781] pci 0000:01:05.0: reg 0x18: [mem 0x90200000-0x9020ffff]
[    0.209792] pci 0000:01:05.0: reg 0x24: [mem 0x90100000-0x901fffff]
[    0.209810] pci 0000:01:05.0: supports D1 D2
[    0.209901] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.209905] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.209908] pci 0000:00:01.0:   bridge window [mem 0x90100000-0x902fffff]
[    0.209912] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
[    0.209952] pci 0000:00:05.0: PCI bridge to [bus 02]
[    0.210060] pci 0000:03:00.0: [10ec:8136] type 00 class 0x020000
[    0.210074] pci 0000:03:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.210095] pci 0000:03:00.0: reg 0x18: [mem 0x90010000-0x90010fff 64bit pref]
[    0.210109] pci 0000:03:00.0: reg 0x20: [mem 0x90000000-0x9000ffff 64bit pref]
[    0.210119] pci 0000:03:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
[    0.210167] pci 0000:03:00.0: supports D1 D2
[    0.210169] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.217653] pci 0000:00:06.0: PCI bridge to [bus 03]
[    0.217662] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.217668] pci 0000:00:06.0:   bridge window [mem 0x90000000-0x900fffff 64bit pref]
[    0.217769] pci 0000:00:14.4: PCI bridge to [bus 04] (subtractive decode)
[    0.217778] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.217781] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.217783] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.217785] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.217787] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.217790] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.217792] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.217794] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.217796] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.217798] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.217800] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.217802] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.217804] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.217807] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.217809] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xf7ffffff] (subtractive decode)
[    0.217811] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xfed3ffff] (subtractive decode)
[    0.217813] pci 0000:00:14.4:   bridge window [mem 0xfed45000-0xffffffff] (subtractive decode)
[    0.217826] pci_bus 0000:00: on NUMA node 0
[    0.218280] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.218347] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.218413] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.218476] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.218528] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.218569] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.218610] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.218651] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.219193] ACPI: \_SB_.PCI0: notify handler is installed
[    0.219250] Found 1 acpi root devices
[    0.219297] ACPI: EC: GPE = 0x5, I/O: command/status = 0x66, data = 0x62
[    0.219402] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.219404] vgaarb: loaded
[    0.219405] vgaarb: bridge control possible 0000:01:05.0
[    0.219592] SCSI subsystem initialized
[    0.219594] ACPI: bus type ATA registered
[    0.219637] libata version 3.00 loaded.
[    0.219652] ACPI: bus type USB registered
[    0.219672] usbcore: registered new interface driver usbfs
[    0.219680] usbcore: registered new interface driver hub
[    0.219697] usbcore: registered new device driver usb
[    0.219782] PCI: Using ACPI for IRQ routing
[    0.221671] PCI: pci_cache_line_size set to 64 bytes
[    0.221726] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.221730] e820: reserve RAM buffer [mem 0x00224400-0x002fffff]
[    0.221732] e820: reserve RAM buffer [mem 0x00234400-0x002fffff]
[    0.221734] e820: reserve RAM buffer [mem 0x6e44a000-0x6fffffff]
[    0.221736] e820: reserve RAM buffer [mem 0x6fd3f000-0x6fffffff]
[    0.221738] e820: reserve RAM buffer [mem 0x6ff00000-0x6fffffff]
[    0.221823] NetLabel: Initializing
[    0.221825] NetLabel:  domain hash size = 128
[    0.221826] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.221835] NetLabel:  unlabeled traffic allowed by default
[    0.221916] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.221920] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.223947] Switched to clocksource hpet
[    0.228897] AppArmor: AppArmor Filesystem Enabled
[    0.228930] pnp: PnP ACPI init
[    0.228945] ACPI: bus type PNP registered
[    0.229245] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.229248] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.229251] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.229253] system 00:00: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.229256] system 00:00: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.229258] system 00:00: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.229263] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.229397] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.229431] pnp 00:02: [dma 4]
[    0.229451] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.229481] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.229527] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.229558] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.229588] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.229620] pnp 00:07: Plug and Play ACPI device, IDs SYN1e35 SYN1e00 SYN0002 PNP0f13 (active)
[    0.229665] system 00:08: [io  0x0400-0x04cf] could not be reserved
[    0.229668] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.229670] system 00:08: [io  0x04d6] has been reserved
[    0.229672] system 00:08: [io  0x0550] has been reserved
[    0.229675] system 00:08: [io  0x0680-0x06ff] has been reserved
[    0.229677] system 00:08: [io  0x077a] has been reserved
[    0.229679] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.229681] system 00:08: [io  0x0c14] has been reserved
[    0.229684] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.229686] system 00:08: [io  0x0c6c] has been reserved
[    0.229688] system 00:08: [io  0x0c6f] has been reserved
[    0.229691] system 00:08: [io  0x0cd0-0x0cdb] has been reserved
[    0.229693] system 00:08: [io  0x0380-0x0387] has been reserved
[    0.229695] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.229763] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.229766] system 00:09: [mem 0xffe00000-0xffffffff] has been reserved
[    0.229769] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.230234] pnp: PnP ACPI: found 10 devices
[    0.230239] ACPI: bus type PNP unregistered
[    0.230242] PnPBIOS: Disabled by ACPI PNP
[    0.265996] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.266018] pci 0000:00:05.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.266023] pci 0000:00:05.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.266026] pci 0000:00:05.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.266042] pci 0000:00:05.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.266045] pci 0000:00:05.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.266047] pci 0000:00:05.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.266055] pci 0000:00:05.0: BAR 14: assigned [mem 0x90400000-0x905fffff]
[    0.266062] pci 0000:00:05.0: BAR 15: assigned [mem 0x90600000-0x907fffff 64bit pref]
[    0.266068] pci 0000:00:06.0: BAR 14: assigned [mem 0x90800000-0x908fffff]
[    0.266071] pci 0000:00:05.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.266075] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.266078] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.266082] pci 0000:00:01.0:   bridge window [mem 0x90100000-0x902fffff]
[    0.266085] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
[    0.266088] pci 0000:00:05.0: PCI bridge to [bus 02]
[    0.266090] pci 0000:00:05.0:   bridge window [io  0x1000-0x1fff]
[    0.266094] pci 0000:00:05.0:   bridge window [mem 0x90400000-0x905fffff]
[    0.266097] pci 0000:00:05.0:   bridge window [mem 0x90600000-0x907fffff 64bit pref]
[    0.266101] pci 0000:03:00.0: BAR 6: assigned [mem 0x90020000-0x9002ffff pref]
[    0.266103] pci 0000:00:06.0: PCI bridge to [bus 03]
[    0.266106] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.266109] pci 0000:00:06.0:   bridge window [mem 0x90800000-0x908fffff]
[    0.266112] pci 0000:00:06.0:   bridge window [mem 0x90000000-0x900fffff 64bit pref]
[    0.266116] pci 0000:00:14.4: PCI bridge to [bus 04]
[    0.266135] pci 0000:00:01.0: setting latency timer to 64
[    0.266345] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.266347] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.266350] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.266352] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.266354] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.266356] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.266358] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.266360] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.266362] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.266364] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.266366] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.266368] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.266370] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.266372] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.266374] pci_bus 0000:00: resource 18 [mem 0x80000000-0xf7ffffff]
[    0.266377] pci_bus 0000:00: resource 19 [mem 0xfc000000-0xfed3ffff]
[    0.266379] pci_bus 0000:00: resource 20 [mem 0xfed45000-0xffffffff]
[    0.266381] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.266383] pci_bus 0000:01: resource 1 [mem 0x90100000-0x902fffff]
[    0.266386] pci_bus 0000:01: resource 2 [mem 0x80000000-0x8fffffff 64bit pref]
[    0.266388] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.266390] pci_bus 0000:02: resource 1 [mem 0x90400000-0x905fffff]
[    0.266392] pci_bus 0000:02: resource 2 [mem 0x90600000-0x907fffff 64bit pref]
[    0.266395] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.266397] pci_bus 0000:03: resource 1 [mem 0x90800000-0x908fffff]
[    0.266399] pci_bus 0000:03: resource 2 [mem 0x90000000-0x900fffff 64bit pref]
[    0.266401] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.266403] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.266405] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.266407] pci_bus 0000:04: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.266410] pci_bus 0000:04: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.266412] pci_bus 0000:04: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.266414] pci_bus 0000:04: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.266416] pci_bus 0000:04: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.266418] pci_bus 0000:04: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.266420] pci_bus 0000:04: resource 13 [mem 0x000dc000-0x000dffff]
[    0.266422] pci_bus 0000:04: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.266424] pci_bus 0000:04: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.266426] pci_bus 0000:04: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.266428] pci_bus 0000:04: resource 17 [mem 0x000ec000-0x000effff]
[    0.266430] pci_bus 0000:04: resource 18 [mem 0x80000000-0xf7ffffff]
[    0.266432] pci_bus 0000:04: resource 19 [mem 0xfc000000-0xfed3ffff]
[    0.266434] pci_bus 0000:04: resource 20 [mem 0xfed45000-0xffffffff]
[    0.266467] NET: Registered protocol family 2
[    0.266629] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.266663] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.266696] TCP: Hash tables configured (established 8192 bind 8192)
[    0.266721] TCP: reno registered
[    0.266723] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.266731] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.266786] NET: Registered protocol family 1
[    0.266795] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    1.051562] pci 0000:01:05.0: Boot video device
[    1.051570] PCI: CLS 64 bytes, default 64
[    1.051617] Trying to unpack rootfs image as initramfs...
[    1.482973] Freeing initrd memory: 19644K (f5992000 - f6cc1000)
[    1.483084] Simple Boot Flag at 0x44 set to 0x1
[    1.483129] LVT offset 1 assigned for vector 0x400
[    1.483138] IBS: LVT offset 1 assigned
[    1.483158] perf: AMD IBS detected (0x0000001f)
[    1.483190] Scanning for low memory corruption every 60 seconds
[    1.483426] Initialise module verification
[    1.483479] audit: initializing netlink socket (disabled)
[    1.483492] type=2000 audit(1387113696.376:1): initialized
[    1.506343] bounce pool size: 64 pages
[    1.506353] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.507530] zbud: loaded
[    1.507578] VFS: Disk quotas dquot_6.5.2
[    1.507623] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.508099] fuse init (API version 7.22)
[    1.508166] msgmni has been set to 1723
[    1.508474] Key type asymmetric registered
[    1.508476] Asymmetric key parser 'x509' registered
[    1.508507] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.508534] io scheduler noop registered
[    1.508536] io scheduler deadline registered (default)
[    1.508559] io scheduler cfq registered
[    1.508669] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    1.508717] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    1.508768] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.508784] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.509556] ACPI: AC Adapter [ACAD] (on-line)
[    1.509621] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.509625] ACPI: Power Button [PWRB]
[    1.509676] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.510032] ACPI: Lid Switch [LID]
[    1.510095] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.510100] ACPI: Power Button [PWRF]
[    1.510148] ACPI: processor limited to max C-state 1
[    1.510886] [Firmware Bug]: Invalid critical threshold (0)
[    1.512687] thermal LNXTHERM:00: registered as thermal_zone0
[    1.512691] ACPI: Thermal Zone [THRM] (64 C)
[    1.512765] GHES: HEST is not enabled!
[    1.512850] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.514017] Linux agpgart interface v0.103
[    1.515319] brd: module loaded
[    1.515888] loop: module loaded
[    1.516213] libphy: Fixed MDIO Bus: probed
[    1.516294] tun: Universal TUN/TAP device driver, 1.6
[    1.516296] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.516325] PPP generic driver version 2.4.2
[    1.516359] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.516361] ehci-pci: EHCI PCI platform driver
[    1.516550] ehci-pci 0000:00:12.2: setting latency timer to 64
[    1.516560] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.516565] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.516571] QUIRK: Enable AMD PLL fix
[    1.516573] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.516585] ehci-pci 0000:00:12.2: debug port 1
[    1.516623] ehci-pci 0000:00:12.2: irq 17, io mem 0x90308600
[    1.516727] isapnp: Scanning for PnP cards...
[    1.570979] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.571001] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.571003] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.571005] usb usb1: Product: EHCI Host Controller
[    1.571007] usb usb1: Manufacturer: Linux 3.11.0-14-generic ehci_hcd
[    1.571009] usb usb1: SerialNumber: 0000:00:12.2
[    1.571108] hub 1-0:1.0: USB hub found
[    1.571112] hub 1-0:1.0: 5 ports detected
[    1.571376] ehci-pci 0000:00:13.2: setting latency timer to 64
[    1.571382] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.571387] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.571390] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.571401] ehci-pci 0000:00:13.2: debug port 1
[    1.571425] ehci-pci 0000:00:13.2: irq 17, io mem 0x90308500
[    1.620051] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.620079] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.620081] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.620083] usb usb2: Product: EHCI Host Controller
[    1.620084] usb usb2: Manufacturer: Linux 3.11.0-14-generic ehci_hcd
[    1.620086] usb usb2: SerialNumber: 0000:00:13.2
[    1.620155] hub 2-0:1.0: USB hub found
[    1.620158] hub 2-0:1.0: 5 ports detected
[    1.620350] ehci-pci 0000:00:16.2: setting latency timer to 64
[    1.620355] ehci-pci 0000:00:16.2: EHCI Host Controller
[    1.620359] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.620362] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.620373] ehci-pci 0000:00:16.2: debug port 1
[    1.620395] ehci-pci 0000:00:16.2: irq 17, io mem 0x90308400
[    1.669034] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.669044] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.669046] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.669048] usb usb3: Product: EHCI Host Controller
[    1.669050] usb usb3: Manufacturer: Linux 3.11.0-14-generic ehci_hcd
[    1.669052] usb usb3: SerialNumber: 0000:00:16.2
[    1.810722] hub 3-0:1.0: USB hub found
[    1.810725] hub 3-0:1.0: 4 ports detected
[    1.810836] ehci-platform: EHCI generic platform driver
[    1.810846] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.810847] ohci-platform: OHCI generic platform driver
[    1.810852] uhci_hcd: USB Universal Host Controller Interface driver
[    1.810923] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.829843] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.829847] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.829901] mousedev: PS/2 mouse device common for all mice
[    1.830003] rtc_cmos 00:04: RTC can wake from S4
[    1.830097] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.830122] rtc_cmos 00:04: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.830180] device-mapper: uevent: version 1.0.3
[    1.873891] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.873907] platform eisa.0: Probing EISA bus 0
[    1.873929] platform eisa.0: EISA: Detected 0 cards
[    1.873936] cpufreq-nforce2: No nForce2 chipset.
[    1.873939] cpuidle: using governor ladder
[    1.873940] cpuidle: using governor menu
[    1.873948] ledtrig-cpu: registered to indicate activity on CPUs
[    1.874031] TCP: cubic registered
[    1.874115] NET: Registered protocol family 10
[    1.874283] NET: Registered protocol family 17
[    1.874296] Key type dns_resolver registered
[    1.874411] Using IPI No-Shortcut mode
[    1.874474] PM: Hibernation image not present or could not be loaded.
[    1.874477] Loading module verification certificates
[    1.878280] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 94b4c972d56471bcbe88837e8baa241d98a4e0f0'
[    1.878294] registered taskstats version 1
[    1.927120] isapnp: No Plug & Play device found
[    1.929482] Key type trusted registered
[    1.931741] Key type encrypted registered
[    1.934197] AppArmor: AppArmor sha1 policy hashing enabled
[    1.934450]   Magic number: 9:365:382
[    1.934544] rtc_cmos 00:04: setting system clock to 2013-12-15 13:21:37 UTC (1387113697)
[    1.934614] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.934644] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.934645] EDD information not available.
[    1.940059] ACPI: Battery Slot [BAT0] (battery present)
[    1.940417] Freeing unused kernel memory: 880K (c1962000 - c1a3e000)
[    1.940449] Write protecting the kernel text: 6356k
[    1.940507] Write protecting the kernel read-only data: 2644k
[    1.940508] NX-protecting the kernel data: 5932k
[    1.958921] systemd-udevd[92]: starting version 204
[    1.960236] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.989820] video: module verification failed: signature and/or required key missing - tainting kernel
[    2.035177] ahci 0000:00:11.0: version 3.0
[    2.044393] ohci-pci: OHCI PCI platform driver
[    2.050945] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.050951] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.051253] wmi: Mapper loaded
[    2.051436] acpi device:04: registered as cooling_device1
[    2.051477] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.051516] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[    2.053732] [drm] Initialized drm 1.1.0 20060810
[    2.054275] scsi0 : ahci
[    2.060000] scsi1 : ahci
[    2.060104] ata1: SATA max UDMA/133 abar m1024@0x90308000 port 0x90308100 irq 19
[    2.060107] ata2: SATA max UDMA/133 abar m1024@0x90308000 port 0x90308180 irq 19
[    2.060359] ohci-pci 0000:00:12.0: setting latency timer to 64
[    2.060363] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    2.060369] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
[    2.060400] ohci-pci 0000:00:12.0: irq 18, io mem 0x90307000
[    2.065717] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.065731] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.065956] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    2.066117] r8169 0000:03:00.0 eth0: RTL8102e at 0xf8456000, 78:ac:c0:53:74:ee, XID 04e00000 IRQ 42
[    2.090350] microcode: CPU0: patch_level=0x010000c8
[    2.090431] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.125233] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.125238] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.125240] usb usb4: Product: OHCI PCI host controller
[    2.125243] usb usb4: Manufacturer: Linux 3.11.0-14-generic ohci_hcd
[    2.125245] usb usb4: SerialNumber: 0000:00:12.0
[    2.125814] hub 4-0:1.0: USB hub found
[    2.125825] hub 4-0:1.0: 5 ports detected
[    2.127039] ohci-pci 0000:00:13.0: setting latency timer to 64
[    2.127044] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    2.127051] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    2.127071] ohci-pci 0000:00:13.0: irq 18, io mem 0x90306000
[    2.196151] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    2.196156] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.196158] usb usb5: Product: OHCI PCI host controller
[    2.196160] usb usb5: Manufacturer: Linux 3.11.0-14-generic ohci_hcd
[    2.196162] usb usb5: SerialNumber: 0000:00:13.0
[    2.196270] hub 5-0:1.0: USB hub found
[    2.196312] hub 5-0:1.0: 5 ports detected
[    2.196578] ohci-pci 0000:00:14.5: setting latency timer to 64
[    2.196582] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    2.196587] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 6
[    2.196605] ohci-pci 0000:00:14.5: irq 18, io mem 0x90305000
[    2.207266] [drm] radeon kernel modesetting enabled.
[    2.207657] [drm] initializing kernel modesetting (RS880 0x1002:0x9712 0x103C:0x1604).
[    2.207679] [drm] register mmio base: 0x90200000
[    2.207680] [drm] register mmio size: 65536
[    2.207772] ATOM BIOS: HP_JoYaHeWi
[    2.207795] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[    2.207798] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    2.207803] [drm] Detected VRAM RAM=256M, BAR=256M
[    2.207804] [drm] RAM width 32bits DDR
[    2.207890] [TTM] Zone  kernel: Available graphics memory: 441664 kiB
[    2.207892] [TTM] Zone highmem: Available graphics memory: 900054 kiB
[    2.207893] [TTM] Initializing pool allocator
[    2.207897] [TTM] Initializing DMA pool allocator
[    2.207916] [drm] radeon: 256M of VRAM memory ready
[    2.207917] [drm] radeon: 512M of GTT memory ready.
[    2.207928] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.214607] [drm] Loading RS780 Microcode
[    2.215123] r600_cp: Failed to load firmware "radeon/RS780_pfp.bin"
[    2.215127] [drm:r600_startup] *ERROR* Failed to load firmware!
[    2.215130] radeon 0000:01:05.0: disabling GPU acceleration
[    2.216202] radeon 0000:01:05.0: f68c1400 unpin not necessary
[    2.216734] [drm] radeon atom DIG backlight initialized
[    2.216735] [drm] Radeon Display Connectors
[    2.216737] [drm] Connector 0:
[    2.216738] [drm]   VGA-1
[    2.216740] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    2.216742] [drm]   Encoders:
[    2.216743] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.216744] [drm] Connector 1:
[    2.216745] [drm]   LVDS-1
[    2.216747] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    2.216748] [drm]   Encoders:
[    2.216749] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[    2.216750] [drm] Connector 2:
[    2.216752] [drm]   HDMI-A-1
[    2.216753] [drm]   HPD1
[    2.216755] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[    2.216756] [drm]   Encoders:
[    2.216757] [drm]     DFP1: INTERNAL_UNIPHY
[    2.216828] [drm] radeon: power management initialized
[    2.254520] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    2.254525] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.254528] usb usb6: Product: OHCI PCI host controller
[    2.254530] usb usb6: Manufacturer: Linux 3.11.0-14-generic ohci_hcd
[    2.254531] usb usb6: SerialNumber: 0000:00:14.5
[    2.254785] hub 6-0:1.0: USB hub found
[    2.254792] hub 6-0:1.0: 2 ports detected
[    2.255049] ohci-pci 0000:00:16.0: setting latency timer to 64
[    2.255053] ohci-pci 0000:00:16.0: OHCI PCI host controller
[    2.255058] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 7
[    2.255076] ohci-pci 0000:00:16.0: irq 18, io mem 0x90304000
[    2.314485] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    2.314489] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.314491] usb usb7: Product: OHCI PCI host controller
[    2.314493] usb usb7: Manufacturer: Linux 3.11.0-14-generic ohci_hcd
[    2.314495] usb usb7: SerialNumber: 0000:00:16.0
[    2.314736] hub 7-0:1.0: USB hub found
[    2.314743] hub 7-0:1.0: 4 ports detected
[    2.482347] tsc: Refined TSC clocksource calibration: 2294.254 MHz
[    2.550317] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.550347] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.550369] usb 5-1: new low-speed USB device number 2 using ohci-pci
[    2.551177] ata1.00: ATA-8: Hitachi HTS725025A9A364, PC2OC72E, max UDMA/100
[    2.551182] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.552234] ata1.00: configured for UDMA/100
[    2.552337] ata2.00: ATAPI: hp       CDDVDW TS-L633R, 0200, max UDMA/100
[    2.552377] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72502 PC2O PQ: 0 ANSI: 5
[    2.552569] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.552614] sd 0:0:0:0: [sda] Write Protect is off
[    2.552616] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.552652] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.553117] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.554735] ata2.00: configured for UDMA/100
[    2.557969] scsi 1:0:0:0: CD-ROM            hp       CDDVDW TS-L633R  0200 PQ: 0 ANSI: 5
[    2.565556] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.565561] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.565914] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.566020] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.602395]  sda: sda1 sda2 < sda5 >
[    2.602844] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.717594] usb 5-1: New USB device found, idVendor=093a, idProduct=2510
[    2.717599] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.717602] usb 5-1: Product: USB OPTICAL MOUSE
[    2.717604] usb 5-1: Manufacturer: PIXART
[    2.732104] hidraw: raw HID events driver (C) Jiri Kosina
[    2.742880] usbcore: registered new interface driver usbhid
[    2.742884] usbhid: USB HID core driver
[    2.748260] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input5
[    2.749097] hid-generic 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:13.0-1/input0
[    3.210273] [drm] fb mappable at 0x80141000
[    3.210277] [drm] vram apper at 0x80000000
[    3.210278] [drm] size 4325376
[    3.210280] [drm] fb depth is 24
[    3.210281] [drm]    pitch is 5632
[    3.210481] fbcon: radeondrmfb (fb0) is primary device
[    3.277033] Console: switching to colour frame buffer device 170x48
[    3.288298] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[    3.288300] radeon 0000:01:05.0: registered panic notifier
[    3.288415] [drm] Initialized radeon 2.34.0 20080528 for 0000:01:05.0 on minor 0
[    3.481926] Switched to clocksource tsc
[    3.499617] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.499622] EXT4-fs (sda1): write access will be enabled during recovery
[    4.918289] EXT4-fs (sda1): recovery complete
[    4.922675] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   12.472880] Adding 1827836k swap on /dev/sda5.  Priority:-1 extents:1 across:1827836k FS
[   13.308886] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.964454] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.179991] systemd-udevd[372]: starting version 204
[   14.414529] lp: driver loaded but no devices found
[   14.439183] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.569589] init: rsyslog main process (405) terminated with status 1
[   14.569613] init: rsyslog main process ended, respawning
[   14.877333] Bluetooth: Core ver 2.16
[   14.877379] NET: Registered protocol family 31
[   14.877381] Bluetooth: HCI device and connection manager initialized
[   14.877388] Bluetooth: HCI socket layer initialized
[   14.877391] Bluetooth: L2CAP socket layer initialized
[   14.877395] Bluetooth: SCO socket layer initialized
[   14.877698] ACPI Warning: 0x00000b00-0x00000b07 SystemIO conflicts with Region \_SB_.PCI0.SMBS.SMBI 1 (20130517/utaddress-251)
[   14.877704] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.919737] Bluetooth: RFCOMM TTY layer initialized
[   14.919750] Bluetooth: RFCOMM socket layer initialized
[   14.919752] Bluetooth: RFCOMM ver 1.11
[   14.945505] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.945510] Bluetooth: BNEP filters: protocol multicast
[   14.945519] Bluetooth: BNEP socket layer initialized
[   15.160976] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   15.166538] sp5100_tco: PCI Revision ID: 0x42
[   15.166615] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[   15.166628] sp5100_tco: Last reboot was not triggered by watchdog.
[   15.170351] sp5100_tco: initialized (0xf842cb00). heartbeat=60 sec (nowayout=0)
[   15.215220] init: avahi-cups-reload main process (446) terminated with status 1
[   15.378437] type=1400 audit(1387113710.951:2): apparmor="STATUS" operation="profile_load" parent=456 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=472 comm="apparmor_parser"
[   15.378447] type=1400 audit(1387113710.951:3): apparmor="STATUS" operation="profile_load" parent=456 profile="unconfined" name="/usr/sbin/cupsd" pid=472 comm="apparmor_parser"
[   15.379227] type=1400 audit(1387113710.951:4): apparmor="STATUS" operation="profile_replace" parent=456 profile="unconfined" name="/usr/sbin/cupsd" pid=472 comm="apparmor_parser"
[   15.382998] type=1400 audit(1387113710.955:5): apparmor="STATUS" operation="profile_load" parent=468 profile="unconfined" name="/sbin/dhclient" pid=480 comm="apparmor_parser"
[   15.383008] type=1400 audit(1387113710.955:6): apparmor="STATUS" operation="profile_load" parent=468 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=480 comm="apparmor_parser"
[   15.383012] type=1400 audit(1387113710.955:7): apparmor="STATUS" operation="profile_load" parent=468 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=480 comm="apparmor_parser"
[   15.383692] type=1400 audit(1387113710.955:8): apparmor="STATUS" operation="profile_replace" parent=468 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=480 comm="apparmor_parser"
[   15.383698] type=1400 audit(1387113710.955:9): apparmor="STATUS" operation="profile_replace" parent=468 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=480 comm="apparmor_parser"
[   15.384070] type=1400 audit(1387113710.955:10): apparmor="STATUS" operation="profile_replace" parent=468 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=480 comm="apparmor_parser"
[   15.394554] kvm: disabled by bios
[   15.577309] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.597418] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   15.637903] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   15.642726] hda-intel 0000:00:14.2: Using LPIB position fix
[   15.642767] snd_hda_intel 0000:00:14.2: setting latency timer to 64
[   15.656545] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[   15.676859] SKU: Nid=0x1d sku_cfg=0x4017992d
[   15.676863] SKU: port_connectivity=0x1
[   15.676865] SKU: enable_pcbeep=0x1
[   15.676866] SKU: check_sum=0x00000007
[   15.676867] SKU: customization=0x00000099
[   15.676868] SKU: external_amp=0x5
[   15.676869] SKU: platform_type=0x1
[   15.676870] SKU: swap=0x0
[   15.676871] SKU: override=0x1
[   15.677088] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   15.677090]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   15.677092]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   15.677093]    mono: mono_out=0x0
[   15.677094]    inputs:
[   15.677096]      Internal Mic=0x19
[   15.677097]      Mic=0x18
[   15.677099] realtek: No valid SSID, checking pincfg 0x4017992d for NID 0x1d
[   15.677104] realtek: Enabling init ASM_ID=0x992d CODEC_ID=10ec0270
[   15.686552] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   15.686668] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   16.404772] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20130517/dsopcode-236)
[   16.404781] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f5035360), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
[   16.404791] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f5035480), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
[   16.404824] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20130517/dsopcode-236)
[   16.404828] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f5035360), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
[   16.404834] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f5035480), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
[   16.414582] input: HP WMI hotkeys as /devices/virtual/input/input8
[   16.414800] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20130517/dsopcode-236)
[   16.414806] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f5035360), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
[   16.414815] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f5035480), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
[   16.414846] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20130517/dsopcode-236)
[   16.414850] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f5035360), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
[   16.414856] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f5035480), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
[   16.480145] init: failsafe main process (554) killed by TERM signal
[   16.614350] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xe40000/0xa0400, board id: 3655, fw id: 639099
[   16.717451] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   17.069595] type=1400 audit(1387113712.643:11): apparmor="STATUS" operation="profile_load" parent=759 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=764 comm="apparmor_parser"
[   17.656216] init: Failed to spawn acpid main process: unable to execute: No such file or directory 
```

---

### Post by bdice1986 on 2013-12-15
oh, I just found this too.

[TABLE="width: 700"]
[TR]
[TD]uninitiated[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][IMG]http://ubuntuforums.org/usr/share/checkbox/report/images/fail.png[/IMG][/TD]
[TD="class: label"]graphics/compiz_check[/TD]
[TD="bgcolor: #FF0000"]FAILED[/TD]
[TD]OpenGL vendor string: VMware, Inc. OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.3, 128 bits) OpenGL version string: 2.1 Mesa 9.2.1 Not software rendered: no Not blacklisted: yes GLX fbconfig: yes GLX texture from pixmap: yes GL npot or rect textures: yes Compiz supported: no[/TD]
[/TR]
[TR]
[TD][IMG]http://ubuntuforums.org/usr/share/checkbox/report/images/pass.png[/IMG][/TD]
[TD="class: label"]graphics[/TD]
[/TR]
[/TABLE]

---

### Post by tgalati4 on 2013-12-15
You have some ACPI errors.  compiz_check is not critical, it just means you will have problems with 3D rendering of animation effects.

Try using some different kernel boot switches to get around the ACPI issue.

A Haiku for your troubles:

Paravirtualized
and paralyzed with fear, yet
BIOS is not hacked.

---

### Post by bdice1986 on 2014-02-06
OK, but maybe someone could explain why I get the exact same dmesg w/the exact same errors on all my machines, HP-intel, Compaq-AMD, Lenovo-intell, regardless of OS.Ubuntu, Fedora-15,19, Suse-12.3, Slackware, whether I boot from HD or live CD or DVD. The UFW logs are allways disabled (net.netfilter.nf_log.0 thru log.12 = NONE) They cant be enabled on any of my machines. They used to be enabled by default. The only log files that aren't completely empty are dmesg, udev, kernel and alternatives logs. Also, many config files are not set properly. Etc-hosts.allow file is set to ALL (uncommented). hosts.deny always reads #ALL: PARANOID (commented out). Thats just a small example. And when one of these settings changes on one of my machines, within a few hours they all change. (hosts.deny file used to be empty on all machines until about a month ago). If you can explain to me how six different computers from two manufacturers, running different CPU's (2 AMD, 4 Intel) with four different OS's all have the exact same misconfiguration at the same time. including booting from live media. And when one of those configs changes (by itself) it changes on all my machines. Why is it so hard hard to believe that this problem is real. Is it that hard to believe that I'm the target of some whack-job hacker. I need help with this situation but it seems that the only people who have the knowledge to help me are are too busy trying to come up with some half-witted quip to insult me rather than assist me. Do you think I would offer to ship one of my machines to someone willing to help me if I wasn't sure there is a problem? Just what I want to do with all my spare time and money, write whiny letters on the internet and send my $500 plus computers to strangers. If there's anyone willing to give me the benefit of the doubt, I sure would appreciate it. We just replaced two of our business computers last month and very expensive software because they were compromised as well.


Better to remain silent and be thought a fool,
than to speak out and remove all doubt.

Abraham Lincoln

---

### Post by CharlesA on 2014-02-06
Easy fix.

Take those machines off the network and see if the files still change. If I was a hacker, and I had root access to a bunch of machines, I wouldn't wait "a few hours" to make changes.

My bet is all 6 are running the same or similar kernels, which accounts for the paravirtualization message.

---

### Post by ventrical on 2014-02-10
> **bdice1986 said:**
> OK, but maybe someone could explain why I get the exact same dmesg w/the exact same errors on all my machines, HP-intel, Compaq-AMD, Lenovo-intell, regardless of OS.Ubuntu, Fedora-15,19, Suse-12.3, Slackware, whether I boot from HD or live CD or DVD. The UFW logs are allways disabled (net.netfilter.nf_log.0 thru log.12 = NONE) They cant be enabled on any of my machines. They used to be enabled by default. The only log files that aren't completely empty are dmesg, udev, kernel and alternatives logs. Also, many config files are not set properly. Etc-hosts.allow file is set to ALL (uncommented). hosts.deny always reads #ALL: PARANOID (commented out). Thats just a small example. And when one of these settings changes on one of my machines, within a few hours they all change. (hosts.deny file used to be empty on all machines until about a month ago). If you can explain to me how six different computers from two manufacturers, running different CPU's (2 AMD, 4 Intel) with four different OS's all have the exact same misconfiguration at the same time. including booting from live media. And when one of those configs changes (by itself) it changes on all my machines. Why is it so hard hard to believe that this problem is real. Is it that hard to believe that I'm the target of some whack-job hacker. I need help with this situation but it seems that the only people who have the knowledge to help me are are too busy trying to come up with some half-witted quip to insult me rather than assist me. Do you think I would offer to ship one of my machines to someone willing to help me if I wasn't sure there is a problem? Just what I want to do with all my spare time and money, write whiny letters on the internet and send my $500 plus computers to strangers. If there's anyone willing to give me the benefit of the doubt, I sure would appreciate it. We just replaced two of our business computers last month and very expensive software because they were compromised as well.


Better to remain silent and be thought a fool,
than to speak out and remove all doubt.

Abraham Lincoln

 I had previously worked  with security professionals on some of the problems you have mentioned but only on Windows OSs. It is generally agreed  between malware removal professionals that once a system is infected with malware, that system, both hardware and software, will never be the same. Then there is the question of 'interfection' between open shares. It is also possible for a polymorphic/stealth malware to take up residence in an infected network router and can remain there and until that router  (or service) is changed then the problem will not be solved, it will persist.

  Please give me some time to think on this .. 

Regards..

edit..

Could you list the dd/mm/yy of your machines.

---

### Post by newbie2244 on 2014-03-12
You don't have malware and you don't have a hacked BIOs. The Cog and Pholden gave you some answers. Think about what they said.  Just for fun, read your BIOS settings and write them down in a notebool dedicated to your admin activities on your machines.(Yes, paper and pen are the way to go. [br]-->[/br]   I was just reading output of dmesg on my machine and found the same mesg as you did - paravirtualized kernel running on bare hardware.  When I read what paravirtualization was and that the more recent kernels are enabled for it, I finally had an answer and a name for how I set up my system and why it was working a certain way. And then I accessed the forums for more practical insight and found your post.[br]-->[/br]  [br]and.[/br]  Now some questions for you: Are your machines dual-boot or multi-boot? Are you running VMWare or some other virtual manager software on all your machines?  Do you have guest accounts or guest software?  Do you know what malware actually is and how it is supposed to work?  You should know the answers to these questions before you think malware and viruses.         [br]Lastly[/br] As for security pro's, -- lots of info, not enough knowledge to back up the info. Malware even on WIndows systems is largely a myth but when it happens it comes from MS via a circuitous route under the guise of research.

---

