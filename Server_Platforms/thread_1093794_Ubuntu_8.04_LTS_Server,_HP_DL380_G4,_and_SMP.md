---
title: "Ubuntu 8.04 LTS Server, HP DL380 G4, and SMP"
date: 2009-03-11
forum: Server Platforms
---

### Post by jberanek on 2009-03-11
I'm hoping someone has a solution.  My work is using Ubuntu 8.04 LTS Server 64bit on an HP DL380 G4 with two 3.0Ghz single core Intel Xeon processors.  After installation, Ubuntu did not recognize the second processor. Initially, this server functioned as a sandbox so a single processor was not a concern, but now we are attempting to run VMWare Server with multiple VMs and need the extra processor for performance.

The only research I've been able to uncover recommend replacing the desktop kernel with the generic kernel in order to make SMP work.  However, this machine is a server and should have have the desktop oriented kernel flags associated with the generic kernel.  My question, is there some issue with 8.04 LTS Server (using the server kernel) that does not allow SMP by default? How can we enable Ubuntu to recognize the second processor?

V/r,

Jason Beranek

---

### Post by capscrew on 2009-03-12
See "[COLOR="Blue"]**[Is a dedicated SMP kernel available from Ubuntu Server install CD]("https://help.ubuntu.com/community/ServerFaq")**[/COLOR]?"

This is about 3/4 of the way down the page.

---

### Post by mikeblaa on 2009-03-13
Some more details on the issue. The server is running kernel version 2.6.24-23 and uname reports the kernel is SMP enabled. 

The dmidecode utility sees 2 CPUs from reading the BIOS. 

The mpstat and lshw utilities both see 2 CPUs but mpstat only reports stats from one and lshw reports that one CPU is disabled. 

The output of /proc/cpuinfo only shows 1 CPU.

What follows are truncated outputs from the utilities. Full outputs are attached.

**_uname output_**
Linux omaha-sandbox 2.6.24-23-server #1 SMP Mon Jan 26 01:36:05 UTC 2009 x86_64 GNU/Linux

**_dmidecode output (truncated)_**
# dmidecode 2.9
SMBIOS 2.3 present.
76 structures occupying 1958 bytes.
...
Handle 0x0400, DMI type 4, 32 bytes
Processor Information
	Socket Designation: Proc 1
	Type: Central Processor
	Family: Xeon
	Manufacturer: Intel
...
Handle 0x0406, DMI type 4, 32 bytes
Processor Information
	Socket Designation: Proc 2
	Type: Central Processor
	Family: Xeon
	Manufacturer: Intel

**_mpstat output_**
Linux 2.6.24-23-server (omaha-sandbox) 	03/13/2009

02:45:28 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
02:45:28 PM  all    8.60    0.00   56.16    2.07    0.00    0.20    0.00   32.98   2091.79
02:45:28 PM    0    8.60    0.00   56.16    2.07    0.00    0.20    0.00   32.98   2091.79
02:45:28 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

**_lshw output (truncated)_**
omaha-sandbox
    description: Rack Mount Chassis
    product: ProLiant DL380 G4
    vendor: HP
...
     *-cpu:0
          description: CPU
          product: Intel(R) Xeon(TM) CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Proc 1
          size: 3GHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall x86-64 constant_tsc up pebs bts pni monitor ds_cpl cid cx16 xtpr
...
     *-cpu:1 DISABLED
          description: CPU
          vendor: Intel
          physical id: 406
          bus info: cpu@1
          slot: Proc 2
          size: 3GHz
          clock: 800MHz
...

**_cat /proc/cpuinfo output_**
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	:                   Intel(R) Xeon(TM) CPU 3.00GHz
stepping	: 3
cpu MHz		: 3000.105
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc up pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr
bogomips	: 6004.20
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:


I'm at a loss with 8.04 LTS. I'm now to the point of trying to either upgrade to 8.10 or try CentOS.

Anyone seen this?

---

### Post by mikeblaa on 2009-03-18
The issue has been resolved. Even though the kernel is an SMP capable kernel, turns out the kernel "alternatives" logic was disabling SMP at boot. This was discovered by examining dmsg:

```

omaha-sandbox:~$ dmesg | grep SMP
[    0.000000] Linux version 2.6.24-23-server (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 01:36:05 UTC 2009 (Ubuntu 2.6.24-23.48-server)
[    0.000000] SMP: Allowing 0 CPUs, 0 hotplug CPUs
[   62.647003] SMP alternatives: switching to UP code
[   62.647906] Freeing SMP alternatives: 24k freed
[   62.980391] SMP motherboard not detected.
[   63.013734] SMP disabled

```

Investigation turned back to the hardware BIOS. Some older posts ([here]("http://forums.fedoraforum.org/archive/index.php/t-54033.html")) suggested changing the BIOS OS setting to "Linux".

This server was running BIOS version P51 (08/16/2005) with ROM-Based Setup Utility version 2.10. This particular BIOS version would not allow me to change the "OS" setting, it reported that the server no longer needed this set.

Reading other posts that mentioned the problem might be with APIC. First tried turning APIC off in the kernel but that had no effect.

Final resolution came from changing the following BIOS option:
```

Advanced Options -> MPS Table Mode to Full Table APIC

```

---

