---
title: "New to building a virtual box."
date: 2016-12-23
forum: Virtualisation
---

### Post by grey1beard on 2016-12-23
Just created a new install of 14.04 in an ageing RM Notebook, 32bit, with 2.6G ram and 150GB disk.
I need to install a VB to run Corel 8 suite in XP. It would also be good to run my printer within the same environment.
Is that doable without complications ? I wont be using it for any other resource hungry software.
John

---

### Post by kingneutron on 2016-12-23
--If it's 32-bit, depending on which virtualization software you use, you may have issues because the CPU probably doesn't support hardware virtualization.

--Post results of ' cat /proc/cpuinfo '

( my relevant cpuinfo looks like this, my AMD processor supports virtualization )
```

flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca  
cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt
pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc
extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy **svm**
extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt  
cpb hw_pstate vmmcall npt lbrv svm_lock nrip_save pausefilter


```

--In my opinion, you would be better served by creating your VM on more modern hardware (at least 64-bit, although I've run into virtualization issues on a Toshiba Satellite L645 laptop that had a 64-bit CPU but no hardware virtualization support - Qubes OS would not let me install a Windows 7 64-bit VM) since older hardware will run the VM slower than you might like, if it runs at all.

--Short form: You could give it a try, see if it works, might be slow.  If XP doesn't install or doesn't run right then try different hardware. The good part about VMs though is that they are portable, you could migrate it to better hardware if necessary.

REF:
[http://unix.stackexchange.com/questions/22130/will-vmx-cpu-flags-increase-the-speed-of-virtual-machine-software-like-virtual](http://unix.stackexchange.com/questions/22130/will-vmx-cpu-flags-increase-the-speed-of-virtual-machine-software-like-virtual)

[https://www.virtualbox.org/manual/ch03.html](https://www.virtualbox.org/manual/ch03.html)

---

### Post by howefield on 2016-12-23
Thread moved to the "*Virtualisation*" forum.

---

### Post by grey1beard on 2016-12-23
cat/proc/cpuinfo ?

'no such file or directory'

Please advise - I guess there's something I don't know
John

---

### Post by howefield on 2016-12-23
> **grey1beard said:**
> cat/proc/cpuinfo ?

Put a space between cat and /proc/cpuinfo

---

### Post by grey1beard on 2016-12-23
Thanks. Did that, then discovered I have no tool bar at the top of my terminal window, which flummoxed me for a bit.
I've just copied what I assume is the relevant section of the o/p rather than all of it. Is that helpful ?
John

> flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm arat

---

### Post by SeijiSensei on 2016-12-23
It's certainly possible to run VirtualBox on a 32-bit system.  It will only support 32-bit OS images, but that's fine for XP.

You'll want to give XP at least 768 MB or memory or perhaps 1024.  Otherwise you should be fine.  

Running the printer from XP is going to be dicey.  If it's a networked printer, you should be fine.  But if it's connected via USB or a parallel port, things might not go so well.  I'd set up the printer in Linux, then share it with Samba so you can connect to it from XP.  If you search Google for printing from a VB guest, you'll see lots of advice.

---

### Post by grey1beard on 2016-12-23
Many thanks - looks like a slow, methodical slog .
Regards
John

---

### Post by howefield on 2016-12-24
Another option is to use Wine which will probably have lower overheads than Virtualising.

Corel 8 has a Silver rating on the Wine database but that is old and only one rating, every chance it will perform fine for your needs. I'm sure a virtual machine will work on your machine and if I recall correctly you are using 12.04 with Unity so might not be a "pleasant" experience.

---

### Post by grey1beard on 2016-12-24
Hi howefield,
Yes, I tried using Corel in Wine in 12.04, and it was very frustrating ! Pretty well useless, in fact, so I gave up, and took to dual booting with XP.
Now that I'm becoming a little more flexible in my old age, I've loaded 14.04 exclusively on another laptop, and decided to take the plunge by trying a virtual box running xp. 
An added complication for me to ponder is that I've got a Bamboo graphics tablet that only seems to work in Win 7, whereas my corel 8 doesn't ! Looks like the simplest route might be to invest in a later version of Corel, but that then puts me back to spending time becoming familiar with a later graphics prog, as well as a new os.
Alternatively, ditch the tablet, stick with xp(which I'm used to, pre Ubuntu days)and sort out a VB, then get a compatible graphics tablet.
Or just learn to use and love Inkscape.
Decisions, decisions .............
Happy Christmas everyone.
John

---

### Post by SeijiSensei on 2016-12-25
You may or may not get the graphics tablet working with a virtual machine.  You'll have to do some configuration to pass through the USB connection.  Here's the documentation from VB:  [https://www.virtualbox.org/manual/ch03.html#idm1631](https://www.virtualbox.org/manual/ch03.html#idm1631)  There are also many pages on the Internet about this that you can find with a Google search.  

These are the same issues that I mentioned in regards to a printer connected via USB.

---

### Post by grey1beard on 2016-12-25
Thanks SeijiSensei, I shall proceed with caution.
Merry Christmas

John

---

