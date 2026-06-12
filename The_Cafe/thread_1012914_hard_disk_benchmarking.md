---
title: "hard disk benchmarking"
date: 2008-12-16
forum: The Cafe
---

### Post by jsowoc on 2008-12-16
Hi, I have a WinXP Pro/Ubuntu Hardy dual-boot system on one hard drive, and recently added a second hard drive for my files. On this second (non-system) hard drive, I'd like to create a "temp" partition where I could work on movies (i.e. a few large files), extract archives (i.e. a hundred thousand source files).

I don't need any permissions, journalling, etc.; all I need is speed. From what I've read, these are my choices:
- ext2 (I'd be using an IFS for Windows, any suggestions for speed?)
- ntfs (I'd be using ntfs-3g for Linux, unless any suggestions)
- fat/vfat

Does anyone know of any nice hard disk benchmark utilities that I could run to help me decide? Ideally, I'd like to run the same program under Windows and Linux to get a better feel for the numbers.

P.S. I know there are a few million hits for various benchmarks already done, but I would like to perform them on my specific hardware setup. For example, this one:
[http://ubuntuforums.org/showthread.php?t=364031](http://ubuntuforums.org/showthread.php?t=364031)

---

### Post by sydbat on 2008-12-16
Choose ntfs. Ubuntu can read/write to it easily. 

Personally, I would not let my Windows partition access my Linux files, but that is my bias.

About benchmarks - not sure if they are necessary. The speed will be determined by the connection (sata or ide). If it is sata, you should have good enough throughput.

---

### Post by jsowoc on 2008-12-17
I figured out that I can run bonnie++ under Cygwin, but I didn't let the benchmarks finish because bonnie++ was running very slowly under Cygwin. I didn't feel it would be a fair comparison.

I do have a set of benchmarks done under 64-bit Ubuntu Hardy with versions of ntfs-progs, etc., as in the repositories. The hardware is a Seagate 1TB Barracuda 7200.11 SATA II, with the partition occupying the first 64 GB of the hard drive. Processor was a Core2 Duo E8400, and I was not doing other things on the computer at the time.

vfat under Linux (formatted using mkfs.vfat)
```

Version 1.03e       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
jsowoc-deskto 7400M 68668  96 90968  13 46149   8 72292  93 110127   5 259.0   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16   149  99   293  99  1395 100   247  99   288  99   480  99
```

ntfs under Linux (formatted from Windows with "full format")
```

Version 1.03e       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
jsowoc-deskto 7400M 44559  56 81971   8 35776   4 69651  94 103851   3 154.9   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 10790   8 +++++ +++ 12558  10  8610  11 +++++ +++ 10377   7
```

ext2 under Linux (formatted with mke2fs)
```

Version 1.03e       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
jsowoc-deskto 7400M 70856  97 103352   9 45189   5 87793  88 109088   5 246.4   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  8178  99 +++++ +++ +++++ +++  5827  99 +++++ +++ 18925  99
```

It seems that for most things (except creating tiny files) ext2 is faster than ntfs, with vfat trailing the pack. I realise this could be because of my implementation, but that is part of what I am testing.

Any suggestions on Windows-native benchmarks I could run to look at ext2/ntfs under Windows?

---

