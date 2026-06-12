---
title: "Trying to install on IBM OpenPower server"
date: 2008-08-26
forum: Server Platforms
---

### Post by kasper.sorensen on 2008-08-26
Hello everybody

I'm having a very hard time installing the [community port of Ubuntu Server]("http://cdimage.ubuntu.com/ports/releases/8.04/release/") on to an IBM PowerServer 710 (even though it says on the webpage that it's a supported platform).

Once I boot up on the CD this is what I get:

> 
Please wait, loading kernel...
   Elf32 kernel loaded...
Loading ramdisk...
ramdisk loaded at 02200000, size: 5775 Kbytes
OF stdout device is: /vdevice/vty@30000000
command line: ro ramdisk_size=8192 file=/cdrom/preseed/ubuntu-server.seed quiet -- 
memory layout at init:
  alloc_bottom : 027a4000
  alloc_top    : 20000000
  alloc_top_hi : 20000000
  rmo_top      : 20000000
  ram_top      : 20000000
Looking for displays
instantiating rtas at 0x07734000 ... done
WARNING: maximum CPUs (1) exceeded: ignoring extras
copying OF device tree ...
Building dt strings...
Building dt structure...
Device tree strings 0x02aa5000 -> 0x02aa600f
Device tree struct  0x02aa7000 -> 0x02aad000
Calling quiesce ...
returning from prom_init
DEFAULT CATCH!, exception-handler=fff00300 
at   %SRR0: 0000000000c3c214   %SRR1: 8000000000003002 
Call History
------------
@  - c3c1a8 
find-method  - c46bcc 
(poplocals)  - c3a710 
$call-method  - c46c84 
(poplocals)  - c3a710 
key-fillq  - c471fc 
?xoff  - c472f8 
(poplocals)  - c3a710 
(stdout-write)  - c47924 
(type)  - c479b0 
_syscatch  - c4d804 
_exception  - c4d2c8 
<excp>  - c3982c 
_syscatch  - c4d768 
_syscatch  - c4d768 
invalid pointer - 0 

Client's Fix Pt Regs:
 00 00080000000001f4 ffffffffff0747d4 00000000deadbeef fffffffffffffffc
 04 0000000000000000 0000000000000000 0000000000000000 0000000000000001
 08 0000000000001000 0000030002001000 0000000000000001 0000000000001000
 0c 0000000022000022 0000000000000000 0000000001f0bec4 000000000193fb0c
 10 0000000000daba20 0000000000daba20 0000000000c469cc 0000000000c46bcc
 14 0000000000000000 0000000001bfff81 000000000193f9cc 0000000001f0a5d4
 18 0000000000c13000 0000000000c38000 0000000000c14f40 0000000000c16fc0
 1c 0000000000c20000 0000000000c3fda8 0000000000c11f98 0000000000c10fd0
Special Regs:
    %IV: 00000300     %CR: 84000022    %XER: 00000000  %DSISR: 08000000 
  %SRR0: 0000000000c3c214   %SRR1: 8000000000003002 
    %LR: 0000000000c3c1a8    %CTR: 0000000000000000 
   %DAR: ffffffffff0747d4 
Virtual PID = 0 
PFW: Unable to send error log!
 ofdbg


I've also tried installing the Debian Etch powerpc image, but with the same result. Have any one of you got any idea what these error messages mean? And have anyone succesfully installed Debian or Ubuntu Server on an IBM OpenPower server? If so I'd love to hear how you did!

---

