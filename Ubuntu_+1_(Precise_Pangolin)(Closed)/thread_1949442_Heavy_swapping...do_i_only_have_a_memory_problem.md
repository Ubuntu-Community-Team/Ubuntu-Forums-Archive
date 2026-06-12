---
title: "Heavy swapping...do i only have a memory problem?"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rparree on 2012-03-30
Lately i am suffering from long freezes (average 10 minutes, last week twice i had two of more than an hour, during which i have reset my laptop).

I just suffered from another one, while trying to create a screencast for a training.

What i would like to know, am i only suffering from insufficient physical memory or might there something else going on as well.

I am running Kubuntu:
kernel: 3.2.0-20-generic
Ubuntu 12.04 precise (development branch)

Have 4GB of RAM (ordering more already)

Here are some lines from vmstat:
```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
1  0   1921    113      6   2157    0    0   296   136 1598 3865 82  8  9  1
 2  0   1921    108      6   2176    0    0    16     0 1453 3130 74  5 21  0
 0  2   1931    119      6   2178    0 9668   568  9868 6855 3748 69 12  0 19
 5  2   1931     98      6   2202    0    0  2604     8 4958 3125 66  8  3 24
 1  4   1932     96      6   2204    0 1096  3112  1100 4035 2679 48  8  1 43
 2  4   1932    119      4   2188    0    0  2364    36 15909 2754 57 12  9 22
 0  4   1937     97      4   2206    0 4968  3464  4968 3889 3085 55 10  1 35
 7  3   1937    101      0   2212    0    0  3168   160 12122 2931 63 11  1 26
 1  4   1942    104      0   2210    0 4932  3348  5232 16944 3087 66 12  3 20
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 4  3   1942    112      0   2228    0    0  1616     4 3713 3234 57  8  3 33
 1  1   1942     98      0   2246    0    0  2384     4 1458 2787 52  9  1 39
 6  4   1942     87      0   2263    0    0  1216 28088 1799 2978 59  9 13 19
 1  7   1942     87      0   2276    0   24  2952   164 5537 3100 48  9  4 40
 0 10   1958     90      0   2274    0 15812  1020 15812 3197 1462  8  8  0 84
 3 11   1960     87      0   2275    0 1576  2104  1664 1690 1838 24  4  0 72
 0 26   1960     90      0   2272    0  228 27908   576 4431 4094  1  0  0 99
 0 23   1960    108      0   2255    0    0 11108    20 1704 1994  0  1  0 99
 0 20   1960    114      0   2249    0    0 57940    28  660  702  0  0  0 100
 0 37   1960    116      0   2250    0    0 57680     0 33431 38990  1  1  0 98
 0 39   1960    117      0   2249    0    0 44396     0 7782 9600  0  0  0 99
....
....
....
1  0   1921    113      6   2157    0    0   296   136 1598 3865 82  8  9  1
 2  0   1921    108      6   2176    0    0    16     0 1453 3130 74  5 21  0
 0  2   1931    119      6   2178    0 9668   568  9868 6855 3748 69 12  0 19
 5  2   1931     98      6   2202    0    0  2604     8 4958 3125 66  8  3 24
 1  4   1932     96      6   2204    0 1096  3112  1100 4035 2679 48  8  1 43
 2  4   1932    119      4   2188    0    0  2364    36 15909 2754 57 12  9 22
 0  4   1937     97      4   2206    0 4968  3464  4968 3889 3085 55 10  1 35
 7  3   1937    101      0   2212    0    0  3168   160 12122 2931 63 11  1 26
 1  4   1942    104      0   2210    0 4932  3348  5232 16944 3087 66 12  3 20
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 4  3   1942    112      0   2228    0    0  1616     4 3713 3234 57  8  3 33
 1  1   1942     98      0   2246    0    0  2384     4 1458 2787 52  9  1 39
 6  4   1942     87      0   2263    0    0  1216 28088 1799 2978 59  9 13 19
 1  7   1942     87      0   2276    0   24  2952   164 5537 3100 48  9  4 40
 0 10   1958     90      0   2274    0 15812  1020 15812 3197 1462  8  8  0 84
 3 11   1960     87      0   2275    0 1576  2104  1664 1690 1838 24  4  0 72
 0 26   1960     90      0   2272    0  228 27908   576 4431 4094  1  0  0 99
 0 23   1960    108      0   2255    0    0 11108    20 1704 1994  0  1  0 99
 0 20   1960    114      0   2249    0    0 57940    28  660  702  0  0  0 100
 0 37   1960    116      0   2250    0    0 57680     0 33431 38990  1  1  0 98
 0 39   1960    117      0   2249    0    0 44396     0 7782 9600  0  0  0 99
...
...
...
 1  8   2082    105      1   2246  128    0  3840    24 2630 4426 70  4  1 26
 5 12   2082    105      1   2247  192    0  3176     0 1232 2356 66  2  0 32
 1 11   2082    107      1   2246   32    0  4784    20 1196 2047 63  4  0 33
```

---

### Post by Paddy Landau on 2012-03-30
This belongs in the [Ubuntu+1 (Precise Pangolin)]("http://ubuntuforums.org/forumdisplay.php?f=412") forum, because it is still in Beta.

You have sufficient RAM. Are you sure you have swap turned on? System Monitor > Resources > Memory and Swap History will tell you how much swap is available. It should be the same as your RAM or more.

---

### Post by rparree on 2012-03-30
Don't the vmstat output swpd column and si/so columns indicate that swap is turned on?

I ran:
```
swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       4191228 0       -1

```

I have the feeling my system blocks because of the swapping. I have 99-100% of processes waiting on CPU while the system seems to be swapping out? It seems my phiscical free memory goes to single digit MBs. Or am i misinterpreting the vmstat output?

---

### Post by jerome1232 on 2012-03-30
Your misinterpreting, most of it is used by cache which is memory not being used for anything so it just sticks files in there that might be accessed again soon. Cached space will be immediately released if applications need the space.

You might see a small amount of swap usage because the system will page out data if it's something that just doesn't get accessed again by the program while it's running.

---

### Post by nothingspecial on 2012-03-30
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by rparree on 2012-03-30
Interesting..

A line like:

```
0 10   1958     90      0   2274    0 15812  1020 15812 3197 1462  8  8  0 84
```

Does that not mean I have 1958Mb in swap, only 90Mb left of physical RAM, a buffer size of 90M and a cache which had to be emptied? Just swapped out (so) 15812m to disk?

I have been always under the impression that the so/si indicate swapping I/O in and out?

So what is wrong with my system if i am interpreting my vmstat numbers wrong...The whole system just freezes and the only thing i see is disk I/O (on iotops and on my disk light indicator)

---

### Post by meborc on 2012-03-30
to be sure, use top or htop to get more human readable information :D

in my example, 0 swap is used

---

### Post by dino99 on 2012-03-30
> **rparree said:**
> Interesting..

A line like:

```
0 10   1958     90      0   2274    0 15812  1020 15812 3197 1462  8  8  0 84
```

Does that not mean I have 1958Mb in swap, only 90Mb left of physical RAM, a buffer size of 90M and a cache which had to be emptied? Just swapped out (so) 15812m to disk?

I have been always under the impression that the so/si indicate swapping I/O in and out?

So what is wrong with my system if i am interpreting my vmstat numbers wrong...The whole system just freezes and the only thing i see is disk I/O (on iotops and on my disk light indicator)

To get a visual check, you can install the System-Monitor in the taskbar: hit "Alt" key down + right click on the taskbar, then select "add to panel" and choose System Monitor. When it has been instaaled, double-click on its icone to get the screen data.
Or into a terminal, run : free

---

### Post by jerome1232 on 2012-03-30
> **rparree said:**
> Interesting..

A line like:

```
0 10   1958     90      0   2274    0 15812  1020 15812 3197 1462  8  8  0 84
```

Does that not mean I have 1958Mb in swap, only 90Mb left of physical RAM, a buffer size of 90M and a cache which had to be emptied? Just swapped out (so) 15812m to disk?

I have been always under the impression that the so/si indicate swapping I/O in and out?

So what is wrong with my system if i am interpreting my vmstat numbers wrong...The whole system just freezes and the only thing i see is disk I/O (on iotops and on my disk light indicator)

Almost, if I'm reading that right your cache still has 2274 mb's in it, yet as you say, you system is thrashing the swap.


What is your swappiness at? Try adjusting it like 10 and see what happens.

:confused:

---

### Post by meborc on 2012-03-30
you can always do ```
sudo swapoff -a
```if you have enough memory (4GB is enough) and work without swap

---

### Post by NHclimber on 2012-03-30
> **rparree said:**
> ... while trying to create a screencast for a training.

What are you using to "create a screencast for a training"?

It looks to me like something is just spawning over and over and over again until the machine becomes totally I/O bound or maybe something deadlocks. For example, from your vmstat

> **rparree said:**
> 
Here are some lines from vmstat:
```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 ...
 0 37   1960    116      0   2250    0    0 57680     0 33431 38990  1  1  0 98

```

Here you have 37 waiting processes, with 33431 interrupts, 38990 context switches and 98% of cpu time is waiting for i/o completion. Something other than not enough physical ram is wrong -- start with top.

---

### Post by rparree on 2012-03-30
I am using kazam. But had the same problem last week when i was not making a screencast (at that time i had also a virtualbox running).  I really assumed that when my free memory reaches below 100MB (from 4GB) that it would be a memory problem. 


The problems also are "new", they only happened suddenly. Recent changes:

-Kernel update
-kubuntu 12.04 precise (development branch)
-kde 4.8 update (but that's a while ago, prior to my ubunty)

I had swapiness set to 10 (in /etc/sysctl.conf), but have put it back to 60 as i thought that had something to do with it. 

I had top running as well, for memory it shows the same. What else should i be looking at. I can easily get my system to the same state (tomorrow) and have top/htop running. I will post an update.

For the rest my system only seem to have become much better and much more responsive since those updates. Just this thing is killing me!

---

### Post by matt_symes on 2012-03-30
Hi

NHclimber has hit the nail on the head. You're I/O bound. This is not a swap problem

You can try to use dstat if get more information.

```
sudo apt-get install dstat
```

To get top block io processes.

```
sudo dstat --top-bio-adv
```

Check out the man page for dstat. There's a lot more you can get.

Kind regards

---

### Post by jbicha on 2012-03-30
I don't use Kazam but a new fix was just uploaded with version [1.0.5]("https://launchpad.net/ubuntu/+source/kazam/1.0.5-0ubuntu1").

---

### Post by rparree on 2012-03-31
Thanks i will update soon, however i don't think it is kazam, as i had the same problems last week when not running kazam (not even installed)
Last week i thought it had to do with VirtualBox, but than this week same happened while using kazam.

---

### Post by rparree on 2012-03-31
been trying the whole day to get the freeze-up while running dstat (amazing program BTW, thanks for that-will come in handy often in my work).

Kind of bizar that no freeze-up has happened yet. I even tried to put more weight into it while recording (by running some extra processes like JBoss and WebLogic)

I have not made any updates between yesterday and now. Some updates are waiting for me. 

I will keep dstat running on my other screen while making screencasts - "hopefully" the crash will occur again while dstat is running (can't believe i am saying that, but can't stand problems that just disappear without knowing why :)


I saw my misinterpretation. The "free" memory in vmstat is without buffers/cache (stupid me, i knew that). However, am still puzzled over the SO/SI values at the same time while processes where waiting for CPU. But if something was draining my disk, than swapping will also be more difficult.

---

### Post by rparree on 2012-03-31
Well it did happen. Guess what makes the difference is when during  audio recording i actually talk (i did enable audio but was not talking this morning). Just did a real screencast and the system froze again. 

I have attached a image of part of dstat's output that seems to be during the freezing period (it was rendered after this period)

Large writes  for the virtual memory management (kswapd0)

---

### Post by rparree on 2012-03-31
I saw the following messages in syslog:

```
Mar 31 13:37:30 rparree-linux kernel: [ 1043.475361] CE: hpet increased min_delta_ns to 20113 nsec
Mar 31 13:42:05 rparree-linux pulseaudio[2278]: [alsa-source] asyncq.c: q overrun, queuing locally
Mar 31 13:42:18  pulseaudio[2278]: last message repeated 9 times
Mar 31 13:42:18 rparree-linux pulseaudio[2278]: [alsa-source] ratelimit.c: 1189 events suppressed
Mar 31 13:42:18 rparree-linux pulseaudio[2278]: [alsa-source] asyncq.c: q overrun, queuing locally
Mar 31 13:42:58  pulseaudio[2278]: last message repeated 10 times
Mar 31 13:44:14 rparree-linux pulseaudio[2278]: [alsa-source] ratelimit.c: 1421 events suppressed
Mar 31 13:44:14 rparree-linux pulseaudio[2278]: [alsa-source] asyncq.c: q overrun, queuing locally
Mar 31 13:44:24  pulseaudio[2278]: last message repeated 10 times
Mar 31 13:44:24 rparree-linux pulseaudio[2278]: [alsa-source] ratelimit.c: 1448 events suppressed
Mar 31 13:44:24 rparree-linux pulseaudio[2278]: [alsa-source] asyncq.c: q overrun, queuing locally
Mar 31 13:45:10  pulseaudio[2278]: last message repeated 10 times
Mar 31 13:45:10 rparree-linux pulseaudio[2278]: [alsa-source] ratelimit.c: 1008 events suppressed
Mar 31 13:45:10 rparree-linux pulseaudio[2278]: [alsa-source] asyncq.c: q overrun, queuing locally
Mar 31 13:46:28  pulseaudio[2278]: last message repeated 10 times
Mar 31 13:50:12 rparree-linux pulseaudio[2278]: [alsa-source] ratelimit.c: 923 events suppressed
Mar 31 13:50:12 rparree-linux pulseaudio[2278]: [alsa-source] asyncq.c: q overrun, queuing locally
Mar 31 13:50:17  pulseaudio[2278]: last message repeated 10 times
Mar 31 13:50:17 rparree-linux pulseaudio[2278]: [alsa-source] ratelimit.c: 584 events suppressed
Mar 31 13:50:17 rparree-linux pulseaudio[2278]: [alsa-source] asyncq.c: q overrun, queuing locally
Mar 31 13:51:44  pulseaudio[2278]: last message repeated 10 times
Mar 31 13:53:51 rparree-linux rtkit-daemon[2280]: The canary thread is apparently starving. Taking action.
Mar 31 13:53:51 rparree-linux rtkit-daemon[2280]: Demoting known real-time threads.
Mar 31 13:53:52 rparree-linux rtkit-daemon[2280]: Successfully demoted thread 2317 of process 2278 (n/a).
Mar 31 13:53:52 rparree-linux rtkit-daemon[2280]: Successfully demoted thread 2316 of process 2278 (n/a).
Mar 31 13:53:52 rparree-linux rtkit-daemon[2280]: Successfully demoted thread 2311 of process 2278 (n/a).
Mar 31 13:53:52 rparree-linux rtkit-daemon[2280]: Successfully demoted thread 2278 of process 2278 (n/a).
Mar 31 13:53:52 rparree-linux rtkit-daemon[2280]: Demoted 4 threads.
```

And looking around, i found this... [http://www.linuxquestions.org/questions/mandriva-30/pulse-audio-appears-to-be-causing-hd-to-thrash-repeatedly-774595/](http://www.linuxquestions.org/questions/mandriva-30/pulse-audio-appears-to-be-causing-hd-to-thrash-repeatedly-774595/)

and [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354220](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354220)
Are these overruns *due* to my problem or the *cause* of my problem?

---

### Post by NHclimber on 2012-03-31
> **rparree said:**
> Are these overruns *due* to my problem or the *cause* of my problem?

As much as I dislike PulseAudio - its design, its implementation, pretty much everything about it -- I have to say that the write queue being full is probably a symptom and not a cause.

Although there is a slight possibility that this is an audio driver bug, kazam is most likely the culprit.  Python is good for plenty of simple stuff but IMO not for things like this.

---

### Post by matt_symes on 2012-04-01
Hi

> Although there is a slight possibility that this is an audio driver bug, kazam is most likely the culprit. Python is good for plenty of simple stuff but IMO not for things like this.

I concur. Have you tried another screencasting program ?

Kind regards

---

### Post by rparree on 2012-04-01
I have used recordmydesktop in the past, but had problems with audio synchronization. I would like to believe it is a Kazam problem, but like i said earlier in this thread. i had the same problems last week when using virtualbox (actually those system freezings took an hour, when i decided to reset my laptop).

---

### Post by rparree on 2012-04-01
just froze my system using virtualbox. I have attached a dstat screenshot from during the "crash"

---

### Post by matt_symes on 2012-04-01
Hi

I'm not sure what to suggest here but your I/O wait (under CPU wa) is high. This seems to be causing your freezes.

Every time your system is freezing the I/O wait time is far too high. 

Your system is also using more swap over time. This may just be unrelated, a side effect or could be caused by a memory leak some where. It would have to be a big one though.

Your previous dstat readings did seem to show that Kazam was causing the problem, however the image above would suggest that Virtual box is also causing the same issue.

What are all the specs of your PC (lshw) ? 

Does this happen with non intensive applications ? What other applications cause this problem ?

Kind regards

---

### Post by NHclimber on 2012-04-02
> **rparree said:**
> just froze my system using virtualbox. I have attached a dstat screenshot from during the "crash"

I can bring my 8 core, 10GB, striped RAID system to a standstill with virtualbox as well. Just a function of how many VMs are running with how much base memory assigned to each and what I'm doing inside them.

From your latest dstat output, it looks like you're load-testing the machine. What are you actually doing/what programs are running when this happens?

---

### Post by rparree on 2012-04-02
With kazam i am just recording desktop, might be 1 or 2 minutes into the recording. With VirtualBox, nothng special. Happened before actually doing nothing (however perhaps when virtualbox went idle perhaps some process started on the guest linux system)



My lshw request.

```

    description: Portable Computer
    product: Precision M6300 ()
    vendor: Winbond Electronics
    serial: 1D4283J
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=portable uuid=44454C4C-4400-1034-8032-B1C04F38334A
  *-core
       description: Motherboard
       product: 0WY897
       vendor: Winbond Electronics
       physical id: 0
       serial: .1D4283J.CN129617A42418.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A13
          date: 01/04/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7800  @ 2.60GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 2601MHz
          capacity: 2601MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 4MiB
             capacity: 4MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: HYMP325S64AMP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: 00005027
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: HYMP325S64AMP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             serial: 00001028
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
       *-ide:1
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=16) ioport:eff0(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK1234GS
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: AH00
                serial: 966M0780T
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000c1ff2
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 720d33b3-86ac-4a25-a086-fed57168a1b3
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-01-04 09:04:09 filesystem=ext4 lastmountpoint=/ modified=2012-03-29 20:30:47 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-04-02 21:01:19 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 4093MiB
                   capacity: 4093MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4093MiB
                      capabilities: nofs

```

---

### Post by NHclimber on 2012-04-02
For a basically idle machine, that is a *huge* memory footprint. The most recent dstat attachment you posted shows phys memory usage of 2.6G and already using almost 1G of swap.

Maybe you misconfigured the VM: the base memory assigned to the VM is unavailable to the host.  Can you post a screenshot of the VM VirtualBox Manager with the running VM highlighted ? (this show the base memory assigned to the VM)

Also, a screenshot of 'top' with the VM running would be helpful as well (press 'M' to sort by MEM usage).

Just by way of comparison, my idle machine right after session start has a 500M footprint.

If I build a kernel, watch the Onion in firefox (that already has 8 open tabs to a bunch of junk), load my 1G of evolution mail, and have 15+ terminals open and countless emacs windows strewn about 4 workspaces, the phys memory footprint goes up to about 1.6G or so.

---

### Post by rparree on 2012-04-03
I gave my virtualbox "too much" memory (it is in fact used by students during our courses). 
Do you think my kazam freeze-ups and virtualbox freeze-ups are unrelated?

Just te ensure: i am not running Kazam inside the virtualbox. Just have seen the same kind of freeze-ups , two weeks ago having VirtualBox and last week using kazam. 

Attached screenshot from Virtualbox settings.

---

### Post by NHclimber on 2012-04-03
> **rparree said:**
> I gave my virtualbox "too much" memory (it is in fact used by students during our courses).
[....]
Attached screenshot from Virtualbox settings.

Yep, too much memory.

> **rparree said:**
> Do you think my kazam freeze-ups and virtualbox freeze-ups are unrelated?

Well, they're related in the sense that both cause heavy swapping by demanding too much phys memory. But not likely related in any other way.  Although, paging shouldn't really cause "freezeups" but see below.

> **rparree said:**
> Just te ensure: i am not running Kazam inside the virtualbox. Just have seen the same kind of freeze-ups , two weeks ago having VirtualBox and last week using kazam. 


I surmised as much.  An interesting experiment would be to set the swappiness value to 0 (turn swap off) and run the kazam/PulseAudio test again to see what happens.

BTW, that's what I meant about PulseAudio's design: basically it turns an app problem (too much vmem demanded)  into a system problem (the "freezeup" you experience).

Also, you should be aware that VirtualBox is the least reliable hypervisor. Its driver's dfsg status (resulting in "tainted" kernel) is because the kernel group considers it to be junk. See [http://www.phoronix.com/scan.php?page=news_item&px=OTk5Mw](http://www.phoronix.com/scan.php?page=news_item&px=OTk5Mw)

---

### Post by SeijiSensei on 2012-04-03
> **NHclimber said:**
> Also, you should be aware that VirtualBox is the least reliable hypervisor. Its driver's dfsg status (resulting in "tainted" kernel) is because the kernel group considers it to be junk. See [http://www.phoronix.com/scan.php?page=news_item&px=OTk5Mw](http://www.phoronix.com/scan.php?page=news_item&px=OTk5Mw)

After reading that article and the discussion that follows, I think the best we can say is one of the kernel developers at RedHat thinks it is "garbage."  I also think using the "taint" function in this case is unwarranted.  The traditional definition of a tainted kernel is that it uses closed-source proprietary modules like my NVIDIA driver.  VirtualBox is licensed under the GPL.

I also don't entirely trust a RedHat developer commenting about the quality of software from Oracle.  To say the two companies have an [antagonistic relationship]("http://www.zdnet.com/blog/open-source/red-hat-turns-on-oracle-and-other-red-hat-linux-clone-makers/8485") is an understatement.

---

### Post by Paddy Landau on 2012-04-03
> **NHclimber said:**
> ... VirtualBox is the least reliable hypervisor. ...
[http://www.phoronix.com/scan.php?page=news_item&px=OTk5Mw](http://www.phoronix.com/scan.php?page=news_item&px=OTk5Mw)
> **SeijiSensei said:**
> ... an [antagonistic relationship]("http://www.zdnet.com/blog/open-source/red-hat-turns-on-oracle-and-other-red-hat-linux-clone-makers/8485") ...
Wow. That was interesting.

Personally, I have not had any issues running Windows XP, Windows 8, and various versions of Ubuntu and other Linux in Virtual Box. I have an occasional bug with Virtual Box where, *after* closing a machine, I have to restart it and delete an orphaned snapshot, but that is minor. The machine itself and the saved snapshots are never compromised.

---

### Post by NHclimber on 2012-04-03
I agree that its not right to use taint in this way. Just reporting.

I see now I have implied that I think its junk.  Thats not my opinion and I should have been way clearer there.  It is my opinion that its not as robust as some other products, but thats my personal opinion that stems from direct experience.  Your mileage may vary.

In general, virtualization is significantly trickier than might appear and full of workarounds and special handling.

---

