---
title: "Amazon EC2 and Natty Narwhal?"
date: 2010-12-06
forum: Server Platforms
---

### Post by victorhooi on 2010-12-06
heya,

I'm trying to startup a new Amazon EC2 micro instance with Natty Narwhal (yes, I know it's early alpha) and I can't seem to get the box to actually bootup properly.

It's not responding to pings or SSH (and both ICMP and TCP 22 are allowed in the Amazon security groups).

In the console log, I see:

```
   Xen Minimal OS!
  start_info: 0xac4000(VA)
    nr_pages: 0x26700
  shared_inf: 0xdee36000(MA)
     pt_base: 0xac7000(VA)
nr_pt_frames: 0x9
    mfn_list: 0x990000(VA)
   mod_start: 0x0(VA)
     mod_len: 0
       flags: 0x0
    cmd_line:  root=/dev/sda1 ro 4
  stack:      0x94f860-0x96f860
MM: Init
      _text: 0x0(VA)
     _etext: 0x5ff6d(VA)
   _erodata: 0x78000(VA)
     _edata: 0x80b00(VA)
stack start: 0x94f860(VA)
       _end: 0x98fe68(VA)
  start_pfn: ad3
    max_pfn: 26700
Mapping memory range 0xc00000 - 0x26700000
setting 0x0-0x78000 readonly
skipped 0x1000
MM: Initialise page allocator for c01000(c01000)-26700000(26700000)
MM: done
Demand map pfns at 26701000-2026701000.
Heap resides at 2026702000-4026702000.
Initialising timer interface
Initialising console ... done.
gnttab_table mapped at 0x26701000.
Initialising scheduler
Thread "Idle": pointer: 0x2026702010, stack: 0x26640000
Initialising xenbus
Thread "xenstore": pointer: 0x20267027c0, stack: 0x26650000
Dummy main: start_info=0x96f960
Thread "main": pointer: 0x2026702f70, stack: 0x26660000
"main" "root=/dev/sda1" "ro" "4" 
vbd 2049 is hd0
******************* BLKFRONT for device/vbd/2049 **********


backend at /local/domain/0/backend/vbd/954/2049
Failed to read /local/domain/0/backend/vbd/954/2049/feature-barrier.
Failed to read /local/domain/0/backend/vbd/954/2049/feature-flush-cache.
16777216 sectors of 512 bytes
**************************

    [H
    [J  Booting 'Ubuntu natty (development branch), kernel 2.6.37-7-virtual'



root  (hd0)

 Filesystem type is ext2fs, using whole disk

kernel  /boot/vmlinuz-2.6.37-7-virtual root=LABEL=uec-rootfs ro console=hvc0 

initrd  /boot/initrd.img-2.6.37-7-virtual



close blk: backend at /local/domain/0/backend/vbd/954/2049

```

It just seems to hang there, and the box doesn't respond. Booting up a 10.04 (Maverick Meerkat) instance works fine.

Any idea what the above might mean? Do I have to do something special to get it to boot properly? I tried this with both the Natty Narwhal Alpha 1 as well as a current daily build from today (2010-12-07).

Cheers,
Victor

---

### Post by rameshoty on 2011-01-20
Dear Friend,

I am also getting same problem. I am using slackware13.1 image with Amazon(ec2) bundle with (aki-407d9529 aki-4c7d9525) both aki, I am getting same problem.

2011-01-20T18:05:29+0000
Xen Minimal OS!
  start_info: 0xb10000(VA)
    nr_pages: 0x6a400
  shared_inf: 0xbf706000(MA)
     pt_base: 0xb13000(VA)
nr_pt_frames: 0x9
    mfn_list: 0x967000(VA)
   mod_start: 0x0(VA)
     mod_len: 0
       flags: 0x0
    cmd_line: root=/dev/sda1 ro 4
  stack:      0x946780-0x966780
MM: Init
      _text: 0x0(VA)
     _etext: 0x621f5(VA)
   _erodata: 0x76000(VA)
     _edata: 0x7b6d4(VA)
stack start: 0x946780(VA)
       _end: 0x966d34(VA)
  start_pfn: b1f
    max_pfn: 6a400
Mapping memory range 0xc00000 - 0x6a400000
setting 0x0-0x76000 readonly
skipped 0x1000
MM: Initialise page allocator for e6c000(e6c000)-0(6a400000)
MM: done
Demand map pfns at 6a401000-7a401000.
Heap resides at 7a402000-ba402000.
Initialising timer interface
Initialising console ... done.
gnttab_table mapped at 0x6a401000.
Initialising scheduler
Thread "Idle": pointer: 0x7a402008, stack: 0x6a030000
Initialising xenbus
Thread "xenstore": pointer: 0x7a402478, stack: 0x6a040000
Dummy main: start_info=0x966880
Thread "main": pointer: 0x7a4028e8, stack: 0x6a050000
"main" "root=/dev/sda1" "ro" "4" 
vbd 2049 is hd0
******************* BLKFRONT for device/vbd/2049 **********


backend at /local/domain/0/backend/vbd/171/2049
Failed to read /local/domain/0/backend/vbd/171/2049/feature-barrier.
Failed to read /local/domain/0/backend/vbd/171/2049/feature-flush-cache.
20971520 sectors of 0 bytes
**************************
vbd 2050 is hd1
******************* BLKFRONT for device/vbd/2050 **********


backend at /local/domain/0/backend/vbd/171/2050
Failed to read /local/domain/0/backend/vbd/171/2050/feature-barrier.
Failed to read /local/domain/0/backend/vbd/171/2050/feature-flush-cache.
312705024 sectors of 0 bytes
**************************
vbd 2051 is hd2
******************* BLKFRONT for device/vbd/2051 **********


backend at /local/domain/0/backend/vbd/171/2051
Failed to read /local/domain/0/backend/vbd/171/2051/feature-barrier.
Failed to read /local/domain/0/backend/vbd/171/2051/feature-flush-cache.
1835008 sectors of 0 bytes
**************************
[H[J
    GNU GRUB  version 0.97  (1740800K lower / 0K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grubdom>                                                                       [9;10H
root@support:~# 

How to fix this issue, Please help me, 

Thanks for advance.

RAMESH

---

### Post by mconigliaro on 2011-06-23
I'm seeing the same thing on a couple instances after upgrading to pv-grub kernels on 10.04 LTS. I used the instructions here: [http://ubuntu-smoser.blogspot.com/2011/02/migrating-to-pv-grub-kernels-for-kernel.html](http://ubuntu-smoser.blogspot.com/2011/02/migrating-to-pv-grub-kernels-for-kernel.html)

---

