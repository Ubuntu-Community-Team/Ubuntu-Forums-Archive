---
title: "Windows on Xen bad IO performance"
date: 2018-07-26
forum: Virtualisation
---

### Post by jakkuk on 2018-07-26
Hi!

I have a number of different hosts with different xen and windows versions, but they all share the same thing. Each time I install xen windows pv drivers 8.2.0 from here: [https://www.xenproject.org/developers/teams/windows-pv-drivers.html](https://www.xenproject.org/developers/teams/windows-pv-drivers.html) I'm getting worse IO performance than before, on standard Windows drivers.

This one setup for example:
Host:
- X5450, 8GB ram, 240 samsung evo SSD
VM:
- win 2016, 4GB ram, all CPU cores, LVM volume used as the VMs drive (in all cases below).

Xen without PV drivers:
- I'm getting about seq read 34 MB/s, seq write 34 MB/s, random seek + rw 34 MB/s in Passmark
- Atto benchmark runs and provides so so results
- system is always usable

Xen with PV drivers:
- I'm getting about seq read seq read 239 MB/s, seq write 242 MB/s, random seek + rw 241 MB/s in Passmark
- Atto benchmark runs and after a few minutes halts the system, the results are given below
- When the IO is saturated (or something else) the VM halts and takes hours to complete tasks, like the atto benchmark

[ATTACH=CONFIG]280523[/ATTACH][ATTACH=CONFIG]280524[/ATTACH]

KVM with signed drivers from Fedora:
- I'm getting about seq read 147 MB/s, seq write 187 MB/s, random seek + rw 189 MB/s in Passmark
- Atto benchmark runs and provides so so results (so so but better than xen with PV)
- system is always usable
[ATTACH=CONFIG]280525[/ATTACH]

I want to use Xen - the example above is an isolated testbed, that I want to use for testing the functionality before going on PROD. What should I do? What do you recommend? Maybe there are some settings that I've omitted.

---

### Post by jakkuk on 2018-07-30
I found out that I need to modify the gnttab_max_frames parameter to the xen hypervisor at boottime. A lot of links and reading starts here: [https://wiki.gentoo.org/wiki/Xen#Xen_domU_hanging_with_kernel_4.3.2B](https://wiki.gentoo.org/wiki/Xen#Xen_domU_hanging_with_kernel_4.3.2B)

I did some testing and I am very confused right now. The gnttab_max_frames is by default 32 (increased to 64 in some xen version), and to solve the issues i would need to set it higher to 256. The results I get seem to show something totally different. 

New test rig:
[LIST]
[*] ubuntu 18.04 LTS with everything from normal repositories, updated, xen 4.9
[*] i5-8500, 16GB ram, Samsung 850 evo SSD,
[*] windows 2016 installed on a LVM volume,
[*] xen pv drivers 8.2.0 installed on Windows,
[*] logged to the VM using VNC from a laptop in the same local network.
[/LIST]


I've tested this at the following values of gnttab_max_frames:
[LIST]
[*]4
[*]10
[*]64
[*]256
[*]4096
[/LIST]

Passmark provides consistent results at around 510 MB/s READ, 305 MB/s WRITE, 330 MB/s Random ReadWrite, regardless of the setting of gnttab_max_frames. I guess that it does not saturate the grant tables mechanism of XEN that much. But with ATTO, the situation is sooo different.

**gnttab_max_frames = 4 **

Windows is very snappy, responsive, even under heavy load from ATTO.
Atto shows good results, with some signs of saturation with packets bigger than 512KB.

**gnttab_max_frames = 10 **

Windows is very snappy but stops being responsive, even under heavy load from ATTO.
Atto shows mediocre results, saturation is very high with packets bigger than 512KB.

**gnttab_max_frames = 64**

You can feel that the windows windows open a little bit slower, system feels dead with high load from ATTO.
Atto shows bad results, saturation kills the system with packets bigger than 512KB. System is getting back OK after ATTO finishes.

**gnttab_max_frames = 256**
Even worse than 64, the results show similarity to 64, but the system just did not react. I fed up with waiting. 

**gnttab_max_frames = 4096 **
Windows did not boot. I just got fed up with waiting.

Atto screenshots are here, each has a caption saying at which gnttab_max_frames setting is was taken. A comment, if you do ATTO benchmark on a normal drive (or old Xen with GPLPV drivers on windows 2008) you get stable results from 64KB up, bars don't get shorter. Shorter bars at larger packets mean that the IO queue gets saturated or there is some IO usage going on elsewhere - I made sure it does not happen in these tests. [https://imgur.com/gallery/aUPSsCo]("https://imgur.com/gallery/aUPSsCo")

To sum up:
[LIST]
[*]Windows behaves better when I reduce gnttab_max_frames. Quite the opposite to what the internet is saying. 
[*]What did I do wrong?
[/LIST]

---

