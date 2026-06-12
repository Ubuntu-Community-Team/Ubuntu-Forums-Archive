---
title: "how to enable dedicated graphics card to default instead of integrated graphics unit"
date: 2024-10-01
forum: Ubuntu Development Version
---

### Post by zarosath on 2024-10-01
[]("https://askubuntu.com/posts/1528707/timeline")  
          
                                        i'm running Ubuntu 24.10 beta set to launch october. well, it seems  applications are running the APU as they used to be called instead of  the dedicated card, this causes my blitzmax application i am developing  to segmentation fault (old software) and not run.
 even a bench testing app i ran from the web seems to be using my APU  instead of the dedicated card. I'm asking why this is and how i can use  the dedicated card so my applications can run and have the APU on standby  for apps like firefox and things. google search brings up old Ubuntu  releases and different hardware.


     
                                  my hardware is a amd ryzen 7000 series cpu/gpu and an amd Radeon rx 6550m gpu dedicated card.

---

### Post by zarosath on 2024-10-01
it used to work on ubuntu 24.04 but now its using the APU on fresh install of 24.10 beta yesterday.

---

### Post by zarosath on 2024-10-02
here is from IRC my messages. nobody seems to want to respond about this.

> Wednesday, October 2, 2024] [11:31:21 AM MDT]<william> hi! i'm trying to use my dedicated graphics card over my APU for my old software application for some reason in 24.10 my card isnt being enabled for use
[Wednesday, October 2, 2024] [11:31:38 AM MDT]<william> it was default for such applications (the card) in ubuntu 24.04
[Wednesday, October 2, 2024] [11:31:49 AM MDT]<william> i do not know how
[Wednesday, October 2, 2024] [11:32:29 AM MDT]<william> can anybody offer insight?
[Wednesday, October 2, 2024] [11:34:53 AM MDT]<william> on my part, graphics is AMD Radeon&#8482; 780M (APU) and graphics 1 is the dedicated card
[Wednesday, October 2, 2024] [11:37:22 AM MDT]<william> with nvidia i had the option to install/uninstall drivers in the additional drivers section but this is a amd build

i hope its okay to share that.

---

### Post by QIII on 2024-10-02
If you want to use your dedicated card exclusively, it would be best to set it as the primary in your BIOS/EFI.  Generally, an integrated GPU will be chosen by the BIOS/EFI by default.

Or do you want to be able to switch back and forth?

Just a note:  Development versions may have bugs/kinks that have not been worked out yet.  Best to use a supported version.

---

### Post by deadflowr on 2024-10-02
Looking here: [https://answers.launchpad.net/ubuntu/noble/+package/switcheroo-control](https://answers.launchpad.net/ubuntu/noble/+package/switcheroo-control)
I read:

>  For systems that have both an integrated GPU and a dedicated GPU, this
 package by default will force the integrated GPU to be used to save power.
 .
 You can launch individual apps using the dedicated GPU by running them
 with the environment variable DRI_PRIME=1. Or you can right-click on the
 app (while it's not running) in GNOME Shell's Activities Overview
 and choose the "Launch using Dedicated Graphics Card" option.
 .
 If this default behavior is not appropriate, uninstall this package or
 set xdg.force_integrated=0 as a kernel command-line option in your
 bootloader.

So I guess you can try setting the kernel parameter option.

---

### Post by zarosath on 2024-10-02
i've found this for instance but i do not want to break my install and i do not know why it is set up correctly in 24.04 and not 24.10

[https://www.reddit.com/r/linux_gaming/comments/wjkqtw/dri_prime_operates_backwards/](https://www.reddit.com/r/linux_gaming/comments/wjkqtw/dri_prime_operates_backwards/)

---

### Post by zarosath on 2024-10-02
thank you for your responses, i'll check those.

---

### Post by zarosath on 2024-10-02
seems the applications are still using the integrated gpu i've tried those and also xrandr setprovideroffloadsink and prime but it may be the applications which were working fine under 24.04.

i am considering just installing 24.04 for now but i wanted the updated kernel version. i dont know what gives. i've had the issue in the past were i simply installed/used the nvidia proprietary driver however in this case its AMD which the applications were working in 24.04. i have no idea. is there anything we could check? GpuTest_Linux_x64_0.7.0 seems to run the integrated gpu and my application i am working on with old software seems to use whatever the OS gives it and it wont run without the dedicated card.

---

### Post by zarosath on 2024-10-02
i should also reply that package is installed and i am going to search about it

---

### Post by zarosath on 2024-10-02
i have tried your solutions but it has not succeeded.

i can see the bios hybridgraphics option but it is greyed out and inaccessible in bios, its an msi bravo 15 b7e laptop and its under amd graphics configuration (i forgot the name this config is under, AMD something.) i even set different settings in there from the integrated graphics processor to discreet card.

none of the software options have worked. albeit maybe i didnt change the bootloader settings i opened grub config file and added the kernel command and even tried it in terminal. if i uninstall switcheroo-control, after removing switcheroo package it didnt list my dedicated card in the OS settings/about system.

i can report with more clarity later i am confusing. i think i am going to install ubuntu 24.04.1 where it was working and hope when 24.10 launches i will not have this issue upon upgrading. i will report then.

---

### Post by zarosath on 2024-10-03
alright i have reason to believe the beta just doesnt include the gpu kernel driver module? because i could (but failed) install amdgpu-dkms i'm back on ubuntu 24.04.1 and may upgrade later sometime after release may be things may be working then..

i have no idea maybe somebody could offer input someone has knowledge about this? i finally bought a amd radeon PC after having my nvidia/intel build and because everybody was saying i should be using AMD RADEON or else no support and now everybody is pushing linux nvidia builds architecture about this a lot of people using nvidia. it sucks that AMD may not be making GPU cards very much anymore i hope they'll keep producing mid-range graphics cards.

i tried the Reverse Prime (xrandr command) and it still couldnt fix it, i believe the kernel radeon drivers were just not installed and i were unable to resolve so i've reinstalled ubuntu 24.04.1 and will stick to it for a long while. So.. My issue i am having is not resolved but it is kind of, this could be the very reason my dedicated card wasnt being used for opengl applications the kernel module driver just was not installed for the dedicated card or something on beta ubuntu 24.10.

i like my AMD build a lot it was the best for the budget i got it for linux but i'm telling  you those users were mean 2022-2023 on the forums here when i had an issue with my intel/nvidia card and that nvidia  is being used more the prime architecture for hybridgraphics almost  seems biased towards it at least on arch linux. no idea why somebody  couldnt offer a clue here ubuntu. maybe after release somebody will  notice that applications are not using the dedicated radeon card by  default for game applications with the hybridgraphics and we cannot  rewrite the applications or change locked bios settings. seems to be  working as intended on ubuntu 24.04.1

i'm just grateful i can use linux/ubuntu on my new laptop anyway with the LTS release.

---

