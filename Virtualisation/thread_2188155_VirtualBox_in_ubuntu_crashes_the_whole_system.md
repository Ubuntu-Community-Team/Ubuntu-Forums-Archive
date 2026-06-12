---
title: "VirtualBox in ubuntu crashes the whole system"
date: 2013-11-15
forum: Virtualisation
---

### Post by nikola-puric92 on 2013-11-15
Hi,

I have a problem with using VirtualBox in ubuntu 13.10. Whenever I start a virtual machine ubuntu switches to the console with a  message that a panic occured and then I have to restart the computer. This happens with WinXP and Minix3 3.2.1, haven't tested others. On rare cases instead of crashing ubuntu I get a message that VirtualBox crashed but it continues to work except the main  VBox window get's messed up. I tried messing with the settings but nothing helped. At first I downloaded VirtualBox from Software Center but then i downloaded it from the official website but still the same thing occures. I have no idea what else to do.

Thanks in advance.

---

### Post by ibjsb4 on 2013-11-17
What are your computer specifications (ram,cpu)?

---

### Post by nikola-puric92 on 2013-11-17
It's 2 GB Ram and Intel® Core&#8482;2 CPU E7500 @ 2.93GHz × 2  processor. I think that should't be the problem since I check and I always have above 1GB free ram and the processor should be sufficent too. The only thing that could maybe cause the problem is the graphics card since it is very weak, it's Intel® 945G x86/MMX/SSE2.

---

### Post by ibjsb4 on 2013-11-17
Have you gone through BIOS and looked for any visualization options?

I do not know anything about the 945G chip set, but I did take a look at  drivers and if I read correctly There are restricted drivers available.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=intel+945g+drivers&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=intel+945g+drivers&sa=Search&cof=FORID:9)

You have tried vBox on three different platforms without success.  Maybe you should try VMware.

[URL="https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/6_0"]https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/6_0


[/URL]

---

### Post by nikola-puric92 on 2013-11-17
> You have tried vBox on three different platforms without success.

I think you misunderstood. This is happening only since I installed ubuntu 13.10 and I am trying to run winXP nad minix3 within VBox. I had no problems with VBox on win7 on the same machine so I was thinking the problem was with ubuntu(ex. drivers) or vbox.
I will try the drivers and hope it works.

---

### Post by nikola-puric92 on 2013-11-19
I couldn't install the drivers because of some dependencies it cannot find (will check up on that later). I also tried VMvare but with the same problem. I wrote down what comes up on the scrren this time:
```

[3302.340682] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000b00
[3302.340682]
[3302.340784] drm_kms_helper: panic ocured, switching back to text console.

```

---

### Post by ibjsb4 on 2013-11-19
I have not ran into this problem before.  So I did a couple of searches.

[https://www.google.com/search?client=ubuntu&channel=fs&q=exitcode%3D0x00000b00&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=exitcode%3D0x00000b00&ie=utf-8&oe=utf-8)

[https://www.google.com/search?client=ubuntu&channel=fs&q=drm_kms_helper%3A+panic+ocured%2C+switching+back+to+text+console&ie=utf-8&oe=utf-8#channel=fs&q=drm_kms_helper+panic+occurred+switching+back+to+text+console](https://www.google.com/search?client=ubuntu&channel=fs&q=drm_kms_helper%3A+panic+ocured%2C+switching+back+to+text+console&ie=utf-8&oe=utf-8#channel=fs&q=drm_kms_helper+panic+occurred+switching+back+to+text+console)

And found this.

[http://askubuntu.com/questions/293486/ubuntu-13-change-drm-kms-helper-poll-param](http://askubuntu.com/questions/293486/ubuntu-13-change-drm-kms-helper-poll-param)

This solution is untested by me, up to you if you want to try it.

You did install dkms and build-essential on the host?
```

sudo apt-get install dkms build-essential
```

Also there is the general fix-all command:
```

sudo /etc/init.d/vboxdrv setup
```

Got nothing else for you :(

---

