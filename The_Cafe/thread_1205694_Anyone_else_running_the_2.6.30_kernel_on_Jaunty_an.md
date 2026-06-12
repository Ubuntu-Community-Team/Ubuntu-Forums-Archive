---
title: "Anyone else running the 2.6.30 kernel on Jaunty and see a performance boost?"
date: 2009-07-06
forum: The Cafe
---

### Post by bxcrx on 2009-07-06
I upgraded my Desktop running the 2.6.28 kernel in Jaunty to the 2.6.30 kernel because I needed to disable ipv6 easily and I had no luck by any other method.  I could swear that I've noticed some performance enhancements too particularly with  the **185.18.14 nvidia driver**.  Then again it could be faster due to ipv6 now being disabled.  

note*: This kernel (2.6.30) is not officially supported by Ubuntu for Jaunty Jackalope so results may vary.


I also upgraded my nvidia video driver while running the 2.6.28 kernel before upgrading to the 2.6.30 kernel.

**I installed the 185.14.18 nvidia video driver from a PPA found here:**


[https://launchpad.net/~brandonsnider/+archive/ppa]("https://launchpad.net/~brandonsnider/+archive/ppa")


**[COLOR="Red"]note* It seems like there is a bug with the 180.xx version nvidia driver, so if you run into trouble its suggested to upgrade to the 185.14.18 version first then upgrade to the 2.6.30 kernel.[/COLOR]**

**This downloads the 2.6.30 kernel via Terminal**

[HTML]
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb[/HTML]


**This installs the 2.6.30 kernel via Terminal**

[HTML]
sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb
[/HTML]


**Updating Grub**

After it would install the 2.6.30 kernel it didn't show up or boot into it upon restart so I had to run the following three commmands to get it to work there-after.

This backs up your current boot list via Terminal:

**sudo cp /boot/grub/menu.lst /boot/grub/menu.list.back**

*This removes your current boot list via Terminal:*
[COLOR="Red"]
**sudo rm -rf /boot/grub/menu.lst**[/COLOR]

*This will generate a new "menu.lst" file via Terminal:*

note* It should say that it didn't detect the "menu.lst" file and then have a "y/N" answer for the question to make a new one. Select "y" of course!

**sudo update-grub**

note* if it doesn't generate a new "menu.lst" file then put your old one back via Terminal:
[B]
sudo cp /boot/grub/menu.list.back /boot/grub/menu.list[/B]


*You can see if you've booted into the right kernel via terminal by:*

**sudo uname -a **

Then you'll see the version that you've booted into.

If you would like to choose a kernel that you would like to boot into then download and install startupmanager via Terminal:
[B]
sudo apt-get install startupmanager[/B]

You can see the example here:

[http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html]("http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html")

---

### Post by lovinglinux on 2009-07-06
How do you revert that if something goes wrong? Can you simply restore the menu.list backup?

---

### Post by Sealbhach on 2009-07-06
Does it boot up faster? I was considering doing this to see if I could get my webcam working, seems a little risky though, don't they always have warnings that installing a newer kernel might break your system?

.

---

### Post by DougieFresh4U on 2009-07-06
If your using 'ATI' for graphics and use 'fglrx' driver, don't plan on much success with the newer kernels.

---

### Post by RD1 on 2009-07-06
I've been running 2.6.30 series kernel since the rc5 release (running the final now). I've noticed improved performance, especially snappier video response. No negative issues at all ... and my webcam works now! Also shaved about 5 seconds off my boot-time.

I just downloaded the appropriate .debs from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

I used headers-all, headers-i386, image-i386, and source-all.

Just run the debs .... I'm not sure of the correct order but, if you get the order wrong, Gdebi will spit out an error telling you which package needs to be installed first.

The new kernel will be added to your grub menu. Use System>Administration>StartUpManager to see which kernels are installed and select your default. If you have problems with the new kernel, your merely need to reselect your old kernel.

---

### Post by spongypants23 on 2009-07-06
I'm intrigued, but also a bit afraid of messing up my system.

How dangerous would this be to do on Jaunty? Are there giant risks?

---

### Post by snowpine on 2009-07-06
Spongypants, the risks are very small, because if there's a problem, you can simply reboot and choose the old kernel from the Grub menu.

---

### Post by exploder on 2009-07-06
I am running the 2.6.30 kernel to resolve the Intel issue with the Jaunty base. I am actually running LinuxMint 7 KDE CE release candidate.The newer kernel greatly improves the Intel issue and does provide a faster boot time. Things do seem quicker but this may be due to the graphics issue being resolved with this kernel.

---

### Post by Pogeymanz on 2009-07-06
I upgraded the kernel and the intel drivers and my performance went WAY up.

The risk is pretty small if you also keep the old kernel installed.

---

### Post by RD1 on 2009-07-06
> I'm intrigued, but also a bit afraid of messing up my system.

How dangerous would this be to do on Jaunty? Are there giant risks?

Maybe I'm being dense but ... What risks? You're not overwriting your system. You're just ADDING another kernel to choose from. You can have as many kernels installed on your computer as you like. If it doesn't work out, you simply reboot and select the old kernel from the grub menu.

Personally, I recommend the .30 kernel. Your mileage may vary though. All I can say is, give it a shot. I see no great risk.

---

### Post by imlinux on 2009-07-06
thanks for the post, i just installed it,it does have better performance.

---

### Post by lovinglinux on 2009-07-06
> **RD1 said:**
> I've been running 2.6.30 series kernel since the rc5 release (running the final now). I've noticed improved performance, especially snappier video response. No negative issues at all ... and my webcam works now! Also shaved about 5 seconds off my boot-time.

I just downloaded the appropriate .debs from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

I used headers-all, headers-i386, image-i386, and source-all.

Just run the debs .... I'm not sure of the correct order but, if you get the order wrong, Gdebi will spit out an error telling you which package needs to be installed first.

The new kernel will be added to your grub menu. Use System>Administration>StartUpManager to see which kernels are installed and select your default. If you have problems with the new kernel, your merely need to reselect your old kernel.

I just installed all recommended debs, but llirc and nVida modules fail to install. Do you know how to solve this?

---

### Post by RD1 on 2009-07-06
Do you have dkms installed? 

```
sudo apt-get install dkms
```

this will then reconfigure drivers for the new kernel on re-boot.

---

### Post by spongypants23 on 2009-07-06
I was unable to install the nVidia drivers after installing 2.6.30.

I don't use the drivers from the repos, I get mine from nVidia's website since they're more up-to-date.

---

### Post by Mazza558 on 2009-07-06
> **lovinglinux said:**
> I just installed all recommended debs, but llirc and nVida modules fail to install. Do you know how to solve this?

Are you using the nvidia ppa?

You might want to try booting into the new kernel and installing the very latest drivers via command-line.

---

### Post by lovinglinux on 2009-07-06
> **RD1 said:**
> Do you have dkms installed? 

```
sudo apt-get install dkms
```

this will then reconfigure drivers for the new kernel on re-boot.

Yes, I have the latest version.

The Apparmor module is not loading either. So unless there is a solution, it's a no go for me.

---

### Post by RD1 on 2009-07-06
Looks like there may be a problem with nVidia and the 2.6.30 kernel. (SURPRISE!)

Look here ... [https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/384639/comments/8]("https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/384639/comments/8")

Apparently you need to install the new nvidia drivers before the kernel.

I really don't know much about the nVidia problems. I'm stuck with the built in Intel video on my laptop.

---

### Post by lovinglinux on 2009-07-06
> **RD1 said:**
> Looks like there may be a problem with nVidia and the 2.6.30 kernel. (SURPRISE!)

Look here ... [https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/384639/comments/8]("https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/384639/comments/8")

Apparently you need to install the new nvidia drivers before the kernel.

I really don't know much about the nVidia problems. I'm stuck with the built in Intel video on my laptop.

:lol:

Does it worth the trouble?

---

### Post by infoseeker on 2009-07-06
While we are on the topic of kernels, what is the reason for this, as its been some time now:
```
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic

```

---

### Post by lovinglinux on 2009-07-06
> **Mazza558 said:**
> Are you using the nvidia ppa?

You might want to try booting into the new kernel and installing the very latest drivers via command-line.

Nope.

I'm starting to think it's too much trouble. Does it really have performance benefits? I noticed  a lot of performance improvements with recent updates, specially when the[ kernel was updated, along with xorg and compiz](http://ubuntuforums.org/showthread.php?t=1195028).

---

### Post by Cam42 on 2009-07-06
Umm...> sudo **rm -rf** /boot/grub/menu.lst what does that do?

---

### Post by spongypants23 on 2009-07-06
> **Cam42 said:**
> Umm... what does that do?

Removes the file. The command "sudo rm -rf" should really never be used unless you know **exactly** what you are doing. It would be better to open Nautilus as root and delete the file.

---

### Post by LookTJ on 2009-07-06
> **Cam42 said:**
> Umm... what does that do?
it removes the file, though you don't need the r flag

---

### Post by Sealbhach on 2009-07-06
OK, that all worked fine. First I had to update my Nvidia driver from 180.44 to 185.18.14 but very easy to do using .debs from here:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/)

Then installed the new kernel using the .debs from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Was surprisingly easy doing it all with .debs, thanks for all the info in this thread everyone.

.

---

### Post by Arup on 2009-07-06
> **Sealbhach said:**
> OK, that all worked fine. First I had to update my Nvidia driver from 180.44 to 185.18.14 but very easy to do using .debs from here:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/)

Then installed the new kernel using the .debs from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Was surprisingly easy doing it all with .debs, thanks for all the info in this thread everyone.

.

When you installed the nvidia driver, did it complain of incompatibility with gcc 4.3 as the driver is written with gcc 4.4?

---

### Post by Sealbhach on 2009-07-06
> **Arup said:**
> When you installed the nvidia driver, did it complain of incompatibility with gcc 4.3 as the driver is written with gcc 4.4?

Nope. Not that I noticed. Installed fine anyway.

.

---

### Post by Arup on 2009-07-06
> **Sealbhach said:**
> Nope. Not that I noticed. Installed fine anyway.

.

Did you install the nvidia driver from the nvidia site or from Ubuntu site?

---

### Post by kpkeerthi on 2009-07-06
I installed it but don't see any performance improvement. I'm using nvidia, 185.18.14. Intel users will surely see some improvement. I reverted back to .28 kernel as I found VTs stopped working altogether.

For those running nvidia binary driver downloaded off nvidia website, I recommend configuring dkms ([http://ubuntuforums.org/showthread.php?t=1036788]("http://ubuntuforums.org/showthread.php?t=1036788")). It works flawlessly for me.

---

### Post by Sealbhach on 2009-07-06
> **Arup said:**
> Did you install the nvidia driver from the nvidia site or from Ubuntu site?

The Ubuntu .deb.

.

---

### Post by X-BANE on 2009-07-06
> **Arup said:**
> When you installed the nvidia driver, did it complain of incompatibility with gcc 4.3 as the driver is written with gcc 4.4?

I got this error as well, but the driver installed successfully.

---

### Post by szadek_ on 2009-07-07
I followed the instructions , installed first nvidia driver , and then the kernel , no error's found .... rebooted , the wireless card was not recognized ... to bad , i can confirm perfomance it was indeed better ( using kde 4.3 rc1 ) , but , no wireless , back to old kernel ... too bad =/ .

---

### Post by Blacklightbulb on 2009-07-07
No thanks enough debugging for today but tomorrow is another day right.;)

---

### Post by koleoptero on 2009-07-08
I installed it when I saw this thread. I didn't see any significant performance improvements, although the system was a bit more responsive sometimes. But then I got glitches in sound so I removed it and reinstalled the 2.6.28 of jaunty.

---

### Post by kpkeerthi on 2009-07-18
I **compiled** it from source to see if it would fix [this issue]("http://ubuntuforums.org/showpost.php?p=7507778&postcount=1") I had and I'm happy with the end result.

This was my first kernel compilation exercise and it was a great learning experience. I have spent almost 9 hours on this to come up with a config that suits my laptop, with only the right set of required modules and no extras in the kernel. 

_**My kernel config summary:**_
1. Optimized for Pentium-M CPU
2. Low-latency desktop
3. Disabled IPv6
4. Graphics drivers - only vga & vesa support. (I use nvidia binary driver).
5. Wireless drivers - only ipw2200
6. File system - only ext2/3/4 and JFS
7. Disabled all profiling/debug/statistics related kernel configs
8. Audio - only intel HDA and Creative Audigy (emu10k1)
9. Disabled unnecessary CPU scaling drivers
... and many more that would take a day for me list them all here. The standard 'generic' Ubuntu kernel comes packed with so much, with little extra care I managed to create a kernel image as small as 16 Mb, stripping all those unneeded extras.

**_What did the new kernel fix for me?_**
1. The annoying system beep is gone - disabled in kernel config.
2. CPU frequency scaling now works properly for me. Sometime the processor won't go above 800Mhz before (even while encoding videos!).
3. Boot time (from GRUB -> **Desktop**) reduced to 36 seconds from 45 seconds.
4. Idle memory (RAM) usage reduced to 140 Mb from 190 MB.
5. Idle CPU usage is 1%. It constantly fluctuated between 4 to 10% every 2 seconds before.
6. Complete freeze due to EXT4.

* The above comparisons were made with the same set of applications, daemons and startup applications, latest nvidia binary driver (185.18.14) and compiz running on Ubuntu/GNOME.

**_My (rather outdated) Laptop:_**
Dell XPS M170: Centrino 2.13Ghz (single core), 2 GB RAM, Nvidia 7800 GTX, 100 GB HDD.

[[img]http://xs141.xs.to/xs141/09296/new-kernel-conky795.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs141&d=09296&f=new-kernel-conky795.png)

---

### Post by Sealbhach on 2009-07-18
I perceived there was some extra heating and fan noise the the 2.6.30 kernel so I switched back. 

.

---

