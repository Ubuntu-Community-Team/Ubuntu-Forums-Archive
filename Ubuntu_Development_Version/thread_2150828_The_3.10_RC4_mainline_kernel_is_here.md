---
title: "The 3.10 RC4 mainline kernel is here"
date: 2013-06-02
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-06-02
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc4-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc4-saucy/)
easy installer
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

---

### Post by slickymaster on 2013-06-04
Thanks for the heads up, pqwoerituytrueiwoq. Already downloading it.

---

### Post by Chanath on 2013-06-04
Installed 3.10 RC4, and while installing it said that certain firmware was not found, and not installed, so I used apt-get -f install later. It is working, but would the missing firmare be a problem?

---

### Post by slickymaster on 2013-06-04
> **Chanath said:**
> Installed 3.10 RC4, and while installing it said that certain firmware was not found, and not installed, so I used apt-get -f install later. It is working, but would the missing firmare be a problem?

Everything went fine here:```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
3.10.0-031000rc4-generic
```But you could eventually face some problems with the device(s) controlled by that missing firmware. How did you installed the kernel? Can you post the commands you used?

---

### Post by Chanath on 2013-06-04
> **slickymaster said:**
> How did you installed the kernel? Can you post the commands you used?

Downloaded linux image & headers from here; [http://kernel.ubuntu.com/~kernel-ppa....10-rc4-saucy/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.10-rc4-saucy/")
and did sudo dpkg -i <the .deb package>
When installing the kernel image, it said there were some firmware missing and sort of didn't install it fully. So, I did sudo apt-get -f install and everything went well.

---

### Post by zika on 2013-06-04
Could You look into /var/log/dpkg.log just to see what went missing in that case...?

---

### Post by IanW on 2013-06-04
I found that dkms didn't want to build nvidia-319 against this kernel (or any 3.10 series kernel) until I added xorg-edgers PPA.

---

### Post by pqwoerituytrueiwoq on 2013-06-04
> **IanW said:**
> I found that dkms didn't want to build nvidia-319 against this kernel (or any 3.10 series kernel) until I added xorg-edgers PPA.i assumed everyone here knew that from last week when rc3 came out

3.10 works fine on raring with no proprietary drivers, but don't expect virtualbox to work (doing this on my laptop)

has anyone noticed the new cpu scaling driver [FONT=courier new]intel_pstate[/FONT] can run the cpu below the min frequency
```
~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver
intel_pstate
```
```
~$ cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_{min,cur}_freq 
800000
800000
782000
782000
```
* you need to chmod the cpuinfo_cur_freq file to 444 to read it, the default is 400, so you need sudo by default
i have also seen it run at 805000 and 828000

---

### Post by IanW on 2013-06-04
> **pqwoerituytrueiwoq said:**
> i assumed everyone here knew that from last week when rc3 came out

I jumped in at the weekend, and went straight to rc4.

---

### Post by jfernyhough on 2013-06-05
I've just gone for rc4 (as I found patches for fglrx, though I've now lost console/ttys). First impressions are good, everything seems even faster than before. (Random example: with 3.9.4 when I clicked Home in Google+ the Firefox tab would freeze for a moment, with 3.10rc4 there's no pause).

---

### Post by xeizo on 2013-06-06
> **jfernyhough said:**
> I've just gone for rc4 (as I found patches for fglrx, though I've now lost console/ttys). First impressions are good, everything seems even faster than before. (Random example: with 3.9.4 when I clicked Home in Google+ the Firefox tab would freeze for a moment, with 3.10rc4 there's no pause).

Well, I tried both RC4 and todays daily, after adding xorg-edgers so did Nvidia actually install but it didn't work. Both kernels booted alright, but hung on the gnome login screensaver(running gnome-shell at the moment). ctrl-alt-F1 and it was possible to start X, but only with fallback driver to a fallback desktop. Not so funny, so I'm back at 3.9 where everything works ....

---

### Post by Chanath on 2013-06-08
Now that Saucy repos has GS 3.8.2, I reinstalled yesterday's Saucy daily image and installed GS in it, after that installed the kernel 3.10RC4. Everything works well. Earlier, I had GS 3.8.2 from Gnome3 Staging PPA, which is from Raring and when upgraded, I lost the background. The Unity side is also doing very well.:mad:

---

### Post by IanW on 2013-06-09
> **xeizo said:**
> Well, I tried both RC4 and todays daily, after adding xorg-edgers so did Nvidia actually install but it didn't work. Both kernels booted alright, but hung on the gnome login screensaver(running gnome-shell at the moment). ctrl-alt-F1 and it was possible to start X, but only with fallback driver to a fallback desktop. Not so funny, so I'm back at 3.9 where everything works ....

I think what fixed it for me (I have a GTX670 so I'm using nvidia-319) was to lock nvidia-319 to the xorg-edgers/saucy version to stop it being overriden by saucy's own nvidia-319 & install "nvidia-persistanced"

---

### Post by pqwoerituytrueiwoq on 2013-06-09
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc5-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc5-saucy/)
rc5 is here

---

### Post by tad1073 on 2013-06-10
Could you take me through the steps that you used?

---

### Post by zika on 2013-06-10
> **pqwoerituytrueiwoq said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc5-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc5-saucy/)
rc5 is here
[http://ubuntuforums.org/showthread.php?t=2152781](http://ubuntuforums.org/showthread.php?t=2152781)

---

### Post by pqwoerituytrueiwoq on 2013-06-10
> **tad1073 said:**
> Could you take me through the steps that you used?To install it click the second link and follow the instructions

---

