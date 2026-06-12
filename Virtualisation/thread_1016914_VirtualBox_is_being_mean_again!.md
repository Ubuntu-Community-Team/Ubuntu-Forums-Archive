---
title: "VirtualBox is being mean again!"
date: 2008-12-20
forum: Virtualisation
---

### Post by Cadeyrn on 2008-12-20
Ugh, I got VirtualBox to launch properly, but once I get to Windows XP Installation formatting its own partition of my virtual hard drive, it simply closes. No error message. But my computer still continues to lag like HELL as if it were still installing, and when I relaunch VirtualBox it says that virtual machine was aborted. Here's the log of the entire "aborted" session:

```

00:15:47.514 Guest CPUM state: se
00:15:47.514 eax=0000f001 ebx=0000d69d ecx=00160001 edx=00000000 esi=0000000c edi=0000ffd8
00:15:47.514 eip=00000a6e esp=0000ffb6 ebp=0000ffca iopl=0         nv up di pl zr na pe nc
00:15:47.514 cs={f000 base=00000000000f0000 limit=0000ffff flags=00000000} dr0=00000000 dr1=00000000
00:15:47.514 ds={0000 base=0000000000000000 limit=0000ffff flags=00000000} dr2=00000000 dr3=00000000
00:15:47.514 es={07c0 base=0000000000007c00 limit=0000ffff flags=00000000} dr4=00000000 dr5=00000000
00:15:47.514 fs={0000 base=0000000000000000 limit=0000ffff flags=00000000} dr6=ffff0ff0 dr7=00000400
00:15:47.514 gs={0000 base=0000000000000000 limit=0000ffff flags=00000000} cr0=60000010 cr2=00000000
00:15:47.514 ss={0000 base=0000000000000000 limit=0000ffff flags=00000000} cr3=00000000 cr4=00000000
00:15:47.514 gdtr=0000000000000000:ffff  idtr=0000000000000000:ffff  eflags=00000002
00:15:47.514 ldtr={0000 base=00000000 limit=0000ffff flags=00000080}
00:15:47.514 tr  ={0000 base=00000000 limit=0000ffff flags=00000080}
00:15:47.514 SysEnter={cs=0000 eip=00000000 esp=00000000}
00:15:47.514 FPU:
00:15:47.514 FCW=037f FSW=0000 FTW=00
00:15:47.514 res1=00 FOP=0000 FPUIP=00000000 CS=0000 Rsvrd1=0000
00:15:47.514 FPUDP=0000 DS=0000 Rsvrd2=0000 MXCSR=00000000 MXCSR_MASK=00000000
00:15:47.514 MSR:
00:15:47.514 EFER         =0000000000000000
00:15:47.514 PAT          =0007040600070406
00:15:47.514 STAR         =0000000000000000
00:15:47.514 CSTAR        =0000000000000000
00:15:47.514 LSTAR        =0000000000000000
00:15:47.514 SFMASK       =0000000000000000
00:15:47.514 KERNELGSBASE =0000000000000000
00:15:47.514 ***
00:15:47.514 Guest paging mode:  Real, changed 0 times, A20 enabled
00:15:47.514 Shadow paging mode: 32-bit
00:15:47.514 Host paging mode:   32-bit+G
00:15:47.514 ***
00:15:47.514 Active Timers (pVM=b42e4000)
00:15:47.514 pTimerR3 offNext  offPrev  offSched Clock Time               Expire             State                     Description
00:15:47.515 b403a500 00037df0 00000000 00000000 Real  000000000020372108 000000000020368117 ACTIVE                    VGA Refresh Timer
00:15:47.515 b40722f0 00000000 fffc8210 00000000 Real  000000000020372108 000000000020368139 ACTIVE                    EMT Yielder
00:15:47.515 b402b090 00043570 00000000 00000000 Virt  000000044000426281 000000043998721898 ACTIVE                    PDM Poller
00:15:47.515 b406e600 00000000 fffbca90 00000000 Virt  000000044000426281 000000044005755325 ACTIVE                    Audio timer
00:15:47.515 b402cd70 00000360 00000000 00000000 VrSy  000000043990379379 000000044045304780 ACTIVE                    i8254 Programmable Interval Timer
00:15:47.515 b402d0d0 000445b0 fffffca0 00000000 VrSy  000000043990379379 000000044990000000 ACTIVE                    MC146818 RTC/CMOS - Second
00:15:47.515 b4071680 00000000 fffbba50 00000000 VrSy  000000043990379379 000001228417501410 ACTIVE                    ACPI Timer
00:15:47.515 ***
00:15:47.515 Shadow GDT (GCAddr=a099f000):
00:15:47.515 ffd8 - 0de80087 a0008901 - base=a0010de8 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
00:15:47.515 ffe0 - 0d600087 a0008b01 - base=a0010d60 limit=00000087 dpl=0 TSS32Busy Present 16-bit  HyperTSS
00:15:47.515 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
00:15:47.515 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
00:15:47.515 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
00:15:47.515 ***
00:15:47.515 ***
00:15:47.515 ss:sp=0000:ffb6 0000:ff80 TO 0000:1007f:
00:15:47.515 b43fe258 0000: 00 00 00 00 02 00 a8 ff-0c 01 d8 ff 0c 00 a8 ff ................
00:15:47.515 b43fe268 0010: 9a ff 00 00 00 00 01 00-0a 0e 00 00 c0 07 46 00 ..............F.
00:15:47.515 b43fe278 0020: e5 05 00 f0 46 02 9c d6-ae ff 00 00 9d d6 ca ff ....F...........
00:15:47.515 b43fe288 0030: 57 0a 00 f0 9d d6 00 00-c0 ff 00 00 00 00 d0 ff W...............
00:15:47.515 b43fe298 0040: 00 00 d0 ff 00 00 00 00-76 00 d4 ff b7 17 07 00 ........v.......
00:15:47.515 b43fe2a8 0050: 9d d6 00 00 f0 ff dc a1-00 00 00 00 80 00 00 00 ................
00:15:47.515 b43fe2b8 0060: 01 00 00 01 00 00 c0 07-00 00 00 80 02 00 c0 9f ................
00:15:47.515 b43fe2c8 0070: f6 ff 19 a9 03 00 f8 ff-c2 e2 00 f0 82 02 00 00 ................
00:15:47.515 b43fe2d8 0080: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe2e8 0090: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe2f8 00a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe308 00b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe318 00c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe328 00d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe338 00e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe348 00f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 2000:0000 TO 2000:01ff:
00:15:47.515 b43fe258 0000: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe268 0010: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe278 0020: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe288 0030: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe298 0040: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe2a8 0050: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe2b8 0060: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe2c8 0070: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe2d8 0080: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe2e8 0090: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe2f8 00a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe308 00b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe318 00c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe328 00d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe338 00e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe348 00f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe358 0100: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe368 0110: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe378 0120: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe388 0130: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe398 0140: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe3a8 0150: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe3b8 0160: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe3c8 0170: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe3d8 0180: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe3e8 0190: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe3f8 01a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe408 01b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe418 01c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe428 01d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe438 01e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 b43fe448 01f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:15:47.515 ************** End of Guest state at power off ***************
00:15:47.515 Changing the VM state from 'SUSPENDED' to 'OFF'.
00:15:47.517 Changing the VM state from 'OFF' to 'DESTROYING'.
00:15:47.517 ************************* Statistics *************************
00:15:47.517 /Devices/ATA0/Unit0/AtapiDMA            0 times
00:15:47.517 /Devices/ATA0/Unit0/AtapiPIO            0 times
00:15:47.517 /Devices/ATA0/Unit0/DMA                 0 times
00:15:47.517 /Devices/ATA0/Unit0/PIO                 4 times
00:15:47.517 /Devices/ATA0/Unit0/ReadBytes        1024 bytes
00:15:47.517 /Devices/ATA0/Unit0/WrittenBytes        0 bytes
00:15:47.517 /Devices/ATA0/Unit1/AtapiDMA            0 times
00:15:47.517 /Devices/ATA0/Unit1/AtapiPIO            0 times
00:15:47.517 /Devices/ATA0/Unit1/DMA                 0 times
00:15:47.517 /Devices/ATA0/Unit1/PIO                 0 times
00:15:47.517 /Devices/ATA0/Unit1/ReadBytes           0 bytes
00:15:47.517 /Devices/ATA0/Unit1/WrittenBytes        0 bytes
00:15:47.517 /Devices/ATA1/Unit0/AtapiDMA            0 times
00:15:47.517 /Devices/ATA1/Unit0/AtapiPIO           10 times
00:15:47.517 /Devices/ATA1/Unit0/DMA                 0 times
00:15:47.517 /Devices/ATA1/Unit0/PIO                 0 times
00:15:47.517 /Devices/ATA1/Unit0/ReadBytes       20480 bytes
00:15:47.517 /Devices/ATA1/Unit0/WrittenBytes        0 bytes
00:15:47.517 /Devices/ATA1/Unit1/AtapiDMA            0 times
00:15:47.517 /Devices/ATA1/Unit1/AtapiPIO            0 times
00:15:47.517 /Devices/ATA1/Unit1/DMA                 0 times
00:15:47.517 /Devices/ATA1/Unit1/PIO                 0 times
00:15:47.517 /Devices/ATA1/Unit1/ReadBytes           0 bytes
00:15:47.517 /Devices/ATA1/Unit1/WrittenBytes        0 bytes
00:15:47.517 /Devices/PCNet0/ReceiveBytes            0 bytes
00:15:47.517 /Devices/PCNet0/TransmitBytes           0 bytes
00:15:47.517 /GVMM/Sum/HaltBlocking              21388 calls
00:15:47.517 /GVMM/Sum/HaltCalls                 62152 calls
00:15:47.517 /GVMM/Sum/HaltNotBlocking           40764 calls
00:15:47.517 /GVMM/Sum/HaltTimeouts              10816 calls
00:15:47.517 /GVMM/Sum/HaltWakeUps                   0 calls
00:15:47.517 /GVMM/Sum/PollCalls                     0 calls
00:15:47.517 /GVMM/Sum/PollHalts                     0 calls
00:15:47.517 /GVMM/Sum/PollWakeUps                   0 calls
00:15:47.517 /GVMM/Sum/WakeUpCalls               13565 calls
00:15:47.517 /GVMM/Sum/WakeUpNotHalted           11430 calls
00:15:47.517 /GVMM/Sum/WakeUpWakeUps                 0 calls
00:15:47.517 /GVMM/VM/HaltBlocking               21388 calls
00:15:47.517 /GVMM/VM/HaltCalls                  62152 calls
00:15:47.517 /GVMM/VM/HaltNotBlocking            40764 calls
00:15:47.517 /GVMM/VM/HaltTimeouts               10816 calls
00:15:47.517 /GVMM/VM/HaltWakeUps                    0 calls
00:15:47.518 /GVMM/VM/PollCalls                      0 calls
00:15:47.518 /GVMM/VM/PollHalts                      0 calls
00:15:47.518 /GVMM/VM/PollWakeUps                    0 calls
00:15:47.518 /GVMM/VM/WakeUpCalls                13565 calls
00:15:47.518 /GVMM/VM/WakeUpNotHalted            11430 calls
00:15:47.518 /GVMM/VM/WakeUpWakeUps                  0 calls
00:15:47.518 /GVMM/VMs                               1 calls
00:15:47.518 /MM/HyperHeap/cbFree               914688 bytes
00:15:47.518 /MM/HyperHeap/cbHeap              1310656 bytes
00:15:47.518 /PDM/VUSB0/cUrbsInPool                  0 count
00:15:47.518 /PDM/VUSB1/cUrbsInPool                  0 count
00:15:47.518 /PGM/cGuestModeChanges                  0 times
00:15:47.518 /PROF/EM/Halted                  140088315 ticks/call ( 79570162947 ticks,     568 times, max 2273291581, min    1331)
00:15:47.518 /PROF/EM/Total                   80665885124 ticks/call ( 80665885124 ticks,       1 times, max 80665885124, min 80665885124)
00:15:47.518 /PROF/VM/Halt/Block               1260453 ticks/call ( 78328374762 ticks,   62143 times, max  24633015, min    2321)
00:15:47.518 /PROF/VM/Halt/Poll                   9573 ticks/call (   687748919 ticks,   71838 times, max    201685, min    4114)
00:15:47.518 /PROF/VM/Halt/Timers                 5376 ticks/call (   386205754 ticks,   71838 times, max  15319733, min    1419)
00:15:47.518 /PROF/VM/Halt/Yield                     0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:15:47.518 /TM/R3/1nsSteps                     31666 times
00:15:47.518 /TM/VirtualSync/CurrentOffset      506377 ns
00:15:47.518 ********************* End of statistics **********************
00:15:47.530 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
```

---

### Post by Titan8990 on 2008-12-20
Does your hardware support virtualization?

---

### Post by Cadeyrn on 2008-12-20
That depends. Does the August 2006 edition of the iMac, 2nd worst model, Intel, have hardware that supports it?

I do have a decent processor and video card and hard drive and everything. I don't see why it shouldn't support it.

---

### Post by Cadeyrn on 2008-12-20
That depends. Does the August 2006 edition of the iMac, 2nd worst model, Intel, have hardware that supports it?

I do have a decent processor and video card and hard drive and everything. I don't see why it shouldn't support it.

EDIT: Aw crap, double-post.

---

### Post by Cadeyrn on 2008-12-20
BUMP.

I need this fixed!!!

---

### Post by Shazaam on 2008-12-20
Go here and download/burn the live cd iso...
```
http://gparted.sourceforge.net/download.php
```
1. Set your VBox vm to boot from the cd first and pop the gparted cd in.
2. Make sure the cdrom is mounted (vm Settings).
3. Start the vm.
4. Use the GParted livecd to make the vm partion(s) you need, formatted to ntfs.
5. Reboot the vm.
6. Try to install Windows again.

---

### Post by Cadeyrn on 2008-12-21
Alright, thanks. I'm sure this'll work but I can't try it yet because 50 MB will take pretty long on my internet.

I'll try it tomorrow.

---

### Post by Cadeyrn on 2008-12-21
Alright, thanks. I'm sure this'll work but I can't try it yet because 50 MB will take pretty long on my internet.

I'll try it tomorrow.

---

### Post by Shazaam on 2008-12-21
In a pinch you could use the Ubuntu livecd version of gparted. I like the stand-alone version because it has a basic linux os and gparted only so you don't have other unneeded stuff loading up at boot.

---

### Post by Cadeyrn on 2008-12-21
So, how does this thing work? Is it just an iso that GParted turns into a shortcut for whatever disc is in the physical drive?

---

### Post by Cadeyrn on 2008-12-21
Alright, I managed to figure it out for myself and chose the auto-livecd thing. It did its stuff and asked me about my keyboard and language and stuff, and when it was eventually finished loading GParted it turned into this:

Edit bodhi.zazen : Please do not post such large images on the forums, use thumb nails , LOL

Truthfully, the VM became resized to be bigger than my computer screen, but I wanted to resize it before I took the picture for no apparent reason. XD

---

### Post by Shazaam on 2008-12-21
Try to boot it again but this time, when the first screen comes up, choose "force vesa" instead of the default first line and that should take care of the graphics glitch.

---

### Post by Cadeyrn on 2008-12-21
Umm... This time it did this:

[IMG]http://img116.imageshack.us/img116/6309/vboxbug2nq9.png[/IMG]

By the way, ignore the messed-up toolbars--that's because I have a full screen game in the other workspace.

---

### Post by Shazaam on 2008-12-21
Hmmm. You may have to close everything but VirtualBox. How much memory do you have and how much do you have allocated to the Windows vm?

---

### Post by Cadeyrn on 2008-12-21
XDDDDDDDDDDDDDDDDDDD I'm such an idiot.

Looking back at the settings I just realized I set the RAM to 2.5 GHz, thinking it was the partition size! I set it to 512 MB and tried running it without any other programs, and... I got the same result as the last screenshot. :\

---

### Post by Cadeyrn on 2008-12-21
And then I remembered my computer only has 512, so I set it to 224 MB. But still the same result.

---

### Post by Cadeyrn on 2008-12-22
Bump!

---

