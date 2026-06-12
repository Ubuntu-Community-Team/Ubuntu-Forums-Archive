---
title: "kernel 3.2.0-12 won't detect Unity 3D, -10 works fine"
date: 2012-01-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-01-31
Just did an omnibus update.  New kernel will not bring up  Unity 3D or compiz effects but works great on 3.2.0-10.

---

### Post by dino99 on 2012-01-31
hm, dont you feel you get a lot more troubles than other users ? (wonder why)

proposed workaround:
- purge then reinstall: 
dkms
faulty kernel (2 headers + image )
compiz/unity
graphic driver

---

### Post by jfernyhough on 2012-01-31
Sometimes my fglrx kernel module doesn't build or register correctly with a new kernel. A simple reinstall of the driver fixes it.

(There's probably a way to get DKMS to rebuild/reinstall directly but 'sudo dpkg -i *.deb' or 'sudo apt-get install--reinstall fglrx' is very easy to do and to remember).

---

### Post by ventrical on 2012-01-31
> **dino99 said:**
> hm, dont you feel you get a lot more troubles than other users ? (wonder why)



@dino99

  This is Beta Testing .  At least I thought we were suppossed to  post  our problems with Precise here in the forums.

---

### Post by ventrical on 2012-01-31
> **jfernyhough said:**
> Sometimes my fglrx kernel module doesn't build or register correctly with a new kernel. A simple reinstall of the driver fixes it.

(There's probably a way to get DKMS to rebuild/reinstall directly but 'sudo dpkg -i *.deb' or 'sudo apt-get install--reinstall fglrx' is very easy to do and to remember).


  I have a nVidia card on this tower. I tried to re-install the driver but the hardware jockey  will not install it.
So I am assuming that somthing in the last update did not  include the NVidia driver for kernel 3.2.0-12 because it works great in -10.

---

### Post by dino99 on 2012-01-31
> **ventrical said:**
> I have a nVidia card on this tower. I tried to re-install the driver but the hardware jockey  will not install it.
So I am assuming that somthing in the last update did not  include the NVidia driver for kernel 3.2.0-12 because it works great in -10.

both ATI + Nvidia  in the same box?
if so, getting warnings with xconfig can be easily understood. By the way xconfig should not be used, follow the ubuntu spirit, not the nvidia one.

---

### Post by ventrical on 2012-01-31
> **dino99 said:**
> both ATI + Nvidia  in the same box?
if so, getting warnings with xconfig can be easily understood. By the way xconfig should not be used, follow the ubuntu spirit, not the nvidia one.

  I disabled the ATI onboard video chip during alpha Ocelot testing. Could not get Unity 3D. I got a new nVidia card about 6 months ago . Has worked great with Unity 3D and compiz/ccsm until 3.2.0-12.

---

### Post by ventrical on 2012-01-31
Ok... found it here:

[COLOR=Blue]18.[/COLOR]Just tried installing Precise for the first time today, using Alpha 1. I have an nvidia gs7600 card.
Installation went fine but on reboot the system repeatedly hung without    booting to the Desktop. The 'nomodeset' option did not help.
Updating the packages from the recovery mode terminal didn't work    either, nor did trying to start lightdm after a terminal log in.
What finally allowed booting to the Desktop was removing all nvidia packages and then reinstalling *nvidia-current* (which also installed nvidia-settings). 	Code:
 	sudo apt-get purge nvidia*  sudo apt-get install nvidia-current

---

