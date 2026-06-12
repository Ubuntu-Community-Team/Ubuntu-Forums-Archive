---
title: "Plymouth issue (not dualboot)"
date: 2016-01-20
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2016-01-20
I'm not able to get rid of the very long Plymouth sequence.  Running Kernel 4.4 alone and with other flavors I was getting just a few lines. Try many things so far.  Usually removing quiet splash was fine but now its worst: The sequence is longer and disorderly.  

So, which parameter(s) I have to modify(gedit)?
Thanks in advance,

```
x@uk:~$ dpkg -l | grep grub
ii  grub-common                                   2.02~beta2-33                              amd64        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                         0.7                                        amd64        GRUB gfxpayload blacklist
ii  grub-pc                                       2.02~beta2-33                              amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                   2.02~beta2-33                              amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                  2.02~beta2-33                              amd64        GRand Unified Bootloader (common files for version 2)
xx@uk:~$ 

```

gksu gedit /etc/default/grub
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=Ubuntu\ Kylin
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by tista on 2016-01-20
@MikeMecanic,

I'm not quite sure about Kylin though, **"noplymouth"** kernel parameter did not work for stopping plymouth splash?
Or I'm afraid that your kernel had some "wait" caused in your hardware specific problems... If so, you should do systemd-analyze to track down and determine which part of boot sequence had such wait.

Regards.
Tista

---

### Post by MikeMecanic on 2016-01-20
Thanks for replying Tista.  Your answer and the results remind me that I didn't run this command line to disable some programms on startup.  By doing so, I gain 3 seconds on startup: 


Visualize Startup Applications:
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

```
xx@uk:~$ sudo systemd-analyze
[sudo] password for xx: 
Startup finished in 3.886s (kernel) + 10.584s (userspace) = 14.471s
xx@uk:~$
```
Does 14 seconds acceptable?

That's the way Kernel 4.4 loads (default) when you run it alone in Gnome, Xubuntu and Kylin now: No boot image and no boot messages (4-5 lines only).   Sounds very good because I'm not getting black screen issues on startup anymore.

```
gksu gedit /etc/default/grub
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0                    **/Set to one you get the boot image**
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=Ubuntu\ Kylin
GRUB_CMDLINE_LINUX_DEFAULT=**[COLOR=#ff0000]"quiet"[/COLOR]** ** /just have to delete splash**
GRUB_CMDLINE_LINUX=                              [B]/When this parameter was there, removing splash didn't work. 
[/B]```
sudo update-grub2
```

---

### Post by tista on 2016-01-20
For example, my VAIO Z 2011 runs like this chart:

[[img]http://s10.postimg.org/49hxvbm1x/boot_chart.jpg[/img]](http://postimg.org/image/49hxvbm1x/)

And top-10 blames are:
```

           450ms dev-dm\x2d3.device
           340ms ssh.service
           228ms networking.service
           197ms loadcpufreq.service
           177ms accounts-daemon.service
           165ms binfmt-support.service
           152ms irqbalance.service
           137ms systemd-logind.service
           131ms grub-common.service
           120ms speech-dispatcher.service
```

Just my thoughts, 14 seconds boot is too slow if SSDs were employed...

Regards.
Tista

---

### Post by MikeMecanic on 2016-01-24
Today's updates screw up the boot sequence.  I'm back to original setting except for the boot image. Set that way, I don't have the boot messages not even the 4-5 lines.  The boot image was not there originally (dark grey screen) but Kylin have pretty nice one.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=3  
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=Ubuntu\ Kylin
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="locale=zh_CN"

---

