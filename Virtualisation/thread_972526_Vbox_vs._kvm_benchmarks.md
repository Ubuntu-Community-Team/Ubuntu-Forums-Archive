---
title: "Vbox vs. kvm benchmarks"
date: 2008-11-05
forum: Virtualisation
---

### Post by rmcewen on 2008-11-05
I ran some common benchmarks to test the performance of kvm/VBox guests.

I tested using iperf for network performance, bonnie++ for disk io, and nbench for cpu.

I ran all three tests in the following environments:

a. Natively on the host machine which is an AMD quad core box with 8GB ram, running Ubuntu 8.04 server, and raid 1.

b. KVM guest running Ubuntu 8.04 server, 1GB ram, 1 cpu, bridged networking.  Virtio drivers installed on guest.

c. VBox guest running Ubuntu 8.04 server, 1GB ram, 1 cpu, bridged networking.  VBox guest extensions installed on guest. Hardware virtualization turned on.

This isn't a scientific test and results only reflect my particular installation.

In summary, both guests appeared to achieve near native performance for the cpu.  kvm achieved near native performance on the network test while VBox was quite a bit slower.  Disk benchmarks were mixed, likely due to the guest "filesystems" being actually flat files on the host.

```
*******************************************************************
Ubuntu Host
*******************************************************************

root@vhost:~# iperf -c 192.168.1.21 -r -t 60 -w 256K
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size:   256 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.1.21, TCP port 5001
TCP window size:   256 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
[  5] local 192.168.1.24 port 34100 connected with 192.168.1.21 port 5001
[  5]  0.0-60.0 sec  6.22 GBytes    890 Mbits/sec
[  4] local 192.168.1.24 port 5001 connected with 192.168.1.21 port 42290
[  4]  0.0-60.0 sec  6.57 GBytes    941 Mbits/sec

bonnie++ -u root -s 16g -n 256
Version 1.03b       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
vhost           16G 60520  98 78100   9 31212   3 59705  96 73122   3 467.9   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                256  2656  21 +++++ +++  2564   6  2483  19 +++++ +++   479   1

root@ubuntu:~/nbench-byte-2.2.3# ./nbench

BYTEmark* Native Mode Benchmark ver. 2 (10/95)
Index-split by Andrew D. Balsa (11/97)
Linux/Unix* port by Uwe F. Mayer (12/96,11/97)

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :          1413.2  :      36.24  :      11.90
STRING SORT         :             212  :      94.73  :      14.66
BITFIELD            :      3.4596e+08  :      59.35  :      12.40
FP EMULATION        :           376.4  :     180.61  :      41.68
FOURIER             :           22821  :      25.95  :      14.58
ASSIGNMENT          :          28.292  :     107.66  :      27.92
IDEA                :          6405.4  :      97.97  :      29.09
HUFFMAN             :          2203.6  :      61.11  :      19.51
NEURAL NET          :          41.374  :      66.46  :      27.96
LU DECOMPOSITION    :          1417.9  :      73.46  :      53.04
==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 81.417
FLOATING-POINT INDEX: 50.226
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : AuthenticAMD AMD Phenom(tm) 9850 Quad-Core Processor 2490MHz
L2 Cache            : 512 KB
OS                  : Linux 2.6.24-19-server
C compiler          : gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
libc                : libc-2.7.so
MEMORY INDEX        : 17.185
INTEGER INDEX       : 23.035
FLOATING-POINT INDEX: 27.857
Baseline (LINUX)    : AMD K6/233*, 512 KB L2-cache, gcc 2.7.2.3, libc-5.4.38


*******************************************************************
Ubuntu Guest - VirtualBox
*******************************************************************
root@ubuntu:~# iperf -c 192.168.1.21 -r -t 60 -w 256K
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size:   240 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.1.21, TCP port 5001
TCP window size:   240 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
[  5] local 192.168.1.188 port 41367 connected with 192.168.1.21 port 5001
[  5]  0.0-60.0 sec  3.12 GBytes    446 Mbits/sec
[  4] local 192.168.1.188 port 5001 connected with 192.168.1.21 port 41881
[  4]  0.0-60.0 sec  2.53 GBytes    363 Mbits/sec

bonnie++ -s 1g -n 256 -u root
Version 1.03b       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ubuntu           1G 26181  48 45633   4 111211   3 56238  84 591957   4 10422  99
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                256  4170  53 +++++ +++  7182  97  4056  93 143594  98  3707  75

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :          1412.5  :      36.22  :      11.90
STRING SORT         :          212.64  :      95.01  :      14.71
BITFIELD            :      3.4052e+08  :      58.41  :      12.20
FP EMULATION        :          379.12  :     181.92  :      41.98
FOURIER             :           23040  :      26.20  :      14.72
ASSIGNMENT          :          28.321  :     107.77  :      27.95
IDEA                :          6437.4  :      98.46  :      29.23
HUFFMAN             :          2212.9  :      61.36  :      19.60
NEURAL NET          :          41.014  :      65.89  :      27.71
LU DECOMPOSITION    :          1438.1  :      74.50  :      53.80
==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 81.465
FLOATING-POINT INDEX: 50.476
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : 4 CPU AuthenticAMD AMD Phenom(tm) 9850 Quad-Core Processor 2500MHz
L2 Cache            : 512 KB
OS                  : Linux 2.6.24-19-generic
C compiler          : gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
libc                : libc-2.7.so
MEMORY INDEX        : 17.117
INTEGER INDEX       : 23.127
FLOATING-POINT INDEX: 27.996
Baseline (LINUX)    : AMD K6/233*, 512 KB L2-cache, gcc 2.7.2.3, libc-5.4.38

*******************************************************************
Ubuntu Guest - KVM
*******************************************************************
root@ubuntu:~/nbench-byte-2.2.3# iperf -c 192.168.1.21 -r -t 60 -w 256K
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size:   240 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.1.21, TCP port 5001
TCP window size:   240 KByte (WARNING: requested   256 KByte)
------------------------------------------------------------
[  5] local 192.168.1.32 port 48184 connected with 192.168.1.21 port 5001
[  5]  0.0-60.0 sec  6.57 GBytes    941 Mbits/sec
[  4] local 192.168.1.32 port 5001 connected with 192.168.1.21 port 58301
[  4]  0.0-60.0 sec  6.57 GBytes    941 Mbits/sec

Version 1.03b       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ubuntu           1G 45843  83 55582   5 44949   9 55360  95 499887  66 +++++ +++
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                256 66952  75 471763 100 47008  47 83531  90 +++++ +++ 10979  12

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :            1419  :      36.39  :      11.95
STRING SORT         :          213.28  :      95.30  :      14.75
BITFIELD            :      3.5392e+08  :      60.71  :      12.68
FP EMULATION        :          377.76  :     181.27  :      41.83
FOURIER             :           22941  :      26.09  :      14.65
ASSIGNMENT          :            28.4  :     108.07  :      28.03
IDEA                :            6420  :      98.19  :      29.15
HUFFMAN             :          2201.9  :      61.06  :      19.50
NEURAL NET          :          41.007  :      65.87  :      27.71
LU DECOMPOSITION    :          1430.1  :      74.09  :      53.50
==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 81.905
FLOATING-POINT INDEX: 50.307
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : AuthenticAMD QEMU Virtual CPU version 0.9.1 2500MHz
L2 Cache            : 512 KB
OS                  : Linux 2.6.24-19-server
C compiler          : gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
libc                : libc-2.7.so
MEMORY INDEX        : 17.372
INTEGER INDEX       : 23.088
FLOATING-POINT INDEX: 27.902


```

---

