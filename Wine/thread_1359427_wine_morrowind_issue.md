---
title: "wine morrowind issue"
date: 2009-12-19
forum: Wine
---

### Post by Gosujii-sama on 2009-12-19
Reinstalled complete system fresh of ubuntu 9.04 upgraded to 9.10 installed wine setup wine now trying to install morrowind i get this error:

```
construct@Diabolic:~$ wine /media/cdrom0/Setup.exe
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0032fe58 EBP:0032fea8 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:7b8b4ff4 ECX:5663afaa EDX:0032ff10
 ESI:7ffdf000 EDI:004024b5
Stack dump:
0x0032fe58:  004024c3 7ffdf000 7b8b4ff4 00000000
0x0032fe68:  00000000 00000000 00000000 00000000
0x0032fe78:  00000000 680222fe 00000000 00000000
0x0032fe88:  00000000 00000000 00000000 00000000
0x0032fe98:  00000000 00000000 7b8b4ff4 7ffdf000
0x0032fea8:  0032fee8 7b8774a4 7ffdf000 00000000
Backtrace:
=>0 0x00000000 (0x0032fea8)
  1 0x7b8774a4 in kernel32 (+0x574a4) (0x0032fee8)
  2 0x7bc6daa4 call_thread_func+0xc() in ntdll (0x0032fef8)
  3 0x7bc6dc70 call_thread_entry_point+0x70() in ntdll (0x0032ffc8)
  4 0x7bc4a2fa in ntdll (+0x3a2fa) (0x0032ffe8)
  5 0x68024e9d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
0x00000000: addb	%al,0x0(%eax)
Modules:
Module	Address			Debug info	Name (18 modules)
PE	  400000-  411000	Deferred        setup
ELF	68000000-6801d000	Deferred        ld-linux.so.2
ELF	6801d000-68158000	Export          libwine.so.1
ELF	68158000-68171000	Deferred        libpthread.so.0
ELF	68171000-68175000	Deferred        libdl.so.2
ELF	68175000-6819b000	Deferred        libm.so.6
ELF	6819b000-681b2000	Deferred        libnsl.so.1
ELF	681b2000-681bd000	Deferred        libnss_nis.so.2
ELF	681bd000-681c9000	Deferred        libnss_files.so.2
ELF	681c9000-681de000	Deferred        system.drv16.so
PE	681d0000-681de000	Deferred        system.drv16
ELF	6c431000-6c439000	Deferred        libnss_compat.so.2
ELF	75b8a000-75cce000	Deferred        libc.so.6
ELF	7b800000-7b972000	Export          kernel32<elf>
  \-PE	7b820000-7b972000	\               kernel32
ELF	7bc00000-7bcb4000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb4000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\Setup.exe
	00000009    0 <==
0000000e 
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
0000001a 
	0000001b    0
Backtrace:
=>0 0x00000000 (0x0032fea8)
  1 0x7b8774a4 in kernel32 (+0x574a4) (0x0032fee8)
  2 0x7bc6daa4 call_thread_func+0xc() in ntdll (0x0032fef8)
  3 0x7bc6dc70 call_thread_entry_point+0x70() in ntdll (0x0032ffc8)
  4 0x7bc4a2fa in ntdll (+0x3a2fa) (0x0032ffe8)
  5 0x68024e9d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)

```

what have i missed? if i remember right i had to custom install libwine.so.1 n such but i doubt thats the case anymore so.... ya

---

### Post by beastrace91 on 2009-12-19
What Wine version? I know under the latest version the Morrowind installer should load right up.

~Jeff

---

### Post by Gosujii-sama on 2009-12-19
I'm using the newest version 1.1.35 should I regress it? I have three games I want working with wine one being morrowind one being war3tft one being d2lod. so finding a regression all 3 work on has been tricky. maybe i should consider like your tag says multiple wine installs for each individual game with its best regression for that game. I'm going to just do that. Do you know which version worked best on morrowind?

---

### Post by beastrace91 on 2009-12-19
I know personally the last Wine version I had time to sit down and play Morrowind on was 1.1.32 (and I also had D2 and WC3 running under this as well).

I'd start there if I where you, before that I also had good luck getting most of my games to run under 1.1.28

Regards,
~Jeff

---

