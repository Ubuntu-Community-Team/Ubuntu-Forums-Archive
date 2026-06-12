---
title: "Kernel 4.19.0-041900rc2-generic is available from kernel-ppa"
date: 2018-09-04
forum: Ubuntu Development Version
---

### Post by mrfelker on 2018-09-04
The latest kernel from kernel-mainline is available and works great

---

### Post by corradoventu on 2018-09-24
also rc4 works fine... but can I do something useful by testing it?
```
corrado@corrado-HP-p7-cc-0911:~$ uname -a
Linux corrado-HP-p7-cc-0911 4.19.0-041900rc4-generic #201809162031 SMP Sun Sep 16 20:33:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-HP-p7-cc-0911:~$ inxi -SCx
System:    Host: corrado-HP-p7-cc-0911 Kernel: 4.19.0-041900rc4-generic x86_64 bits: 64 
           compiler: gcc v: 8.2.0 Desktop: Gnome 3.30.0 Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
CPU:       Topology: Dual Core model: Intel Core i5-4210U bits: 64 type: MT MCP arch: Haswell 
           rev: 1 L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 19155 
           Speed: 798 MHz min/max: 800/2700 MHz Core speeds (MHz): 1: 798 2: 799 3: 798 4: 798 
corrado@corrado-HP-p7-cc-0911:~$ 
```

---

### Post by #&amp;thj^% on 2018-10-05
Some of the fixes for 4.19
```
User visible changes:

* allow defrag on opened read-only files that have rw permissions; similar
to what dedupe will allow on such files


Core changes:

* tree checker improvements, reported by fuzzing:
* more checks for: block group items, essential trees
* chunk type validation
* mount time cross-checks that physical and logical chunks match
* switch more error codes to EUCLEAN aka. EFSCORRUPTED


Fixes:

* fsync corner case fixes

* fix send failure when root has deleted files still open

* send, fix incorrect file layout after hole punching beyond eof

* fix races between mount and deice scan ioctl, found by fuzzing

* fix deadlock when delayed iput is called from writeback on the same
inode; rare but has been observed in practice, also removes code

* fix pinned byte accounting, using the right percpu helpers; this should
avoid some write IO inefficiency during low space conditions

* don't remove block group that still has pinned bytes

* reset on-disk device stats value after replace, otherwise this would
report stale values for the new device


Cleanups:

* time64_t/timespec64 cleanups

* remove remaining dead code in scrub handling NOCOW extents after
disabling it in previous cycle

* simplify fsync regarding ordered extents logic and remove all the
related code

* remove redundant arguments in order to reduce stack space consumption

* remove support for V0 type of extents, not in use since 2.6.30

* remove several unused structure members

* fewer indirect function calls by inlining some callbacks

* qgroup rescan timing fixes

* vfs: iget cleanups


```
More information here: [https://www.phoronix.com/scan.php?page=article&item=linux-419-features&num=1](https://www.phoronix.com/scan.php?page=article&item=linux-419-features&num=1)
and as reported here: [https://linux.slashdot.org/story/18/...e-linux-kernel](https://linux.slashdot.org/story/18/...e-linux-kernel)
> "Using the newly minted Linux 4.19 feature code, fresh benchmarks were carried out looking at the performance cost of Spectre/Meltdown/Foreshadow mitigations on Intel Xeon v. AMD EPYC CPUs," writes an anonymous Slashdot reader:
Workloads affected by these CPU vulnerabilities mainly deal with I/O and frequent kernel calls while CPU bound tests are still found to be minimally impacted. When toggling these mitigations on Linux 4.19, Intel Xeon CPUs were found to be 10~15% slower with the default kernel while AMD EPYC CPUs dropped to about 5% slower.
I notice no impact here with:
```
System:
  Host: me-750-417c **Kernel: 4.19.0-041900rc6-lowlatency x86_64 bits: 64 **
  compiler: gcc v: 8.2.0 Desktop: Xfce 4.12.3 tk: Gtk 2.24.31 
  info: xfce4-panel wm: Compiz 0.9.13.1 dm: lightdm 1.26.0 
  Distro: Ubuntu 18.04.1 LTS (Bionic Beaver) 
CPU:
  Topology: Dual Core model: Intel Core i5-3320M bits: 64 type: MT MCP 
  arch: Ivy Bridge rev: 9 L2 cache: 3072 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 20753 
  Speed: 3227 MHz max: 3300 MHz Core speeds (MHz): 1: 3227 2: 3100 3: 2947 
  4: 3044 

```

---

### Post by corradoventu on 2018-10-24
also the new 4.19 works fine for me on Cosmic
```
corrado@corrado-p9-cosmic-x:~$ inxi -Sx
System:
  Host: corrado-p9-cosmic-x Kernel: 4.19.0-041900-generic x86_64 bits: 64 
  compiler: gcc v: 8.2.0 Desktop: Gnome 3.30.1 
  Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
corrado@corrado-p9-cosmic-x:~$ 
```

---

### Post by oldos2er on 2018-10-24
Cosmic is released, so closed.

---

