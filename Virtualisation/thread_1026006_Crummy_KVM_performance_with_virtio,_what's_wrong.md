---
title: "Crummy KVM performance with virtio, what's wrong?"
date: 2008-12-30
forum: Virtualisation
---

### Post by EightBitHustler on 2008-12-30
I've configured a server to support our development team and test a potential configuration for production.

I initially tried to configure [Xen only do discover Dom0 is not supported in 8.10]("http://ubuntuforums.org/showthread.php?t=990180"), but KVM looked like an attractive alternative. After some trail and error I got a VM working with virtio_net and virtio_blk with the image on an LVM2 volume.

While I'm unimpressed with the net IO and CPU results, the disk IO is less than desirable. Looking around the discussion board I came across this post

[http://ubuntuforums.org/showthread.php?t=972526&highlight=virtio]("http://ubuntuforums.org/showthread.php?t=972526&highlight=virtio")

Which leads me to believe something isn't quite right with my configuration. I've attached the XML dumps from libvirt for vm01 (file based image) and vm02 (lvm based image). I've also attached performance benchmarks from the host system and both VMs. While running the benchmark on the host I shutdown both VMs. While benchmarking the VMs I disabled the other.

If anyone out there has any insight, it would be greatly appreciated. I would love to get this working and deploy KVM over VMWare ESX.

**colossus (Host)**
```

---------------
1x1000BASE-T, 8 Core, 16GB RAM, 4x15K RPM Hardware RAID5
---------------
Linux colossus 2.6.27-9-server #1 SMP Thu Nov 20 22:56:07 UTC 2008 x86_64 GNU/Linux
---------------
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           X5460  @ 3.16GHz
stepping        : 6
cpu MHz         : 3158.737
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca sse4_1 lahf_lm
bogomips        : 6317.47
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:
*******************************************************************
me@colossus:~$ iperf -c xxx.xxx.xxx.14 -r -t 60 -w 256K
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size:   256 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to xxx.xxx.xxx.14, TCP port 5001
TCP window size:   256 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
[  5] local xxx.xxx.xxx.206 port 43906 connected with xxx.xxx.xxx.14 port 5001
Waiting for server threads to complete. Interrupt again to force quit.
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-60.0 sec  6.55 GBytes    938 Mbits/sec

me@colossus:/data/vm$ bonnie++ -s 32g -n 256
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
colossus        32G 76730  88 218667  46 96284  17 76906  81 273038  23  1141   3
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                256 67646  87 +++++ +++ 13106  15 72814  92 +++++ +++ 12249  16
colossus,32G,76730,88,218667,46,96284,17,76906,81,273038,23,1141.5,3,256,67646,87,+++++,+++,13106,15,72814,92,+++++,+++,12249,16

me@colossus:~/nbench-byte-2.2.3$ ./nbench 

BYTEmark* Native Mode Benchmark ver. 2 (10/95)
Index-split by Andrew D. Balsa (11/97)
Linux/Unix* port by Uwe F. Mayer (12/96,11/97)

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :          1499.7  :      38.46  :      12.63
STRING SORT         :          330.64  :     147.74  :      22.87
BITFIELD            :      6.0249e+08  :     103.35  :      21.59
FP EMULATION        :           327.6  :     157.20  :      36.27
FOURIER             :           33763  :      38.40  :      21.57
ASSIGNMENT          :          45.146  :     171.79  :      44.56
IDEA                :          9100.4  :     139.19  :      41.33
HUFFMAN             :          3057.6  :      84.79  :      27.07
NEURAL NET          :          67.226  :     107.99  :      45.43
LU DECOMPOSITION    :          2112.7  :     109.45  :      79.03
==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 109.365
FLOATING-POINT INDEX: 76.847
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : 8 CPU GenuineIntel Intel(R) Xeon(R) CPU           X5460  @ 3.16GHz 3159MHz
L2 Cache            : 6144 KB
OS                  : Linux 2.6.27-9-server
C compiler          : gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
libc                : libc-2.8.90.so
MEMORY INDEX        : 28.018
INTEGER INDEX       : 26.758
FLOATING-POINT INDEX: 42.622
Baseline (LINUX)    : AMD K6/233*, 512 KB L2-cache, gcc 2.7.2.3, libc-5.4.38
* Trademarks are property of their respective holder.

```

**vm01 (Guest)**

```

<domain type='kvm'>
  <name>vm01</name>
  <uuid>7efa39f0-1c1c-a8c7-8af8-8ac93852e455</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/data/vm/1/vm01-kvm/disk0.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='disk'>
      <source file='/data/vm/1/vm01-kvm/disk1.qcow2'/>
      <target dev='hdb' bus='ide'/>
    </disk>
    <interface type='bridge'>
      <mac address='52:54:00:e7:40:74'/>
      <source bridge='br0'/>
      <target dev='vnet1'/>
      <model type='virtio'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
  </devices>
</domain>
*******************************************************************
me@vm01:~$ iperf -c xxx.xxx.xxx.14 -r -t 60 -w 256K
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size:   256 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to xxx.xxx.xxx.14, TCP port 5001
TCP window size:   256 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
[  5] local xxx.xxx.xxx.208 port 42280 connected with xxx.xxx.xxx.14 port 5001
Waiting for server threads to complete. Interrupt again to force quit.
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-60.0 sec  1.03 GBytes    147 Mbits/sec

me@vm01:~$ bonnie++ -s 2g -n 256
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
vm01             2G  3867  90 15525  69 15619  46  4908  98 54912  78 337.1  97
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                256  2957  95 36378  91  2908  80  2953  95 57011  96  2443  72
vm01,2G,3867,90,15525,69,15619,46,4908,98,54912,78,337.1,97,256,2957,95,36378,91,2908,80,2953,95,57011,96,2443,72

me@vm01:~/nbench-byte-2.2.3$ ./nbench 

BYTEmark* Native Mode Benchmark ver. 2 (10/95)
Index-split by Andrew D. Balsa (11/97)
Linux/Unix* port by Uwe F. Mayer (12/96,11/97)

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :           333.4  :       8.55  :       2.81
STRING SORT         :          16.104  :       7.20  :       1.11
BITFIELD            :      5.3435e+07  :       9.17  :       1.91
FP EMULATION        :           25.21  :      12.10  :       2.79
FOURIER             :          2502.4  :       2.85  :       1.60
ASSIGNMENT          :          6.9528  :      26.46  :       6.86
IDEA                :          595.95  :       9.11  :       2.71
HUFFMAN             :          303.15  :       8.41  :       2.68
NEURAL NET          :          4.4887  :       7.21  :       3.03
LU DECOMPOSITION    :          195.32  :      10.12  :       7.31
==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 10.474
FLOATING-POINT INDEX: 5.922
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : AuthenticAMD QEMU Virtual CPU version 0.9.1 3159MHz
L2 Cache            : 512 KB
OS                  : Linux 2.6.27-9-server
C compiler          : gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
libc                : libc-2.8.90.so
MEMORY INDEX        : 2.446
INTEGER INDEX       : 2.747
FLOATING-POINT INDEX: 3.284
Baseline (LINUX)    : AMD K6/233*, 512 KB L2-cache, gcc 2.7.2.3, libc-5.4.38
* Trademarks are property of their respective holder.

me@vm01:~$ lsmod | grep virtio
virtio_net             19584  0 
virtio_pci             15104  0 
virtio_ring            12800  1 virtio_pci
virtio                 14084  2 virtio_net,virtio_pci

```

**vm02 (Guest)**

```

<domain type='kvm'>
  <name>vm02</name>
  <uuid>2a4a9234-e8cf-b01c-c21c-b0aea193fc4b</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/dev/virtualization/vm02'/>
      <target dev='vda' bus='virtio'/>
    </disk>
    <interface type='bridge'>
      <mac address='52:54:00:fd:e2:84'/>
      <source bridge='br0'/>
      <target dev='vnet2'/>
      <model type='virtio'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
  </devices>
</domain>
*******************************************************************
me@vm02:~$ iperf -c xxx.xxx.xxx.14 -r -t 60 -w 256K
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size:   256 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to xxx.xxx.xxx.14, TCP port 5001
TCP window size:   256 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
[  5] local xxx.xxx.xxx.209 port 40649 connected with xxx.xxx.xxx.14 port 5001
Waiting for server threads to complete. Interrupt again to force quit.
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-60.0 sec    887 MBytes    124 Mbits/sec

me@vm02:~$ bonnie++ -s 2g -n 256
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
vm02             2G  4226  92 17541  71 22417  53  5650  98 80662  70  1283  97
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                256  3453  95 37876  98  3839  83  3598  95 53105  98  3534  77
vm02,2G,4226,92,17541,71,22417,53,5650,98,80662,70,1282.5,97,256,3453,95,37876,98,3839,83,3598,95,53105,98,3534,77

me@vm02:~/nbench-byte-2.2.3$ ./nbench

BYTEmark* Native Mode Benchmark ver. 2 (10/95)
Index-split by Andrew D. Balsa (11/97)
Linux/Unix* port by Uwe F. Mayer (12/96,11/97)

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :          337.04  :       8.64  :       2.84
STRING SORT         :          15.984  :       7.14  :       1.11
BITFIELD            :      5.3752e+07  :       9.22  :       1.93
FP EMULATION        :          25.219  :      12.10  :       2.79
FOURIER             :          2389.3  :       2.72  :       1.53
ASSIGNMENT          :           6.939  :      26.40  :       6.85
IDEA                :          597.85  :       9.14  :       2.71
HUFFMAN             :          302.46  :       8.39  :       2.68
NEURAL NET          :          4.5689  :       7.34  :       3.09
LU DECOMPOSITION    :          193.12  :      10.00  :       7.22
==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 10.487
FLOATING-POINT INDEX: 5.843
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : AuthenticAMD QEMU Virtual CPU version 0.9.1 3159MHz
L2 Cache            : 512 KB
OS                  : Linux 2.6.27-9-server
C compiler          : gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
libc                : libc-2.8.90.so
MEMORY INDEX        : 2.443
INTEGER INDEX       : 2.755
FLOATING-POINT INDEX: 3.241
Baseline (LINUX)    : AMD K6/233*, 512 KB L2-cache, gcc 2.7.2.3, libc-5.4.38
* Trademarks are property of their respective holder.

me@vm02:~/nbench-byte-2.2.3$ lsmod | grep virtio
virtio_net             19584  0 
virtio_blk             14728  4 
virtio_pci             15104  0 
virtio_ring            12800  1 virtio_pci
virtio                 14084  3 virtio_net,virtio_blk,virtio_pci

```

Anything look odd to you?

Thanks!
EightBit

---

### Post by EightBitHustler on 2008-12-30
I came across this page:
[http://libvirt.org/drvqemu.html]("http://libvirt.org/drvqemu.html")

> 
**KVM hypervisor:** The driver will probe /usr/bin  for the presence of qemu-kvm and /dev/kvm device node. If both are found, then KVM fullyvirtualized, hardware accelerated guests will be available. 


I've installed the proper kvm & qemu packages as prescribed in the documentation, but I don't see **/dev/kvm**. 

```

dportello@colossus:~$  ls /dev/k*
/dev/kmem  /dev/kmsg

```

Could this be an issue?

---

### Post by EightBitHustler on 2008-12-30
I also came across this post:
[http://ubuntuforums.org/showthread.php?t=422737#post2553459]("http://ubuntuforums.org/showthread.php?t=422737#post2553459")

Which recommends:
```

sudo modprobe kvm-intel

```

My results are:
```

FATAL: Error inserting kvm_intel (/lib/modules/2.6.27-9-server/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported

```

I see that these kvm modules exist:
```

meo@colossus:~$ ls /lib/modules/2.6.27-9-server/kernel/arch/x86/kvm/
kvm-amd.ko  kvm-intel.ko  kvm.ko

```

I see these modules are loaded:
```

me@colossus:~$ lsmod | grep kvm
kvm                   165744  0

```

Could the lack of a properly loaded kvm-intel module be the cause?

---

### Post by EightBitHustler on 2008-12-30
...And I finally answered my own question by rereading the docs and diving further into the forum

according to...
[https://wiki.ubuntu.com/kvm]("https://wiki.ubuntu.com/kvm")

> 
Typing dmesg you may find the following at the end:-
 kvm: disabled by bios


Sure enough...
```

me@colossus:~$ dmesg | grep kvm
[   27.586229] kvm: disabled by bios
[  282.772155] kvm: disabled by bios

```

DOH!

Moral of the story RTFM!

---

### Post by EightBitHustler on 2008-12-31
This morning I had someone in my office enable the virtualization extensions in the BIOS. I re-ran my bonnie benchmarks and here are the results

```

-------------------------------------------------------------------------------
Host system
-------------------------------------------------------------------------------

Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
colossus        32G 76730  88 218667  46 96284  17 76906  81 273038  23  1141   3
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                256 67646  87 +++++ +++ 13106  15 72814  92 +++++ +++ 12249  16
colossus,32G,76730,88,218667,46,96284,17,76906,81,273038,23,1141.5,3,256,67646,87,+++++,+++,13106,15,72814,92,+++++,+++,12249,16

-------------------------------------------------------------------------------
Before virtual extensions were enabled
-------------------------------------------------------------------------------

Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
vm02             2G  4226  92 17541  71 22417  53  5650  98 80662  70  1283  97
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                256  3453  95 37876  98  3839  83  3598  95 53105  98  3534  77
vm02,2G,4226,92,17541,71,22417,53,5650,98,80662,70,1282.5,97,256,3453,95,37876,98,3839,83,3598,95,53105,98,3534,77

-------------------------------------------------------------------------------
After virtual extensions were enabled
-------------------------------------------------------------------------------

Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
vm02             2G 71855  85 260611  25 211285  31 88313  93 414699  30 +++++ +++
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                256 67351  90 517207  98 44379  72 71398  96 +++++ +++ 34968  72
vm02,2G,71855,85,260611,25,211285,31,88313,93,414699,30,+++++,+++,256,67351,90,517207,98,44379,72,71398,96,+++++,+++,34968,72

```

As you can see the performance is near the host system. On this test I had another vm running, but not doing anything with it.

On some of the metrics, the performance appears to be better than the host. I'm sure this could be due to caching.

**Net performance**
```

-------------------------------------------------------------------------------
Host system
-------------------------------------------------------------------------------

me@colossus:~$ iperf -c guardian -r -t 60
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to guardian, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  5] local xxx.xxx.xxx.206 port 53483 connected with xxx.xxx.xxx.205 port 5001
Waiting for server threads to complete. Interrupt again to force quit.
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-60.0 sec  6.58 GBytes    942 Mbits/sec

-------------------------------------------------------------------------------
Guest system
-------------------------------------------------------------------------------
me@vm02:~$iperf -c guardian -r -t 60        
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to guardian, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  5] local xxx.xxx.xxx.209 port 38786 connected with xxx.xxx.xxx.205 port 5001
Waiting for server threads to complete. Interrupt again to force quit.
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-60.0 sec  5.10 GBytes    731 Mbits/sec

```

**CPU performance**
```

-------------------------------------------------------------------------------
Host system (8 cores, I'm guessing nbench only operates on one core)
-------------------------------------------------------------------------------
me@colossus:~/nbench-byte-2.2.3$ ./nbench 

BYTEmark* Native Mode Benchmark ver. 2 (10/95)
Index-split by Andrew D. Balsa (11/97)
Linux/Unix* port by Uwe F. Mayer (12/96,11/97)

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :          1503.3  :      38.55  :      12.66
STRING SORT         :          333.84  :     149.17  :      23.09
BITFIELD            :       6.047e+08  :     103.73  :      21.67
FP EMULATION        :           327.2  :     157.01  :      36.23
FOURIER             :           33823  :      38.47  :      21.61
ASSIGNMENT          :          45.084  :     171.55  :      44.50
IDEA                :          9100.4  :     139.19  :      41.33
HUFFMAN             :          3067.7  :      85.07  :      27.16
NEURAL NET          :          67.506  :     108.44  :      45.62
LU DECOMPOSITION    :            2115  :     109.57  :      79.12
==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 109.622
FLOATING-POINT INDEX: 77.026
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : 8 CPU GenuineIntel Intel(R) Xeon(R) CPU           X5460  @ 3.16GHz 3159MHz
L2 Cache            : 6144 KB
OS                  : Linux 2.6.27-9-server
C compiler          : gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
libc                : libc-2.8.90.so
MEMORY INDEX        : 28.130
INTEGER INDEX       : 26.788
FLOATING-POINT INDEX: 42.722
Baseline (LINUX)    : AMD K6/233*, 512 KB L2-cache, gcc 2.7.2.3, libc-5.4.38
* Trademarks are property of their respective holder.
-------------------------------------------------------------------------------
Guest system (1 core)
-------------------------------------------------------------------------------
me@vm02:~/nbench-byte-2.2.3$ ./nbench 

BYTEmark* Native Mode Benchmark ver. 2 (10/95)
Index-split by Andrew D. Balsa (11/97)
Linux/Unix* port by Uwe F. Mayer (12/96,11/97)

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :          1497.8  :      38.41  :      12.62
STRING SORT         :          334.08  :     149.28  :      23.11
BITFIELD            :      6.0398e+08  :     103.60  :      21.64
FP EMULATION        :           326.4  :     156.62  :      36.14
FOURIER             :           33739  :      38.37  :      21.55
ASSIGNMENT          :          45.026  :     171.33  :      44.44
IDEA                :          9096.4  :     139.13  :      41.31
HUFFMAN             :            3060  :      84.85  :      27.10
NEURAL NET          :          66.933  :     107.52  :      45.23
LU DECOMPOSITION    :          2119.4  :     109.80  :      79.28
==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 109.453
FLOATING-POINT INDEX: 76.798
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : GenuineIntel QEMU Virtual CPU version 0.9.1 3159MHz
L2 Cache            : 2048 KB
OS                  : Linux 2.6.27-9-server
C compiler          : gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
libc                : libc-2.8.90.so
MEMORY INDEX        : 28.113
INTEGER INDEX       : 26.728
FLOATING-POINT INDEX: 42.595
Baseline (LINUX)    : AMD K6/233*, 512 KB L2-cache, gcc 2.7.2.3, libc-5.4.38
* Trademarks are property of their respective holder.

```

**Final verdict**, KVM is fantastic!

---

### Post by cderigo on 2009-01-28
z

---

