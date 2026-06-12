---
title: "Installing banana8 on Ubuntu 16.04"
date: 2016-09-09
forum: Ubuntu Studio
---

### Post by Balamku on 2016-09-09
I am trying to run Banana8 on my Ubuntu (freshly upgraded to 16.04 LTS while trying to resolve this installation problem). 
The installation seems pretty simple: [https://www.banana.ch/en/bananaforlinux](https://www.banana.ch/en/bananaforlinux) 
I downloaded and extracted the file. I did run banana8.sh and it told me it successfully did do its things. I did build the icon as instructed but upon double clicking PyPar2 started. I looked for a solution and apparently a broken Qt5 installation causes this. I installed Qt5 and now I have the correct icon and locked it to the launcher, but it does nothing when I click it. 
The file has read and write permission and "Allow executing file as programm" is activated. The terminal shows it in green (read that this should be executable). 

Trying to start via terminal gives this message:
```
j@Serval:~/banana8/bin$ ./banana8.sh
./banana8.sh: line 13: /home/j/banana8/bin/./banana8: cannot execute binary file: Exec format error
j@Serval:~/banana8/bin$ 

"inside" the banana8.sh has the following:
#!/bin/bash
appname=`basename $0 | sed s,\.sh$,,`

dirname=`dirname $0`
tmp="${dirname#?}"

if [ "${dirname%$tmp}" != "/" ]; then
dirname=$PWD/$dirname
fi
LD_LIBRARY_PATH=$dirname
export LD_LIBRARY_PATH
export QT_QPA_PLATFORM_PLUGIN_PATH=$dirname/plugins
$dirname/$appname "$@"
```

If I count right $dirname/$appname "$@" should be line 13, but it give me no clue....

I run a dual boot on iMac Intel® Core™2 Duo CPU E7600 @ 3.06GHz × 2 - 32-bit -384.4 GB partition 3.9 GiB memory
The only things non standard are a lot of audio software installations and customizings for rosegarden etc, but the upgrade to 16.04 eliminated a lot of it....

Please consider me "absolute beginner" - had to digest "metainformation", especially if I need to translate it into terminal commands.

Thx!

Found out that I might run the wrong ubuntu version (32 bit) 
```
j@Serval:~$ uname -i
i686

--> the hardware is 64 bit, but the threads I found seem to be based on "older versions, or at least all the returns I get do not match ... --> does i686 translate to 32 or 64 bit???

Answer or clue how to find out greatly appreciated!

Problem is indeed the 32 bit installation

j@Serval:~$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Model name:            Intel(R) Core(TM)2 Duo CPU     E7600  @ 3.06GHz
Stepping:              10
CPU MHz:               2926.000
CPU max MHz:           3059.0000
CPU min MHz:           1596.0000
BogoMIPS:              6102.96
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority dtherm
j@Serval:~$
```

---

### Post by Balamku on 2016-09-12
I have had Ubuntu 14.04 LTS (was maybe a mistake in the first place to install the "standard") with lots of audio software running as a dual boot on an iMac. 
Rosegarden and especially all the audio settings took weeks to work stable with lots and lots of reading through posts and copy/pasting solutions into the terminal window, manual installations of missing packages etc. 

This week I upgraded to Ubuntu 16.04 LTS.

A tiny book-keeping software refuses to run in my 32 bit Ubuntu (clearly no 32 bit support vendor support). 

I am wondering if 
- I should change the kernel (the idea came up before, since some people advised a different kernel for rosegarden), 
- should I install everything from scratch (with the risk that it might not work and I spend weeks again). 
- And if I install from scratch, which version is best for audio?

Sorry this might sound too global, but it sould have been the one question I should have posted before starting this "project". I am no regular Ubuntu user, so everything takes a long time to understand and resolve...

---

### Post by mörgæs on 2016-09-12
> **Balamku said:**
> 
A tiny book-keeping software refuses to run in my 32 bit Ubuntu (clearly no 32 bit support vendor support). 


Which? Did in run in a 32 bit 14.04?

Though it does happen that some applications are 64 bit only it's a rare event. Chrome is one of the few examples. Best is to investigate this in depth first.

---

### Post by Balamku on 2016-09-13
Its Banana8 ([www.banana.ch]("http://www.banana.ch")) and the website states it does not support 32 bit. It never ran on 14.04 and I did the upgrade because I thought it would help. [https://ubuntuforums.org/showthread.php?t=2336535&highlight=banana8](https://ubuntuforums.org/showthread.php?t=2336535&highlight=banana8) has all the details. Thinking of adding another boot partition....

---

### Post by howefield on 2016-09-13
> **Balamku said:**
> A tiny book-keeping software refuses to run in my 32 bit Ubuntu (clearly no 32 bit support vendor support). 

I am wondering if 
- I should change the kernel (the idea came up before, since some people advised a different kernel for rosegarden), 
- should I install everything from scratch (with the risk that it might not work and I spend weeks again). 
- And if I install from scratch, which version is best for audio?

Threads merged.

Does it have to be that particular application, are there no other alternatives that do support 32 bit ?

You are really looking at a clean reinstall with 64 bit to use that application.

---

### Post by Balamku on 2016-09-13
I spend the last days looking at alternatives, but haven't found anything "no-cloud" without paying a fortune....

---

