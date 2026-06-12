---
title: "Ubuntu 6.10 install on Fujitsu PrimePower 200 Sparc64 problem"
date: 2006-11-23
forum: Sun Sparc Users
---

### Post by slo on 2006-11-23
I have a Fujitsu Prrimepower 200 with Sparc64 CPU,
when I install Ubuntu 6.10 Sparc64 on it, I found:
```

Stop-A
ok boot cdrom
screen not found.
Can't open input device.
Keyboard not present.  Using ttya for input and output.



Fujitsu PRIMEPOWER 200 1x SPARC64 IV 602MHz, No Keyboard
OpenBoot 3.11 J , 2048 MB memory installed, Serial #15891257.
Ethernet address 0:80:17:84:7b:39, Host ID: 80f27b39.
SCF Version: 3.3.F , RCI Version: 0001



Rebooting with command: boot cdrom
Boot device: /pci@17,4000/scsi@3/disk@4,0:f  File and args: 
SILO Version 1.4.12
\


                       Welcome to Ubuntu edgy!

This is an Ubuntu installation CDROM, built on 20061025.1.
Keep it once you have installed your system, as you can boot from it
to repair the system on your hard disk if that ever becomes necessary.

WARNING: You should completely back up all of your hard disks before
  proceeding. The installation procedure can completely and irreversibly
  erase them! If you haven't made backups yet, remove the rescue CD from
  the drive and press L1-A to get back to the OpenBoot prompt.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

[ ENTER - Boot install ]   [ Type "rescue" - Boot into rescue mode ]
boot: 
Allocated 8 Megs of memory at 0x40000000 for kernel
Loaded kernel version 2.6.17
Loading initial ramdisk (5260517 bytes at 0x100000000 phys, 0x40C00000 virt)...
Illegal Instruction
%TL:1 %TT:10 %TPC:404434 %TnPC:404438 %TSTATE:4400001600 
%PSTATE:16 ( IE:1 PRIV:1 PEF:1 )
ok 

```
Is there anybody can help me ?

---

### Post by netztier on 2006-11-23
> **slo said:**
> Is there anybody can help me ?

Yes there is: You!

Searching forums and/or Googlespace with the actual text of the error message often yields the best results. 

Give it a try: search the SPARC forum with ***illegal instruction***. You'll get at least half a dozen threads that describe very similar problems as the one you are experiencing. See this thread: [Initial ramdisk error]("http://www.ubuntuforums.org/showthread.php?t=219746&page=2&highlight=illegal+instruction")

The solution hints can be summarized like this:

[LIST]
[*]update the OBP to the latest version available for your machine
[*]reduce memory size, either by removing some of the RAM physically
[*]or by appending [FONT="Courier New"]**mem=512 **[/FONT]as parameter when starting the installer
[*]cold-boot the machine, interrupt early with <stop-A> and then issue the [FONT="Courier New"]**boot cdrom **[/FONT]command
[/LIST]

If you've already tried all of this, then please state this clearly in your original posting, so others can see what you have already tried - it's just unproductive guesswork otherwise.

regards

Marc

---

### Post by slo on 2006-11-24
this happaned when I input boot cdrom
installer just not startup, so ,how to appending mem=512 ?

---

### Post by netztier on 2006-11-26
> **slo said:**
> this happaned when I input boot cdrom
installer just not startup, so ,how to appending mem=512 ?

When the installer CD boots up and asks you if you wanted to boot "rescue" or hit <Enter> to start install, you type the following instead of <enter>:

```
install mem=512
```

You can also press <tab>. This will give you a list of selectable boot options, of which "rescue" and "install" are just a few (and "install" would be the default)

regards

Marc

---

### Post by slo on 2006-11-26
Thanks a lot!
I try to do you idea,but still faile:
```

Welcome to Ubuntu edgy!
 
This is an Ubuntu installation CDROM, built on 20061025.1.
Keep it once you have installed your system, as you can boot from it
to repair the system on your hard disk if that ever becomes necessary.
 
WARNING: You should completely back up all of your hard disks before
  proceeding. The installation procedure can completely and irreversibly
  erase them! If you haven't made backups yet, remove the rescue CD from
  the drive and press L1-A to get back to the OpenBoot prompt.
 
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
 
[ ENTER - Boot install ]   [ Type "rescue" - Boot into rescue mode ]
boot: install mem=512
Allocated 8 Megs of memory at 0x40000000 for kernel
Loaded kernel version 2.6.17
Loading initial ramdisk (5260517 bytes at 0x100800000 phys, 0x40C00000 virt)...
Data Access Exception
%TL:1 %TT:30 %TPC:40004414 %TnPC:40004418 %TSTATE:9900001600 
%PSTATE:16 ( IE:1 PRIV:1 PEF:1 )
D-FAR:0 
D-FTR:f455 ( W:1 PRIV:1 ASI:45 FTYPE:f ) 
ok 

```

---

### Post by netztier on 2006-11-27
> **slo said:**
> Thanks a lot!
I try to do you idea,but still faile:


Well, what about the other hints?
[LIST]
[*]removing physical memory to have less than 512Mbyte left
[*]cold-booting the machine before **[FONT="Courier New"]<Stop-A>[/FONT]** and [FONT="Courier New"]**ok> boot cdrom**[/FONT]
[*]updating the OBP to the latest version available
[/LIST]

Have you tried these, too? What were the results? 
On the other hand, a Fujitsu SPARC machine is even more exotic than a SUN Microsystems machine, so I wonder if you've ever found any reports of one of these running Linux successfully?

regards

Marc

---

