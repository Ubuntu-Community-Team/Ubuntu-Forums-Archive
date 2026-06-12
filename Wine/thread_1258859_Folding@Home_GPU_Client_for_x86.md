---
title: "Folding@Home GPU Client for x86"
date: 2009-09-05
forum: Wine
---

### Post by coolbrook on 2009-09-05
I followed the instructions at the **[http://gpu2.twomurs.com/index.php?title=Main_Page](http://gpu2.twomurs.com/index.php?title=Main_Page)** wiki and this is the output of my attempt to run the GPU client for x86 Linux

```
--- Opening Log file [September 5 11:15:01 UTC] 


# Windows GPU Console Edition #################################################
###############################################################################

                       Folding@Home Client Version 6.23

                          

###############################################################################
###############################################################################

Launch directory: Z:\home\steven\Folding@home-Win32-GPU_XP-623
Executable: Z:\home\steven\Folding@home-Win32-GPU_XP-623\Folding@home-Win32-GPU.exe
Arguments: -forcegpu nvidia_g80 

[11:15:01] Configuring Folding@Home...

User name [Anonymous]? coolbrook
Team Number [0]? 
Passkey []? 
Ask before fetching/sending work (no/yes) [no]? 
Use proxy (yes/no) [no]? 
Acceptable size of work assignment and work result packets (bigger units
 may have large memory demands) -- 'small' is <5MB, 'normal' is <10MB, and
 'big' is >10MB (small/normal/big) [normal]? 
Change advanced options (yes/no) [no]? 

[11:15:46] - Ask before connecting: No
[11:15:46] - User name: coolbrook (Team 0)
[11:15:46] - User ID: 
[11:15:46] - Machine ID: 2
[11:15:46] 
[11:15:46] Work directory not found. Creating...
[11:15:46] Could not open work queue, generating new queue...
[11:15:46] - Preparing to get new work unit...
[11:15:46] + Attempting to get work packet
[11:15:46] - Connecting to assignment server
[11:15:46] - Successful: assigned to (171.64.65.106).
[11:15:46] + News From Folding@Home: Welcome to Folding@Home
[11:15:46] Loaded queue successfully.
[11:15:47] + Closed connections
[11:15:47] 
[11:15:47] + Processing work unit
[11:15:47] Core required: FahCore_11.exe
[11:15:47] Core not found.
[11:15:47] - Core is not present or corrupted.
[11:15:47] - Attempting to download new core...
[11:15:47] + Downloading new core: FahCore_11.exe
[11:15:48] + 10240 bytes downloaded
[11:15:48] + 20480 bytes downloaded
[11:15:48] + 30720 bytes downloaded
[11:15:48] + 40960 bytes downloaded
[11:15:48] + 51200 bytes downloaded
[11:15:48] + 61440 bytes downloaded
[11:15:48] + 71680 bytes downloaded
[11:15:48] + 81920 bytes downloaded
[11:15:48] + 92160 bytes downloaded
[11:15:49] + 102400 bytes downloaded
[11:15:49] + 112640 bytes downloaded
[11:15:49] + 122880 bytes downloaded
[11:15:49] + 133120 bytes downloaded
[11:15:49] + 143360 bytes downloaded
[11:15:49] + 153600 bytes downloaded
[11:15:49] + 163840 bytes downloaded
[11:15:49] + 174080 bytes downloaded
[11:15:49] + 184320 bytes downloaded
[11:15:49] + 194560 bytes downloaded
[11:15:49] + 204800 bytes downloaded
[11:15:49] + 215040 bytes downloaded
[11:15:49] + 225280 bytes downloaded
[11:15:49] + 235520 bytes downloaded
[11:15:49] + 245760 bytes downloaded
[11:15:49] + 256000 bytes downloaded
[11:15:49] + 266240 bytes downloaded
[11:15:49] + 276480 bytes downloaded
[11:15:49] + 286720 bytes downloaded
[11:15:49] + 296960 bytes downloaded
[11:15:49] + 307200 bytes downloaded
[11:15:49] + 317440 bytes downloaded
[11:15:49] + 327680 bytes downloaded
[11:15:49] + 337920 bytes downloaded
[11:15:49] + 348160 bytes downloaded
[11:15:49] + 358400 bytes downloaded
[11:15:50] + 368640 bytes downloaded
[11:15:50] + 378880 bytes downloaded
[11:15:50] + 389120 bytes downloaded
[11:15:50] + 399360 bytes downloaded
[11:15:50] + 409600 bytes downloaded
[11:15:50] + 419840 bytes downloaded
[11:15:50] + 430080 bytes downloaded
[11:15:50] + 440320 bytes downloaded
[11:15:50] + 450560 bytes downloaded
[11:15:50] + 460800 bytes downloaded
[11:15:50] + 471040 bytes downloaded
[11:15:50] + 481280 bytes downloaded
[11:15:50] + 491520 bytes downloaded
[11:15:50] + 501760 bytes downloaded
[11:15:50] + 512000 bytes downloaded
[11:15:50] + 522240 bytes downloaded
[11:15:50] + 532480 bytes downloaded
[11:15:50] + 542720 bytes downloaded
[11:15:51] + 552960 bytes downloaded
[11:15:51] + 563200 bytes downloaded
[11:15:51] + 573440 bytes downloaded
[11:15:51] + 583680 bytes downloaded
[11:15:51] + 593920 bytes downloaded
[11:15:51] + 604160 bytes downloaded
[11:15:51] + 614400 bytes downloaded
[11:15:51] + 624640 bytes downloaded
[11:15:51] + 634880 bytes downloaded
[11:15:51] + 642475 bytes downloaded
[11:15:51] Verifying core Core_11.fah...
[11:15:51] Signature is VALID
[11:15:51] 
[11:15:51] Trying to unzip core FahCore_11.exe
[11:15:52] Decompressed FahCore_11.exe (1843200 bytes) successfully
[11:15:57] + Core successfully engaged
[11:16:02] 
[11:16:02] + Processing work unit
[11:16:02] Core required: FahCore_11.exe
[11:16:02] Core found.
[11:16:02] Working on queue slot 01 [September 5 11:16:02 UTC]
[11:16:02] + Working ...
wine: Unhandled illegal instruction at address 0x553b1e (thread 0020), starting debugger...
Unhandled exception: illegal instruction in 32-bit code (0x00553b1e).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00553b1e ESP:0033fda4 EBP:0033fe70 EFLAGS:00010202(  R- --  I   - - - )
 EAX:cccccccc EBX:00000001 ECX:00000000 EDX:005dfddc
 ESI:00555290 EDI:0033fe70
Stack dump:
0x0033fda4:  00555330 00555290 00000001 cccccccc
0x0033fdb4:  cccccccc cccccccc cccccccc cccccccc
0x0033fdc4:  cccccccc cccccccc cccccccc cccccccc
0x0033fdd4:  cccccccc cccccccc cccccccc cccccccc
0x0033fde4:  cccccccc cccccccc cccccccc cccccccc
0x0033fdf4:  cccccccc cccccccc cccccccc cccccccc
Backtrace:
=>0 0x00553b1e in fahcore_11 (+0x153b1e) (0x0033fe70)
  1 0x00517c89 in fahcore_11 (+0x117c89) (0x0033ff08)
  2 0x7b8776f9 in kernel32 (+0x576f9) (0x0033ffe8)
0x00553b1e: repe (bad)	
Modules:
Module	Address			Debug info	Name (24 modules)
PE	  400000-  5e6000	Export          fahcore_11
ELF	7b800000-7b96b000	Export          kernel32<elf>
  \-PE	7b820000-7b96b000	\               kernel32
ELF	7bc00000-7bcae000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcae000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7ec85000-7ecda000	Deferred        advapi32<elf>
  \-PE	7ec90000-7ecda000	\               advapi32
ELF	7ecda000-7ed08000	Deferred        ws2_32<elf>
  \-PE	7ece0000-7ed08000	\               ws2_32
ELF	7ed08000-7ed13000	Deferred        libgcc_s.so.1
ELF	7ee06000-7ee51000	Deferred        libcudart.so.2
PE	7ee51000-7ee67000	Deferred        nvcuda
ELF	7ee67000-7ee72000	Deferred        libnss_files.so.2
ELF	7ee72000-7ee8a000	Deferred        libnsl.so.1
ELF	7ee8a000-7ee93000	Deferred        libnss_compat.so.2
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7efed000-7eff6000	Deferred        librt.so.1
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c28000-b7c2c000	Deferred        libdl.so.2
ELF	b7c2c000-b7d7b000	Deferred        libc.so.6
ELF	b7d7b000-b7d93000	Deferred        libpthread.so.0
ELF	b7da7000-b7ee2000	Deferred        libwine.so.1
ELF	b7ee4000-b7f00000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	0000001e    0
	0000001d    0
	0000001c    0
	0000001b    0
	00000009    0
0000000e 
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000018    0
	00000016    0
	00000013    0
	00000012    0
0000001f (D) Z:\home\steven\Folding@home-Win32-GPU_XP-623\FahCore_11.exe
	00000020    0 <==
00000023 
	00000024    0
Backtrace:
=>0 0x00553b1e in fahcore_11 (+0x153b1e) (0x0033fe70)
  1 0x00517c89 in fahcore_11 (+0x117c89) (0x0033ff08)
  2 0x7b8776f9 in kernel32 (+0x576f9) (0x0033ffe8)
[11:16:37] CoreStatus = C000001D (-1073741795)
[11:16:37] Client-core communications error: ERROR 0xc000001d
[11:16:37] This is a sign of more serious problems, shutting down.

```
My hardware is in the first line of my signature.  Help is greatly appreciated.

---

### Post by RabidWeezle on 2009-09-05
might I suggest the boinc client, I've used it on rosetta@home myself, and I think it's already setup for folding@home

---

### Post by coolbrook on 2009-09-06
I'm running BOINC.  I want to make use of my CUDA enabled GPU on 32-bit Linux.

---

### Post by castlefox on 2009-09-06
"might I suggest the boinc client, I've used it on rosetta@home myself, and I think it's already setup for folding@home "

Im rather sure rosetta@home can not help contribute to folding@home



What version of WINE are you using ?

---

### Post by coolbrook on 2009-09-06
I received an update to Wine through update manager since your post.

Version 1.1.29 (though it must have been a minor update)


I tried to run folding@home again and achieved the same result.  I'll reboot and try it again. I've made a duplicate of the original post at foldingforum.org, so hopefully I can get this thing working and if not then I'll see if a Wine bug report can help.  I'm still happy to take advice here.

---

