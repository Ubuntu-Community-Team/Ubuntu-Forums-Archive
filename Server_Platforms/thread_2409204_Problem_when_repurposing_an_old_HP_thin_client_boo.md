---
title: "Problem when repurposing an old HP thin client boot stops. (32bit)."
date: 2018-12-29
forum: Server Platforms
---

### Post by adrian-h on 2018-12-29
My first post on here, I am not an expert but can muddle though instructions!
I have been repurposing a couple of old HP thin clients both 32 bi devices a T5730 and a T5740.

I am trying to install Ubuntu 16.04.05 server i386 on them the T5730 with a AMD Sempron 2100+ processor has installed fine and that is running along nicely.

The T5740 with a Intel Atom N280 is not it hangs at boot time. The installer works and progresses fine and gets to the end and reboots the machine, that is when it fails, the last few messages on the screen are:

[0.021880] Last level iTLB entries: 4KB 32, 2MB 0,4MB 0
[0.021927] Last level dTLB entries 4KB 64, 2MB 0, 4MB 8, 16MB 0
[0.022833] Feeing SMP alternatives memory: 32K

And that is the last thing that happens

Using a USB install stick I noticed I also have the option to go into safe mode and repair a broken system so that I did and in /var/log and using dmesg | less I could find the same messages and also another message 

[0.028029] ftrace:allocating 31517 entries in 62 pages        So I guess t such that is where the boot fails.

[0.052195] smpboot: APIC(0) Converting physical 0 to logical package 0.                                                  -----------------  I think this is when I boot up in safe mode?
[0.052216] smpboot: Max logical packages: 2
[0.052232] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[0.052658] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1

Unfortunately I do not know what to try next.
I have tried several versions of Ubuntu with success such as 14.04 server i386 works OK and 15.04 server i386 works OK but as I am trying to learn about linux and mysql operations I would like to use 16.04 as that is working on the other thin client and has a bit longer in support yet!  
So I am wondering if from safe mode I could try installing an earlier version of the linux kernel such as the 4.4.0-31-generic as installed with 14.04 rather than 4.4.0-141-generic as the installer installs and how i could do this, or could someone let me know what else to try?

Many thanks

Adrian

---

### Post by howefield on 2018-12-29
Thread moved to the "*Server Platforms*" forum.

---

### Post by adrian-h on 2018-12-29
Thanks for moving the post to the server platforms forum.

The issue may well not be down to the kernel I found a web page on downloading other versions and tried 4.4.0.04040 that seems to have the same issue i wil go back a bit further and try some older ones but think I am on the wrong track, I just got the idea after find posts about the N280 processor, it seems to be a single core that can do 2 threads, not that I am really aware of what that means?

I will keep plugging along.

I do get a message when in rescue mode and adding images of 
:  Failed to connect to lvmetad. Falling back to internal scanning, but the images are there in advanced mode boot options so assuming issue is down to being in safe mode/rescue mode.

Adrian

---

### Post by adrian-h on 2018-12-29
OK I have solved this issue for my device, it was nothing to do with any kernel, modeset, ACPI, PAE or any such thing.  It was a bug in the Bios.  I only managed to find it by searching the internet on anything to do with HP-T5740 and found a post on firmware on a Parky Towers web site dedicated to thin clients of all types, he mentioned a bios update from 1.01 to 1.04.  So downloaded USD dos boot disk later and bios updated.

I have installed on my system the standard kernel for 16.04 which is 4.4.0-141-generic, and kernel 4.15.0 HWE, and kernel 4.6.7-generic and now the system will boot with any of them.

So now i can get on with what I intended to do with the box and learn more about operating the software.

Adrian

---

