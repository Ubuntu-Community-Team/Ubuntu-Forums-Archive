---
title: "Do you need to enable PAE on Ubuntu Server 8.04"
date: 2010-10-21
forum: Server Platforms
---

### Post by monkeymaximus on 2010-10-21
Hi,   First I have spent a considerable time trying to search and figure out exactly why only 3.5gb of my 4gb of RAM is showing up on my 32 bit Ubuntu 8.04.4 LTS server.  I understand that with a 32 bit kernel (i know i should reinstall to 64bit but that is not currently an option) it is only capable of seeing 3.5 GB of ram. All the blogs / articles / forum entries I find are talking about Ubuntu Desktop (none of them server which is why I am here) and switching to the server kernel. I also found articles saying that PAE is built in by default on Ubuntu server. So am I correct in saying it should already be there?   Do I need to do anything to get PAE working? Or is something else wrong which is why I am only seeing 3.5GB of the 4GB installed.  Thanks for your guys time.

---

### Post by lykwydchykyn on 2010-10-21
It's conceivable it's being taken by shared memory on an onboard video card. If memory serves, the 32 bit limit is more like 3.3 or 3.1 GB; it's conceivable that 512 MB might be used by an onboard video, though that would be a tad high.

---

### Post by monkeymaximus on 2010-10-21
Its a rack server at SoftLayer so I would hope a video card on that kind of computer wouldn't be trying take 512MB.   Is there a known way to check?  Btw if its helpful I get the following when I run free -m.               total       used       free     shared    buffers     cached Mem:          3545       3233        312          0         54       2670 -/+ buffers/cache:        508       3037 Swap:         1996         39       1957    .    Also not sure if it makes a difference but previously I had 2GB of ram in the computer and I saw all 2GB of it. I ran lshw -businfo and it actually sees the full "4GiB System Memory".

---

### Post by lykwydchykyn on 2010-10-22
You could check the BIOS to see if any memory is being shared, and what it says.

Can you post the output of "uname -a"?  Let's make sure you have the right kernel installed.

Also, you may want to run:
```

grep pae /proc/cpuinfo

```
To see if your cpu has pae support.  If it does, you'll see a line "flags: " followed by a bunch of three letter acronyms.  If it doesn't, that command will return nothing.

---

### Post by monkeymaximus on 2010-10-22
uname -a  Linux site.com 2.6.24-27-generic #1 SMP Wed Mar 24 10:04:52 UTC 2010 i686 GNU/Linux  grep pae /proc/cpuinfo flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_

---

### Post by lykwydchykyn on 2010-10-22
Your cpu supports pae, but you're running the "generic" kernel, which does not have pae enabled.  I believe in 8.04 you want to install the "-server" kernel which will.

Since I don't have a hardy system readily available, I can't confirm this will be the right command, but you want to do something like:

```

sudo apt-get install linux-image-server

```

---

