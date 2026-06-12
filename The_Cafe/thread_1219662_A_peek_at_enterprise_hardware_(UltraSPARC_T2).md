---
title: "A peek at enterprise hardware (UltraSPARC T2)"
date: 2009-07-22
forum: The Cafe
---

### Post by toupeiro on 2009-07-22
Its not really everyone who gets the opportunity to pop the hood on some of the cool enterprise hardware out there.  SPARC architecture is on rather shaky ground since the Oracle buyout, with all kinds of rumors flying around.  The truth about SPARC hardware, as hardware, is that it is some phenomenal stuff.  I just recently got my hands on a T5220 server with a Single UltraSPARC T2 running solaris 10.  For those unfimilar, the UltraSPARC T2 is capable of handling 64 threads per socket.  I thought I would do a prtdiag to show how this CPU registers to the operating system because I think it is rather impressive.  prtdiag can display system information, similar to cat /proc/cpuinfo etc etc.. in Linux.  And yes, you are reading it right.  The OS registers 64 processors.. They don't call the UltraSPARC T2 "coolthreads" for nothing. :)  Keep in mind, this is a 2RU, single socket server.  The T2 Plus can handle 128 threads per socket simultaneously!  If you figure that a standard Intel or AMD chip can handle 2 threads per core, think of how many, or what kind of an Intel or AMD server you would need to handle the same amount of multi-threaded operations that this server can do.  Oh, and last but not least, they are certified to support ubuntu!

```
========================= CPUs ===============================================

 

                            CPU                 CPU

Location     CPU   Freq     Implementation      Mask

------------ ----- -------- ------------------- -----

MB/CMP0/P0   0     1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P1   1     1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P2   2     1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P3   3     1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P4   4     1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P5   5     1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P6   6     1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P7   7     1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P8   8     1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P9   9     1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P10  10    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P11  11    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P12  12    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P13  13    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P14  14    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P15  15    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P16  16    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P17  17    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P18  18    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P19  19    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P20  20    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P21  21    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P22  22    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P23  23    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P24  24    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P25  25    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P26  26    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P27  27    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P28  28    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P29  29    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P30  30    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P31  31    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P32  32    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P33  33    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P34  34    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P35  35    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P36  36    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P37  37    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P38  38    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P39  39    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P40  40    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P41  41    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P42  42    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P43  43    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P44  44    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P45  45    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P46  46    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P47  47    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P48  48    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P49  49    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P50  50    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P51  51    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P52  52    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P53  53    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P54  54    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P55  55    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P56  56    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P57  57    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P58  58    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P59  59    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P60  60    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P61  61    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P62  62    1165 MHz SUNW,UltraSPARC-T2

MB/CMP0/P63  63    1165 MHz SUNW,UltraSPARC-T2
```

---

### Post by stwschool on 2009-07-22
I want one.

---

### Post by handy on 2009-07-22
What's the story on GPU's or graphic card slots on these things?

Can you plug in a current nVidia equipped card (or two, or more)? :)

Great games server, if you could get a good 3D graphics card into it as well it looks like you could host various & multiple games whilst playing one as well...

---

### Post by toupeiro on 2009-07-22
There are 6 PCI-E slots total on these servers.  2x 8-lane and 4x 4-lane.  There are no SLi capabilities on this machine.  This is a rack-mount only piece of hardware.  You wouldn't want this sitting on your desk. :)

I know sun used to be in the high end visualisation market, but they aren't really so much anymore.  At least, not one of the key players.   Sun used to have its own branded XVR series video cards which used ATi or NVidia chipsets, but this was some time ago, and in their workstation models. Their big card in their SPARC workstations was the XVR-2500 which was an ATi FireMV.  the ATi Fire line were equivalent to NVidia's Quadro-FX line.  They were beasts (and still are.)  The Sun Ultra 24 workstation can run a Quadro-FX 5600 card, but the only thing is that the Ultra 24 is a Nehalem workstation, so I doubt that a vanilla Quadro-FX card would work in a SPARC machine, even though its using a PCI-E form factor.


This is really an enterprise server.  In fact, the server itself does not even come with on board video.  It's optional to order an XVR card, but its designed to run completely headless.  This would be a killer game Server, as in to host a game environment that thousands of people played on, but maybe not so much to be a client gaming machine.

---

### Post by handy on 2009-07-22
Thanks for your informative reply. :)

It certainly looks built to do a lot of work.

---

### Post by osifanatic on 2011-11-10
Has anyone been able to install some version of Ubuntu as the Base OS for one of these T5220's?  I read only a few months back that this piece of hardware is "Certified" to run Ubuntu, but now the links have gone cold.

I'd -REALLY- like to get some Linux flavor on the box rather than Solaris, so if anyone has been successful in doing so, can you please let me know so I know how to continue?

Cheers,
-Chris

---

### Post by CharlesA on 2011-11-10
Ancient thread. Closed.

---

