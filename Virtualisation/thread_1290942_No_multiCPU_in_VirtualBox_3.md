---
title: "No multiCPU in VirtualBox 3"
date: 2009-10-14
forum: Virtualisation
---

### Post by dargaud on 2009-10-14
Hello all,
I have _one_ program that still needs windows _and_ lots of CPU. The latest WINE update of last week reverted all the speed I could previously get (I can see the icons being drawn one after the other...), so I updated virtualBox to virtualbox-3.0 and was delighted to see the new multiprocessor option... except that it doesn't seem to work.

Now I'm not sure where the problem is. Is it that XP was installed in single CPU and now ignores new available CPUs ? Or some problem in VB not showing the processors properly ?

I'd appreciate if someone can help me diagnose this.

```
$ sudo aptitude show virtualbox-3.0
Package: virtualbox-3.0
Version: 3.0.8-53138_Ubuntu_jaunty
...

$ uname -a
Linux penguin 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

$ lshw
lshw
penguin                   
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M. 
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M. 
    width: 64 bits                 
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core                                                                                
       description: Motherboard                                                         
       product: M3A790GXH/128M                                                          
       vendor: ASRock                                                                   
       physical id: 0                                                                   
     *-firmware                                                                         
          description: BIOS                                                             
          vendor: American Megatrends Inc.                                              
          physical id: 0                                                                
          version: P1.00 (02/13/2009)                                                   
          size: 64KiB                                                                   
          capacity: 960KiB                                                              
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot                                      
     *-cpu                                                                                                                                     
          description: CPU                                                                                                                     
          product: AMD Phenom(tm) II X4 10 Processor                                                                                           
          vendor: Advanced Micro Devices [AMD]                                                                                                 
          physical id: 4                                                                                                                       
          bus info: cpu@0                                                                                                                      
          version: AMD Phenom(tm) II X4 10 Processor                                                                                           
          serial: To Be Filled By O.E.M.                                                                                                       
          slot: CPUSocket                                                                                                                      
          size: 800MHz                                                                                                                         
          capacity: 2600MHz                                                                                                                    
          width: 64 bits                                                                                                                       
          clock: 200MHz                                                                                                                        
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpufreq                                                                               
        *-cache:0                                                                                                                              
             description: L1 cache                                                                                                             
             physical id: 5                                                                                                                    
             slot: L1-Cache                                                                                                                    
             size: 512KiB                                                                                                                      
             capacity: 512KiB                                                                                                                  
             capabilities: pipeline-burst internal varies data                                                                                 
        *-cache:1                                                                                                                              
             description: L2 cache                                                                                                             
             physical id: 6                                                                                                                    
             slot: L2-Cache                                                                                                                    
             size: 2MiB                                                                                                                        
             capacity: 2MiB                                                                                                                    
             capabilities: pipeline-burst internal varies unified                                                                              
...

```

---

### Post by Perryg on 2009-10-14
To be able to use SMP in VBox you will need to turn on hardware-v in the bios.  VBox is looking for the VMX flag and from what I see here it is not available.

---

### Post by maxxjr on 2009-10-14
> **dargaud said:**
> Hello all,
I have _one_ program that still needs windows _and_ lots of CPU. The latest WINE update of last week reverted all the speed I could previously get (I can see the icons being drawn one after the other...), so I updated virtualBox to virtualbox-3.0 and was delighted to see the new multiprocessor option... except that it doesn't seem to work.

Now I'm not sure where the problem is. Is it that XP was installed in single CPU and now ignores new available CPUs ? Or some problem in VB not showing the processors properly ?



Two points:

One, is that the IO APIC functionality currently has a bug for AMD processors.  This is required for multiple CPU's.  When I tried VirtualBox a few releases ago, the dual-CPU virtual PC was ~3x slower compared to the single-CPU vPC, in installing and booting Windows.  A release note for one of the newer versions of Virtualbox states that the performance issue has been improved, but not fixed.  ...be aware in this case.

Also, just adding a second virtual CPU to a Windows guest did not work for me.  I ended up re-installing the Windows OS on the dual-CPU virtual PC in order to get Windows to see the second CPU.  You might try installing/re-installing a service pack to see if that might help the exising installation pick up the second CPU.  My guess is that there is an install-time configuration of single- or multi-CPU for Windows, and once it's set...It isn't something that is detected automatically at run time.  

(I ended up using the demo version of VMware workstation to create a 2-CPU VM that works much better.  The demo-period expired, but I am still able to run the VM with the free VMware player.)

---

### Post by Perryg on 2009-10-14
I just did an install of Windows XP pro 32 bit with SMP enabled in VirtualBox and it installed just fine and the speed is better than that of a single processor. VBox version is 3.0.8 PUEL. Both processors are active and there does not seem to be a problem.  I will say that trying to change Windows kernel after the fact is not advisable and MS seems to agree with me on this point.  IO APIC of course needs to be enabled as well as VT-x but you can forget nested pages as Win XP pro will not see nor use them since it is not 64 bit. But I need to make it clear that you must be able to support VT-x/AMd-v with your system bios. You also need to either have the SP2 version or a patch from MS to make this happen since it was not supported it the original release of XP.

---

### Post by cnbiz850 on 2009-10-14
I installed Vista on VBox 3.0.8 on Karmic 64bits.  Initially, I didn't set anything regarding the CPU's.  I found that it is using close to 100% CPU on my system even though the VM is idling.  Followed some web advice and set CPU affinity (taskset -c 1 VirtualBox) for VBox, then it is back to normal.

---

### Post by dargaud on 2009-10-15
OK, I'll see to reinstalling XP. It's a minmal install in order to run just one or two progs, so it shouldn't take too long. As for VT-x/AMd-v, I don't know, I just pored all over my BIOS and the closest I could find is [Secure virtual machine] or maybe [Enhanced Halt State]. And I just upgraded my BIOS (with great difficulty) just to make sure.

---

### Post by dargaud on 2009-10-18
Thanks, that worked. I mean reinstalling XP in a second virtual machine. The stupid thing can't figure out that the number of processors has changed like Linux can. I now runs 4 times faster (at least , I think the BIOS update sped things up by a big factor as well).

---

### Post by jocampo on 2009-10-18
Yeah, Windows is not like Linux. If you installed the Os with 1 single CPU it will not recognize the other one if you later have the option via VirtualBox (of course, with the flag enable via board)

---

### Post by dargaud on 2009-10-20
Well, I marked the thread as solved, but there's still some lingering problem. So I read / process / write large (>40Mb) image files in the virtual machine via a \\VBOXSVR mapped directory. It goes very fast for the first few images (1s per image) and then it stops to a crawl (2 minutes and over per image). I suspect some kind of cache problem but can't put a finger on it.

All CPUs are 100% on the windows guest and the linux host. I/Os are shown as minimal, Ubuntu has 8Bg of mem, XP has 3 Gb reserved so it can't be a swap problem. The XP guest is very unresponsive once this kicks in (its kernel time is 50 to 80%). Beuh... :confused:

---

### Post by eracerbe on 2012-02-29
The solution is here : [http://forums.freebsd.org/showthread.php?t=17650]("http://forums.freebsd.org/showthread.php?t=17650")

Type this :

```
VBoxManage modifyvm <VM_Name> --ioapic on
```

And start the VM again. It works for me on a Debian 6 64bits Host with a Debian 6 64bits VM.

---

