---
title: "windows 7 vm running very slowly"
date: 2012-06-21
forum: Virtualisation
---

### Post by Matt26 on 2012-06-21
i'm running a windows 7 ultimate virtualbox vm under ubuntu 12.04 32bit.  both windows 7 vm and ubuntu host have all of the latest updates applied.

i've noticed that the vm runs really slow- for example, it takes an usually long time for the "Starting Windows" splash screen to load before the log in screen appears, and there are very noticeable delays when opening pretty much anything from the desktop- for example, Control panel or Internet Explorer.

i haven't encountered any errors in windows so far, is just seems to be a performance issue.

i've run the same version of windows 7 (same install disc) on the same computer in the past (not as a vm) and it ran smoothly, so i'm not sure what to check.

does anyone know what might be causing this?

thanks!

---

### Post by SeijiSensei on 2012-06-21
How much memory is allocated to the VM?  Anything less than a gigabyte is likely to require the Windows OS to do a lot of swapping to the disk.  You'll need to assign even more memory to the VM if you want to have a lot of Windows applications open simultaneously.  I generally start with 1.5 GB if I can afford it.

Also what kind of processor does this machine have?  Remember that the CPU will be running all of Linux and all of Windows.  

In general, though, I'd start with the memory allocation.

---

### Post by CharlesA on 2012-06-21
+1 to memory.

---

### Post by Dlambert on 2012-06-21
If you have a multi-core cpu you can allocate 2 or more cores to the vm.

---

### Post by teward on 2012-06-21
> **Matt26 said:**
> i'm running a windows 7 ultimate virtualbox vm under ubuntu 12.04 32bit. both windows 7 vm and ubuntu host have all of the latest updates applied.
 
i've noticed that the vm runs really slow- for example, it takes an usually long time for the "Starting Windows" splash screen to load before the log in screen appears, and there are very noticeable delays when opening pretty much anything from the desktop- for example, Control panel or Internet Explorer.
 
i haven't encountered any errors in windows so far, is just seems to be a performance issue.
 
i've run the same version of windows 7 (same install disc) on the same computer in the past (not as a vm) and it ran smoothly, so i'm not sure what to check.
 
does anyone know what might be causing this?
 
thanks!
 
 
Put more memory allocation to the VM (at least 512MB if you can, 1GB recommended).  Also if you have a multi-core processor, give the VM more cores o work with.

---

### Post by Matt26 on 2012-06-21
i'm using older hardware (intel pentium 4 3ghz) with 2GB ddr ram (maximum supported).

i have 890mb of ram allocated to the vm at the moment- i had 1gb allocated with the same performance issues, and i was seeing a warning in virtualbox about allocating more than half of the host's memory to the vm, so i dropped it down to 890mb.

i'm not running any applications in ubuntu either, other than firefox with one tab open.  i also don't have any applications open in windows while the vm is running.

is this hardware setup too old to be running the vm without these delays/performance issues?

thanks!

---

### Post by drmrgd on 2012-06-21
> **Matt26 said:**
> i'm using older hardware (intel pentium 4 3ghz) with 2GB ddr ram (maximum supported).

i have 890mb of ram allocated to the vm at the moment- i had 1gb allocated with the same performance issues, and i was seeing a warning in virtualbox about allocating more than half of the host's memory to the vm, so i dropped it down to 890mb.

i'm not running any applications in ubuntu either, other than firefox with one tab open.  i also don't have any applications open in windows while the vm is running.

is this hardware setup too old to be running the vm without these delays/performance issues?

thanks!

This actually may be your problem right here.  I've found that on my old P4 chipset, VT-x is not supported (i.e. I can't enable it in BIOS).  Running an VM using any software (Virtual Box or VMware Player), I found that no matter how much RAM I allocated, it ran really sluggishly for me too. You may not be able to get very good performance out of your CPU for virtualization (although I'm no expert on the matter!).

---

### Post by QIII on 2012-06-21
VT-x being absent might keep it from running altogether, so that may or may not be it.

The later Pentiums had dual threading, and that may be just enough to assign a "core" to the VM.  But it would certainly cause a lot of head-bumping inside the CPU.  The low memory is probably on the lower limits of viability for Win 7, too.

If that is on a Socket 775 motherboard and the specs on your motherboard allow it, you might be able to find a low-wattage used Core 2 Duo or Pentium D at a second-hand computer parts reseller for US$25 or US$35.  That would be a pretty cheap upgrade that might not break the bank.

---

### Post by drmrgd on 2012-06-21
> **QIII said:**
> VT-x being absent would probably keep it from running altogether, so that may or may not be it.

The later Pentiums had dual threading, and that may be just enough to assign a "core" to the VM.  But it would certainly cause a lot of head-bumping inside the CPU.  The low memory is probably on the lower limits of viability for Win 7, too.

If that is on a Socket 775 motherboard and the specs on your motherboard allow it, you might be able to find a low-wattage used Core 2 Duo or Pentium D at a second-hand computer parts reseller for US$25 or US$35.  That would be a pretty cheap upgrade that might not break the bank.

Hmmm...that's a really interesting thing to look into.  I believe my CPU was just before multicores really started taking off and  was one of the first HT processors.  That probably answers your question of virtualization sine I know for sure I don't have VT-x support.  The OP might have the same CPU as I do since I think mine is clocked at 3.2 GHz too (not at home at the moment and can't check).  But, anyway, yeah....if I could pick up something like that for <$50, that might be pretty sweet!

---

### Post by QIII on 2012-06-21
Go with the Core 2 Duo if you can find one.  The Pentium D architecture made them run really hot (something on the order of 130 watts!), so a good cooler would probably be a good idea.  That would add to the cost of the upgrade.

Anyway, back to the OP's question -- that would be my suggestion if you can swing it.  But don't do it unless your motherboard supports VT-x or you will have wasted your money.

---

### Post by CharlesA on 2012-06-21
> **QIII said:**
> Go with the Core 2 Duo if you can find one.  The Pentium D architecture made them run really hot (something on the order of 130 watts!), so a good cooler would probably be a good idea.  That would add to the cost of the upgrade.

Anyway, back to the OP's question -- that would be my suggestion if you can swing it.  But don't do it unless your motherboard supports VT-x or you will have wasted your money.

+1. I'd suggest upgrading to a cheap cpu/mobo/memory combo instead of trying to swap out the CPU. LGA 775 is dead and it is going to be hard to find a reasonably priced dual core CPU.

---

### Post by QIII on 2012-06-21
True that.

Still, it really sucks when the best suggestion one can make is for someone else to spend money.

---

### Post by CharlesA on 2012-06-21
> **QIII said:**
> True that.

Still, it really sucks when the best suggestion one can make is for someone else to spend money.

Yep. :(

I've run a Win7 VM with 1GB of memory and it ran fine, but I was running off a dual core with 6GB of ram total.

It's likely the system they are trying to use as a vm host isn't beefy enough to run the VM quickly. :(

---

### Post by Matt26 on 2012-06-22
thanks for everyone's input!

i wasn't considering a hardware limitation as being part of the equation here, but yeah i can see how my setup might have a bearing on the vm's performance.. and i believe i have a socket 478 motherboard with a non-HT pentium 4.

is there a 'safe mode' (like Windows) that ubuntu can run in which will still allow me to run the vm?  i'm curious to see how the vm will run in that case.

i'm guessing that it won't make any major difference, but i'm still interested in seeing what happens!

thanks!

---

### Post by CharlesA on 2012-06-22
Give the VM a gig a RAM and see what happens. If it doesn't launch properly, you can always reduce it.

---

### Post by DWade on 2012-06-22
I believe the problem is in 12.04.  I have Windows 7 64 bit virtual I run in Windows 7, Ubuntu 10.04 and in 12.04.  It's twice as slow running it in 12.04 and It has locked up Ubuntu 12.04 where I have issues. Now for the 3rd time.  I have tried fixing Ubuntu 2 times this third time I just erased and started over. 

I have my computer's drive partition as partition 1 - Windows 7 professional, partition 2 - Ubuntu LTS 10.04, Partition 3 - Ubuntu LTS 12.04 and Partition 4 Extended with a 400 gig Data partition and 6 Gig linux swap.

Now I have just reloaded 12.04 for the fourth time. I have just installed Virtual box 4.1.12 and will upgrade to 4.1.14.  And it seems that 4.1.16 seems to be worse. So it could be a Virtualbox problem.

I am this time going to copy my apt directory, since APTonCD will not restore and use the Backup on system setting to see if that will speed up the 2 day reload all my software problem to a half hour maybe, as I continue to figure out what is causing this lock up problem.

---

### Post by CharlesA on 2012-06-22
4.1.18 was just released. I haven't noticed any sluggishness on my VM, but it could be my imagination cuz I access it via remote desktop.

---

### Post by DWade on 2012-06-22
First what is your windows 7 VM. 32 bit or 64 bit?  I had a 32 bit running but don't want to activate it, holding it out for another computer, where as my 64 bit is activated.  But does not run correctly in Ubuntu 12.04 and it could be a host 32 to a guest 64 bit problem.

---

### Post by CharlesA on 2012-06-22
> **DWade said:**
> First what is your windows 7 VM. 32 bit or 64 bit?  I had a 32 bit running but don't want to activate it, holding it out for another computer, where as my 64 bit is activated.  But does not run correctly in Ubuntu 12.04 and it could be a host 32 to a guest 64 bit problem.

Ah that could be.

I'm running 64-bit host with Win7 Pro x64 as the guest.

---

### Post by DWade on 2012-06-22
I might need to go to Virtual Box and post my problems there.  I remember a problem testing Windows 8 64 bit in Ubuntu 11.10, now that I think about it. 

I just figured it was the Developers Preview problem since Developer Preview is the Pre - Beta Release and Consumer Preview was the Beta Release which I took the 32 bit that time and the new one Release preview is the RC candidate, they are just using different names.

---

### Post by Matt26 on 2012-06-27
i upgraded both virtualbox and the extension pack to the latest version '4.1.18' and also increased the memory allocation to 985MB- the most i can assign without getting the memory allocation warning from virtualbox.

unfortunately, still rather sluggish startup and general access delays.

i also increased the pagefile size in the Windows VM because i think it was set to the same size as the memory allocated to the VM.. i doubt that will make much difference but i'm just trying different things out.

does anyone know if the option (checkbox) to allow the VM to use the host I/O cache feature (under the Storage section in virtualbox VM settings) may have any bearing on VM disk performance?  i tried enabling it but i don't think that it made much difference.

thanks!

---

### Post by haqking on 2012-06-27
> **Matt26 said:**
> i upgraded both virtualbox and the extension pack to the latest version '4.1.18' and also increased the memory allocation to 985MB- the most i can assign without getting the memory allocation warning from virtualbox.

unfortunately, still rather sluggish startup and general access delays.

i also increased the pagefile size in the Windows VM because i think it was set to the same size as the memory allocated to the VM.. i doubt that will make much difference but i'm just trying different things out.

does anyone know if the option (checkbox) to allow the VM to use the host I/O cache feature (under the Storage section in virtualbox VM settings) may have any bearing on VM disk performance?  i tried enabling it but i don't think that it made much difference.

thanks!

You are trying to a run a modern OS on virtualised hardware and on 985MB of RAM when the min requirements for it are 1GB.

What performance do you expect ?

---

### Post by drmrgd on 2012-06-27
> **Matt26 said:**
> i upgraded both virtualbox and the extension pack to the latest version '4.1.18' and also increased the memory allocation to 985MB- the most i can assign without getting the memory allocation warning from virtualbox.

unfortunately, still rather sluggish startup and general access delays.

i also increased the pagefile size in the Windows VM because i think it was set to the same size as the memory allocated to the VM.. i doubt that will make much difference but i'm just trying different things out.

does anyone know if the option (checkbox) to allow the VM to use the host I/O cache feature (under the Storage section in virtualbox VM settings) may have any bearing on VM disk performance?  i tried enabling it but i don't think that it made much difference.

thanks!

I still really think it's your processor.  While the amount of RAM you have available could certainly be an issue, without VT-x on the chipset, virtualization doesn't work all that well and would be a much bigger problem.  I'm almost positive it didn't exist on the Socket 478 chips like yours. 

Like I said, on my system without VT-x, I can run Windows in a virtual machine, but it's really sluggish, just as you describe.  I think you're experiencing the best performance you're going to get out of your hardware unfortunately.

---

