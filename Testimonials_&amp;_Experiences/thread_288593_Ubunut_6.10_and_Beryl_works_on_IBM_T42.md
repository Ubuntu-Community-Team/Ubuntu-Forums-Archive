---
title: "Ubunut 6.10 and Beryl works on IBM T42"
date: 2006-10-30
forum: Testimonials &amp; Experiences
---

### Post by rbalfour on 2006-10-30
I GOT BERYL TO WORK! WHOOT!

I made a short [YouTUBE video]("http://www.youtube.com/watch?v=X_cggDTaRLE") of Beryl in action. Also I am posting my hardware specs. To those who are trying to get Beryl to work...there is HOPE!

> 
IBM Thinkpad T42 with 2GB of mem.
[QUOTE]
lspci commmand:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

top command:
op - 16:53:10 up  1:48,  2 users,  load average: 1.47, 1.21, 1.15
Tasks: 135 total,   2 running, 132 sleeping,   0 stopped,   1 zombie
Cpu(s): 22.6%us, 12.5%sy,  0.0%ni, 64.2%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2075460k total,   827772k used,  1247688k free,      476k buffers
Swap:        0k total,        0k used,        0k free,   516120k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3841 root      15   0  155m  62m  11m R 23.8  3.1   5:58.84 Xorg               
12420 mod       15   0 47776  16m  10m S  6.6  0.8   0:01.94 gnome-terminal     
10187 mod       15   0  133m  41m  20m S  3.1  2.0   0:06.96 mozilla-thunder    
 6311 mod       15   0 17256 9.8m 7424 S  0.5  0.5   0:22.65 gworldclock        
 6387 mod       15   0 53272 6416 3704 S  0.5  0.3   0:15.77 beryl              
12523 mod       15   0  2252 1156  844 R  0.5  0.1   0:00.06 top                
 4452 mod       15   0 58480  19m  13m S  0.2  1.0   0:12.06 gnome-panel        
 4748 mod       15   0  141m  12m 7432 S  0.2  0.6   0:06.08 ciphire-mail       
 4775 mod       16   0 36576  15m  10m S  0.2  0.8   0:06.07 main-menu          
11946 mod       15   0  173m  59m  26m S  0.2  3.0   0:32.50 firefox-bin        
    1 root      16   0  1632  536  448 S  0.0  0.0   0:00.94 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.19 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.15 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    7 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            

cat proc command:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 6
cpu MHz         : 600.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips        : 1200.15

[/QUOTE]

---

### Post by cinephy on 2006-10-30
Just a quick post to confirm this. I have beryl and kiba-dock up and running in Edgy on my T42. I spent almost all day yesterday getting this configured on my ATI Mobility 7500 (that's right, i said 7500). This is the first time I've ever had glxgears running faster than 1200 fps (I think the final numbers were close to 3000 fps). I'll post later today how I did this but I can say after trying a few configurations the simplest was the one that worked best. OK, off to work now but I promise to post up my configuration by the end of the night. 

[SIZE="2"]edit: So, funny thing happened as I was posting my configuration last night - my cpu locked up. I think I need to reconfigure this card to get it a little more stable. I'll post settings when it's more stable.[/SIZE]

---

### Post by rbalfour on 2006-10-31
I think the lock up is happening with kiba-dock. Not to stable right now.
Also Thanks for the confirm.

---

### Post by klato on 2006-10-31
Id be interested as hell to know how you get 3000fps on a radeon 7500! I can only get 1050, and that's only if I make my desktop 16 bit in xorg.conf. Also, in the video, you said you had it running without XGL/AIGLX...I didn't know that was possible?

---

### Post by Shiro Ishii on 2006-11-01
Cinephy, please do tell us how you did it.  I've got a T42 with Radeon Mobility 7500, which I was able to play Neverwinter Nights on under Breezy.  I've just installed Edgy, and want to know what to do before installing NWN.  ;)

---

### Post by klato on 2006-11-06
cinephy/rbalfour: Would you guys mind posting your configs?

---

### Post by GStubbs43 on 2006-11-08
> **klato said:**
> Id be interested as hell to know how you get 3000fps on a radeon 7500! I can only get 1050, and that's only if I make my desktop 16 bit in xorg.conf. Also, in the video, you said you had it running without XGL/AIGLX...I didn't know that was possible?


I don't think it is, but 6.10 *comes with* AIGLX pre-installed, so he probably has it without knowing. ;)

---

### Post by inetd on 2006-11-12
I followed this howto and beryl is working no problem.  One thing you need to have is the restricted-modules installed.

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

---

### Post by MooSchmoo on 2007-02-04
> **klato said:**
> cinephy/rbalfour: Would you guys mind posting your configs?

Yeah I've been trying to get this working for a while too.. no joy, any chance you can post the relevant configs and let us know what drivers/beryl packages you're using? :)

---

