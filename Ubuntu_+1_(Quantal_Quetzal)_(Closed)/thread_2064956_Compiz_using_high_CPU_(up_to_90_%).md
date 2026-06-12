---
title: "Compiz using high CPU (up to 90 %)"
date: 2012-09-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Dammerl on 2012-09-30
Dear friends, 

I need your help. Since upgrading from 12.04 to 12.10 (alpha 3, beta 1, beta 2), compiz has a constant CPU usage of up to 90 %, even when idle with only 1 terminal open, running *top*. This is when running *Unity* or *Gnome*. If I run *Gnome Classic (no effects)*, the CPU usage is normal. I am at a loss on how to narrow down the culprit. 

I have a 2005 Dell Latitude D610 with an Intel Pentium M Processor 2.13 GHz and Vesa Intel 915GM/910ML/915MS Graphics card and 1.2 Gb memory. Is this already too old for Ubuntu?

Any suggestions are highly appreciated, but please keep it sort of simple as I am not that technical, albeit willing to try quiet a lot!


Best wishes
Tom

---

### Post by cwsnyder on 2012-09-30
You do realize that one of the major changes in 12.04 to 12.10 was the elimination of Unity 2D?  Compiz will be emulated using your CPU if you don't have a GPU which supports hardware acceleration.

I think you should probably re-think using Unity on this laptop.  It is 7 years old, but would probably run Xubuntu or Lubuntu fine and probably Kubuntu.

Not that it won't run Unity Ubuntu, but it will probably keep your CPU hopping.

---

### Post by cariboo on 2012-09-30
> **Dammerl said:**
> Dear friends, 

I need your help. Since upgrading from 12.04 to 12.10 (alpha 3, beta 1, beta 2), compiz has a constant CPU usage of up to 90 %, even when idle with only 1 terminal open, running *top*. This is when running *Unity* or *Gnome*. If I run *Gnome Classic (no effects)*, the CPU usage is normal. I am at a loss on how to narrow down the culprit. 

I have a 2005 Dell Latitude D610 with an Intel Pentium M Processor 2.13 GHz and Vesa Intel 915GM/910ML/915MS Graphics card and 1.2 Gb memory. Is this already too old for Ubuntu?

Any suggestions are highly appreciated, but please keep it sort of simple as I am not that technical, albeit willing to try quiet a lot!


Best wishes
Tom

Check to see if you are using the i915 driver, instead of the vesa driver.

---

### Post by jerrylamos on 2012-09-30
Hmmm.  My IBM Thinkpad T40 has a Pentium M.  If I do a:

cat /proc/cpuinfo | grep flags

there is no "pae" in the list so 12.10 Ubuntu live install image checks for the flag and won't boot.  It's got something to do with memory sizes of 4G and up I think.

Now I was able to install 12.04 2D just fine on the Thinkpad.  Upgrading to 12.10 sort of worked with about half the packages held back.  So I re-installed 12.04 2D and am using that as well as a second partition with 12.04 Lubuntu.

I'm curious if you have a pae flag?

---

### Post by Dammerl on 2012-09-30
Dear All,

many thanks for the responses so far!

@cwsnyder I was hoping that my hardware would still be up for the job but certainly will look into the other variants - I am sure they will do the job equally fine.

@jerrylamos I have the pae flag but I am not sure what this really means.

@ cariboo907 How can I check this? Running *lshw -c video* brings up the line [I]
Configuration: latency=0[/I]; 
Running *lspci -k | grep VGA* gives
*VGA compatible controller: Intel Corporation Mobility 915 GM/GMS/910GML Express Graphics Controller (rev 03)*

I should add, I had to set the *nomodeset* kernel boot option as my computer otherwise would boot to a black screen.

Best wishes
Tom

---

### Post by cariboo on 2012-09-30
@Dammerl try:

```
sudo lshw -C display
```

I have an Nvida graphics adapter, and the result I get looks like this:

```
udo lshw -C display
[sudo] password for cariboo: 
  *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: **driver=nvidia** latency=0
       resources: irq:18 memory:df000000-dfffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:ef80(size=128) memory:def80000-deffffff
```

I bolded the driver in my case.

---

### Post by Dammerl on 2012-10-01
Hi Cariboo907,

I ran this command and here is my output:
[INDENT][INDENT]```
 sudo lshw -C display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:dff00000-dff7ffff ioport:ec38(size=8) memory:c0000000-cfffffff memory:dfec0000-dfefffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:dff80000-dfffffff
```
[/INDENT][/INDENT]It appears I have no driver installed ?!? By the way, the second display presumably is the monitor of the docking station, which currently does not work at all (but first things first).

Best wishes
Tom

---

### Post by dino99 on 2012-10-01
you only have 1,2 Gb ram, so no need to dream about compiz. You should be happy to see it running without crashing :p

Choose Lubuntu or xubuntu or something "light" if you cant add more ram (at least 4 Gb)

you should have xserver-xorg-video-intel driver installed.

---

### Post by Dammerl on 2012-10-01
Hi Dino 99,

I guess my hardware is too old ... I am actually installing Lubuntu-Desktop as I type to see whether this brings back the joy.

I am still wondering, though, whether my graphics driver isn't working correctly. My *xorg.conf* lists *vesa* as my driver and I am wondering whether to change this to  *intel* ...


Best wishes
Tom

---

### Post by dino99 on 2012-10-01
ah, you should not have a xorg.conf as now the kernel directly deal with X. So for testing, rename it as xorg.conf.original (or whatever you like) before dropping it to the bin.

---

### Post by funicorn on 2012-10-01
I think you should consider archlinux, a better choice for hardware platform of limited resources. And it's said ARCH is more suitable to learn how to act like a real linux user.

---

### Post by ventrical on 2012-10-01
> **Dammerl said:**
> Hi Cariboo907,

I ran this command and here is my output:[INDENT][INDENT]```
 sudo lshw -C display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:dff00000-dff7ffff ioport:ec38(size=8) memory:c0000000-cfffffff memory:dfec0000-dfefffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:dff80000-dfffffff
```[/INDENT][/INDENT]It appears I have no driver installed ?!? By the way, the second display presumably is the monitor of the docking station, which currently does not work at all (but first things first).

Best wishes
Tom

I have the same adapter card:

```

lspciventrical@ventrical-ME051:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ventrical@ventrical-ME051:~$ lspci


```

and I had to install the Intel drivers but I forget exactly what I did.

---

### Post by ventrical on 2012-10-01
Oy!

```


[sudo] password for ventrical: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dff00000-dff7ffff ioport:eff8(size=8) memory:c0000000-cfffffff memory:dfec0000-dfefffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:dff80000-dfffffff
ventrical@!


```

edit:

 I DO have the graphics driver.

---

### Post by jerrylamos on 2012-10-01
> **dino99 said:**
> you only have 1,2 Gb ram, so no need to dream about compiz. You should be happy to see it running without crashing :p

Choose Lubuntu or xubuntu or something "light" if you cant add more ram (at least 4 Gb)

you should have xserver-xorg-video-intel driver installed.?
This Acer Aspire 1 netbook has 1G:
jerry@Aspire1:~$ cat /proc/meminfo
MemTotal:        1016284 kB
MemFree:          153892 kB
Buffers:           46192 kB
Cached:           332328 kB
SwapCached:          228 kB
Active:           362968 kB
Inactive:         403204 kB
Active(anon):     264692 kB
Inactive(anon):   303532 kB
Active(file):      98276 kB
Inactive(file):    99672 kB
Unevictable:       31176 kB
Mlocked:           31176 kB
HighTotal:        124400 kB
HighFree:          11644 kB
LowTotal:         891884 kB
LowFree:          142248 kB
SwapTotal:       2044088 kB
SwapFree:        2021672 kB
.....

That's 1G running Ubuntu B2 as installed now all I've got up is Firefox with 5 tabs and a terminal session.  Do note this pc is about a year old and this model is still for sale, say $250 at Walmart.  I'm using a TV 1366x768 monitor, say $80 on sale, and a remote keyboard & mouse.

I'm not sure what you're running that needs 4G?

Now I'm no fan of Compiz.  The command "top" shows 6.2% for Compiz at the moment.  Seems to me it was higher than that, maybe double, earlier than this B2.

From reading this forum the graphics controller and driver are involved.  This is:
Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

Now this thread in this forum shows ways to reduce some extra default overhead:
[http://ubuntuforums.org/showthread.php?t=2064664&highlight=opengl](http://ubuntuforums.org/showthread.php?t=2064664&highlight=opengl)

To some extent this is a development forum so there's some tendency to have everything on every default on every feature running.  I don't know if there will be a "this is what people usually use and no more" option set short of Lubuntu or Xubuntu or ...

During Alpha and early Beta I frequently did
sudo apt-get install lxde
on top of regular Ubuntu.  No Compiz.  Noticeably more efficient.

With B2 I'm using unity mostly by using some hidden wireless WPA connect workarounds and some manual screen resolution settings.

Anyway I'm not sure what people are running that can't get by with 1G. I've got a 2G notebook and a 2G tower. They're faster with B2 esp. the 3.3 gHz tower but not markedly so.

Now the new theme is "Ubuntu everywhere".  Hmmm.  My Asus eee TF101 tablet has 1 G, 2 cpu's (so does the netbook), boots and connects to hidden wireless WPA in a flash leaving Ubuntu in the dust.  Hmmm.  Is there that much difference in overhead between Ubuntu and Android?

---

### Post by vasa1 on 2012-10-01
> **funicorn said:**
> **I think you should consider archlinux**, a better choice for hardware platform of limited resources. And it's said ARCH is more suitable to learn how to act like a real linux user.
Did you read the OP's first post fully?

---

### Post by funicorn on 2012-10-01
Yes. And I think he can never make it on a platform with only 1GB memory. ARCH is not that complicated, all you need is to install the necessary packages  and to start them one after another.

> **vasa1 said:**
> Did you read the OP's first post fully?

---

### Post by BigSilly on 2012-10-01
> **funicorn said:**
> ...ARCH is more suitable to **learn how to act like a real linux user**.

Wow, what does *that* mean? Do I get to swagger into bars chewing a toothpick, with my slicked back hair and tight jeans, and get to grab the first hot chick I see and driver her into the night on my Hot Rod?

Or is it something else?

---

### Post by ventrical on 2012-10-01
> **Dammerl said:**
> Dear friends, 

I need your help. Since upgrading from 12.04 to 12.10 (alpha 3, beta 1, beta 2), compiz has a constant CPU usage of up to 90 %, even when idle with only 1 terminal open, running *top*. This is when running *Unity* or *Gnome*. If I run *Gnome Classic (no effects)*, the CPU usage is normal. I am at a loss on how to narrow down the culprit. 

I have a 2005 Dell Latitude D610 with an Intel Pentium M Processor 2.13 GHz and Vesa Intel 915GM/910ML/915MS Graphics card and 1.2 Gb memory. Is this already too old for Ubuntu?

Any suggestions are highly appreciated, but please keep it sort of simple as I am not that technical, albeit willing to try quiet a lot!


Best wishes
Tom

 I have the Dell Inspiron B130 with almost exact same hardware (Only 1GB of Ram) 1.6GHz processor..Intel Celeron M and compiz and Unity 3D are working just great.

---

### Post by funicorn on 2012-10-01
u really cannot tell the tone, can u 

> **BigSilly said:**
> Wow, what does *that* mean? Do I get to swagger into bars chewing a toothpick, with my slicked back hair and tight jeans, and get to grab the first hot chick I see and driver her into the night on my Hot Rod?

Or is it something else?

---

### Post by jerrylamos on 2012-10-01
> **funicorn said:**
> Yes. And I think he can never make it on a platform with only 1GB memory. My 1G Acer Aspire 1 runs Ubuntu.  Firefox, videos, Office, email, ...  Earlier today I saw 6% Compiz see my reply elsewhere in this thread.

At the moment entering this reply, on my 2G Acer 5253 notebook compiz is running about 6% to 7% and Xorg about 13% totalling near 20%.  This is a dual cpu unit so I assume that's 20% of both.  Response time no problem.  

Could be video controller and driver have a lot to do with it.  This is 
Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]
with whatever driver Ubuntu chose to install with.

Earlier in 12.10 development Ubuntu was sluggish on all of my test pc's except the 3.3 gHz one processor Compaq Presario.  That's got a ATI Radeon Xpress 200 I think, it's not on so I forget.

If Compiz is up to 90% there is in my opinion (not a developer) a bug.

When 12.10 was sluggish I just did sudo apt-get install lxde which is for what I do efficient, quick, and doesn't use Compiz.

For a while early in 12.10 the check for pae flag didn't work so I was running my IBM Thinkpad T40 with 768 MB 1.5 mHz.  Ran O.K., response time was usable.  I put Precise 2D on it and it is a comfortable portable laptop.

For ordinary usage I don't have a problem with the 1G netbook, including BBC videos.

---

### Post by jerrylamos on 2012-10-01
Gtkperf on B2 i386 on Compaq 3.3 gHz, note Firefox is up as usual.

23.03 seconds unity/compiz/xorg up to 78.8%
logged out, logged in lxde
15.18 seconds lxde xorg up to 64%

So unity/compiz 52% slower partly explained by compiz/xorg.

Just curious.

p.s. Maverick 10.10 no effects 14 seconds.

---

### Post by cariboo on 2012-10-01
> **jerrylamos said:**
> Gtkperf on B2 i386 on Compaq 3.3 gHz, note Firefox is up as usual.

23.03 seconds unity/compiz/xorg up to 78.8%
logged out, logged in lxde
15.18 seconds lxde xorg up to 64%

So unity/compiz 52% slower partly explained by compiz/xorg.

Just curious.

p.s. Maverick 10.10 no effects 14 seconds.

There is something definitely wrong with your installation. My gtkperf result looks like this:

> GtkPerf 0.40 - Starting testing: Mon Oct  1 19:03:35 2012

GtkEntry - time:  0.02
GtkComboBox - time:  0.97
GtkComboBoxEntry - time:  0.42
GtkSpinButton - time:  0.05
GtkProgressBar - time:  0.09
GtkToggleButton - time:  0.33
GtkCheckButton - time:  0.06
GtkRadioButton - time:  0.09
GtkTextView - Add text - time:  0.60
GtkTextView - Scroll - time:  0.07
GtkDrawingArea - Lines - time:  0.35
GtkDrawingArea - Circles - time:  0.40
GtkDrawingArea - Text - time:  0.33
GtkDrawingArea - Pixbufs - time:  0.07
 --- 
Total time:  3.83

that's with an AMD Athlon II X2 240 CPU. partial cpuinfo:

> cariboo@alexis:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 6
model name	: AMD Athlon(tm) II X2 240 Processor
stepping	: 2
microcode	: 0x10000c7
cpu MHz		: 2812.979
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
bogomips	: 5625.95
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

**Note:** This cpu runs at 2812.979Mhz, that's the default setup, no overclocking.

Other specs asre:

[LIST]
[*]2GiB Ram
[*]Nvidia Gefore 210 graphics adapter
[/LIST]

As you can see this is a fairly low end setup, and it's about 2½ years old.

---

### Post by effenberg0x0 on 2012-10-01
> **cariboo907 said:**
> There is something definitely wrong with your installation. My gtkperf result looks like this:



that's with an AMD Athlon II X2 240 CPU. partial cpuinfo:



**Note:** This cpu runs at 2812.979Mhz, that's the default setup, no overclocking.

Other specs asre:

[LIST]
[*]2GiB Ram
[*]Nvidia Gefore 210 graphics adapter
[/LIST]

As you can see this is a fairly low end setup, and it's about 2½ years old.

<Probably OT>
Out of curiosity, I'd really like to see some structured results of comparisons of gtkperf and glxgears running with proper VGA drivers (direct rendering) and with llvmpipe in AMD, ATI, Intel. Imagune if we had something like this:

GPU Vendor: AMD,  NVidia or Intel
GPU Model: XXXX
glxgears (Direct Rendering): xxxx.xxx FPS
glxgears (Indirect Rendering - llvmpipe): xxxx.xxx FPS
gtkperf (Direct Rendering): xxxx.xxx Seconds
gtkperf (Indirect Rendering - llvmpipe): xxxx.xxx Seconds

But:
- We don't have critical mass to test that in Ubuntu+1. Maybe we will once QQ is released;
- If we launch such a request we will be flooded with support requests from people that borked their installs while enabling/disabling/switching VGA drivers; 
- This survey is probably undoable. Ubuntu benchmarking should be automated. 
</OT>

Regards,
Effenberg

---

### Post by Dammerl on 2012-10-01
Removing *xorg.comf* or changing its setting from *Vesa* to *intel* results in an error at boot up
*Running in low graphics mode*
No recovery from there (Ctrl-Alt-F2 still works). 

I guess I have now tried so many different things that the system might be  "a bit out of sync" ...

---

### Post by cariboo on 2012-10-02
> **Dammerl said:**
> Removing *xorg.comf* or changing its setting from *Vesa* to *intel* results in an error at boot up
*Running in low graphics mode*
No recovery from there (Ctrl-Alt-F2 still works). 

I guess I have now tried so many different things that the system might be  "a bit out of sync" ...

You can't just change /etc/X11/xorg.conf, you also have to load the module, you can use the following command:

```
sudo modprobe i915
```

If the module is loaded properly, you won't see any feedback.

---

### Post by Dammerl on 2012-10-03
Ufortunately, even with running modprobe does not fix the problem and  hit the wall when getting to the login screen. I think I need to find out how to best remove and freshly reinstall the graphics driver. I will report back how this goes, but it may take a while before I can focus on this.

Many thanks for your help so far
Tom

---

### Post by funicorn on 2012-10-04
try this,
dconf reset -f  /org/compiz/

then
setsid unity

---

