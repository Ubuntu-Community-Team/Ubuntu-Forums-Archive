---
title: "newly installed RAM issue--Ubuntu 9.04(Jaunty)"
date: 2009-06-09
forum: Server Platforms
---

### Post by Jago6060 on 2009-06-09
Quick run down: Ubuntu Server 9.04(64 bit) with all necessary packages, etc.  OS is installed on a SuperMicro Server.  SM Server has 3.2 Intel Xeon CPU, 2GB stock RAM(2x1GB), 2GB aftermarket RAM(2x1GB), 500GB hard drive, NIC cards, etc.

Problem:  The 2GB of aftermarket(Brand: Crucial) ram was recently installed.  It is matched to the specs exactly.  The problem is that Ubuntu is not recognizing it.  Here is some output...

root@supermicro:~# free -m
                    total       used       free     shared    buffers     cached
Mem:          1986       1910         75          0         77       1281
-/+ buffers/cache:        551       1435
Swap:          5820         43       5777
root@supermicro:~# 


root@supermicro:~# dmidecode |more

Handle 0x0017, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: Single-bit ECC
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4   <-------------(sees 4 sticks of RAM but doesn't use all of them?)

I haven't figured out if it's Ubuntu that's not recognizing the RAM, or if its the BIOS causing Ubuntu to not recognize the RAM.  Any help would be greatly appreciated!

---

### Post by windependence on 2009-06-09
Be very careful where you put the RAM sticks. On the SuperMicro board, they have to be populated a certain way or they will not be recognized. Read over the board manual again and let us know if that solved the problem.

-Tim

---

### Post by Jago6060 on 2009-06-10
Thanks, I'll check the manual.  Just for the record, I tried a few different configurations and if I had it wrong, the system would beep numerous times and refuse to start.  So I figured I cured the problem when I got the system to boot...am I wrong in this assumption?  Also, the Ram is seated the in the following pattern: Stock RAM slots 1 & 3, Aftermarket RAM slots 2 & 4.

---

### Post by Jago6060 on 2009-06-10
Ok, I checked the manual and it just confirmed what I've already found.  My RAM "positioning" is correct.  I'm still not sure exactly what the problem is though.  Both the BIOS and Ubuntu are only recognizing 2GB of RAM.  Any ideas?

---

### Post by Jago6060 on 2009-06-10
Problem solved.  My IT Manager ordered Dual Channel Ram without knowing the server doesn't support it.  :(

---

