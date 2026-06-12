---
title: "slow virtual box (throttled cpu?)"
date: 2008-06-18
forum: Virtualisation
---

### Post by tesna on 2008-06-18
Hello All, 

I tried to use virtual box to run winxp fresh install on my hardy, running on Thinkpad T61, 2GB ram, 2ghz T7300, nvidia quadro, etc. But why the guest system running quite slow. 

On hardy, 3d works fine, my bluetooth mouse working properly. Overall ubuntu runs pretty smooth and fast. But I need Excel 2007 for work, because I use some functions which only available on excel 2007. Tried to use wine, but I only managed to get office 2003 to work properly, excel 2007 always crash after splash image, so I gave up using wine. 

Tried to install VMware, but somehow I couldn't get it to work. So I decided to try VirtualBox. The whole setup went fine, I'm quite suprised that the installer size is much smaller than vmware. Configure VM with 512 MB ram, 8 MB video, 10G hdd space, then run windows xp setup (SP2). 

The install went pretty long, but I'm patient and finally it finished. Install guest additions, then install office 2007. Generally it runs, but it feels much slower than the XP running on vmware on my main os (vista x64).

I look at cpu frequency monitor applet and cpu usage applet, the cpu usage is always high (100%) when working with excel, but the frequency stays at 800mhz (throttled mode). Why it didn't automatically increase the freq? When I'm working with high load programs on ubuntu I saw the numbers increased to 2Ghz (full speed) when needed. I think this is causing the slowness of my Virtualbox machine. How do I fix it?

---

### Post by tesna on 2008-06-19
guys, I think I found the problem. I noticed after I turned on a VM in VirtualBox the cpu is fixed at 800Mhz (throttled), even after I configured the cpu management to performance instead ondemand. The CPU clock was fixed to 2Ghz then I set the cpu management to performance, but as soon as I start the VM in virtualbox, it drops down to 800Mhz and it stays that way even I stopped the VM and exit virtual box then use cpuburnP6. The problem is fixed when I restart the machine.

I decided to remove powernowd and instlal cpufreq-utils and use that instead to manage my cpu clock, now the cpu clocks never locks to throttled position.

---

