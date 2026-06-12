---
title: "Only one CPU shows on P-4 dual core"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by djsroknrol on 2012-04-20
I did a clean install of Precise on a P-4 2.8 MHz but only one core shows in cpuinfo....how can I turn the other CPU on, if that's even possible?

---

### Post by Gompa on 2012-04-20
what kernel are you using ?
you can run uname -a to check it

---

### Post by djsroknrol on 2012-04-20
```
bob@Ubuntu:~$ uname -a
Linux Ubuntu 3.2.0-17-generic-pae #27-Ubuntu SMP Fri Feb 24 15:59:25 UTC 2012 i686 i686 i386 GNU/Linux
bob@Ubuntu:~$ 


```

I was going to try:

```
MAXCPUS=2
```

in my menu.list and see if that helps next.....

---

### Post by djsroknrol on 2012-04-20
MAXCPUS didn't work....:(

---

### Post by for.i.am.root on 2012-04-20
There is no second core on any P4. Check your BIOS and make sure HT is on.

It's a single core dual thread CPU. And I don't think the 2.8 is HT. I think the 3.2 was.

Edit:

Some 2.8's were hyper threaded. Sorry.

---

### Post by pbrane on 2012-04-20
post the output of **cat /proc/cpuinfo**. that will help us help you.

---

### Post by djsroknrol on 2012-04-20
```
bob@Ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 9
microcode	: 0x2e
cpu MHz		: 2792.930
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips	: 5585.86
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

bob@Ubuntu:~$ 

```

I couldn't find a SMP kernel in Synaptic and I know that it showed 2 CPU's in Lucid....:(

---

### Post by for.i.am.root on 2012-04-20
[http://ark.intel.com/products/27495/Intel-Pentium-4-Processor-supporting-HT-Technology-2_80-GHz-512K-Cache-800-MHz-FSB](http://ark.intel.com/products/27495/Intel-Pentium-4-Processor-supporting-HT-Technology-2_80-GHz-512K-Cache-800-MHz-FSB)

Northwood C family CPU. 
Is Ubuntu handling thread counting differently now?
Yup. Hyper Threading disabled by default now.

Re: [http://ubuntuforums.org/showthread.php?p=895077](http://ubuntuforums.org/showthread.php?p=895077)

Just realized that's a really old post. Oops.

I know... I'm the worst with editing my post. I post stuff and ask questions them answer my questions via an edit and sometimes it's missed.

I hate double posting though.

---

### Post by dino99 on 2012-04-20
[QUOTE=djsroknrol]

in my menu.list and see if that helps next.....[/QUOTE]

P4 have a single core, and you should no more use menu.list with actual config. Now grub2 aka grub-pc is used.

---

### Post by for.i.am.root on 2012-04-20
I have the same family CPU in a rig here. I'm downloading precise now. I'll let you know what I figure out. Probably pae related.

> 
To detect if you are using hyperthreading (aka Intel Hyperthreading Technology) you can use dmidecode.

In a terminal:

sudo dmidecode > /tmp/dmidecode.txt gksudo gedit /tmp/dmidecode.txt

Look for a Status value of Populated, Enabled (shown below between * ... *) i.e. "Enabled" means that hyperthreading is active


[http://askubuntu.com/questions/72999/how-can-i-test-if-ubuntu-activated-hyperthreading](http://askubuntu.com/questions/72999/how-can-i-test-if-ubuntu-activated-hyperthreading)

---

### Post by anselm on 2012-04-20
Hi,

Make sure HT is enabled in your bios.

When I installed my P4 3.06 Ht, I had to enable HT in the bios.

12.04 see's my P4 as a dual core.

---

### Post by djsroknrol on 2012-04-20
I can't explain how or why it showed 2 CPU's in Lucid...I just presumed that it would show 2 CPU's again in Precise and it doesn't. Here's my dmidecode.tex on the processor:
```
# dmidecode 2.11
SMBIOS 2.3 present.
76 structures occupying 2653 bytes.
Table at 0x000FBF10.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Intel Corp.
	Version: BF86510A.86A.0075.P24.0503071605
	Release Date: 03/07/2005
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 kB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
	Manufacturer:                                
	Product Name:                                
	Version:                        
	Serial Number:                                
	UUID: 21FFF857-A330-11D7-B9BC-00E018EB099A
	Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Intel Corporation              
	Product Name: D865GLC                        
	Version: AAC28903-403           
	Serial Number: BTLC32500733                   

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer:                                
	Type: Unknown
	Lock: Not Present
	Version:                        
	Serial Number:                                
	Asset Tag:                                
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Other
	Security Status: Other
	OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: J2E1
	Type: Central Processor
	Family: Pentium 4
	Manufacturer: Intel            
	ID: 29 0F 00 00 FF FB EB BF
	Signature: Type 0, Family 15, Model 2, Stepping 9
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Multi-threading)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Pentium(R) 4 processor                     
	Voltage: 3.3 V 2.9 V
	External Clock: 200 MHz
	Max Speed: 3060 MHz
	Current Speed: 2800 MHz
	Status: **Populated, Enabled**
	Upgrade: Socket 478
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.

```

---

### Post by for.i.am.root on 2012-04-20
Socket 478 is a North wood. Only the 3.06 GHz version had HT. Is this a laptop or desktop?

Has to be a laptop with the Northwood Pentium 4 M 2.8 HT.

Hyperthreading is on, not sure why it doesn't show up in the GUI though.

CPU info:
[http://ark.intel.com/products/27375/Mobile-Intel-Pentium-4-Processor-supporting-HT-Technology-2_80-GHz-512K-Cache-533-MHz-FSB](http://ark.intel.com/products/27375/Mobile-Intel-Pentium-4-Processor-supporting-HT-Technology-2_80-GHz-512K-Cache-533-MHz-FSB)

---

### Post by djsroknrol on 2012-04-20
Desktop...that's why I threw the MB info in there:

```
Base Board Information
	Manufacturer: Intel Corporation              
	Product Name: D865GLC                        
	Version: AAC28903-403           
	Serial Number: BTLC32500733              
```

---

### Post by for.i.am.root on 2012-04-20
Works fine on Dell Optiplex GX620 Pentium 4 2.8 HT.

See attached.

---

### Post by for.i.am.root on 2012-04-20
> **djsroknrol said:**
> Desktop...that's why I threw the MB info in there:

```
Base Board Information
	Manufacturer: Intel Corporation              
	Product Name: D865GLC                        
	Version: AAC28903-403           
	Serial Number: BTLC32500733              
```

If it's a Desktop P4 @ 2.8 GHz socket 478 then it is not hyper threaded.
WRONG! It's a Costa Rica chip. DUH. Somebody slap me.

What threw me off was the cache. The 2.8 prescott (P4 HT, socket 478 ) has 1024 of cache, not 512. His only has 512k of cache. I forgot about the stupid Costa Rica chips. And I thought I was awesome when I bought one back in 04. :-D

On a side note I don't really like the layout of 12.04. I have no idea where anything is and have been using F2 for everything :-D

---

### Post by djsroknrol on 2012-04-20
There has to be an answer for this...any ideas anyone?

---

### Post by ventrical on 2012-04-20
> **for.i.am.root said:**
> Works fine on Dell Optiplex GX620 Pentium 4 2.8 HT.

See attached.


  I have 2 Dells that will not report my dual cores one a P4 2.8 GXOpit270 and the other a  Dimension 3100 3.0GHz. They are both desktops , but when I remove them and put them in another PC then the dual core shows up.

---

### Post by for.i.am.root on 2012-04-20
Check your dmidecode. The hyper threading is enabled just not showing up as a second core. (On the OP's, anyway)

I have a problem with my rig at home still reporting 2.6 even though it's at 3.192 right now. It runs at 3.192, just gnome-system-monitor reports 2.6 incorrectly.

Check your BIOS settings and see if that helps.

---

### Post by ventrical on 2012-04-20
> **for.i.am.root said:**
> Check your dmidecode. The hyper threading is enabled just not showing up as a second core. (On the OP's, anyway)

I have a problem with my rig at home still reporting 2.6 even though it's at 3.192 right now. It runs at 3.192, just gnome-system-monitor reports 2.6 incorrectly.

Check your BIOS settings and see if that helps.

On the Diemension the hyperthreading was turned off.. so now I have :

```
ventrical@ventrical-Dell-DV051:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 1
microcode    : 0x17
cpu MHz        : 2992.509
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr
bogomips    : 5985.01
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 1
microcode    : 0x17
cpu MHz        : 2992.509
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr
bogomips    : 5984.94
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

ventrical@ventrical-Dell-DV

```

---

### Post by for.i.am.root on 2012-04-20
Siblings 2 means it is utilizing both threads.

It's not a true dual core processor. It's a single core with 2 threads. This *may* be why it is not showing up as a dual core.

---

### Post by ventrical on 2012-04-20
> **for.i.am.root said:**
> Siblings 2 means it is utilizing both threads.

It's not a true dual core processor. It's a single core with 2 threads. This *may* be why it is not showing up as a dual core.


But it is showing up as dual core now, after I enabled HT.

---

### Post by cariboo on 2012-04-20
Dual threading will show up as dual cores, even though it isn't. My [atom 270]("http://ark.intel.com/products/36331/Intel-Atom-Processor-N270-(512K-Cache-1_60-GHz-533-MHz-FSB)") is a single core processor with hyper-threading, it also shows as a dual core cpu when running 

```
cat /proc/cpuinfo
```

@ventrical, if you check the Intel web site, you'll see that your cpu is also a single core:

[http://ark.intel.com/products/27497/Intel-Pentium-4-Processor-supporting-HT-Technology-3_00-GHz-1M-Cache-800-MHz-FSB](http://ark.intel.com/products/27497/Intel-Pentium-4-Processor-supporting-HT-Technology-3_00-GHz-1M-Cache-800-MHz-FSB)

---

### Post by ventrical on 2012-04-20
> **cariboo907 said:**
> Dual threading will show up as dual cores, even though it isn't. My [atom 270]("http://ark.intel.com/products/36331/Intel-Atom-Processor-N270-%28512K-Cache-1_60-GHz-533-MHz-FSB%29") is a single core processor with hyper-threading, it also shows as a dual core cpu when running 

```
cat /proc/cpuinfo
```@ventrical, if you check the Intel web site, you'll see that your cpu is also a single core:

[http://ark.intel.com/products/27497/Intel-Pentium-4-Processor-supporting-HT-Technology-3_00-GHz-1M-Cache-800-MHz-FSB](http://ark.intel.com/products/27497/Intel-Pentium-4-Processor-supporting-HT-Technology-3_00-GHz-1M-Cache-800-MHz-FSB)

 Yes ... I see that now .. What a bummer ! :) So , it appears, on my Dell Opti also.. but I still have a couple more to test.

---

### Post by ventrical on 2012-04-20
The one with my nvidiaGF210/218 has a dual core.

```
~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) D  CPU 2.66GHz
stepping    : 7
microcode    : 0x3
cpu MHz        : 2666.857
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips    : 5333.71
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) D  CPU 2.66GHz
stepping    : 7
microcode    : 0x3
cpu MHz        : 2666.857
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips    : 5334.01
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

dale@dale-desktop:~$ 

```

---

### Post by ventrical on 2012-04-20
Thats 2 ! :

I'm so embarassed..

```
~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 104
model name    : AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57
stepping    : 2
cpu MHz        : 1900.000
cache size    : 256 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips    : 3790.43
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 104
model name    : AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57
stepping    : 2
cpu MHz        : 1900.000
cache size    : 256 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips    : 3790.49
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

dale@dale-laptop:~$ 

```

---

### Post by for.i.am.root on 2012-04-20
I'll save you the trouble. There are no dual core Pentium 4. Pentium D 805 was the first. Which by the way is only about $20 bucks and over clocks very high very easily.

Air cooled my 2.6 was running at 3.6. But the FSB is only 533.

I have an e2220 which I picked up real cheap as well and is oc'd easily from 2.6 to 3.2 and 800 FSB. It'll run you about $30.

---

### Post by ventrical on 2012-04-20
> **for.i.am.root said:**
> I'll save you the trouble. There are no dual core Pentium 4. Pentium D 805 was the first. Which by the way is only about $20 bucks and over clocks very high very easily.

Air cooled my 2.6 was running at 3.6. But the FSB is only 533.

I have an e2220 which I picked up real cheap as well and is oc'd easily from 2.6 to 3.2 and 800 FSB. It'll run you about $30.


  Thanks for the info. I think I'll look into some minor upgrades about here. The 2.66 dual is faster than the others. Mabey it being a Dual core is why. This has been a really good infosession about processors.

  Just an off topic side note ..were there any big problems when you O'cled your 2.66?

---

### Post by for.i.am.root on 2012-04-20
Nope. Both the Pentium D 805 and e2220 are just "soft" locked to their respective speeds. You should skip the lower FSB and just pick up the e2220, which has an unlocked multiplier.

The Pentium D 805 has a 20x multiplier so you will be stuck at a FSB (probably) less than 200. Right around 170 which means you need ram rated at least 800 or you have to over clock your 667 ram. Any faster than 800 and your rig will constantly freeze / crash.

E2220 is 800 with an unlocked multiplier so you can adjust your bus speed and lower your multiplier.

For instance on my rig (e2220) my multiplier is 12 and my bus is at 266 to match my RAM (266*4=1064) makes my rig run at (266*12=3192) 3.2 instead of 2.6.

Stock heat sink will get you at least 2.9 if that specific one can be overclocked.

If it is a stock brand mobo (OEM) you probably won't be able to overclock.

Anyway, overclocking is beyond the scope of this topic and I hate drifting off topic. I can help you out if needed. Just let me know.

---

### Post by ventrical on 2012-04-20
Just doing some reading up ... How can we tell that Precise is actually using both cores in a genuine dual core processor? I was reading where often programs are written (ie games) where the AI and other instructions will only utilize one core, leaving the other null. Is there a sudo command to actually tell us if both cores are being used other that what is shown by the System Monitor?

with Precise it is concurrency=makefile

It used to be concurrency=shell to make both cores work. I wonder what changed?

---

### Post by xyzzyman on 2012-04-20
> **ventrical said:**
> Just doing some reading up ... How can we tell that Precise is actually using both cores in a genuine dual core processor? I was reading where often programs are written (ie games) where the AI and other instructions will only utilize one core, leaving the other null. Is there a sudo command to actually tell us if both cores are being used other that what is shown by the System Monitor?

with Precise it is concurrency=makefile

It used to be concurrency=shell to make both cores work. I wonder what changed?

Even when you're 'main' running program is single-threaded, the scheduler in the kernel will make use of the other cores because you have all those other processes running.

---

### Post by VinDSL on 2012-04-20
S478 P4s RAWK!  :D

Here's my Extreme Edition...

```
vindsl@Zuul:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping	: 5
microcode	: 0x1b
cpu MHz		: 3407.588
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips	: 6815.17
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping	: 5
microcode	: 0x1b
cpu MHz		: 3407.588
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips	: 6815.82
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

```


The P4EE uses single-core NetBurst microarchitecture, but shows up as dual-core, in "System Details" & Conky, because of Hyper-Threading technology.


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-20-apr-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-20-apr-2012-1.png")[/INDENT]

---

### Post by for.i.am.root on 2012-04-20
I actually like your desktop! I might just upgrade now and put a bunch of time into customizing it thanks to you.

Sorry, off topic again.

---

### Post by Bill Murnane on 2012-04-20
This may be similar to my setup, a Pentium D which instead of multiple cores per processor had 2 processors. It also supports Hyperthreading.
Natty  cpuinfo:

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 3
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 4
cpu MHz        : 2992.584
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 5985.16
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 3
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 4
cpu MHz        : 2992.584
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 5985.33
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:
```

Under Oneiric and since I have had to run with acpi=off or nolapic due to a kernel bug.  See launchpad bug #878031
Since then only 1 processor is detected.
I have unsuccessfully tried to report this bug upstream.

---

### Post by ventrical on 2012-04-21
I got pretty well the same thing here Vin.

---

### Post by for.i.am.root on 2012-04-21
Hi Bill:

Not sure what is going on with the GUI app or how it works but cpuinfo is reporting 2 cpu's and both are hyper threaded. The siblings flag will report the number of threads. In this case 2 threads each.

You can verify that they are both enabled using dmidecode. You can also check your settings in the BIOS and verify that it did not get reset somehow.

---

### Post by Bill Murnane on 2012-04-21
Yes, that's the last kernel on which it did. Now only one processor shows. I thought it might throw some light on the original problem reported here.
Now that kernel.bugzilla.org is again available I reported the upstream bug, 43140 - Bad EIP value during startup in all Kernels, failed after 3.0.0.12 (worked up to 2.6.38.8) , Pentium D processor, Intel D865PERL board with latest available BIOS

---

### Post by VinDSL on 2012-04-21
> **for.i.am.root said:**
> I actually like your desktop! I might just upgrade now and put a bunch of time into customizing it thanks to you.

Sorry, off topic again.
Heh!  Yeah, I have that effect on ppl...

A while back, everyone was complaining about Unity having the icons on the left, instead of the bottom... so, I moved them to the bottom... looked like mung!  

After posting screenies, for a couple of months, with the icons on the bottom, you could have heard a pin drop in the forums, here and elsewhere. Nobody wanted to admit they were wrong.

Anyway, I've been customizing Unity from day-one.  It's easy!  Anyone can do it.  You just have to use a different technique than Gnome 2.

Okay, back on topic, now.  ;)

---

