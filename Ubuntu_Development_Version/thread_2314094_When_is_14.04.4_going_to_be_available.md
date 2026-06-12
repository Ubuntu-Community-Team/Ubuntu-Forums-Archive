---
title: "When is 14.04.4 going to be available?"
date: 2016-02-18
forum: Ubuntu Development Version
---

### Post by markodd on 2016-02-18
Hello,

When is 14.04.4 going to be available for download in the main site: [www.ubuntu.com?](www.ubuntu.com?)

I know it's supposedly today (18th of February) but I'd like to know the exact time. I'm going to format my PC today and I'd like to install the new version..

---

### Post by slickymaster on 2016-02-18
A last-minute bug found with the bcmwl dkms driver on the lts-wily kernel led to one more respin.

[https://lists.ubuntu.com/archives/ubuntu-release/2016-February/003595.html](https://lists.ubuntu.com/archives/ubuntu-release/2016-February/003595.html)

---

### Post by markodd on 2016-02-18
How long is it going to take? Any idea? 

I might just give up, install 14.04.3 and then upgrade ://

---

### Post by slickymaster on 2016-02-18
As Adam states in his email (which I linked in my previous post) new images should be coming out shortly for all flavours.

---

### Post by sudodus on 2016-02-18
The version, which is available at the testing tracker now, will probably be accepted as the final 14.04.4 later today. We can only guess the time. If you are very eager to get it, it's available now via

[http://iso.qa.ubuntu.com/qatracker/milestones/356/builds](http://iso.qa.ubuntu.com/qatracker/milestones/356/builds)

If another version will be uploaded, the changes should be very small ...

---

### Post by markodd on 2016-02-18
> **slickymaster said:**
> As Adam states in his email (which I linked in my previous post) new images should be coming out shortly for all flavours.

Yes, but that was almost 14 hours ago.

---

### Post by buzzingrobot on 2016-02-18
You might see it here ([http://releases.ubuntu.com/](http://releases.ubuntu.com/)) before the edits to ubuntu.com can be made.

---

### Post by grahammechanical on 2016-02-18
It is being tested by the Quality Assurance team. We can download ISO images if we cannot wait.

[http://iso.qa.ubuntu.com/qatracker/milestones/356/builds](http://iso.qa.ubuntu.com/qatracker/milestones/356/builds)

This is the download information for the Ubuntu 14.04.4 daily image of 17 Feb 2016

[http://iso.qa.ubuntu.com/qatracker/milestones/356/builds/112745/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/356/builds/112745/downloads)

Regards

---

### Post by ventrical on 2016-02-18
Just update/upgrade an hour ago.

```

ventrical@ventrical-MS-7798:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by Min_Jia on 2016-02-18
Still not shown up on the main download page.

---

### Post by PaulW2U on 2016-02-18
It's now been officially released: [Ubuntu 14.04.4 LTS released]("https://lists.ubuntu.com/archives/ubuntu-announce/2016-February/000205.html").

---

### Post by fjgaude on 2016-02-19
Seems to run okay on Z170 Skylake system... kernel is 4.2.

---

### Post by QDR06VV9 on 2016-02-19
Thanks for reporting this frank "Z170 Skylake system... kernel is 4.2."
Seen a few in the General forum with issues on 14.04.3..So this will helpful for them!
And Me too I think Trusty is one of the Best OS's I have run in quite a few years now, I have beat the crap out of this system and just keeps on keeping on..:D
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

``` 
Cheers

---

### Post by fjgaude on 2016-02-20
```
frank@flash:~$ inxi -b
System:    Host: flash Kernel: 4.4.0-6-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASRock model: Z170 Gaming-ITX/ac
           Bios: American Megatrends v: P1.80 date: 01/27/2016
CPU:       Dual core Intel Core i3-6100 (-HT-MCP-) speed/max: 799/3700 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.17.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 2560x1440@59.95hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 11.1.2
Network:   Card-1: Intel Ethernet Connection (2) I219-V driver: e1000e
           Card-2: Broadcom BCM4352 802.11ac Wireless Network Adapter
           driver: wl
Drives:    HDD Total Size: 756.2GB (32.2% used)
Info:      Processes: 242 Uptime: 15:59 Memory: 1199.9/15736.5MB
           Client: Shell (bash) inxi: 2.2.33 

```

---

### Post by MikeMecanic on 2016-02-20
```
u@tt:~$ lsb_release-a && uname -r
No LSB modules are available.
DistributorID:    Ubuntu
Description:    Ubuntu14.04.4 LTS
Release:    14.04
Codename:    trusty
4.5.0-040500rc4-generic 

```

...Synaptic

```
u@tt:~$ dpkg --list| grep linux-image 
rc [COLOR=#ff3333]**linux-image**[/COLOR]-4.4.1-040401-generic                     4.4.1-040401.201601311534                           amd64       Linux kernel image for version 4.4.1 on 64 bit x86 SMP 
ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.5.0-040500rc4-generic                4.5.0-040500rc4.201602141731                     amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP 
rc [COLOR=#ff3333]**linux-image**[/COLOR]-extra-4.2.0-27-generic                   4.2.0-27.32~14.04.1                                            amd64        Linux kernel extra modules for version 4.2.0 on 64 bitx86 SMP 
rc [COLOR=#ff3333]**linux-image**[/COLOR]-extra-4.2.0-29-generic                   4.2.0-29.34~14.04.1                                            amd64        Linux kernel extra modules for version 4.2.0 on 64 bitx86 SMP 
u@tt:~$ **dpkg -l |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg--purge **
[sudo] password for u:  

```
...
```
u@tt:~$** sudo apt autoremove **
**E: Invalid operation autoremove **
u@tt:~$ [COLOR=#ff3333]**sudo apt-get autoremove **[/COLOR]

```
...
```
u@tt:~$ dpkg --list| grep linux-image 
ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.5.0-040500rc4-generic                  4.5.0-040500rc4.201602141731                       amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP 
u@tt:~$ sudo reboot  

```

For those who believe that we have to reboot when removing old Kernels


```
u@tt:~$ dpkg --list| grep linux-image
ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.5.0-040500rc4-generic                  4.5.0-040500rc4.201602141731                       amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
u@tt:~$ sudo apt-get autoremove
[sudo] password for u: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
u@tt:~$ exit

```

For those who believe that we don't have to reboot when removing old Kernels, on rare occasions  a residual Kernel remains (Iv'e seen it twice only in the last 14 weeks).  So, it's never too much to check if there all gone.


All the best.
Mike

EDIT: 
```
u@tt:~$ dpkg --list | grep linux-image
ii**[COLOR=#ff0000]  linux-image[/COLOR]**-4.5.0-040500rc4-generic                   4.5.0-040500rc4.201602141731                        amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
ii  [COLOR=#ff0000]**linux-image**[/COLOR]-4.5.0-040500rc5-generic                   4.5.0-040500rc5.201602201730                        amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
u@tt:~$
```

---

