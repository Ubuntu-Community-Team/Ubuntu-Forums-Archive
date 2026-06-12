---
title: "Kernel issues / DSTD issues on Sun-LX50 (SCB2)"
date: 2005-11-01
forum: Server Platforms
---

### Post by Z3K3 on 2005-11-01
Hello all,

I've been fighting with my LX50 for about a week now, the 2.6.10-386 kernel seems to work, but as soon as I attempt to use a newer kernel or a proper 686-smp (dual-processor) kernel I get kernel panics and issues (see attached images):

I tried to trace the issues, and have gone in a few loops.  I'm currently thinking that it is an issue with the DSDT (Differentiated System Description Table), I have dumped, decompiled, and am in the process of debugging, but I'm not sure how to fix the following debug error (incase anyone knows).

Has anyone else experienced issues like this?  How did you resolve them?

FYI: I'm also compiling a 2.6.14-custom-686-smp kernel now to see if that allows me to boot.  Additionally, I was unable to setup the system with the ubuntu-server install CD, I had to use 5.04 (2.6.10) then go from there.

DSDT Compile error:
> dsdt.dsl.new   968:         If (LAnd (LLess (\_SB.PCI0.HEF0.MSIZ,
0x40), Local0))
Error    1048 -                      Method local variable is not
initialized ^  (Local0)

dsdt.dsl.new   970:                     Return (Multiply (Local0, 0x04000000))
Error    1048 -       Method local variable is not initialized ^  (Local0)

Code chunk causing error:
> Method (MDET, 0, NotSerialized)
           {
               If (LAnd (LLess (\_SB.PCI0.HEF0.MSIZ, 0x40), Local0))
               {
                   Return (Multiply (Local0, 0x04000000))
               }
               Else
               {
                   \DEB.BP ("Memory size is 4GB or more!")
                   Return (Ones)
               }
           }

Resources:

[http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)
[http://www.alkemio.org/wordpress/2005/09/23/patching-your-dsdt-with-ubuntu/](http://www.alkemio.org/wordpress/2005/09/23/patching-your-dsdt-with-ubuntu/)
[http://home.fhtw-berlin.de/~s0502837/r31/](http://home.fhtw-berlin.de/~s0502837/r31/)
[http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) (Ubuntu kernel is compiled for DSDT in initrd)

---

