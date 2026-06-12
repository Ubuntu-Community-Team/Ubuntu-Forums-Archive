---
title: "Server on ATOM intel"
date: 2008-11-19
forum: Server Platforms
---

### Post by Diubidone on 2008-11-19
Hi All,

I just got this little machine: MSI WIND NETTOP 120
[http://global.msi.com.tw/html/popup/bb/windpc_en/spec.html](http://global.msi.com.tw/html/popup/bb/windpc_en/spec.html) 

It has winxp preinstalled, and there are different versions of it with Linux preinstalled (not this one).

I wanted to make it a small minimal-install LAMP server to run my SUGARCRM software. But at the same time I want to make sure that Ubuntu has full support of the Intel Atom architecture, in order to use it's low energy benefits and keeping it on for many hours during daytime.

Is it something that can be done with Ubuntu server 8.10? Wich version do I have to install?
I'm reading about some LPIA arch for Atom Intels, do I have to change kernel after the installation? 

I really don't want nor have the time to compile everything manualy (as I've been told by some very lonely linux geek at my work). Any advice? Pliz?:confused:

---

### Post by hrod beraht on 2008-11-19
Is it using the Intel D945GCLF motherboard? If that's the case, [[COLOR="Blue"]Intel's linux-compatibility webpage[/COLOR]]("http://www.intel.com/support/motherboards/desktop/d945gclf/sb/CS-029475.htm") shows that it has native support for everything as long as you are running version 8.04.1 or later.

Bob

---

### Post by Diubidone on 2008-11-20
Thanks For your answer.

It looks like it has native support. Here's my hardware specs...can you give me a confirmation?

	> 

MOTHERBOARD SPECS

MICRO-STAR INTERNATIONAL CO., LTD

Model 	MS-7418
Version 	100
Serial Number 	 
  	 
North Bridge 	Intel i945G/GZ Revision A2
South Bridge 	Intel 82801GB (ICH7/R) Revision A2
  	 
CPU 	Genuine Intel(R) CPU 230 @ 1.60GHz
Cpu Socket 	Socket 437 FCBGA8
  	 
Memory Summary 	 
Maximum Capacity 	2048 MBytes
Memory Slots 	1

CPU SPECS

Number of CPU(s) 	One Physical Processor / One Core / 2 Logical Processors / 64 bits
CPU Full Name 	Genuine Intel(R) CPU 230 @ 1.60GHz
Vendor 	GenuineIntel
CPU Name 	Intel Atom 230
CPU Code Name 	Diamondville
Platform Name 	Socket 437 FCBGA8
Revision 	C0
Technology 	45 nm
Instructions 	MMX, SSE, SSE2, SSE3, SSSE3, ET64, XD, HT
Original Clock 	1600 MHz
Original System Clock 	133 MHz
Original Multiplier 	12.1
CPU Clock 	1600 MHz
System Clock 	133.0 MHz
FSB 	532.0 MHz
L1 Data Cache 	24 KBytes
L1 Instructions Cache 	32 KBytes
L2 Cache 	512 KBytes



What version of Ubuntu server would you advise me to install?
Would I still have the energy benefits coming from the CPU... Does the CPU handles energy saving by itself or is it the O.S that does the job?

Thanks...

---

### Post by smileypaul on 2008-11-20
I cant guarantee the hardware is supported..

but generally its the bios that has a switch to enable or disable the C1E state.. which allows the processor to be operating at a slower rate..

The atom processor basically sips power.. so you shouldnt worry.

---

### Post by Diubidone on 2008-11-21
I installed the 8.10 server and then LAMP options.

Man I can barely notice the machine is on...Thx for your help!:popcorn:

---

