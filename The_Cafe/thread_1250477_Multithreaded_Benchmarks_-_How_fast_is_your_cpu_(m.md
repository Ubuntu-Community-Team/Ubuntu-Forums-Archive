---
title: "Multithreaded Benchmarks - How fast is your cpu? (multithread version)"
date: 2009-08-26
forum: The Cafe
---

### Post by hwttdz on 2009-08-26
Meant to be a sister thread to a thread which seems to be generating a fair bit of interest [Super Pi Ubuntu]("http://ubuntuforums.org/showthread.php?t=60264").  I tested with a multithreaded pi calculation running through wine, I don't like this because it's not at all open and it has to use wine.  So I'm investigating phoronix test suite as an alternative.  

I'm currently having some problems setting up the tests, it appears that phoronix test suite wgets the source for a few different tests, and has no control over the servers, so many of them are down.  

apt-get install phoronix-test-suite
phoronix-test-suite benchmark build-apache

This test seems to work, and it's from the multicore set.  Anyways I'm not impressed by this as a benchmark (my cpu utilization was under 25% for much of the test, and for taking 3*25 seconds for the test itself the script was running for almost twice that long.  Anyways:

```
####################################
Timed Apache Compilation:
Time To Compile

25.5858740807 Seconds
25.5882549286 Seconds
25.2795541286 Seconds

Average: 25.48 Seconds
####################################
```

I'd love to hear other people's suggestions for tests. Oh yes this is a core 2 quad, with
sudo dmidecode |grep -i MHz|grep Current
Current Speed: 3485 MHz

---

### Post by hwttdz on 2009-08-26
Slightly more enlightening is 
phoronix-test-suite benchmark compress-7zip

```
====================================
7-Zip Compression (Run 3 of 3)
====================================


7-Zip (A)  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

RAM size:    3895 MB,  # CPU hardware threads:   4
RAM usage:    850 MB,  # Benchmark threads:      4

Dict        Compressing          |        Decompressing
      Speed Usage    R/U Rating  |    Speed Usage    R/U Rating
       KB/s     %   MIPS   MIPS  |     KB/s     %   MIPS   MIPS

22:    9098   268   3303   8851  |   129899   388   3020  11720
23:    9954   300   3378  10142  |   126116   382   3022  11541
24:    9896   317   3352  10641  |   124267   384   3000  11529
25:    9513   315   3447  10861  |   121965   385   2975  11469
----------------------------------------------------------------
Avr:          300   3370  10124               385   3004  11565
Tot:          343   3187  10844

####################################
7-Zip Compression:
Phoronix Test Suite v1.6.0

9741 Average MIPS
9939 Average MIPS
10124 Average MIPS

Average: 9934.66 Average MIPS
####################################
```

---

