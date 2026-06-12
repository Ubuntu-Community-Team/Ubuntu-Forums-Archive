---
title: "HOWTO: Use b43 driver with 14e4:4315 (Broadcom bcm4312 rev 01)"
date: 2009-09-14
forum: Tutorials
---

### Post by chenxiaolong on 2009-09-14
[COLOR="Green"]2010-05-23: B43 works out of the box with the 14e4:4315 card in Ubuntu 10.04 LTS with PIO mode on and QOS off (on kernel 2.6.33.4 or 2.6.34).[/COLOR]

So, basically, this is how to get it working:

Download the 2.6.33.4 or the 2.6.34 kernel from: 

[2.6.33.4]
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.4-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.4-lucid/)

[2.6.34]
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

You need to install:

linux-headers-*-<amd64/i386>.deb
linux-headers-*-all.deb
linux-image-*-<amd64/i386>.deb

and then run:

```
sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf
```

and reboot and that's it :D.

OR to manually load it during an active seesion:

```
sudo rmmod b43
sudo modprobe b43 pio=1 qos=0
```

NOTE: 
(1) PIO mode is good for downloads and uploads and anything involving a browser, but is very slow when transferring files through any protocol besides HTTP/HTTPS/UDP-Torrent.
(2) Since this wireless card is slow under PIO mode, I don't know if the packet injection speed is fast enough for Aircrack-ng.

**[COLOR="Red"]------------------------------------------------------------------------------------------------------------[/COLOR]**

**[COLOR="Red"]PLEASE DO NOT USE ANY OF THE INSTRUCTIONS BELOW. THEY ARE HERE FOR INFORMATION AND HISTORICAL PURPOSES ONLY.[/COLOR]**

[COLOR="Green"]2010-03-25: After testing distro to distro, I can finally conclude that b43 WILL WORK PERFECTLY in DMA mode with any Linux system running kernel 2.6.33. Is that great or what?[/COLOR]

[COLOR="Green"]2010-02-24: Kernel 2.6.32-14.20-generic works with b43 on Karmic...finally[/COLOR]:D[COLOR="Green] (thanks to mikeioannina for testing).[/COLOR]

[COLOR="Green"]2010-02-21: rlelliott has been kind enough to write a guide, based on his testing, on how to get the b43 driver working under Ubuntu 10.04 Lucid (daily image). The guide can be found here: [http://docs.google.com/View?id=dhkq5635_11f3hjxdp6](http://docs.google.com/View?id=dhkq5635_11f3hjxdp6). Unfortunately, there's still no was to get the card working in Karmic besides using the 2.6.32-11-generic kernel.[/COLOR]

[COLOR="Green"]2010-02-12: Works on SOME routers under kernel 2.6.32-12-generic and compat-wireless-2010-02-01. My router settings are: Region=US; Channel=11; Encryption=WPA2-PSK (AES).[/COLOR]

[COLOR="Red"]2010-02-07: Not working under any kernel, except 2.6.32-11-generic, which does not exist under the Ubuntu Lucid alpha testing repo anymore.[/COLOR]

[COLOR="Orange"]2010-02-07: Changed links for 2.6.32-12.17-generic.[/COLOR]

[COLOR="Orange"]2010-02-03: Changed links for 2.6.32-12.16-generic; Untested.[/COLOR]

[COLOR="Green"]2010-01-29: Working kernel: 2.6.32-11-generic; Working compat-wireless: compat-wireless-2010-01-24.[/COLOR]

---

I have good new for everybody :D. B43 finally working without crashes and kernel panics AND it works perfectly with Aircrack-NG now! First of all, you will be using the ALPHA/BETA kernel from LUCID (10.04), which is **_kernel 2.6.32-14-generic_**. It is a DEVELOPMENT release, but works perfectly nonetheless. 

So, here we go:

Before you even get the kernel, you should download and install the b43 device firmware. Make sure you have the package "[COLOR="SeaGreen"]git-core[/COLOR]" installed then follow the instructions at this link: [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp). It's very easy to follow. They're copy and paste commands.

First of all, download and install the new kernel:

i386 (32 bit)
---------------
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic_2.6.32-14.20_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic_2.6.32-14.20_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic_2.6.32-14.20_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic_2.6.32-14.20_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb)


i386-PAE (32 bit with _>_ 4 GB of RAM)
---------------------------------------------
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic-pae_2.6.32-14.20_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic-pae_2.6.32-14.20_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic-pae_2.6.32-14.20_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic-pae_2.6.32-14.20_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb)


amd64 (64 bit)
----------------
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic_2.6.32-14.20_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic_2.6.32-14.20_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic_2.6.32-14.20_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic_2.6.32-14.20_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb)

I like to download the packages to a new folder, and then run: 

```
sudo dpkg -i linux*2.6.*.deb
```

in the folder.

Sooooo, after you download the new kernel, boot into it by choosing it from the GRUB boot menu.

Then, head on over here: [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and download the latest compat-wireless-2010-**-**.tar.gz package to anywhere, preferably an easy to remember location. The package as of now is, compat-wireless-2010-01-26.tar.bz2. I will be using this version for the commands below. Adjust the commands below based on the file you downloaded.

Open up a Terminal and change to the directory you downloaded the file to:

```
cd /your/path/to/the/directory
```

Extract the file you downloaded:

```
tar jxvf compat-wireless-2010-01-26.tar.bz2
```

Change to the extracted directory:

```
cd compat-wireless-2010-01-26
```

Compile the drivers:

```
make
```

Install the drivers:

```
sudo make install
```

Unload the current drivers: (if you are using the Broadcom STA Driver, run "sudo rmmod wl" first)

```
sudo make unload
```

Refresh the drivers/modules for the current kernel:

```
sudo depmod
sudo depmod -a
```

Enable PIO mode:

```
echo "options b43 pio=1" | sudo tee -a "/etc/modprobe.d/b43-thingy.conf"
```

Remove the package "[COLOR="SeaGreen"]bcmwl-kernel-source[/COLOR]." It's the easiest way to ensure that the b43 driver isn't blacklisted. 

Blacklist the wl driver (STA driver):

```
echo "blacklist wl" | sudo tee "/etc/modprobe.d/wedontneednonossdrivers.conf"
```

Add b43 to /etc/modules so it will load at bootup:

```
echo "b43" | sudo tee -a "/etc/modules"
```

Then, reboot your computer and enjoy your wireless (or use ...ahem...aircrack-ng...ahem... and enjoy your wireless :D).

I have no idea why "sudo modprobe b43" doesn't work after installation, but it doesn't.

--

If AFTER you reboot, you get errors in dmesg like:

```
[   11.788669] b43: Unknown symbol ssb_pcicore_dev_irqvecs_enable
[   11.789575] b43: disagrees about version of symbol ssb_bus_may_powerdown
[   11.789586] b43: Unknown symbol ssb_bus_may_powerdown
[   11.790340] b43: disagrees about version of symbol ssb_dma_free_consistent
[   11.790351] b43: Unknown symbol ssb_dma_free_consistent
[   11.792008] b43: disagrees about version of symbol ssb_bus_suspend
[   11.792020] b43: Unknown symbol ssb_bus_suspend
[   11.793154] b43: disagrees about version of symbol ssb_bus_unregister
[   11.793166] b43: Unknown symbol ssb_bus_unregister
[   11.795081] b43: disagrees about version of symbol ssb_bus_resume
[   11.795093] b43: Unknown symbol ssb_bus_resume
[   11.795509] b43: disagrees about version of symbol ssb_set_devtypedata
[   11.795520] b43: Unknown symbol ssb_set_devtypedata
[   11.796959] b43: disagrees about version of symbol ssb_device_disable
[   11.796972] b43: Unknown symbol ssb_device_disable
[   11.797411] b43: disagrees about version of symbol ssb_pmu_set_ldo_voltage
[   11.797422] b43: Unknown symbol ssb_pmu_set_ldo_voltage
[   11.798340] b43: disagrees about version of symbol ssb_dma_alloc_consistent
[   11.798350] b43: Unknown symbol ssb_dma_alloc_consistent
[   11.799029] b43: disagrees about version of symbol ssb_dma_set_mask
[   11.799042] b43: Unknown symbol ssb_dma_set_mask
[   11.801861] b43: disagrees about version of symbol ssb_device_enable
[   11.801874] b43: Unknown symbol ssb_device_enable
[   11.802820] b43: disagrees about version of symbol ssb_driver_unregister
[   11.802833] b43: Unknown symbol ssb_driver_unregister
[   11.804095] b43: disagrees about version of symbol __ssb_driver_register
[   11.804109] b43: Unknown symbol __ssb_driver_register
[   11.821841] b43: Unknown symbol ssb_bus_pcmciabus_register
[   11.822234] b43: disagrees about version of symbol ssb_bus_powerup
[   11.822243] b43: Unknown symbol ssb_bus_powerup
[   11.826522] b43: disagrees about version of symbol ssb_dma_translation
[   11.826535] b43: Unknown symbol ssb_dma_translation
```

then add these lines to /etc/rc.local (thanks to Muti for this information)

```
modprobe -r b43
sleep 3
modprobe b43
```

**[COLOR="Red"]------------------------------------------------------------------------------------------------------------[/COLOR]**

**[COLOR="Red"]PLEASE DO NOT USE ANY OF THE INSTRUCTIONS BELOW. THEY ARE HERE FOR INFORMATION AND HISTORICAL PURPOSES ONLY.[/COLOR]**

[COLOR="Red"]----------------------[/COLOR]

Unfortunately, only patching the b43 driver will not work because it causes a kernel panic after ten seconds. You have to compile a new kernel with the b43 module patched. But..........that's not so bad. I already patched and compiled it for you :D. I'm just trying to find a free reliable web hosting company to host an apt repository for the patched kernels. I can't afford any paid webhosts--I'm only 14. Please PM any suggestions to me (doesn't need PHP or MySQL, just hosting). 

[COLOR="Red"]----------------------[/COLOR]

**2.6.32.3 Script**

[COLOR="Orange"]New Script for kernel 2.6.32.3 (b43_compile_2.6.32.3.sh & b43_kernel_2.6.32.3.sh): Attached below; also at my website: [http://software.6368.co.cc/linux/b43/patches](http://software.6368.co.cc/linux/b43/patches).[/COLOR]

----------------------

**2.6.32.2 Script**

[COLOR="Red"]Script Update 4 (b43_kernel_2.6.32.2.sh): Backs up and renames /usr/src/linux-source-2.6.32 so there is a clean copy of the source to work with.[/COLOR]

[COLOR="Red"]Script Update 3 (b43_compile_2.6.32.2.sh): Fixed error about modules.symversions.[/COLOR]

[COLOR="Red"]Script Update 2 (b43_kernel_2.6.32.2.sh): Fixed kernel download part (i386 --> i686); added checking for "patch" package.[/COLOR]

[COLOR="Red"]Script Update 1 (b43_compile_2.6.32.2.sh): Included the enabling of PIO mode; stupid mistake on my part.[/COLOR]

---------------------

Great news for everyone!! The b43 driver can now be run in Ubuntu 9.10 Karmic WITHOUT any DMA errors!!:D I created a script this time that will install it for you. :D I couldn't have done it without [COLOR="MediumTurquoise"]emas80[/COLOR] (page 26), O-Hatta ([http://www.incentivespro.com/forum/viewtopic.php?t=222](http://www.incentivespro.com/forum/viewtopic.php?t=222)), and of course, the b43 developers ([http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html](http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html)). 

Unfortunately, it only works on kernel 2.6.32. BUT, the first shell script that I created will automatically download and install kernel 2.6.32.2 from the Ubuntu Kernel PPA and patch the b43 driver to get rid of the DMA problems. If you compiled the 2.6.32 kernel or downloaded it from a third party source, the script also works, but you will have to run it with a parameter (see below). Also, if you already have the 2.6.32.* kernel installed from the Ubuntu Kernel PPA, you can just run the script normally. This script can be run as root or as your regular user. It uses sudo commands, so running the script as root might save you from typing your password a million times. Now lets put this paragraph into action :).

PART 1 (described above) of the script can be downloaded here (also attached to this post as b43_kernel_2.6.32.2.sh): [http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.2.sh](http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.2.sh)

IF YOU WANT TO USE THE 2.6.32.2 KERNEL, USE "2.6.32.2" INSTEAD OF "2.6.32.3", INCLUDING LINKS.

Cases:

1. You are using a 2.6.31 kernel (default in Ubuntu 9.10 Karmic)
   Run [COLOR="Red"]sudo sh b43_kernel_2.6.32.3.sh[/COLOR]

2. You are running a third party or self-compiled version of kernel 2.6.32
   Run [COLOR="Red"]sudo sh b43_kernel_2.6.32.3.sh /path/to/kernel/sources[/COLOR]

3. You already have kernel 2.6.32 installed from the Ubuntu Kernel PPA
   Run [COLOR="Red"]sudo sh b43_kernel_2.6.32.3.sh[/COLOR]

Part 1 of the script makes sure that you are using the 2.6.32 kernel and patches the b43 script for compilation during part 2 of the script. If you were running kernel 2.6.31* and the script installed 2.6.32, you MUST boot into the new kernel for b43 to compile (a.k.a. just reboot). Part 2 will prepare the kernel sources to compile the b43 driver and then compile and install b43. After running the script, you will have to make sure that there IS a "[COLOR="DarkOrchid"]b43[/COLOR]" line in [COLOR="DarkOrchid"]/etc/modules[/COLOR] and make sure that there ISN"T a "[COLOR="DarkOrchid"]blacklist b43[/COLOR]" or "[COLOR="DarkOrchid"]blacklist ssb[/COLOR]" line in any of the files in "[COLOR="DarkOrchid"]/etc/modprobe.d[/COLOR]." You run the second script basically like the same way above.

PART 2 (described above) of the script can be downloaded here (also attached to this post as b43_compile_2.6.32.3.sh): [http://software.6368.co.cc/linux/b43/patches/b43_compile_2.6.32.3.sh](http://software.6368.co.cc/linux/b43/patches/b43_compile_2.6.32.3.sh)

Cases:

1. You are (now) running kernel 2.6.32 from the Ubuntu Kernel PPA
   Run [COLOR="Red"]sudo sh b43_compile_2.6.32.3.sh[/COLOR]

2. You are running a third party or self-compiled version of kernel 2.6.32
   Run [COLOR="Red"]sudo sh b43_compile_2.6.32.3.sh /path/to/kernel/sources

Again, after running part 2 of the script, you will need to make sure that in "[COLOR="DarkOrchid"]/etc/modules[/COLOR]," there IS a "[COLOR="DarkOrchid"]b43[/COLOR]" line and that there ISN'T a "[COLOR="DarkOrchid"]blacklist b43[/COLOR]" or "[COLOR="DarkOrchid"]blacklist ssb[/COLOR]" line in any of the files in "[COLOR="DarkOrchid"]/etc/modprobe.d[/COLOR]."

Then reboot and enjoy your wireless!! :D

Notes:

The patch file from my website (also attached to this post) is NOT the same as the patch at [http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html](http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html), although the patch results ARE the same. Emas80 took the time to read the patch file line-by-line and patch the files manually. I downloaded his patched version of the b43 source files (page 26 of this thread) and ran the [COLOR="DarkOrchid"]diff[/COLOR] command between my unmodified b43 source and his patched source, saving the output to a new patch. The new patch is at [http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.3.patch](http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.3.patch).

If you have any doubts about my scripts, you can open them up and check it. I commented (in the script) what every command does. If there's any typos or problems please PM me so I can fix them. They should be okay; I tested the scripts on my computer.

Again, thanks to anyone who helped me with the script and the developers of the b43 driver. 

[COLOR="Red"]----------------------------------------------------------------------------------------------[/COLOR]
This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.

1. Open up Terminal.

2. Install the "linux-backports-modules-karmic" (newer wireless drivers from compat-wireless) package and the "b43-fwcutter" package (wireless firmware). During installation, if it asks you to fetch the firmware automatically, make sure you select yes.

```
sudo apt-get install linux-backports-modules-karmic b43-fwcutter
```

3. Blacklist the ssb module.

```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
```

4. Blacklist the wl module.

```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
```

5. Reboot

6. Enjoy your wireless!!!

**[COLOR="Red"]----------------------------------------------------------------------------------------------------------------[/COLOR]**

First of all, I want to thank lwfinger at openSUSE forums for making the b43 driver work with the 14e4:4315

The post looks verrrrry long right? Well it's not. All the commands are "copy-n-paste-able" and I recommend that you do copy and paste them so you don't make any mistakes.

So first of all, you need to download the latest compat-wireless from > [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

You can't use wget for this because they have a hotlink prevention system. So just download the > compat-wireless-2.6.tar.bz2 file from that website and SAVE IT TO YOUR HOME DIRECTORY. 

Then open the terminal and run this command to extract the archive

```
tar xjf compat-wireless-2.6.tar.bz2
```

In order for the package to compile, you need to install the kernel headers, if not already installed. Run this in the terminal

```
sudo apt-get install linux-headers-$(uname -r)
```

Then change to the compat-wireless directory: 

```
cd compat-wireless
```

Then compile the source files:

```
sudo make
```

Then install the files:

```
sudo make install
```

Then unload the drivers

```
sudo make unload
```

Then install b43-fwcutter:
VERY IMPORTANT!!: Do NOT choose yes when it asks if you want to automatically fetch the firmware.

```
sudo apt-get install b43-fwcutter
```

Download the Broadcom firmware files

```
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```

Extract the archive

```
tar xjf broadcom-wl-4.150.10.5.tar.bz2
```

Change to the driver directory

```
cd broadcom-wl-4.150.10.5/driver
```

Install the firmware

```
b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

Then blacklist the proprietary driver

```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist.conf
```

And finally..............RESTART!!!




I hope this worked for you. It worked for me. 

By the way, I'm turning 14 on September 26, so wish me a happy birthday :)

---

### Post by Sureshot324 on 2009-09-22
I got an error when I ran the make command:

/home/louis/compat-wireless-2009-09-22/drivers/net/wireless/b43/main.c: In function âb43_do_interruptâ:
/home/louis/compat-wireless-2009-09-22/drivers/net/wireless/b43/main.c:1888: error: âIRQ_WAKE_THREADâ undeclared (first use in this function)
/home/louis/compat-wireless-2009-09-22/drivers/net/wireless/b43/main.c:1888: error: (Each undeclared identifier is reported only once
/home/louis/compat-wireless-2009-09-22/drivers/net/wireless/b43/main.c:1888: error: for each function it appears in.)
/home/louis/compat-wireless-2009-09-22/drivers/net/wireless/b43/main.c: In function âb43_request_firmwareâ:
/home/louis/compat-wireless-2009-09-22/drivers/net/wireless/b43/main.c:2218: warning: format not a string literal and no format arguments
/home/louis/compat-wireless-2009-09-22/drivers/net/wireless/b43/main.c: In function âb43_wireless_core_startâ:
/home/louis/compat-wireless-2009-09-22/drivers/net/wireless/b43/main.c:3867: error: implicit declaration of function ârequest_threaded_irqâ
make[4]: *** [/home/louis/compat-wireless-2009-09-22/drivers/net/wireless/b43/main.o] Error 1
make[3]: *** [/home/louis/compat-wireless-2009-09-22/drivers/net/wireless/b43] Error 2
make[2]: *** [/home/louis/compat-wireless-2009-09-22/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/louis/compat-wireless-2009-09-22] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [modules] Error 2

A ideas?

---

### Post by chenxiaolong on 2009-09-22
That happened to me too. I'm trying to find a solution. I was running a different distro at the time, but now I run Ubuntu. The person who originally said how to make it work said it should work on any distro with a kernel 2.6.27 and up. Apparently that's not true in Ubuntu. I'll post a solution when I find one.

---

### Post by Ayuthia on 2009-09-25
Have you tried the most recent one (dated 25 Sept)?  I was able to get a clean make out of it.  I did not go further with it on this computer because the b43 module is not compatible with my wireless card.

---

### Post by chenxiaolong on 2009-09-25
So it compiles with kernel 2.6.28-15 now? I haven't tried it yet, but thanks for the information. I'll try it as soon as I can.

---

### Post by Ayuthia on 2009-09-25
> **chenxiaolong said:**
> So it compiles with kernel 2.6.28-15 now? I haven't tried it yet, but thanks for the information. I'll try it as soon as I can.

That is what I ran it on a little while ago.  I just wish I had this card to test it out.

---

### Post by Sureshot324 on 2009-09-25
The sep 25 release worked for me.  I guess there was a bug in the earlier testing releases.

---

### Post by chenxiaolong on 2009-09-25
What version of Ubuntu did it work for you on? In Ubuntu Jaunty x64, it compiled, but when I modprobe'd it or restarted, it complains that the code in the b43 driver is wrong or unrecognized. If you do run Ubuntu Jaunty x64 and it works, then I'll try reinstalling (once again) and try it.

---

### Post by Sureshot324 on 2009-09-26
I am using Jaunty x64.  Note that I didn't follow your instructions exactly.  I already had the firmware installed from before by doing 'apt-get install b43-fwcutter' and saying yes to download the firmware, so I skipped all your steps about manually installing the firmware.  Also I didn't blacklist wl.

I can now switch between b43 and wl by doing
rmmod wl
modprobe b43

Kismet is working fine with the b43 driver.  I'm no linux guru so I probably won't be much help, but maybe try 'apt-get remove b43-fwcutter', then go into /lib/firmware and remove everything that says b43, then 'apt-get install b43-fwcutter' and say yes to download the firmware.

---

### Post by Ayuthia on 2009-09-26
> **Sureshot324 said:**
> I am using Jaunty x64.  Note that I didn't follow your instructions exactly.  I already had the firmware installed from before by doing 'apt-get install b43-fwcutter' and saying yes to download the firmware, so I skipped all your steps about manually installing the firmware.  Also I didn't blacklist wl.

I can now switch between b43 and wl by doing
rmmod wl
modprobe b43

Kismet is working fine with the b43 driver.  I'm no linux guru so I probably won't be much help, but maybe try 'apt-get remove b43-fwcutter', then go into /lib/firmware and remove everything that says b43, then 'apt-get install b43-fwcutter' and say yes to download the firmware.

From what I recall, the firmware in the first post is the same as what Jaunty is using.  The firmware changes starting in Karmic.  

chenxiaolong, you might rebuild the module again.  The message sounds like you might have compiled it with a different kernel version.  Usually those messages occur if you compile with the wrong architecture or a different kernel.

---

### Post by chenxiaolong on 2009-09-27
I'll reinstall Ubuntu and try again. So the b43-fwcutter firmware in the repo is the correct firmware? And it works in kernel 2.6.28-15?

---

### Post by Ayuthia on 2009-09-27
> **chenxiaolong said:**
> I'll reinstall Ubuntu and try again. So the b43-fwcutter firmware in the repo is the correct firmware? And it works in kernel 2.6.28-15?

The firmware in 2.6.28-15 is the correct firmware.  You can always verify it in dmesg when you load the b43 module.  The thing that surprised me is that the linuxwireless.org site recommends the newer firmware for LP-PHY cards along with 2.6.31, but the current firmware appears to be working based on Sureshot324's post.

---

### Post by chenxiaolong on 2009-09-27
Alright thanks. I'm reinstalling Ubuntu right now.

By the way, that was the fastest response I ever got in any forum :)

---

### Post by stuben on 2009-09-30
Hi, I tried this guide on a Dell Inspiron 1545, with firmware broadcom-wl-4.150.10.5 and compat-wireless-2009-09-30, but no sign of eth1 or wlan0 devices. Here's the output of various commands:
lspci -nn:
```

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```
modprobe b43
dmesg:
```

b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
cfg80211: Using static regulatory domain info
cfg80211: Regulatory domain: US
        (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
        (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
        (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
cfg80211: Calling CRDA for country: US
b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
b43-phy0: Broadcom 4312 WLAN found (core revision 15)
b43: probe of ssb0:0 failed with error -17
Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]

```

---

### Post by Ayuthia on 2009-09-30
> **stuben said:**
> Hi, I tried this guide on a Dell Inspiron 1545, with firmware broadcom-wl-4.150.10.5 and compat-wireless-2009-09-30, but no sign of eth1 or wlan0 devices. Here's the output of various commands:
lspci -nn:
```

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```
modprobe b43
dmesg:
```

b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
cfg80211: Using static regulatory domain info
cfg80211: Regulatory domain: US
        (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
        (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
        (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
cfg80211: Calling CRDA for country: US
b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
b43-phy0: Broadcom 4312 WLAN found (core revision 15)
b43: probe of ssb0:0 failed with error -17
Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]

```

I don't have this card so I have no way to test this, but the linuxwireless guide recommends using 4.174.64.19 version instead of the one recommened in the original post.  I would make a backup of the current firmware:
```
sudo mv /lib/firmware/b43 /lib/firmware/b43-backup
```
then uninstall b43-fwcutter.

You will then need to follow the steps in the "You are using the b43 driver with an LP-PHY card (e.g. BCM4312)" section of this [guide]("http://linuxwireless.org/en/users/Drivers/b43").

If you don't have git installed, you will need to install git-core from Synaptic or from the Terminal:
```
sudo apt-get install git-core
```

As a caution, once you move the b43 folder in /lib/firmware, you will lose your wireless capabilities (most likely after you restart, but it might be sooner) if you are using the b43 module.  So you might want to switch back to the broadcom sta version until you get it working:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```

Hope that helps.

---

### Post by chenxiaolong on 2009-09-30
Thanks for the information, but the new 4.174.64.19 firmware requires at least the 2.6.31 kernel. So either compile the 2.6.31 kernel or install it from the Ubuntu Kernel  PPA([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)).

---

### Post by Ayuthia on 2009-09-30
I was not for sure about that.  The linuxwireless.org site says:
> Follow these instructions if you are using the b43 driver from linux-2.6.32 and newer or compat-wireless-2.6, or from any current GIT tree, and have a device with a low-power PHY. 

Following their and/or logic, it looks like if you use the compat-wireless-2.6 source, you can use the newer firmware.  

My thought is that the firmware should work with this kernel since you are making the kernel module update to be compatible with the newer firmware.  However, I have not looked at the insides to verify this so I can be completely wrong.

I looked at the openSUSE forum and Larry Finger never specifically states whether the newer firmware will work the Jaunty kernel.  It did look like he was saying that it should work with the current firmware though.

---

### Post by chenxiaolong on 2009-09-30
The compat-wireless package might compile, but the firmware will probably not load, according to the website. Take a look at this picture: [http://pictures.6368.co.cc/v/b43kernel.png.html?g2_imageViewsIndex=1](http://pictures.6368.co.cc/v/b43kernel.png.html?g2_imageViewsIndex=1)

---

### Post by Ayuthia on 2009-09-30
> **chenxiaolong said:**
> The compat-wireless package might compile, but the firmware will probably not load, according to the website. Take a look at this picture: [http://pictures.6368.co.cc/v/b43kernel.png.html?g2_imageViewsIndex=1](http://pictures.6368.co.cc/v/b43kernel.png.html?g2_imageViewsIndex=1)

Yes, but it still has the commas making it look like the newer compat-wireless packages will work with it:
> Linux-2.6.31 and newer, compat-wireless-2.6 package, current GIT trees - for LP-PHY cards 
Is reading to me that it will work with:
[LIST=1]
[*]Kernels 2.6.31 and newer
[*]compat-wireless-2.6 package
[*]current GIT trees
[/LIST]

Hey, wasn't that a snapshot in Windows????  Where's the Linux love????? :P

---

### Post by chenxiaolong on 2009-09-30
Well, this is the thread for the b43 driver with the 14e4:4315 and it's not working for me, so I'm using Windows right now. I really don't like Windows and would rather use Linux, but I'm stuck with Windows until I find a solution.

---

### Post by Ayuthia on 2009-09-30
> **chenxiaolong said:**
> Well, this is the thread for the b43 driver with the 14e4:4315 and it's not working for me, so I'm using Windows right now. I really don't like Windows and would rather use Linux, but I'm stuck with Windows until I find a solution.

From what I have read, it looks like you have a clean compile for the source.  Have you tried uninstalling b43-fwcutter and using the linuxwireless.org version with the newer firmware?

---

### Post by chenxiaolong on 2009-09-30
No I haven't, but I'll do it now. This is under Ubuntu 9.04 Jaunty, not under Ubuntu 9.10 Karmic, right?

---

### Post by Ayuthia on 2009-10-01
> **chenxiaolong said:**
> No I haven't, but I'll do it now. This is under Ubuntu 9.04 Jaunty, not under Ubuntu 9.10 Karmic, right?

Yes.

---

### Post by chenxiaolong on 2009-10-01
Sorry. I didn't have time to do it last night, I had too much homework. I'll definitely do it today because I have no hw :)

---

### Post by chenxiaolong on 2009-10-02
Well, I tried it and apparently, the new firmware does require kernel 2.6.31. It compiles fine in 2.6.28-15, but it doesn't load. Here's what dmesg shows:

```
chenxiaolong@d6657k1:~$ dmesg | tail
[  245.370035] b43-phy0: Controller RESET (DMA error) ...
[  245.596325] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  251.192861] b43-phy0: Controller restarted
[  251.193065] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  251.193073] b43-phy0: Controller RESET (DMA error) ...
[  251.420275] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  256.956956] b43-phy0: Controller restarted
[  256.958720] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  256.958729] b43-phy0: Controller RESET (DMA error) ...
[  257.184369] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
chenxiaolong@d6657k1:~$ 

```

---

### Post by Ayuthia on 2009-10-02
> **chenxiaolong said:**
> Well, I tried it and apparently, the new firmware does require kernel 2.6.31. It compiles fine in 2.6.28-15, but it doesn't load. Here's what dmesg shows:

```
chenxiaolong@d6657k1:~$ dmesg | tail
[  245.370035] b43-phy0: Controller RESET (DMA error) ...
[  245.596325] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  251.192861] b43-phy0: Controller restarted
[  251.193065] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  251.193073] b43-phy0: Controller RESET (DMA error) ...
[  251.420275] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  256.956956] b43-phy0: Controller restarted
[  256.958720] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  256.958729] b43-phy0: Controller RESET (DMA error) ...
[  257.184369] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
chenxiaolong@d6657k1:~$ 

```

So you are still stuck with neither firmware working, correct?  Are you still using the code from the 25th?  I am trying to figure out the difference between yours and Sureshot324.  He is using the Jaunty firmware which I thought you had problems with also.

If you are having problems with both, you might either post something back at the openSUSE forums or send something to the b43 mailing list to see if something is missing.  You will most likely need to post the dmesg messages for both firmware along with which version of b43-fwcutter you are using.

---

### Post by chenxiaolong on 2009-10-02
No, only the new firmware doesn't load. With the included firmware from the repository, it shows a list of networks, but it can't connect to any of them. Also, if I restart back into windows, the card is not recognized until I take the card out of the computer and touch one of the pins.

---

### Post by ghora8685 on 2009-10-04
I have a lenovo ideapad s10-2. After installing ubuntu karmic koala my wireless card Broadcom bcm4312 chip stopped working. It worked fine in jaunty.
so I installed b43-fwcutter as instructed by Metaljaz.
sudo apt-get install b43-fwcutter
It worked fine after that.

How come it worked in jaunty but not in karmic.:confused:

---

### Post by Ayuthia on 2009-10-04
> **chenxiaolong said:**
> No, only the new firmware doesn't load. With the included firmware from the repository, it shows a list of networks, but it can't connect to any of them. Also, if I restart back into windows, the card is not recognized until I take the card out of the computer and touch one of the pins.

I would report the issue with the included firmware with the b43 mailing list.

---

### Post by Ayuthia on 2009-10-04
> **ghora8685 said:**
> I have a lenovo ideapad s10-2. After installing ubuntu karmic koala my wireless card Broadcom bcm4312 chip stopped working. It worked fine in jaunty.
so I installed b43-fwcutter as instructed by Metaljaz.
sudo apt-get install b43-fwcutter
It worked fine after that.

How come it worked in jaunty but not in karmic.:confused:

You might want to check the version of b43-fwcutter that Karmic is using versus Jaunty.  You also might want to check the firmware version that is currently being used with the two.  

Those would be the main differences with using the b43 module.

---

### Post by chenxiaolong on 2009-10-04
I just installed Karmic yesterday because it wouldn't work no matter what in Jaunty. I'll test the b43 driver today.

---

### Post by quagga on 2009-10-04
Hmm, works fine* in Debian Lenny provided I install the 2.6.30 backports kernel version (lenny comes with 2.6.26 which is too old).

One thing I think may be missing in your directions is updating your initramfs after installing the new modules.  

So you'd want to make unload, and then modprobe b43 (to make sure the new module loads and works), then update-initramfs, and then reboot.  

Otherwise some old version of some of the modules were getting installed during the initramfs stage and when I'd modprobe the new b43, errors were thrown left and right.  

* For values of "fine" which include the occasional panic under heavy load.  Better than the wl driver behaved, but I'm still looking forward to my ath9k arriving.

---

### Post by mrcatzilla on 2009-10-10
Hey guys...

I've got a problem getting my
```
root@laptop:~# lspci |grep Bro
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```working with kismet.

Basically, the problem is that I cannot make it give me wlan0 interface (check with iwconfig) for kismet.

Any debug/suggestions/solutions?

What output should I get by typing modprobeb43 anyway?

Also, I seem to have the driver loaded twice:
```
root@laptop:~# dmesg | grep Broa
[   11.362151] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   11.473375] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]
[   11.911829] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[  257.589036] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]

```In reality, I only have a 4312, no 4315.

What makes this even more instersting, is that in lspci -vv, i still get that the driver loaded for the card is wl:
```
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 137c
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=2 PME-
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [d0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 1a-00-d2-ff-ff-73-83-f0
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl, ssb
```Thanks...

---

### Post by chenxiaolong on 2009-10-10
First of all, the BCM4312 revision 1 is the 4315. Could you post the output of iwconfig and ifconfig? From the messages, it seems like the driver is assigning the wireless card as eth1 rather than wlan0.

---

### Post by kevdog on 2009-10-10
You may have loaded b43 but the driver currently assigned to the card is wl:

   Kernel driver in use: wl
    Kernel modules: wl, ssb

---

### Post by chenxiaolong on 2009-10-10
Just a side note: ssb cannot load with wl (or wl has to be loaded first).

---

### Post by mrcatzilla on 2009-10-10
That's correct, I cannot get wlan0 to display despite anything I try.
```
root@laptop:/home/catzilla# iwconfig             
lo        no wireless extensions.                

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"XFV73"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:90:F2:CF:A5   
          Bit Rate=48 Mb/s   Tx-Power:32 dBm                                   
          Retry min limit:7   RTS thr:off   Fragment thr:off                   
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-45 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

root@laptop:/home/catzilla# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:80:42:63:57
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:1a:73:d2:f0:83
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fed2:f083/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2502 errors:0 dropped:0 overruns:0 frame:11551
          TX packets:2165 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2355250 (2.3 MB)  TX bytes:463645 (463.6 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:35008 (35.0 KB)  TX bytes:35008 (35.0 KB)
```

---

### Post by chenxiaolong on 2009-10-10
Alright. It's fine if the wl driver is assigning the wireless card eth1, but the module ssb cannot load with the wl module. All you have to do is:

Unload the wl and ssb module
```
sudo rmmod wl ssb
```

Blacklist the ssb module to prevent it from loading on boot
```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

And reload the wl module
```
sudo modprobe wl
```

And it should work.

---

### Post by mrcatzilla on 2009-10-10
Nope...
```
catzilla@laptop:~$ sudo rmmod wl ssb
[sudo] password for catzilla:       
ERROR: Module ssb does not exist in /proc/modules
catzilla@laptop:~$ echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf                                                                            
blacklist ssb                                                                   
catzilla@laptop:~$ sudo modprobe wl                                             
catzilla@laptop:~$ iwconfig                                                     
lo        no wireless extensions.                                               

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated
          Link Quality:5  Signal level:199  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

catzilla@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:80:42:63:57
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:1a:73:d2:f0:83
          inet6 addr: fe80::21a:73ff:fed2:f083/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:42648 (42.6 KB)  TX bytes:42648 (42.6 KB)
```

---

### Post by kevdog on 2009-10-10
It looks like eth1 is the wireless interface.  What does lshw -C network show?

---

### Post by mrcatzilla on 2009-10-10
```
catzilla@laptop:~$ sudo lshw -C network
[sudo] password for catzilla:          
  *-network                            
       description: Wireless interface 
       product: BCM4312 802.11b/g      
       vendor: Broadcom Corporation    
       physical id: 0                  
       bus info: pci@0000:02:00.0      
       logical name: eth1
       version: 01
       serial: 00:1a:73:d2:f0:83
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.148 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:80:42:63:57
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:3c:ed:2d:a9:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by chenxiaolong on 2009-10-10
Wait, I'm not completely sure if I understood your question. I assumed that you wanted to use wl instead of b43. Is that right?

---

### Post by mrcatzilla on 2009-10-10
Well, no, I wanted to do whatever it takes to make wlan0 appear in the network interfaces list, which (it seems to me) involves using the b43 driver through b43fwcutter.

---

### Post by chenxiaolong on 2009-10-11
The b43 driver with this wireless card is still a work in progress and it's not very stable. Wl assigns the wireless card eth1 and b43 assigns the wireless card wlan0. It doesn't matter what the driver assigns it; it will still work. If you want to use wl, you will have to blacklist b43

```
sudo rmmod b43
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

or if you want to use b43, you will have to blacklist wl

```
sudo rmmod wl
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```



Also, if you want to use the b43 driver, you will need kernel 2.6.31, as the new b43, which support LP-PHY cards (14e4:4315 and USB cards) require kernel 2.6.31 or higher.

---

### Post by FirstByté on 2009-10-12
Nice Thread and Lovely OS.

My pains started when I accepted to upgrade my **xserver-vido-intel-*blah blah blah***, the upgrade with seems to knock my beautiful Intel i965 card info outta the GDM startup database. After 2days of trying I fixed that today by **switching my kernel to 2.6.31** from **2.6.28**.

However that has screwed my Broadcom's wlan. After much hustle I fund my way here.

My problem is I can't build **b43-fwcutter** and 
> lsmod | grep "b43\|ssb\|wl" says I DON'T have any installed! GOOD GRIEVE :P :confused:

```
~$ sudo make install[B]
*[...]*[/B]

make -C /lib/modules/2.6.31-13-generic/build M=/home/ashon/web-files/apps/compat-wireless-2009-10-09 modules
make: *** /lib/modules/2.6.31-13-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I read [somewhere]("http://swiss.ubuntuforums.org/showpost.php?p=7973978&postcount=2") that b43 might have been deprecated. How in the world do I get to fix this WLan issue??? Right now I had to remove the LAN cable from the router-- others are out for now.

I've tried installing the 2.6.31-13 generic header that my system is using now but it's not in the repo yet or somthing like that.

> ~$ uname -a
Linux P34CE 2.6.31-13-generic #44-Ubuntu SMP Sat Oct 10 15:27:55 UTC 2009 i686 GNU/Linux


> $ lspci -nn | grep -i network
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

> ~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.




I've spent 48hours working on this bug.:mad: I asked myself why I upgraded the Intel graphics drivers in the first case!


If any can help, it's appreciated, I need to get back to work ASAP, PLEASE!

---

### Post by FirstByté on 2009-10-12
I forgot to add that the reason I am not able to install fwcutter from the repo is because it requests for my 9.04 Jaunty LiveCD which I don't have since I only upgraded from 8.10 to 9.04 :(

I might try building the fwcutter if it it will from the 8.10 LiveCD. 

BTW: I checked the [LinuxWireless site]("http://linuxwireless.org/download/compat-wireless-2.6/") I didn't see the Sept 25 that someone referenced earlier that it doesn't require 2.6.31 or so.

---

### Post by tormod on 2009-10-12
> **FirstByté said:**
> 
```
~$ sudo make install[B]
*[...]*[/B]
make -C /lib/modules/2.6.31-13-generic/build M=/home/ashon/web-files/apps/compat-wireless-2009-10-09 modules
make: *** /lib/modules/2.6.31-13-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

You have to install the linux-headers package for this kernel version.
> 
I've spent 48hours working on this bug.:mad: I asked myself why I upgraded the Intel graphics drivers in the first case!

Yes, why don't you just revert to the last working driver you had?

---

### Post by chenxiaolong on 2009-10-12
I didn't know that there was kernel 2.6.31 in the repo :D cool. Anyway, for the CD issue, just click System>Administration>Software Sources and disable the CD repo.

---

### Post by mrcatzilla on 2009-10-13
Reinstall the system.
Got the latest kernel, etc.
Getting this:
```
[  149.502662] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  149.709983] phy0: Selected rate control algorithm 'minstrel'
[  149.711153] Registered led device: b43-phy0::tx
[  149.711183] Registered led device: b43-phy0::rx
[  149.711212] Registered led device: b43-phy0::radio
[  149.711294] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]
[  149.860393] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[  149.922708] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[  149.945016] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[  150.100706] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  163.941330] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  164.395381] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  164.395400] b43-phy0: Controller RESET (DMA error) ...
[  164.750317] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  178.633784] b43-phy0: Controller restarted
[  178.636162] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  178.636180] b43-phy0: Controller RESET (DMA error) ...
[  179.018901] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
```Help please =(((((((((((

Endless cycle which doesn't allow me to use the card at all, although now I do have wlan0 in iwconfig:
```
root@laptop:/home/catzilla# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

---

### Post by chenxiaolong on 2009-10-13
Do you have the Dell 1397 wireless card? With the Dell card (which I have), if I use b43, reboot into Windows, and reboot back into Ubuntu, it gives that error. The only way I could fix it is by taking the card out of the computer and touching the pins and putting it back in.

---

### Post by mrcatzilla on 2009-10-13
> **chenxiaolong said:**
> Do you have the Dell 1397 wireless card? With the Dell card (which I have), if I use b43, reboot into Windows, and reboot back into Ubuntu, it gives that error. The only way I could fix it is by taking the card out of the computer and touching the pins and putting it back in.

I am not sure which card I have - I bought it on eBay to replace my Intel 4965AGN (which is not very well supported). Can you take a [look]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=280396653522&ssPageName=STRK:MEWNX:IT") and tell me if it is? 
Anyway, this card works fine in both Windows 7 and Mac OS X 10.5.8, installed on my Sony VAIO VGN-CR190.  Also, my guess is that by touching the pins on the card, you are resetting some internal RAM on it. 
I have absolutely no idea why this has to happen though. Unfortunately, to take out my card, I have to unscrew 4 screws and take out the keyboard - not too convinient.

---

### Post by FirstByté on 2009-10-13
> **tormod said:**
> You have to install the linux-headers package for this kernel version.

I've tried a lot of stuff before I came here to post.

> $ uname -ar
Linux P34CE 2.6.31-13-generic #45-Ubuntu SMP Tue Oct 13 02:08:03 UTC 2009 i686 GNU/Linux


> ~$ sudo apt-get install linux-headers-2.6.31-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.31-13-generic


> ~$ sudo apt-get install linux-headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.30-10 2.6.30-10.12
  linux-headers-2.6.30-10-generic 2.6.30-10.12
  linux-headers-2.6.30-10-generic-pae 2.6.30-10.12
  linux-headers-2.6.28-15-server 2.6.28-15.52
  linux-headers-2.6.28-15-generic 2.6.28-15.52
  linux-headers-2.6.28-15 2.6.28-15.52
  linux-headers-2.6.28-14-server 2.6.28-14.47
  linux-headers-2.6.28-14-generic 2.6.28-14.47
  linux-headers-2.6.28-14 2.6.28-14.47
  linux-headers-2.6.28-13-server 2.6.28-13.45
  linux-headers-2.6.28-13-generic 2.6.28-13.45
  linux-headers-2.6.28-13 2.6.28-13.45
  linux-headers-2.6.28-3-rt 2.6.28-3.12
  linux-ports-headers-2.6.28-6 2.6.28-6.20
  linux-headers-2.6.28-6-386 2.6.28-6.20
  linux-headers-2.6.28-11-server 2.6.28-11.42
  linux-headers-2.6.28-11-generic 2.6.28-11.42
  linux-headers-2.6.28-11 2.6.28-11.42
You should explicitly select one to install.
E: Package linux-headers has no installation candidate


> $ apt-cache search linux-headers-$(`ls /lib/modules`)
bash: 2.6.27-11-generic: command not found
linux-headers-2.6.28-11 - Header files related to Linux kernel version 2.6.28
linux-headers-2.6.28-11-generic - Linux kernel headers for version 2.6.28 on x86/x86_64
linux-headers-2.6.28-11-server - Linux kernel headers for version 2.6.28 on x86/x86_64
linux-headers-2.6.28-6-386 - Linux kernel headers for version 2.6.28 on i386
linux-headers-386 - Linux kernel headers on 386
linux-headers-lbm-2.6.28-11-generic - Header files related to linux-backports-modules version 2.6.28
linux-headers-lbm-2.6.28-11-server - Header files related to linux-backports-modules version 2.6.28
linux-ports-headers-2.6.28-6 - Header files related to Linux kernel version 2.6.28
linux-headers-2.6.28-3-rt - Linux kernel headers for version 2.6.28 on Ingo Molnar's full real time preemption patch (2.6.28-rt)
linux-headers-rt - Rt Linux kernel headers
linux-rt-headers-2.6.28-3 - Header files related to Linux kernel version 2.6.28
linux-headers-2.6.28-13 - Header files related to Linux kernel version 2.6.28
linux-headers-2.6.28-13-generic - Linux kernel headers for version 2.6.28 on x86/x86_64
linux-headers-2.6.28-13-server - Linux kernel headers for version 2.6.28 on x86/x86_64
linux-headers-2.6.28-14 - Header files related to Linux kernel version 2.6.28
linux-headers-2.6.28-14-generic - Linux kernel headers for version 2.6.28 on x86/x86_64
linux-headers-2.6.28-14-server - Linux kernel headers for version 2.6.28 on x86/x86_64
linux-headers-2.6.28-15 - Header files related to Linux kernel version 2.6.28
linux-headers-2.6.28-15-generic - Linux kernel headers for version 2.6.28 on x86/x86_64
linux-headers-2.6.28-15-server - Linux kernel headers for version 2.6.28 on x86/x86_64
linux-headers-generic - Generic Linux kernel headers
linux-headers-lbm-2.6.28-13-generic - Header files related to linux-backports-modules version 2.6.28
linux-headers-lbm-2.6.28-13-server - Header files related to linux-backports-modules version 2.6.28
linux-headers-lbm-2.6.28-14-generic - Header files related to linux-backports-modules version 2.6.28
linux-headers-lbm-2.6.28-14-server - Header files related to linux-backports-modules version 2.6.28
linux-headers-lbm-2.6.28-15-generic - Header files related to linux-backports-modules version 2.6.28
linux-headers-lbm-2.6.28-15-server - Header files related to linux-backports-modules version 2.6.28
linux-headers-server - Linux kernel headers on Server Equipment.
linux-headers-virtual - Linux kernel headers for virtual machines
linux-libc-dev - Linux Kernel Headers for development
linux-headers-2.6.30-10-generic-pae - Linux kernel headers for version 2.6.30 on x86
linux-headers-2.6.30-10-generic - Linux kernel headers for version 2.6.30 on x86/x86_64
linux-headers-2.6.30-10 - Header files related to Linux kernel version 2.6.30


> $ sudo apt-get install linux-headers-2.6.30-10-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.30-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
I have kernel 2.6.31-13 installed as you can see but I CAN'T install the headers... Is there something I'm doing wrong?

> **tormod said:**
> 
Yes, why don't you just revert to the last working driver you had?

I wish I knew how to do that... I tried compiling a couple form the Intel site but no good. I get stuck compiling them.
> xf86-video-intel-2.9.0
xf86-video-intel-2.6.3


[B]
Pls how can I revert to the earlier on just before this 'xserver-xorg-video-intel-2.9.0' update that I have installed? And which is it?[/B] Sorry, I know I should keep track of versions I choose to update. I guess I've learnt my lessons now.

Someone please help out

I wonder why I'm the only one caught in this net :(

> **chenxiaolong said:**
> I didn't know that there was kernel 2.6.31 in the repo :D cool.** [...]**

IMO: I'ld rather not rush to a new kernel till I'm sure most issues are fixed :P

---

### Post by chenxiaolong on 2009-10-14
> **mrcatzilla said:**
> I am not sure which card I have - I bought it on eBay to replace my Intel 4965AGN (which is not very well supported). Can you take a [look]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=280396653522&ssPageName=STRK:MEWNX:IT") and tell me if it is? 
Anyway, this card works fine in both Windows 7 and Mac OS X 10.5.8, installed on my Sony VAIO VGN-CR190.  Also, my guess is that by touching the pins on the card, you are resetting some internal RAM on it. 
I have absolutely no idea why this has to happen though. Unfortunately, to take out my card, I have to unscrew 4 screws and take out the keyboard - not too convinient.

What does the device manager in Windows 7 call your card? The only way I could get it to work again is to take it out and touch the pins. I have no idea whether it resets the internal ram or not. 

Also, what driver are you using for Mac OS X 10.5.8? That's the only thing not working in my installation. :)

---

### Post by chenxiaolong on 2009-10-14
FirstByté, since the kernel is *-generic, it's definitely coming from the Ubuntu repo. I'm pretty sure that it was installed from the Ubuntu proposed repo, which in my previous experiences, doesn't have the headers. As for the graphics, I have no idea. My Intel card works out of the box with 3D acceleration no matter what kernel I use.

---

### Post by mrcatzilla on 2009-10-14
> **chenxiaolong said:**
> What does the device manager in Windows 7 call your card? The only way I could get it to work again is to take it out and touch the pins. I have no idea whether it resets the internal ram or not. 

Also, what driver are you using for Mac OS X 10.5.8? That's the only thing not working in my installation. :)

You can find the driver for 10.5.8 on [insanelymac.com]("http://www.insanelymac.com/forum/index.php?showtopic=51725"). I'll check what Win7 says and edit this post later.

Edit:
Win7 says it's a Broadcom 802.11g Network Adapter

---

### Post by tormod on 2009-10-14
> **FirstByté said:**
> 
I have kernel 2.6.31-13 installed as you can see but I CAN'T install the headers... Is there something I'm doing wrong?

You can find all kernel packages here: [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)
Click the Changelog link to get all intermediate versions.

And trying the latest Karmic should do no harm, they get better and better :) You will keep the old Jaunty kernel anyway.

For reverting the -intel driver, use the ppa-purge tool which you also will find explained on the PPA page.

---

### Post by chenxiaolong on 2009-10-14
It can't even find the package in the repo which is why it's not installing. Just to be sure "sudo apt-get install linux-headers-`uname -r`"doesn't work, right?

---

### Post by FirstByté on 2009-10-15
> **tormod said:**
> You can find all kernel packages here: [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)
Click the Changelog link to get all intermediate versions.

And trying the latest Karmic should do no harm, they get better and better :) You will keep the old Jaunty kernel anyway.

For reverting the -intel driver, use the ppa-purge tool which you also will find explained on the PPA page.

Tormod,
Thanks for your support and help. I'll give the 'ppa-purge' tool a shot. I'm not scared to move up to Karmic. While I found my move from Hardy 8.04 to Intrepid 8.10 a blissful experience, a lot of things that worked OTB for me in Intrepid 8.10 just utterly broke in many areas such as sound jack, graphics (normal|extra compiz effect, 'cause I use Intel's forbidden i965 GPU), just to name a few, during my upgrade to Jaunty, most got resolved much later though.

Above all, I love Ubuntu guys 'cause they work painstakingly to see Ubuntu become the best distro, which I salute them for

> **chenxiaolong said:**
> It can't even find the package in the repo which is why it's not installing. Just to be sure "sudo apt-get install linux-headers-`uname -r`"doesn't work, right?

Regarding my kernel 2.6.31-* issues, I suspected that my '**apt-cache**' dude reports up to 2.6.30-*, so I decided to get it doing
```
sudo apt-get install linux-image-2.6.30-10-generic
```
since for some reasons 2.6.30-* seems to have been removed from the 
> [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/)
list and 2.6.31-13 was giving me headache compiling '**wl**' and '**b43**'.

I was able to compile them smoothly with the kernel 2.6.30-10-generic hearders. Following this _[>> link <<]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new")_ Then I :
```
~$sudo /etc/init.d/networking restart

```

For some reasons, I still get
> $ sudo modprobe -r b43 ssb wl
FATAL: Module wl not found.


So I try **b43** again.
```
~$sudo modprobe b43
```

and my dmesg:

```
~$ dmesg[B]
[...]
[/B]

[  790.785458] cfg80211: Calling CRDA to update world regulatory domain
[  790.903564] cfg80211: World regulatory domain updated:
[  790.903570] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  790.903575] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  790.903580] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  790.903584] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  790.903589] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  790.903593] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  790.925456] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  790.925476] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[  790.992315] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[  791.033018] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  791.100837] b43: probe of ssb0:0 failed with error -17
[  791.100860] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]
[ 1105.881237] b43-pci-bridge 0000:0b:00.0: PCI INT A disabled
[ 1500.796095] CE: hpet increasing min_delta_ns to 22500 nsec
[35735.965224] cfg80211: Calling CRDA to update world regulatory domain
[35736.001190] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[35736.001214] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[35736.021083] cfg80211: World regulatory domain updated:
[35736.021089] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[35736.021095] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[35736.021100] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[35736.021104] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[35736.021108] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[35736.021113] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[35736.069632] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[35736.080645] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[35736.145459] b43: probe of ssb0:0 failed with error -17
[35736.145484] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]
```

Thanks great minds for your support! :popcorn:

---

### Post by tormod on 2009-10-15
> **FirstByté said:**
> Regarding my kernel 2.6.31-* issues, I suspected that my '**apt-cache**' dude reports up to 2.6.30-*, so I decided to get it doing
```
sudo apt-get install linux-image-2.6.30-10-generic
```
since for some reasons 2.6.30-* seems to have been removed from the 

list and 2.6.31-13 was giving me headache compiling '**wl**' and '**b43**'.

apt-get and apt-cache will only look in the repos which you have enabled in Software Sources (sources.list). You probably have picked up the 2.6.30 packages from the xorg-edgers Jaunty repo, which I do not recommend. If you go through the link I gave earlier, you'll find the .debs for linux-image-* and linux-headers-* which you can install using dpkg -i.

Another way is to add the karmic repo, **only** install the kernel packages, and then remove the karmic repo.

---

### Post by FirstByté on 2009-10-15
I consider my WLAN issue **[SOLVED]!!!**

> **tormod said:**
> apt-get and apt-cache will only look in the repos which you have enabled in Software Sources (sources.list). You probably have picked up the 2.6.30 packages from the xorg-edgers Jaunty repo, which I do not recommend. If you go through the link I gave earlier, you'll find the .debs for linux-image-* and linux-headers-* which you can install using dpkg -i.

Another way is to add the karmic repo, **only** install the kernel packages, and then remove the karmic repo.

Let me save you the troubleshooting pains. _I'm posting this so it might help somebody_ going through the same horror :D

I tried the '**ppa-purge**' as you suggested while on kernel 2.6.30-10-generic and it seemed to have purged the new '**xserver-xorg-video-intel**'. I said this because, on my kernel 2.6.28-15 that had the wireless working but had graphics issues (low res of 800x600), the graphics was back to normal when I tried it.

Right now, I guess I might just make **kernel 2.6.28-15** my main/stable kernel for now till Koala's release.

**This info tells me something**. Do you think it can help the forum?

Broadcom's **wl** didn't seem to work in kernel 2.6.3X-XX (on my Wifi card), but my WiFi card tends to work with *only* '**wl**' and not **b43**. *[or possibly I didn't compile it properly, I'll give another try when I'm free though]*

```
$ lspci -nn | grep Broad
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0b:00.0 Network controller [0280]: Broadcom Corporation **BCM4312** 802.11b/g [**14e4:4315**] (rev 01)

```

on **kernel 2.6.28-15** when I 
> ~$ sudo modprobe -r b43 ssb wl
~$ sudo modprobe wl


I get this
```
~$ lsmod | grep "b43\|ssb\|wl"
wl                   1281364  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:230  Noise level:168
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

```

However when I switched to **kernel 2.6.30-10** and ..
> ~$ sudo modprobe -r b43 ssb wl
~$ sudo modprobe wl


it returned
> FATAL: Module wl not found.
 still.

Then I tried
> ~$ sudo modprobe b43
~$ dmesg

result:
```
[ 5597.629154] cfg80211: Calling CRDA to update world regulatory domain
[ 5597.695377] cfg80211: World regulatory domain updated:
[ 5597.695383] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5597.695388] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5597.695393] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5597.695398] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5597.695402] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5597.695406] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5597.795051] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 5597.795070] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[ 5597.860225] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[ 5597.902535] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[ 5597.968415] b43: probe of ssb0:0 failed with error -17
[ 5597.968438] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]

```
**b43 still fails** though the modules seems to have been loaded.
but no '**wlan0**' or '**eth1**' *(only eth0, though I have LAN too, so it should have shown eth0 and eth1 or somethng)*

> 
~$ lsmod | grep "b43\|ssb\|wl"
b43                   167252  0 
ssb                    46740  1 b43
pcmcia                 37292  2 b43,ssb
mac80211              214328  1 b43
cfg80211              128872  2 b43,mac80211
pcmcia_core            35712  3 b43,ssb,pcmcia
led_class               4048  2 b43,sdhci

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



So I guess b43 doesn't really support my WiFi card. I'll still keep this recent kernels for personal troubleshooting but would work primarily on the more *stable* **kernel 2.6.28-15** for now. I know I'll be missing out a bunch, but you can't eat your cake and have :popcorn:

---

### Post by FirstByté on 2009-10-15
> **chenxiaolong said:**
> It can't even find the package in the repo which is why it's not installing. Just to be sure "sudo apt-get install linux-headers-`uname -r`"doesn't work, right?

You are right, since the kernel 2.6.31-XX on which I tried to install the headers for are not in the repo you can't get it using

> ~$ sudo apt-get install linux-headers-$(uname -r)

the best you can do is downloading it from the [Ubuntu Kernels .deb list]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux/") and using a terminal shell 
```
sudo dpkg -i linux-***whatever.deb***
``` to install it just as you would the images as well.


Thanks so much for this thread, and **Happy belated Birthday!** We share the same month my the way. 1st Sept

---

### Post by ld.4lpha on 2009-10-15
Very well done!  Works like a charm.

...except one thing....

When I switch to monitor mode, I can't connect to any network that is using encryption.  In managed mode, all is perfect though.

Thoughts anybody?

Muchas gracias.
LD

---

### Post by kngharv on 2009-10-17
help

during the installation of b43-fwcutter, i pressed YES to extract the firmware.

how to reverse that?  I did that before I read this howto.  I went to /lib/firmware and remove b43 directory.  would that do it?

now, my wireless driver is crippled, I got this message after being connected to an access point for about 30 seconds:


b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000400, 0x00000000, 0x00000000
b43-phy0: Controller RESET (DMA error) ...
b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
b43-phy0: Controller restarted


Help, please.

---

### Post by ld.4lpha on 2009-10-18
You could try:

```
sudo apt-get remove b43-fwcutter
```

and then reinstall it with 

```
sudo apt-get install b43-fwcutter
```

Not sure if this will work or not, but it'd be worth a shot...

Good luck.

LD

---

### Post by h3lladvocate on 2009-10-19
> help  during the installation of b43-fwcutter, i pressed YES to extract the firmware.  how to reverse that? I did that before I read this howto. I went to /lib/firmware and remove b43 directory. would that do it?  now, my wireless driver is crippled, I got this message after being connected to an access point for about 30 seconds:   b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000400, 0x00000000, 0x00000000 b43-phy0: Controller RESET (DMA error) ... b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10) b43-phy0: Controller restarted   Help, please.   I had a simular problem, only mine didn't ask for the update, just updated. Also, I'm having a different problem. When I run  modprobe b43, i get: FATAL: Error inserting b43 (/lib/modules/2.6.29.4/updates/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)  and gmesg give me: b43: Unknown symbol ssb_pmu_set_ldo_paref b43: Unknown symbol ssb_pmu_set_ldo_voltage b43: Unknown symbol ssb_bus_pcmciabus_register  Whats going on? I'm really new to linux and just want to get wireless =( Can someone help me out here?

---

### Post by ld.4lpha on 2009-10-20
> **h3lladvocate said:**
> Whats going on? I'm really new to linux and just want to get wireless =( Can someone help me out here?

If your only objective is to have working WiFi, you probably should just activate the STA module in *Administration > Hardware Drivers.  *(Assuming you are on Jaunty.  I don't think STA is packaged with prior versions.)

This might be the easiest solution for you.

---

### Post by h3lladvocate on 2009-10-20
Unfortuently it wont be that easy, im running on backtrack which is based on debian. Appearently the ssd that comes with backtrack is auto-loaded and start-up and there doesn't seem to be a way to tell it to use the new one created by compat-wireless, unless one of you know some secret method. *sadface*

---

### Post by ld.4lpha on 2009-10-20
Ahh...yep.  I had that same problem with BT.

Now I just run it in a VM with Ubuntu host.  I get the ease of Ubuntu with the tools of BT - best of both worlds.

Let me know if you figure it out.

LD

---

### Post by mrcatzilla on 2009-10-20
secret method:

sudo rmmod ssb
sudo modprobe wl

done =)

And for my problem:
I've had enough of this.
[quote=http://linuxwireless.org/en/users/Drivers/b43]14e4:4312 not supported - ID is duplicated BCM4312 802.11b/g b43 [/quote]
It appears my particular BCM4312 is not supported after all. Buying a 4311.

---

### Post by h3lladvocate on 2009-10-20
> **mrcatzilla said:**
> secret method:

sudo rmmod ssb
sudo modprobe wl

done =)

And for my problem:
I've had enough of this.

It appears my particular BCM4312 is not supported after all. Buying a 4311.

Thats the problem thought, its embeded withing the image file, not a module, so i cant rrmod it. Even so, the whole point of this is to avoid using the wl driver because that essentially isnt a driver at all. Ugh, I'm so frustrated with this crap...

---

### Post by mrcatzilla on 2009-10-21
I don't know what you're talking about, the proprietary driver works just fine work normal wi-fi usage (including WPA-WPA2)
No wlan0, so no kismet though. That's my initial goal with the card, and that's why I ended up buying another one (should arrive in a week or two, ordered, unfortunately, from Hong Kong).

---

### Post by ninja togo on 2009-10-24
I need help (Linux Noob) 
I realized that my wireless drivers stop working... but too late and would like to undo my mistake of doing the tutorial listed here (I find nothing wrong with it, but I don't know what I'm doing) and want to go back to before I did the driver installation with just the regular drivers and all.

Will someone please help me reverse the process

---

### Post by chenxiaolong on 2009-10-24
To revert back to the wl driver:

1. Unload and blacklist b43 driver.

```
sudo rmmod b43
echo "blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
```

2. a. Remove the firmware package (if you installed b43)

```
sudo apt-get remove b43-fwcutter
```

OR b. Remove the firmware files 

```
sudo mv /lib/firmware/b43 /lib/firmware/b43.backup
sudo mv /lib/firmware/b43legacy /lib/firmware/b43legacy.backup
```

3. Remove the "blacklist wl" line from /etc/modprobe.d/blacklist.conf

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

4. Reboot

Hope this works.

---

### Post by ninja togo on 2009-10-24
Hey I'm so sorry if I caused any trouble, just wanted to try something new.

---

### Post by chenxiaolong on 2009-10-24
No trouble. I'm happy to do anything that helps.

---

### Post by sapling on 2009-10-27
Worked for me with the following...

So I followed the main steps in the starting section using my 14e4:4315 that comes inside my hp mini 1100...
I had a fresh install and a fresh update using the ubuntu netbook remix.
My kernel version is 2.6.28-16-generic.
So here is what worked for me...

Code:
sudo apt-get install gcc g++ gawk make automake flex bison binutils cmake autoconf

Downloaded the compat drivers below...

[http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)
You can't use wget for this because they have a hotlink prevention system. So just download the
Quote:
compat-wireless-2.6.tar.bz2
file from that website and saved it to /usr/src

Then open the terminal and run this command to extract the archive

Code:
tar xjf compat-wireless-2.6.tar.bz2

In order for the package to compile, you need to install the kernel headers, if not already installed. Run this in the terminal ( Already had mine from netbook remix) But after the kernel update from -11 I went ahead to avoid confusion and did 

Code:
sudo apt-get autoremove

Code:
sudo apt-get install linux-headers-$(uname -r)

Then change to the compat-wireless directory:

Code:
cd compat-wireless

Then compile the source files:

Code:
sudo make

Then install the files:

Code:
sudo make install

Then unload the drivers

Code:
sudo make unload

Then install b43-fwcutter:
VERY IMPORTANT!!: Do NOT choose yes when it asks if you want to automatically fetch the firmware.

Code:
sudo apt-get install b43-fwcutter

Download the Broadcom firmware files

Code:
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Extract the archive

Code:
tar xjf broadcom-wl-4.150.10.5.tar.bz2

Change to the driver directory

Code:
cd broadcom-wl-4.150.10.5/driver

Install the firmware

Code:
b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

The firmware install Directory I used was /lib/firmware/

Then blacklist the proprietary driver

Code:
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist.conf

after this all I did a reboot

I wanted this to work so i could use aircrack-ng so I installed this next to verify the driver worked correctly with monitoring sooo...

Code:
sudo apt-get install aircrack-ng

Code:
sudo airmon-ng wlan0

wlan0 now becomes mon0 for me at least

Code: 
airodump-ng mon0

My card is seeing and able to capture traffic :)

---

### Post by kevdog on 2009-10-27
sapling 

Great post

---

### Post by korvirlol on 2009-10-30
Hi, ive got a quick (and probably stupid) question about this whole process.

I read that karmic just had come out, so i thought i'd upgrade, but found out that my wireless stopped working. Ive been through this entire thread looking for a solution, but im not sure that i need to install any drivers, or firmware - here is why.

In karmic, network manager says that my wireless is disabled (don't know how to enable, but ive tried a bunch of things), pretty sure it has something to do with loading wrong drivers. The weird part is dmesg has this little gem:

```
eth1: broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
```

but lspci shows:

```
Network controller: Broadcom corp BCM4312 802.11b/g
```

anyways, i dont know if this is even relevant, just seemed weird.

During boot, if i boot into the previous kernel version (2.6.28-16-generic) the wireless works, but for some reason the mouse on my laptop doesnt, so i cant really use this.

Is there a way i can just use the drivers that work in the older kernel version? 

Any insight is greatly appreciated!!

---

### Post by stats on 2009-10-30
For those of you who use karmic, compat-wireless need not be compiled. 
```
sudo apt-get install linux-backports-modules-karmic linux-backports-modules-wireless-karmic-generic b43-fwcutter 
```
is enough. 
Then do 
```
sudo modprobe -r wl
sudo modprobe b43
```
and you're done. If it works and you want to make the change permanent :
First, blacklist the wl module
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then
```
gksudo gedit /etc/modules
```
and add 
```
b43
```
to the end of the file

---

### Post by rusty73 on 2009-10-31
> **stats said:**
> For those of you who use karmic, compat-wireless need not be compiled. 
```
sudo apt-get install linux-backports-modules-karmic linux-backports-modules-wireless-karmic-generic b43-fwcutter 
```is enough. 
Then do 
```
sudo modprobe -r wl
sudo modprobe b43
```and you're done. If it works and you want to make the change permanent :
First, blacklist the wl module
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist.conf
```Then
```
gksudo gedit /etc/modules
```and add 
```
b43
```to the end of the file

Thank u a lot. Works!!! and my computer doesn't became unstable!!! thk :popcorn:

---

### Post by rusty73 on 2009-10-31
Sorry but my answer isn't correct. After an hour my computer freeze and after reboot, the b43 driver load but it throw this error:
"[  699.977734] b43-phy0: Controller RESET (DMA error) ...
[  700.196356] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  705.769367] b43-phy0: Controller restarted
[  705.780442] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  705.780469] b43-phy0: Controller RESET (DMA error) ...
[  706.000430] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  711.545398] b43-phy0: 
[  711.545409] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  711.545431] b43-phy0: Controller RESET (DMA error) ...
"

and i can't load wl driver :(

---

### Post by JBAlaska on 2009-10-31
Nice Howto chenxiaolong, but you might want to add build-essential to it, before the make part for those that don't know already:
```
sudo apt-get install build-essential
```

---

### Post by rusty73 on 2009-10-31
> **rusty73 said:**
> Sorry but my answer isn't correct. After an hour my computer freeze and after reboot, the b43 driver load but it throw this error:
"[  699.977734] b43-phy0: Controller RESET (DMA error) ...
[  700.196356] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  705.769367] b43-phy0: Controller restarted
[  705.780442] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  705.780469] b43-phy0: Controller RESET (DMA error) ...
[  706.000430] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  711.545398] b43-phy0: 
[  711.545409] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  711.545431] b43-phy0: Controller RESET (DMA error) ...
"

and i can't load wl driver :(

I removed all backports package with synaptic and I inserted b43 module into blacklist file and after reboot (because my system freezed again) the system load b43 module and it seem that work well :S:S. That's very very strange.

My system is Dell mini 9 with the damned wireless card.

---

### Post by kngharv on 2009-11-01
> **kngharv said:**
> help

during the installation of b43-fwcutter, i pressed YES to extract the firmware.

how to reverse that?  I did that before I read this howto.  I went to /lib/firmware and remove b43 directory.  would that do it?

now, my wireless driver is crippled, I got this message after being connected to an access point for about 30 seconds:


b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000400, 0x00000000, 0x00000000
b43-phy0: Controller RESET (DMA error) ...
b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
b43-phy0: Controller restarted


Help, please.


Dear all:

I think I found the problem.

According o the B43 driver site, there is a list of chipsets supported, my chipset is "in progress."

So, I apologize for being a dumb *** and wasted a these precious cycle from you guys.

I can't wait to get monitor mode on this chipset works, though.  :)


Harv

---

### Post by danteuk on 2009-11-03
I'm also suffering now I've upgraded from 9.04 to 9.10 ( I actually did it as a clean install of / )

I've tried everything in this thread so far but nothing helps.

Now my wifi doesn't work, when I do modprobe b43 I get dmesg output of:
```

[ 4253.680567] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[ 4253.880930] phy0: Selected rate control algorithm 'minstrel'
[ 4253.882907] Registered led device: b43-phy0::tx
[ 4253.882957] Registered led device: b43-phy0::rx
[ 4253.883002] Registered led device: b43-phy0::radio
[ 4253.883135] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]
[ 4254.042897] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[ 4254.050930] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[ 4254.060369] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[ 4254.210360] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 4268.042984] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 4268.042991] b43-phy0: Controller RESET (DMA error) ...
[ 4268.392879] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
...
[ 4808.924078] b43-phy0: Controller restarted
[ 4808.942918] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 4808.942937] b43-phy0: Controller RESET (DMA error) ...
[ 4809.280448] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```
Those last 4 lines repeat every couple of minute until I get fed up and disable it!

iwconfig reports:
```

$ iwconfig
wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f4000000-f4003fff

```

Anyone any ideas what's broken with this driver since 9.04 ?

---

### Post by chenxiaolong on 2009-11-03
For now, you might want to just use the Broadcom STA (wl) driver, since it's stable and works well in Ubuntu 9.10. I'm waiting until the b43 developers fix what is wrong.

---

### Post by mrcatzilla on 2009-11-03
You may congratulate me, I finally received that BCM4311 card (tnx ebay), and it works fine, including airmon-ng and kismet!
Going to sell the dreaded BCM4312 in a few days. I advise you guys do the same =)

Oh and I installed Debian in place of Ubuntu. Time to move up, you know?

---

### Post by chenxiaolong on 2009-11-03
Too bad for me. Dell uses half size mini-pci express cards.

---

### Post by danteuk on 2009-11-04
Mines a Dell laptop too ( Vostro 1710 ).

I'm using the STA driver now I think. Tried so many things over the last few days!

hybrid-portsrc-x86_64-v5.10.91.9.3.tar.gz
from here:
[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

I had problems with the 80211 libraries and had to do this:
```

export KERN=`uname -r`
rmmod /lib/modules/$KERN/kernel/net/wireless/wl.ko
rmmod /lib/modules/$KERN/kernel/net/wireless/lib80211.ko
rmmod /lib/modules/$KERN/kernel/net/wireless/lib80211_crypt_wep.ko
rmmod /lib/modules/$KERN/kernel/net/wireless/lib80211_crypt_tkip.ko
rmmod /lib/modules/$KERN/kernel/net/wireless/lib80211_crypt_ccmp.ko

cp wl.ko /lib/modules/$KERN/kernel/net/wireless/
insmod /lib/modules/$KERN/kernel/net/wireless/lib80211.ko
insmod /lib/modules/$KERN/kernel/net/wireless/lib80211_crypt_wep.ko
insmod /lib/modules/$KERN/kernel/net/wireless/lib80211_crypt_tkip.ko
insmod /lib/modules/$KERN/kernel/net/wireless/lib80211_crypt_ccmp.ko
insmod /lib/modules/$KERN/kernel/net/wireless/wl.ko
modprobe wl

```

Then I had a new problem, I have two wifi networks at home(long story) one is using WEP ( must change that soon ) and the other is WPA(802.11g).
I used to use the WPA network all the time from 9.04 but now I could only
connect to the WEP network. If I try the WPA it asks for the password but then just waits a while and silently fails, then asks again for the password. No errors appear in dmesg.
I changed my wifi router from WPA to WPA2 and now it also works. 
Now I'm happy :D

Thanks guys for all the suggestions here.

---

### Post by Alacrity on 2009-11-05
To all,

I have the same wireless chip as this thread [Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)] and found that it worked out of the box with Xubuntu 9.10 with both managed mode and full aircrack-ng monitor mode & aireplay-ng commands.  Only an installation of aircrack-ng was needed.

Not sure why...but it did not work out of the box with Ubuntu 9.10.  I used a remastersys of Xubuntu 9.10 on a usb stick (remastersys with the 9.10 requires some fiddling though because of the the new grub 2.0....but, if you have the available PC, just do an install of Xubuntu 9.10 and you are in business).

A

---

### Post by chenxiaolong on 2009-11-05
Alacrity, could you post the result of "lshw -C Network" in terminal? I wonder what driver you're using. I currently use the Broadcom STA (wl) driver, but aircrack-ng doesn't want to work for me. :(

---

### Post by Alacrity on 2009-11-05
> **chenxiaolong said:**
> Alacrity, could you post the result of "lshw -C Network" in terminal? I wonder what driver you're using. I currently use the Broadcom STA (wl) driver, but aircrack-ng doesn't want to work for me. :(

Let me know if this helps....

root@john:/home/john# lshw -C Network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: b1
       serial: 00:26:9e:68:92:7d
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:22 memory:93106000-93106fff ioport:30e0(size=8) memory:93109000-931090ff memory:93109300-9310930f
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:93000000-93003fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 0c:ee:e6:8c:4d:77
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.10.195 multicast=yes wireless=IEEE 802.11bg
root@john:/home/john#



And from dmesg....


 57.811604] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   58.134870] ip_tables: (C) 2000-2006 Netfilter Core Team
[   58.171590] cfg80211: World regulatory domain updated:
[   58.171601]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   58.171611]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   58.171620]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   58.171629]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   58.171638]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   58.171646]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   58.281911] phy0: Selected rate control algorithm 'minstrel'
[   58.284057] Registered led device: b43-phy0::tx
[   58.284122] Registered led device: b43-phy0::rx
[   58.284181] Registered led device: b43-phy0::radio
[   58.284325] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]
[   58.312143] udev: renamed network interface wlan0 to wlan1
[   58.380487] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input8
[   58.765454] eth1: no link during initialization.
[   58.766325] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   58.864128] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   59.844813] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[   59.881741] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   59.881753] HDA Intel 0000:00:08.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   59.881800] HDA Intel 0000:00:08.0: setting latency timer to 64
[   59.919187] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[   60.072134] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)


Or, testing under airmon-ng,

Interface    Chipset        Driver

wlan1        Broadcom    b43 - [phy0]


Remember that this is the FINAL Xubuntu not an RC or Beta.

---

### Post by rusty73 on 2009-11-05
the card works perfectly with fedora 12 and b43 driver

---

### Post by chenxiaolong on 2009-11-05
WOW! Apparently the b43 driver included with Xubuntu works out of the box. That's great! I'll have to find out how to get it working in Ubuntu.

---

### Post by Alacrity on 2009-11-05
> **rusty73 said:**
> the card works perfectly with fedora 12 and b43 driver

Rusty

This is good news also...

Does it work "out of the box"?  If so, you must be using "rawhide" Fedora 12 Beta or Alpha?  Could you confirm which one?

Did you also test for aircrack-ng injection capability?

Thanks in advance.

Olong,

Yes, for some reason Ubuntu 9.10 did not fly for me the same way.  If you get it working, let me know.  Actually, Xubuntu is pretty darn close to Ubuntu except for the missing gnome.....so if one works, the other should work as well.

Good thread.


A

---

### Post by chenxiaolong on 2009-11-05
I downloading Xubuntu to test it right now. Alacrity, does the driver work immediately on the live cd or only after installation? I guessing rusty73 is using Fedora 12 Beta since it's the newest version.

---

### Post by Alacrity on 2009-11-05
Hi Chenx,

I installed Xubuntu 9.10 on an old PC then just pulled in aircrack-ng and airoscript....then did a remastersys....and then put the remastersys on a persistent usb stick.....then booted up my one week old netbook:  HP Mini 311 with Win7.  

And, voila!  All worked well.

I will try the Fedora.  Yes, I had read in another forum that the kernel 2.6.31 supported b43 so I think that is the key.

Although I have no idea why Xubuntu works and Ubuntu does not work.  I also just tried the Ubuntu_netbook_remix 9.10 and it did not work either.

For you, if Xubuntu works, just add gnome and you have Ubuntu I think.......

Let me know how it works for you.

A



Correction:  The usb did not have to be persistent....since it was the full iso.

---

### Post by chenxiaolong on 2009-11-05
I wasn't able to boot Xubuntu, it gave me I/O errors. I'll have to get new DVD-RW discs soon. Anyway, I got the b43 driver to work in the regular Ubuntu. I had to install the "linux-backports-modules-karmic" package and had to blacklist the "ssb" driver. I'm assuming that Xubuntu already has that package, so therefore, it works. Aircrack-ng even works too. I'll update my original post to add this information. Below are my logs for reference:

```
chenxiaolong@d6657k1:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:11 memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:f5:76:51
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.17 latency=0 multicast=yes
       resources: irq:11 memory:fc500000-fc50ffff
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:5f:ba:50:76
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.199 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

```
chenxiaolong@d6657k1:~$ dmesg | grep b43
[    1.913219] b43-pci-bridge 0000:04:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.913235] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[   11.688452] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   11.913476] Registered led device: b43-phy0::tx
[   11.913493] Registered led device: b43-phy0::rx
[   11.913509] Registered led device: b43-phy0::radio
[   19.720671] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   20.084858] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[   20.109624] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[   20.271721] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
```

```
chenxiaolong@d6657k1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"LL_Wireless_N"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:27:46:94:DA   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by Alacrity on 2009-11-05
Sounds like you were very busy!

And, yes, I just booted up my Xubuntu and I see that the linux-backports-modules-karmic 2.6.31.14.27 is already installed.  So, maybe you made a nice guess.

Also, I will try your new process on a persistent 8GB usb and see if I can get Ubuntu going.

A

EDIT:  Tried Ubuntu 9.10 with your process and a persistent usb.  Unfortunately, it did not work for me.  There must be something more in your process that you may not have shown (more than the three steps you show in your initial post).  What else did you add to the original Ubuntu 9.10 ISO?  Compat, firmware, cutter, and so on? At first, I thought maybe on my persistent usb the blacklisted items were not coming thru at the beginning of the boot (when blacklisted items are initially checked during the boot process) but then I booted up the fullly working Xubuntu and there are no blacklisted line items for wl or ssb.

---

### Post by BETELGEUSE58 on 2009-11-06
Thank you

Worked fine for me

---

### Post by rusty73 on 2009-11-06
sorry, but with fedora fail in the same way like ubuntu. DMA problems too. It's stranger because when you install compat-wireless on a fresh install, the driver works well, but if you reboot the computer, the driver fail.

---

### Post by mnoyes on 2009-11-06
Dell mini9 karmic, really been struggling with this lack of wireless (wired connection is fine)

I get this from lshw -C network:

*-network UNCLAIMED              
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f0203fff

I have the STA driver installed. (activated but, it says, "not in use") 

Where to next?

---

### Post by Alacrity on 2009-11-06
Betel,

Which process did you use?  Karmic? or the longer process?




Mnoyes & Rusty,

Have you tried Xubuntu 9.10?


A

---

### Post by tantos on 2009-11-06
Many thanks [chenxiaolong]("http://ubuntuforums.org/member.php?u=724117"), now my wireless works!

---

### Post by chenxiaolong on 2009-11-06
Mnoyes, could you check to see if there's a line that says "b43" in the file "/etc/modules"? If there isn't, just add a new line to the bottom of the file that says "b43" and reboot your computer and you should be fine (if you followed the steps in my original post).

Alacrity, I tried creating a persistent Ubuntu USB after I installed the ubuntu-backports-modules-karmic, the firmware, and blacklisted the ssb and wl driver and it works perfectly for me. I have no idea why it doesn't work for you. For the Xubuntu live USB, are you sure that none of the files in "/etc/modprobe.d/" have a line for blacklisting ssb or wl?

Also, could you boot up the Ubuntu live USB and try unloading b43, ssb, and wl and then try loading the b43 module?

sudo rmmod b43
sudo rmmod ssb
sudo rmmod wl
sudo modprobe b43

---

### Post by Alacrity on 2009-11-06
For the Xubuntu live USB, are you sure that none of the files in "/etc/modprobe.d/" have a line for blacklisting ssb or wl?



Yes, I am positive.  Neither is shown or blacklisted in Xubuntu.  Let me regenerate the USB persistent for Ubuntu 9.10 and I will try your rmmod and modprobe suggestions.


A


EDIT:  Interesting.  Under Xubuntu, a full b43 directory shows up in /lib/firmware....but does not in Ubuntu.  And, as I mentioned, no wl or ssb blacklisted in Xubuntu.  Xubuntu also shows b43-fwcutter as an installed package under synaptic but Ubuntu does not.  Are you sure you did not do a "sudo apt-get install b43-fwcutter"  with Ubuntu 9.10?  Hard to figure ...

---

### Post by chenxiaolong on 2009-11-06
Ohhhhhh. I'm sorry. You Do have to install the b43-fwcutter package. I originally installed the firmware using the Restricted Hardware Drivers application and I completely forgot that it installed the b43-fwcutter package. I'll update my original post to include this.

---

### Post by rusty73 on 2009-11-07
> **Alacrity said:**
> Betel,

Which process did you use?  Karmic? or the longer process?




Mnoyes & Rusty,

Have you tried Xubuntu 9.10?


A

yes, I did. Dmesg show me the same DMA error. I followed de short 
 way.

---

### Post by chenxiaolong on 2009-11-07
Rusty73, could you try unloading the b43 and ssb module and loading the b43 module again and post what dmesg says?

sudo rmmod b43
sudo rmmod ssb
sudo modprobe b43

---

### Post by rusty73 on 2009-11-07
> **chenxiaolong said:**
> Rusty73, could you try unloading the b43 and ssb module and loading the b43 module again and post what dmesg says?

sudo rmmod b43
sudo rmmod ssb
sudo modprobe b43

In xubuntu or ubuntu?, now i have a fresh install of ubuntu karmic (only i updated the system with synaptic, i didn't install any drivers or compat-wireless), by the way, i searched and found inside compat-wireless forums that the best solution is compile the real wireless tree, not the compat wireless.

---

### Post by rusty73 on 2009-11-07
> **rusty73 said:**
> In xubuntu or ubuntu?, now i have a fresh install of ubuntu karmic (only i updated the system with synaptic, i didn't install any drivers or compat-wireless), by the way, i searched and found inside compat-wireless forums that the best solution is compile the real wireless tree, not the compat wireless.

Ok, I did in a fresh ubuntu install. I installed backports modules and b43-fwcutter like your frist post. after this i remove b43 and ssb and load b43 again and this is my dmesg.

[http://pastebin.com/m40bd8055](http://pastebin.com/m40bd8055)

after this i rebooted the computer and this is may dmesg

[http://pastebin.com/m1189dcb4](http://pastebin.com/m1189dcb4)

After the fresh install i had this dmesg  (without any drivers)

[http://pastebin.com/m4ecdea18](http://pastebin.com/m4ecdea18)


I have dell mini9.

---

### Post by chenxiaolong on 2009-11-07
Ok. It seems like ssb is the problem. Try running```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
``` and rebooting and see if it works. If you want to reverse this, simply delete /etc/modprobe.d/blacklist.ssb.conf

---

### Post by chenxiaolong on 2009-11-07
Is anybody else noticing that, with the b43 driver, the wireless disconnects a lot? It happens to me when I'm downloading something for too long.

---

### Post by Alacrity on 2009-11-08
Chenxiaolong,

Had a chance to make a remastersys permanent usb boot with Ubuntu 9.10.  Definitely take the two blacklist items out of your process:  wl and ssb.  They will keep the b43 from working.

My new HP Mini 311 is now very solid with Ubuntu 9.10.  Runs very nice in both managed mode and under monitor/injection modes.

Used ws2-tcl ([http://forum.aircrack-ng.org/index.php?topic=3734.00](http://forum.aircrack-ng.org/index.php?topic=3734.00)) to crack WEP from a long distance in 80 seconds.

b43 under Ubuntu 9.10 seems to be very effective (Tx and Rc).  And, downloading (question from your post) seems fine without the blacklist.

A

---

### Post by chenxiaolong on 2009-11-08
So, using linux-backports-modules-jaunty without blacklisting b43 and ssb works perfectly? Could you try downloading a large file like the Ubuntu live CD to make sure? Whenever I try downloading a large file and the speed is over 650kpbs, the wireless card disconnects (that is, with the blacklists).

---

### Post by rusty73 on 2009-11-08
Sorry, but I have changed wifi card to an atheros from asus eee 900 and works very well. Thanks for all guys but I couldn't wait because I test all ways with the same result, the DMA error.

Thaks a lot.

---

### Post by Alacrity on 2009-11-08
Use only the following command:

sudo apt-get install linux-backports-modules-karmic b43-fwcutter

and your downloading will be fine

and aircrack-ng will also be fine

You mentioned jaunty in your post....that should be karmic.

A

---

### Post by Jekshadow on 2009-11-08
> **rusty73 said:**
> 
after this i rebooted the computer and this is may dmesg

[http://pastebin.com/m1189dcb4](http://pastebin.com/m1189dcb4).

I got the exact same dmesg (or at least the part about the fatal DMA error) until I tried to remove the b43 module, and then my dmesg looked like:

```
[  269.191403] b43-phy0: Controller RESET (DMA error) ...
[  269.530315] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  273.712604] CE: hpet increasing min_delta_ns to 15000 nsec
[  283.333712] b43-phy0: Controller restarted
[  283.523009] BUG: unable to handle kernel NULL pointer dereference at (null)
[  283.523022] IP: [<ffffffff81073d78>] insert_work+0x68/0xc0
[  283.523040] PGD dcc54067 PUD dcd1c067 PMD 0 
[  283.523050] Oops: 0002 [#1] SMP 
[  283.523058] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0/ieee80211/phy0/rfkill1/uevent
[  283.523066] CPU 1 
[  283.523071] Modules linked in: hidp binfmt_misc ppdev bridge stp bnep snd_hda_codec_idt snd_hda_intel snd_hda_codec sha256_generic snd_hwdep cryptd joydev aes_x86_64 aes_generic cbc arc4 ecb snd_pcm_oss snd_mixer_oss snd_pcm dell_wmi b43(-) snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi dell_laptop snd_seq_midi_event dm_crypt psmouse mac80211 snd_seq uvcvideo snd_timer cfg80211 lp sdhci_pci iptable_filter parport serio_raw ip_tables snd_seq_device videodev dcdbas sdhci led_class btusb v4l1_compat snd x_tables v4l2_compat_ioctl32 ricoh_mmc soundcore snd_page_alloc dm_raid45 xor usbhid ohci1394 tg3 ieee1394 ssb pcmcia pcmcia_core video output intel_agp
[  283.523194] Pid: 2471, comm: modprobe Not tainted 2.6.31-14-generic #48-Ubuntu XPS M1330                       
[  283.523201] RIP: 0010:[<ffffffff81073d78>]  [<ffffffff81073d78>] insert_work+0x68/0xc0
[  283.523213] RSP: 0018:ffff8800dcc35c68  EFLAGS: 00010082
[  283.523218] RAX: 0000000000000000 RBX: ffff8801178bb690 RCX: ffff8801178bb698
[  283.523224] RDX: 0000000000000001 RSI: 0000000000000003 RDI: ffff88002801f018
[  283.523229] RBP: ffff8800dcc35c98 R08: 0000000000000000 R09: 0000000000000001
[  283.523235] R10: fecb32e7e33b7407 R11: ffff88010944a8f4 R12: ffff88002801f000
[  283.523241] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000bd1b28
[  283.523249] FS:  00007f16991b26f0(0000) GS:ffff88002803d000(0000) knlGS:0000000000000000
[  283.523255] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  283.523260] CR2: 0000000000000000 CR3: 00000000dcd2b000 CR4: 00000000000006e0
[  283.523266] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  283.523272] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  283.523279] Process modprobe (pid: 2471, threadinfo ffff8800dcc34000, task ffff880112c80000)
[  283.523284] Stack:
[  283.523287]  ffff8800dcc35c78 ffffffff81036419 ffff88002801f000 0000000000000286
[  283.523297] <0> ffff8801178bb690 0000000000000000 ffff8800dcc35cc8 ffffffff810741c1
[  283.523308] <0> ffff880119925400 ffff8801178ba360 ffff8801178bb690 ffff880119910380
[  283.523320] Call Trace:
[  283.523333]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
[  283.523343]  [<ffffffff810741c1>] __queue_work+0x31/0x50
[  283.523351]  [<ffffffff8107425d>] queue_work_on+0x3d/0x50
[  283.523359]  [<ffffffff810742aa>] queue_work+0x1a/0x20
[  283.523398]  [<ffffffffa01cdd2c>] ieee80211_queue_work+0x2c/0x40 [mac80211]
[  283.523425]  [<ffffffffa0243aeb>] b43_led_brightness_set+0x2b/0x30 [b43]
[  283.523437]  [<ffffffff81406438>] led_trigger_set+0xe8/0xf0
[  283.523446]  [<ffffffff814064fa>] led_trigger_unregister+0xba/0xc0
[  283.523477]  [<ffffffffa01ce77d>] ieee80211_led_exit+0x1d/0x90 [mac80211]
[  283.523504]  [<ffffffffa01b50f1>] ieee80211_unregister_hw+0xc1/0xf0 [mac80211]
[  283.523523]  [<ffffffffa0227529>] b43_remove+0xb9/0xc0 [b43]
[  283.523544]  [<ffffffffa003e76b>] ssb_device_remove+0x2b/0x50 [ssb]
[  283.523556]  [<ffffffff81320a73>] __device_release_driver+0x53/0xb0
[  283.523565]  [<ffffffff81320b98>] driver_detach+0xc8/0xd0
[  283.523577]  [<ffffffff8131fbb5>] bus_remove_driver+0x95/0xc0
[  283.523585]  [<ffffffff8132116a>] driver_unregister+0x5a/0x90
[  283.523603]  [<ffffffffa003ec6d>] ssb_driver_unregister+0xd/0x10 [ssb]
[  283.523624]  [<ffffffffa0243e14>] b43_exit+0x10/0x17 [b43]
[  283.523634]  [<ffffffff8108f328>] sys_delete_module+0x1a8/0x280
[  283.523645]  [<ffffffff8107cf29>] ? up_read+0x9/0x10
[  283.523654]  [<ffffffff8152bf74>] ? do_page_fault+0x194/0x370
[  283.523664]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
[  283.523669] Code: e0 48 83 c8 01 48 89 03 48 8b 42 08 48 8d 4b 08 49 8d 7c 24 18 be 03 00 00 00 48 89 4a 08 48 89 53 08 ba 01 00 00 00 48 89 43 10 <48> 89 08 31 c9 e8 ae 6a fd ff 48 8b 5d e0 4c 8b 65 e8 4c 8b 6d 
[  283.523755] RIP  [<ffffffff81073d78>] insert_work+0x68/0xc0
[  283.523765]  RSP <ffff8800dcc35c68>
[  283.523769] CR2: 0000000000000000
[  283.523776] ---[ end trace 117f210cb85ca18a ]---

```

---

### Post by Alacrity on 2009-11-08
Hi Jekshadow...and Rusty,

Please go here first:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

And read it thru.  

Can you post the o/s you are using and the ID of your wireless?  If you are using an older 0/s linux kernel that may be your problem.  You need 2.6.31 and Ubuntu or Xubuntu 9.10 for example.

Have you tried Ubuntu 9.10 with the one xterminal command?  "sudo apt-get install linux-backports-modules-karmic b43-fwcutter"

Also, there are many discussions on different web sites if you google on "b43 DMA error".  It appears they were using the older kernel and a different process.

A

---

### Post by Jekshadow on 2009-11-09
I'm using the 2.6.31 kernel with the latest updates and my wifi card's PCI ID is 14e4:4315. I am using Ubunu 9.10, I freshly installed it a few days after karmic came out and have been updating once every few days. I did try installing the drivers + firmware from source and via repos (removed both between) and both gave the same DMA error.

---

### Post by Alacrity on 2009-11-09
Jekshadow,

You have the right Distro......Ubuntu 9.10

But, with that Distro and kernel, you do not have to install any firmware or drivers other than the one xterm command.  You might be causing a software conflict.  

What if you started fresh and re-installed Ubuntu 9.10 and did that one xterm command?  Then check to see if you are up and running with the b43?

A

---

### Post by Alacrity on 2009-11-09
I see that you are online....if you want, I will stay on and we can chat if you need any clarification.

A

EDIT:  Guess you are AFK. Catch you later.

---

### Post by Jekshadow on 2009-11-09
> **Alacrity said:**
> Jekshadow,

You have the right Distro......Ubuntu 9.10

But, with that Distro and kernel, you do not have to install any firmware or drivers other than the one xterm command.  You might be causing a software conflict.  

What if you started fresh and re-installed Ubuntu 9.10 and did that one xterm command?  Then check to see if you are up and running with the b43?

A

I'm pretty sure I wiped EVERYTHING... I deleted /lib/firmware/b43 and /lib/firmware/bcmxx (I think it was called that), and also /lib/modules/2.6.31-14-generic/updates to get rid of all of the custom kernel modules (I had gotten rid of the nVidia driver and wl before hand, so only the drivers from the package were there). I also uninstalled the packages

---

### Post by Alacrity on 2009-11-09
"pretty sure" hmmmmm.  Something is still causing a conflict for you.  My guess is that it is some software remnant.

Do you have a lot of added software on your Ubuntu o/s and don't want to lose it?

If so, run remastersys and make an iso back-up of your present system.

Then, take a clean Ubuntu 9.10 and install it and add only the one xterm command.

Or, take an Acronis image of your present hdd that you can re-apply if you want.  Then install a clean Ubuntu 9.10

Both of those are good approaches to learn and use anyway.

Otherwise, I throw in the towel and am out of suggestions.

Good luck,

A

---

### Post by Jekshadow on 2009-11-09
> **Alacrity said:**
> "pretty sure" hmmmmm.  Something is still causing a conflict for you.  My guess is that it is some software remnant.

Do you have a lot of added software on your Ubuntu o/s and don't want to lose it?

If so, run remastersys and make an iso back-up of your present system.

Then, take a clean Ubuntu 9.10 and install it and add only the one xterm command.

Or, take an Acronis image of your present hdd that you can re-apply if you want.  Then install a clean Ubuntu 9.10

Both of those are good approaches to learn and use anyway.

Otherwise, I throw in the towel and am out of suggestions.

Good luck,

A

I'll just copy my home dir to an external drive and reinstall.

---

### Post by Alacrity on 2009-11-09
Super clean re-install of Ubuntu 9.10.

And, you are home free.

Enjoy your new b43 wireless but don't forget to post your success in this thread.

A

---

### Post by mnoyes on 2009-11-10
Been awol from this thread for a couple of days. Just tried the instructions for installing b43 and blacklisting ssb. The b43 driver is "activated and in use" but still in WICD no wireless (should see about three possible connections).

lshw -C network

shows

*-network
description: network controller
product: BCM4312 802.11/b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33mhz
capabilities: bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:f0200000-f0203fff

next comes the ethernet interface, which is working

then

*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:21:63:9f:67:51
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by chenxiaolong on 2009-11-10
Mnoyes, try blacklisting wl also, just to make sure it's not hogging the card. And try adding "alias wlan0 b43" in /etc/modprobe.d/aliases.conf and restarting.

---

### Post by mnoyes on 2009-11-10
Hmmm, worked for a minute! ... then WICD froze and when I rebooted, no wireless networks.

I removed and reinstalled WICD but it is still freezing up... forcing me to do a hard reboot several times....

Thanks for your help, by the way!

---

### Post by chenxiaolong on 2009-11-11
Your welcome! You might want to try using Network Manager again because it's working really well with b43 and I don't find any issues with it. I haven't tried Wicd yet, but "if it ain't broke, don't fix it." :)

---

### Post by Alacrity on 2009-11-11
Yes.  I think Chenxiaolong is correct.  Network Manager seems more "robust" than WICD.  That might work for you.

A

---

### Post by mnoyes on 2009-11-11
Finally!

Followed Chenxiaolong's instructions, and the back and forth with various folks, and now I have wireless up and running on my Dell Mini9 using the b43 driver with network manager.

My faith in the Ubuntu forums is restored -- the enthusiasm and patience of users like Chenxiaolong is one of Ubuntu's best assets.:D

...Alas! I spoke too soon. I have a wireless connection, but can't get online... Now to search the threads about network manager and internet connections...

---

### Post by Alacrity on 2009-11-11
Some people have all the fun!

A

---

### Post by raygj on 2009-11-12
see this post it might help you out
[http://ubuntuforums.org/showpost.php?p=8295253&postcount=6]("http://ubuntuforums.org/showpost.php?p=8295253&postcount=6")

---

### Post by chenxiaolong on 2009-11-12
I had to do what the post said in raygj post (if that makes sense) on another HP laptop, but on mine, I just needed to set a manual DNS server (I use OpenDNS).

---

### Post by edgardo1967 on 2009-11-13
Hello everybody. I'm a little confuse about what to do in order to make Broadcom 435 rev 1 with Ubuntu 9.10 works. Could anyone give me some advice in few steps starting from a fresh install of KK in my netbook? Thanks in advance.

---

### Post by Alacrity on 2009-11-13
Gardo,

Do you mean the 14e4:4315 (Broadcom bcm4312 rev 01) wireless chip?  Is that the one you have on your system?

Haven't heard of KK but anyway my take is that you can either:

1.  Use the very first post and the three x term commands.  Chenxiolong updated that post as he found changes.

or

2.  Just use the first x term command in that post which worked for me.  I did not need the blacklist commands.


A

---

### Post by chenxiaolong on 2009-11-13
Alacrity, I think he meant Karmic Koala for KK. :)

---

### Post by brammert on 2009-11-14
Dear All,

I've been trying to get my wireless working for about two weeks now. Just upgraded to karmic and followed the short way of [chenxiaolong]("http://art.ubuntuforums.org/member.php?u=724117")'s post. Before i did so, I could still open the wireless and scan for networks (but couldn't see any). After rebooting I can't open my wireless anymore.[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG] (it's grey and I can't click it in my network connections), so still no wireless for me... Can anybody help me getting it done? I'm pretty new to linux, and hope someone can help me...

btw, I use Kubuntu...

---

### Post by chenxiaolong on 2009-11-14
Could you reattach your screenshots?

---

### Post by brammert on 2009-11-14
here it is, but I'm not completely sure which info you need... Thanks for the quick response!

---

### Post by chenxiaolong on 2009-11-14
Could you post the result of "sudo lshw -C Network"? Also, did you notice that you are on the DSL tab in the screenshot?

---

### Post by brammert on 2009-11-15
here the result is. I know DSL was selected, but I only made the screenshot to show its not possible to open my wireless. 

  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:95300000-95303fff
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:21:70:ba:e3:66
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.7 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:94200000-94203fff ioport:2000(size=256) memory:91000000-9101ffff(prefetchable)

---

### Post by chenxiaolong on 2009-11-15
Could you also post 

"dmesg | grep b43"
"lsmod | grep wl"
"lsmod | grep ssb"?

---

### Post by Kukukes on 2009-11-17
I am using a b43 driver. It worked fine for some 2-3 days until I run ppoeconf. After a reboot ot stopped working. I reinstalled the driver several times, but no success. 
Now Hardware Manager (I am using Russian Ubuntu, so I am sorry for wring translations) says that the the b43 driver is active and in use, but Network Manager says that the hardware is not managed (sorry again for a wrong translation).
ifconfig says:
```

eth0      Link encap:Ethernet  HWaddr 00:24:81:54:9d:ec  
          inet addr:192.168.0.38  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe54:9dec/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1057;&#1089;&#1099;&#1083;&#1082;&#1072;
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29015 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:13583604 (13.5 MB)  TX bytes:4759899 (4.7 MB)
          &#1055;&#1088;&#1077;&#1088;&#1074;&#1072;&#1085;&#1086;:16 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1059;&#1079;&#1077;&#1083;
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1257 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:0 
          RX bytes:43551 (43.5 KB)  TX bytes:43551 (43.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:00:be:9f:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```sudo lshw -C Network says:
```

 *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:24:81:54:9d:ec
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.0.38 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:93100000-93103fff ioport:3000(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:92000000-92003fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:00:be:9f:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```dmesg | grep b43 says:
```

[    1.859516] b43-pci-bridge 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.859528] b43-pci-bridge 0000:06:00.0: setting latency timer to 64
[    7.468364] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    8.099337] Registered led device: b43-phy0::tx
[    8.099366] Registered led device: b43-phy0::rx
[    8.099386] Registered led device: b43-phy0::radio
[   17.950182] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   18.135092] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[   18.142511] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[   18.280171] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
```how to make it work?

---

### Post by tapas_mishra on 2009-11-17
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and read the README given there I tried Debian and it worked

---

### Post by chenxiaolong on 2009-11-17
For some reason pppoeconf turns off Network Manager. All you have to do is:

1) Open up /etc/NetworkManager/nm-system-settings.conf as root.

2) Change "managed=false" to "managed=true". 

3) Restart your computer.

And it should be fine now.

By the way, your translations are fine :)

---

### Post by brammert on 2009-11-17
Sorry for keeping you wait so long. I havent been able to see the laptop last few days. Here are the results you asked for. 

[QUOTE=chenxiaolong;8321115]Could you also post 

"dmesg | grep b43"
result:
10.355720] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.355734] b43-pci-bridge 0000:01:00.0: setting latency timer to 64

"lsmod | grep wl"
There is no result to show for this comment. 

"lsmod | grep ssb"?
Result:
ssb                    52080  1 b44
pcmcia                 40116  1 ssb
pcmcia_core            41796  2 ssb,pcmcia

Thanks for your great help!

---

### Post by Kukukes on 2009-11-17
Dear Chenxiaolong, changing Network Manager conf helped me. Thank you a lot! :P

---

### Post by hemlockz on 2009-11-18
Hey thanks for this! I am trying to get this card to work in ad-hoc mode. Has anyone tried that? I can create the ad-hoc network and join it from another computer but it will not make a connection, or get an IP address.  It's working fine with my eeePC or Sony laptop with Ubuntu no problem.  I guess this 4315 card in the Mini 9 is the only difference.  

So I came across this thread and at first I tried b43 with 9.04 (kernel 2.6.28-11).  I followed the instructions in the post and got it connecting but the whole reason I was trying to upgrade the driver was for ad-hoc support. It still didn't work with b43, so I am now trying to upgrade the kernel to 9.10 and try that route.  I have not ever gotten ad-hoc working on the Dell mini 910 with 4315, using the SLA driver with 9.04.  I'm hoping something has changed in 9.10 kernel 2.6.31 and it will start working, if not I'll try the newer version of b43 that requires 2.6.31 or higher.  Can anyone else here with the 4315 make a connection in ad-hoc mode with Ubuntu?

---

### Post by chenxiaolong on 2009-11-18
I don't have any other computers that have wireless, so I won't be able to test it (except for another laptop, which also has a 4315 card). Sorry!

---

### Post by Alacrity on 2009-11-18
> **hemlockz said:**
> Hey thanks for this! I am trying to get this card to work in ad-hoc mode. Has anyone tried that? I can create the ad-hoc network and join it from another computer but it will not make a connection, or get an IP address.  It's working fine with my eeePC or Sony laptop with Ubuntu no problem.  I guess this 4315 card in the Mini 9 is the only difference.  

So I came across this thread and at first I tried b43 with 9.04 (kernel 2.6.28-11).  I followed the instructions in the post and got it connecting but the whole reason I was trying to upgrade the driver was for ad-hoc support. It still didn't work with b43, so I am now trying to upgrade the kernel to 9.10 and try that route.  I have not ever gotten ad-hoc working on the Dell mini 910 with 4315, using the SLA driver with 9.04.  I'm hoping something has changed in 9.10 kernel 2.6.31 and it will start working, if not I'll try the newer version of b43 that requires 2.6.31 or higher.  Can anyone else here with the 4315 make a connection in ad-hoc mode with Ubuntu?



Assuming your mini 9 boots from either usb or CD, burn a fresh Ubuntu 9.10 and boot up to check your wireless capability.  If you upgrade kernels, no telling what software remains....which could conflict with Ubuntu 9.10

---

### Post by hemlockz on 2009-11-18
Yeah you are right.  I burned a fresh Karmic Kola CD and installed 9.10. No wireless adapter detected.  I used a USB WiFi adapter to connect and followed the three steps at the top of the thread, rebooted, and there is still nothing.  Do I need to reset the card with a jumper like the OP?
```

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
```

```
Nov 18 20:20:48 usb-laptop kernel: [    6.116272] Registered led device: b43-phy0::tx
Nov 18 20:20:48 usb-laptop kernel: [    6.116332] Registered led device: b43-phy0::rx
Nov 18 20:20:48 usb-laptop kernel: [    6.116391] Registered led device: b43-phy0::radio
Nov 18 20:20:48 usb-laptop kernel: [    6.116546] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]
Nov 18 20:20:49 usb-laptop kernel: [    6.915262] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 18 20:20:49 usb-laptop kernel: [    6.974924] __ratelimit: 6 callbacks suppressed
Nov 18 20:20:49 usb-laptop kernel: [    6.974934] type=1505 audit(1258604449.201:12): operation="profile_replace" pid=811 name=/usr/share/gdm/guest-session/Xsession
Nov 18 20:20:49 usb-laptop kernel: [    6.987137] type=1505 audit(1258604449.213:13): operation="profile_replace" pid=814 name=/sbin/dhclient3
Nov 18 20:20:49 usb-laptop kernel: [    6.988021] type=1505 audit(1258604449.213:14): operation="profile_replace" pid=814 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov 18 20:20:49 usb-laptop kernel: [    6.988532] type=1505 audit(1258604449.217:15): operation="profile_replace" pid=814 name=/usr/lib/connman/scripts/dhclient-script
Nov 18 20:20:49 usb-laptop kernel: [    7.004854] type=1505 audit(1258604449.233:16): operation="profile_replace" pid=822 name=/usr/bin/evince
Nov 18 20:20:49 usb-laptop kernel: [    7.018720] type=1505 audit(1258604449.245:17): operation="profile_replace" pid=822 name=/usr/bin/evince-previewer
Nov 18 20:20:49 usb-laptop kernel: [    7.027608] type=1505 audit(1258604449.253:18): operation="profile_replace" pid=822 name=/usr/bin/evince-thumbnailer
Nov 18 20:20:49 usb-laptop kernel: [    7.030806] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
Nov 18 20:20:49 usb-laptop kernel: [    7.047539] udev: renamed network interface wlan0 to wlan2
Nov 18 20:20:49 usb-laptop kernel: [    7.071910] type=1505 audit(1258604449.297:19): operation="profile_replace" pid=827 name=/usr/lib/cups/backend/cups-pdf
Nov 18 20:20:49 usb-laptop kernel: [    7.072991] type=1505 audit(1258604449.301:20): operation="profile_replace" pid=827 name=/usr/sbin/cupsd
Nov 18 20:20:49 usb-laptop kernel: [    7.078292] type=1505 audit(1258604449.305:21): operation="profile_replace" pid=892 name=/usr/sbin/tcpdump
Nov 18 20:20:50 usb-laptop kernel: [    7.996979] b43 ssb0:0: firmware: requesting b43/ucode15.fw
Nov 18 20:20:50 usb-laptop kernel: [    8.049902] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
Nov 18 20:20:50 usb-laptop kernel: [    8.102451] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
Nov 18 20:20:50 usb-laptop kernel: [    8.288416] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:20:50 usb-laptop kernel: [    8.321491] ppdev: user-space parallel port driver
Nov 18 20:20:56 usb-laptop kernel: [   14.652968] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:20:57 usb-laptop kernel: [   14.875804] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:21:03 usb-laptop kernel: [   21.436578] b43-phy0: Controller restarted
Nov 18 20:21:03 usb-laptop kernel: [   21.437190] ADDRCONF(NETDEV_UP): wlan2: link is not ready
Nov 18 20:21:03 usb-laptop kernel: [   21.439257] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:21:03 usb-laptop kernel: [   21.481758] r8169: eth0: link down
Nov 18 20:21:03 usb-laptop kernel: [   21.481932] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 18 20:21:03 usb-laptop kernel: [   21.675887] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:21:09 usb-laptop kernel: [   27.606236] b43-phy0: Controller restarted
Nov 18 20:21:09 usb-laptop kernel: [   27.606278] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:21:10 usb-laptop kernel: [   27.831157] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:21:15 usb-laptop kernel: [   33.497338] b43-phy0: Controller restarted
Nov 18 20:21:15 usb-laptop kernel: [   33.497397] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:21:15 usb-laptop kernel: [   33.712547] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:21:21 usb-laptop kernel: [   39.233315] b43-phy0: 
Nov 18 20:21:21 usb-laptop kernel: [   39.233331] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:21:21 usb-laptop kernel: [   39.233338] Controller restarted
Nov 18 20:21:21 usb-laptop kernel: [   39.448382] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:21:27 usb-laptop kernel: [   44.985333] b43-phy0: 
Nov 18 20:21:27 usb-laptop kernel: [   44.985350] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:21:27 usb-laptop kernel: [   44.985357] Controller restarted
Nov 18 20:21:27 usb-laptop kernel: [   45.200351] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:21:32 usb-laptop kernel: [   50.749330] b43-phy0: Controller restarted
Nov 18 20:21:32 usb-laptop kernel: [   50.760658] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:21:33 usb-laptop kernel: [   50.976374] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:21:38 usb-laptop kernel: [   56.497333] b43-phy0: Controller restarted
Nov 18 20:21:38 usb-laptop kernel: [   56.497410] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:21:38 usb-laptop kernel: [   56.712349] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:21:44 usb-laptop kernel: [   62.233319] b43-phy0: Controller restarted
Nov 18 20:21:44 usb-laptop kernel: [   62.244655] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:21:44 usb-laptop kernel: [   62.460374] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:21:50 usb-laptop kernel: [   67.981320] b43-phy0: Controller restarted
Nov 18 20:21:50 usb-laptop kernel: [   67.981400] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:21:50 usb-laptop kernel: [   68.196370] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:21:55 usb-laptop kernel: [   73.721378] b43-phy0: Controller restarted
Nov 18 20:21:55 usb-laptop kernel: [   73.721397] Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
Nov 18 20:21:55 usb-laptop kernel: [   73.721412] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:21:56 usb-laptop kernel: [   73.957327] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:22:01 usb-laptop kernel: [   79.480351] b43-phy0: Controller restarted
Nov 18 20:22:01 usb-laptop kernel: [   79.481774] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:22:01 usb-laptop kernel: [   79.705266] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:22:07 usb-laptop kernel: [   85.257399] b43-phy0: Controller restarted
Nov 18 20:22:07 usb-laptop kernel: [   85.257456] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:22:07 usb-laptop kernel: [   85.484389] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:22:13 usb-laptop kernel: [   91.005369] b43-phy0: 
Nov 18 20:22:13 usb-laptop kernel: [   91.005403] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:22:13 usb-laptop kernel: [   91.005416] Controller restarted
Nov 18 20:22:13 usb-laptop kernel: [   91.237398] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:22:19 usb-laptop kernel: [   96.817421] b43-phy0: Controller restarted
Nov 18 20:22:19 usb-laptop kernel: [   96.829425] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:22:19 usb-laptop kernel: [   97.048381] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:22:24 usb-laptop kernel: [  102.729383] b43-phy0: Controller restarted
Nov 18 20:22:24 usb-laptop kernel: [  102.729678] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:22:25 usb-laptop kernel: [  102.948417] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:22:30 usb-laptop kernel: [  108.565245] b43-phy0: Controller restarted
Nov 18 20:22:30 usb-laptop kernel: [  108.585312] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:22:31 usb-laptop kernel: [  108.813306] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:22:36 usb-laptop kernel: [  114.441374] b43-phy0: Controller restarted
Nov 18 20:22:36 usb-laptop kernel: [  114.441518] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:22:36 usb-laptop kernel: [  114.656409] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:22:42 usb-laptop kernel: [  120.230333] b43-phy0: Controller restarted
Nov 18 20:22:42 usb-laptop kernel: [  120.241498] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:22:42 usb-laptop kernel: [  120.461338] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 18 20:22:48 usb-laptop kernel: [  125.990354] b43-phy0: Controller restarted
Nov 18 20:22:48 usb-laptop kernel: [  125.990512] b43-phy0: Controller RESET (DMA error) ...
Nov 18 20:22:48 usb-laptop kernel: [  126.208367] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```

Thanks!

---

### Post by mnoyes on 2009-11-19
Hello again,

I had to stop working on fixing my wireless to get real work done. Now, I'm back.

Worried that in all my troubleshooting I had screwed something up, I re-installed 9.1 netbook remix then followed Chen's instructions for getting the wireless set up. 

It all worked as planned, the wireless shows up and I can connect, but no internet connection. I set the DCHP to automatic only and set DNS servers to 208.67.220.220 and 222, but still no go.

ping [http://google.com](http://google.com) tells me unknown host

Next steps?

---

### Post by hemlockz on 2009-11-19
Hey I might have found something that will work for you, but unfortunately my issues of Ad-Hoc is still not working.  I do have WEP and WPA infrastructure working well though with the STA drivers.  Using Dell Mini 910 with that 14e4:4315 card.

Freshly installed 9.10 again.
Run update manager once, reboot.
Run update manager again, to confirm its all up to date.
Start Synaptic Package Manager and install dkms, then install bcmwl-kernel-source
Reboot.
Reboot again.
I think I rebooted once more and then its been working ever since.
Under Hardware Drivers the STA driver was Active and in use after I did those steps.  I've rebooted 5 times since then and connected to WEP and WPA networks.

I think some of the updates are what was needed to make the STA driver work with Network Manager and everything.  If you try any of the b43 driver first, just reinstall a fresh 9.10 because it seems to mess with things somehow.  It does say on Linux Wireless .org that support for the 4315 is still in progress so I am not surprised if it doesn't work

---

### Post by brammert on 2009-11-19
Hej chenxiaolong,

I'm not sure if yo
Sorry for u saw my last post, but I have the results for you. I hope you still want to help. My response are a bit slow because its my girlfriends' laptop, and I don't see her every day. 
Anyway, can you help?

 [quote=chenxiaolong;8321115]Could you also post 
 
 "dmesg | grep b43"
 result:
 10.355720] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 [ 10.355734] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
 
 "lsmod | grep wl"
 There is no result to show for this comment. 
 
 "lsmod | grep ssb"?
 Result:
 ssb 52080 1 b44
 pcmcia 40116 1 ssb
 pcmcia_core 41796 2 ssb,pcmcia

---

### Post by mnoyes on 2009-11-20
I'm going to try hemlockz's suggestion. My six year old son listened to me complaining about the disaster upgrading to 9.1 has been and said, "why don't you just go back to Jackalope?" That's my next step... Anyone know where a person can download 9.04?

---

### Post by hemlockz on 2009-11-20
> **mnoyes said:**
> I'm going to try hemlockz's suggestion. My six year old son listened to me complaining about the disaster upgrading to 9.1 has been and said, "why don't you just go back to Jackalope?" That's my next step... Anyone know where a person can download 9.04?

good luck! [http://releases.ubuntu.com/](http://releases.ubuntu.com/) has the Jackalope :)

---

### Post by mnoyes on 2009-11-20
GREAT!

I followed your instructions to the letter and it worked -- like a charm.

Thanks for your help -- I hope that other Mini9 users find this thread, assuming they run into the same problems I did.

I have to say, upgrading to 9.1 on my Dell mini9 was a disaster -- it took me weeks to get it right (thanks to you). Given that Dell sells minis with Ubuntu installed, Canonical should give some special attention to problems Dell users might run into and work that into the upgrade or at least issue special instructions. 

Thanks again for your collective help, fellow Ubuntu users!:p

---

### Post by HuaiDan on 2009-11-20
I tried the OP method and it worked beautifully, I could browse, download updates...that is, until I rebooted the next day. Now, it reports making a connection and authenticates with the WPA key, but signal status shows no signal, even when I'm sitting right next to the router, and ifconfig yields an inet addr: way outside of my router's IP range. Yes, it IS connecting to my router, it reports my router's SSID. That, and no applications connect.


Any clues?

Edit:
Here's a major piece of the puzzle:  I just unhid my SSID, and it connected the right way this time. Back in business.

I would, however, like to re-hide my SSID and still be able to connect.

Any clues?

---

### Post by Alacrity on 2009-11-20
Great to see everybody's progress.

Mnoyes, what was your final solution?  Reinstall a fresh 9.10 and then use the initial thread's commands?  Or, did you return to 9.04?

HuaiDan,,  yes, my experience has been that some wireless chip/router combinations did not work with a hidden SSID.  So, you may have to live with that.  But, shouldn't a nice complex WPA/WPA2 password be acceptable?  Or, put into your AP router your MAC in the filter section?

A

---

### Post by Bigadada_saba on 2009-11-20
hi  i think you guys are making things way to difficult i could be wrong but here's what worked for me . i'm running 9.10 64 bit on a hp pavilion dv6 1240us with broadcom wireless card.
 
1) i did a fresh install from the live cd
2) after the installation in made sure and turn on the wireless even-though is not detected.
3) then load the the live cd as a source in synaptic
4) then search for broadcom 
5) install the drivers 
6) got to system/administration/hardware drivers 
7) install the STA driver
8) restart your computer then it should be working perfectly


hope this works for you it did for me

---

### Post by kamitsukai on 2009-11-23
I completed the karmic instructions for the wireless and they worked for the first reboot but now theres no wireless....

please help =]

---

### Post by Alacrity on 2009-11-23
> **kamitsukai said:**
> I completed the karmic instructions for the wireless and they worked for the first reboot but now theres no wireless....

please help =]

Hi kamitsukai,

If you are using Linux Mint, which version is it?  If it is Gloria v7, that kernel is an older one (2.6.28) and the karmic process may not work.  If you are using Helena ver rc1, that may work since the kernel is 2.6.31.  

Perhaps if you want to be sure, just install Ubuntu 9.10 which definitely works well.

A

---

### Post by kamitsukai on 2009-11-23
> **Alacrity said:**
> Hi kamitsukai,

If you are using Linux Mint, which version is it?  If it is Gloria v7, that kernel is an older one (2.6.28) and the karmic process may not work.  If you are using Helena ver rc1, that may work since the kernel is 2.6.31.  

Perhaps if you want to be sure, just install Ubuntu 9.10 which definitely works well.

A

Hi I'm using ubuntu 9.10 and it worked for the first reboot and now no longer works.... even after reinstall 

mint has this down and I had no fuss:D

---

### Post by kamitsukai on 2009-11-23
> **kamitsukai said:**
> Hi I'm using ubuntu 9.10 and it worked for the first reboot and now no longer works.... even after reinstall 

mint has this down and I had no fuss:D

Solved I never added "b43" to the file "/etc/modules" lol

:redface::lol:

---

### Post by georg.65 on 2009-11-25
> hi i think you guys are making things way to difficult i could be wrong but here's what worked for me . i'm running 9.10 64 bit on a hp pavilion dv6 1240us with broadcom wireless card.

1) i did a fresh install from the live cd
2) after the installation in made sure and turn on the wireless even-though is not detected.
3) then load the the live cd as a source in synaptic
4) then search for broadcom
5) install the drivers
6) got to system/administration/hardware drivers
7) install the STA driver
restart your computer then it should be working perfectly

hope this works for you it did for me yes same this I've do to and it works, with the Broadcom STA wireless drivers, BCM4321 and driver wl and the wireless connection works very well.

But now I'll like to get in the monitor mode for install kismet and this driver (wl) don't work must be an solution with the b43 driver for monitor mode, to switch between wl and b43, from all that I'm reading in this thread I can't get it to work.

My WLAN card: Dell Wireless 1395 WLAN Mini-Card and

orion@orion-laptop:~$ sudo lshw -C network
[sudo] password for orion:
  *-network              
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 01
       serial: 00:21:00:d8:bd:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.2.137 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:9c000000-9c003fff

...................

orion@orion-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
vboxnet0  no wireless extensions.

pan0      no wireless extensions.

Now I'm removing wl, no internet connection after this

orion@orion-laptop:~$ sudo modprobe -r wl
orion@orion-laptop:~$ sudo modprobe b43            
orion@orion-laptop:~$ sudo lshw -c network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:9c000000-9c003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:45:17:a4
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:32 ioport:3000(size=256) memory:96010000-96010fff(prefetchable) memory:96000000-9600ffff(prefetchable) memory:96020000-9602ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
orion@orion-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:45:17:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4616 (4.6 KB)  TX bytes:4616 (4.6 KB)

orion@orion-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.


And now with the b43 driver can't see anythink.

orion@orion-laptop:~$ sudo modprobe -r b43
orion@orion-laptop:~$ sudo modprobe  wl

After all I'm online again but it took a while time, still can't use b43 to work in monitor mode for starting kismet.


Please help ;)

---

### Post by Alacrity on 2009-11-25
georg,

Can you run:

lspci -vnn | grep 14e4

It's not clear what your exact driver is.....

And maybe look here for your driver capability once you run the lspci command:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

A

---

### Post by georg.65 on 2009-11-25
@ Alacrity          > georg,
 
 Can you run:
 
 lspci -vnn | grep 14e4
 
 It's not clear what your exact driver is.....
 
 And maybe look here for your driver capability once you run the lspci command:
 
 [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
 
 A     Thanks for the help, here the result

orion@orion-laptop:~$ lspci -vnn | grep 14e4
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
orion@orion-laptop:~$ 

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)


**PCI-ID**                  **State**                      **Chip**                                                                      **Driver** 
    
    **14e4:4315     ****in progress  ****BCM4312 802.11b/g - low power ****b43 **


Yes I'm in the same boat with the all in this threat, can used WLAN very well with STA Broadcom (driver wl), but with b43 for monitor mode I have no idea to get it.
Can wait after the State change progress --------->to supported
Or you have one better solution ?  thanks

---

### Post by Alacrity on 2009-11-25
georg,

You have the right card. It should work.  Could you run a quick test?  Does your PC boot from CD or USB?  If so, burn a Ubuntu 9.10 ISO if you don't already have one.  Then boot into the live CD and run the first terminal command in the first post of this thread.  Finally, test your PC and wireless card. You should have "managed" mode.

For kismet and "monitor" mode run these additional commands:

sudo mkdir /usr/src/drivers
cd /usr/src/drivers
sudo wget [http://wireless.kernel.org/download/iw/iw-0.9.18.tar.bz2](http://wireless.kernel.org/download/iw/iw-0.9.18.tar.bz2)
sudo tar jxvf iw-0.9.18.tar.bz2
cd iw-0.9.18
sudo make
sudo make install

If your PC is up and running.....it just means you probably have to re-install your Ubuntu o/s.

---

### Post by georg.65 on 2009-11-25
> georg,

You have the right card. It should work. Could you run a quick test? Does your PC boot from CD or USB? If so, burn a Ubuntu 9.10 ISO if you don't already have one. Then boot into the live CD and run the first terminal command in the first post of this thread. Finally, test your PC and wireless card. You should have "managed" mode.Alacrity,

this is the result of the test, 

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install linux-backports-modules-karmic b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-backports-modules-2.6.31-14-generic
  linux-backports-modules-karmic-generic
The following NEW packages will be installed:
  b43-fwcutter linux-backports-modules-2.6.31-14-generic
  linux-backports-modules-karmic linux-backports-modules-karmic-generic
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,566kB/1,584kB of archives.
After this operation, 4,956kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main linux-backports-modules-2.6.31-14-generic 2.6.31-14.16
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main linux-backports-modules-karmic-generic 2.6.31.14.27
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main linux-backports-modules-karmic 2.6.31.14.27
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.31/linux-backports-modules-2.6.31-14-generic_2.6.31-14.16_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.31/linux-backports-modules-2.6.31-14-generic_2.6.31-14.16_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-karmic-generic_2.6.31.14.27_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-karmic-generic_2.6.31.14.27_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-karmic_2.6.31.14.27_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-karmic_2.6.31.14.27_i386.deb)  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ubuntu:~$


it don't look very well, the ubuntu 9.10 cd is ok, I'm doing the md5sum test after downloading the file and make one cd check disk after that.
Now I'm with the USB stick online, ok I'll shutdown the PC and boot normally and test the wireless card.

---

### Post by georg.65 on 2009-11-25
Now I'm rebooting again, this is the test of my wireless card from **Dell Wireless 1395 WLAN Mini-Card**

orion@orion-laptop:~$ sudo lshw -c network
[sudo] password for orion: 
  *-network               
       description: Wireless interface
       product: **BCM4312 802.11b/g**
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: **eth2**
       version: 01
       serial: 00:21:00:d8:bd:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: **broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg**
       resources: irq:18 memory:9c000000-9c003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:45:17:a4
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:32 ioport:3000(size=256) memory:96010000-96010fff(prefetchable) memory:96000000-9600ffff(prefetchable) memory:96020000-9602ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes



[I]and I'm don't detected wlan with b43 driver
[/I]

orion@orion-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

**eth2      IEEE 802.11bg**  ESSID:""  Nickname:"" **                  *              # yes the wl driver can attached very well***
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
vboxnet0  no wireless extensions.

pan0      no wireless extensions.

orion@orion-laptop:~$ 


Here is the post from the file blacklist-bcm43.conf from /etc/modprobe.de, maybe need to change something I don't no.

[I]# Warning: This file is autogenerated by bcmwl-kernel-source. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx[/I]


When I look at System --> Administration ---> Hardware Drivers it show me only the Broadcom STA wireless Driver activated and currently in use, the b43 driver it don't show me and this driver I'll like to install. 
What I can do the next step now, any idea more thanks.

---

### Post by Alacrity on 2009-11-26
georg,

Sorry you are having difficulties.  I would still go back to the Live CD and access properly the archives.  Or, in Ubuntu 9.10, the b43-fwcutter is also available via synaptic package manager which may be easier for you.  Try that and then see if you have Broadcom b43 usage.  You may have to do a "sudo modprobe b43" after you install the fwcutter.

I personally did not have to do anything beyond that....no blacklisting was required.  In your 2nd post, I get the feeling you may have over blacklisted.... that is why I suggest using the Live CD....see it working....then assuming it works....re-install while duplicating what you did during the Live CD tests.

Or install a fresh Ubuntu 9.10 to run the tests unless you have a lot of software already on your o/s that you don't want to lose. Even if you did, just run a remastersys process to save it as a backup iso for re-installation if necessary.

Or use a process to give you a persistent usb with Ubuntu 9.10 to do your testing.  I think the Live CD is the easiest approach because there is only a very simple process you need to test....not a long list of packages you need to install. The Broadcom bcm4312 essentially works out of the box with Ubuntu 9.10......just needing the fxcutter.

Good luck!

A

---

### Post by georg.65 on 2009-11-26
Alacrity, 

I've installed the b43-fwcutter with the synaptic package manager, after this I'm running this commands

orion@orion-laptop:~$ sudo modprobe b43
[sudo] password for orion: 
orion@orion-laptop:~$ sudo lshw -c network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 01
       serial: 00:21:00:d8:bd:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       [B]configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.2.151 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:9c000000-9c003fff[/B]
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:45:17:a4
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:32 ioport:3000(size=256) memory:96010000-96010fff(prefetchable) memory:96000000-9600ffff(prefetchable) memory:96020000-9602ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


orion@orion-laptop:~$ lsmod
Module                  Size  Used by
[B]b43                   122136  0 
ssb                    35300  1 b43[/B]
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
ipt_REJECT              2812  1 
ipt_LOG                 5344  1 
xt_limit                2176  2 
snd_hda_codec_nvhdmi     4828  1 
xt_tcpudp               2780  8 
xt_state                1820  6 
snd_hda_codec_idt      59844  1 
ipt_addrtype            2204  4 
snd_hda_intel          26920  1 
snd_hda_codec          75708  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
joydev                 10272  0 
snd_hwdep               7200  1 snd_hda_codec
ip6table_filter         3164  1 
ip6_tables             13004  1 ip6table_filter
nf_nat_irc              2012  0 
nf_conntrack_irc        4992  1 nf_nat_irc
nf_nat_ftp              2652  0 
nf_nat                 17808  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      13352  8 nf_nat
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
nf_conntrack_ftp        6880  1 nf_nat_ftp
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack           67608  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          3100  1 
jmb38x_ms               9600  0 
ip_tables              11692  1 iptable_filter
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      8964  0 
lib80211_crypt_tkip     8636  0 
x_tables               16544  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
memstick               10072  1 jmb38x_ms
uvcvideo               59080  0 
psmouse                56180  0 
parport                35340  2 ppdev,lp
snd                    59204  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
**wl                   1272936  0 **
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
nvidia               9586440  39 
lib80211                6432  2 lib80211_crypt_tkip,wl
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
serio_raw               5280  0 
led_class               4096  2 b43,sdhci
btusb                  11856  2 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
r8169                  32064  0 
mii                     5212  1 r8169
intel_agp              27484  0 
agpgart                34988  2 nvidia,intel_agp
video                  19380  0 
output                  2780  1 video


orion@orion-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[B]eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   [/B]
          
vboxnet0  no wireless extensions.

pan0      no wireless extensions.



yes, still don't have the b43, must be one solution to get it to work without installing ubuntu 9.10 again, in the past i'm doing this 3 times because i've trouble to get the other wireless driver wl to work.

georg

---

### Post by chenxiaolong on 2009-11-26
The wl module and the b43 modules can't be loaded at the same time. It simply won't work. Try unloading the wl module then loading b43 and ssb:

sudo rmmod wl b43 ssb
sudo modprobe b43 ssb

Can you also check dmesg for any errors when loading b43?

dmesg | grep b43

---

### Post by georg.65 on 2009-11-26
> **chenxiaolong said:**
> **The wl module and the b43 modules can't be loaded at the same time.** It simply won't work. Try unloading the wl module then loading b43 and ssb:

sudo rmmod wl b43 ssb
sudo modprobe b43 ssb

Can you also check dmesg for any errors when loading b43?

dmesg | grep b43


Yes this I now, but the b43 don't like to load after I'm downloading the wl, here is my post

orion@orion-laptop:~$ sudo rmmod wl b43 ssb
[sudo] password for orion: 
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
orion@orion-laptop:~$ sudo modprobe b43 ssb
FATAL: Error inserting b43 (/lib/modules/2.6.31-15-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)
orion@orion-laptop:~$ dmesg | grep b43
[ 5024.427081] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 5024.427102] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[ 5024.549425] b43: Unknown parameter `ssb'
orion@orion-laptop:~$ 

thanks georg

---

### Post by georg.65 on 2009-11-26
After I'm doing this I'll see in System-->Administration---->Hardware 
Drivers that 

Broadcom b43 wireless driver appears with the message: this driver is not activated (before wasn't there)
Broadcom STA wireless driver the message: this diver is activated but not currently in use

What can bee the next step

---

### Post by chenxiaolong on 2009-11-26
According to the outputs, b43 is saying that there is something wrong with ssb. Do you have the package "linux-backports-modules-karmic" installed? If you don't, could you install it and then run:

sudo rmmod wl b43 ssb
sudo depmod -
sudo modprobe b43 ssb
dmesg | tail

---

### Post by georg.65 on 2009-11-26
yes chenxiaolong, it seems to look a little better 

here is my post

orion@orion-laptop:~$ sudo apt-get install linux-backports-modules-karmic b43-fwcutter
[sudo] password for orion: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following extra packages will be installed:
  linux-backports-modules-2.6.31-15-generic linux-backports-modules-karmic-generic
The following NEW packages will be installed:
  linux-backports-modules-2.6.31-15-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 1,564kB of archives.
After this operation, 4,841kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main linux-backports-modules-2.6.31-15-generic 2.6.31-15.17 [1,557kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main linux-backports-modules-karmic-generic 2.6.31.15.28 [3,264B]                        
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main linux-backports-modules-karmic 2.6.31.15.28 [3,238B]                                
Fetched 1,564kB in 1min 27s (18.0kB/s)                                                                                                     
Selecting previously deselected package linux-backports-modules-2.6.31-15-generic.
(Reading database ... 179810 files and directories currently installed.)
Unpacking linux-backports-modules-2.6.31-15-generic (from .../linux-backports-modules-2.6.31-15-generic_2.6.31-15.17_i386.deb) ...
Selecting previously deselected package linux-backports-modules-karmic-generic.
Unpacking linux-backports-modules-karmic-generic (from .../linux-backports-modules-karmic-generic_2.6.31.15.28_i386.deb) ...
Selecting previously deselected package linux-backports-modules-karmic.
Unpacking linux-backports-modules-karmic (from .../linux-backports-modules-karmic_2.6.31.15.28_i386.deb) ...
Setting up linux-backports-modules-2.6.31-15-generic (2.6.31-15.17) ...
update-initramfs: Generating /boot/initrd.img-2.6.31-15-generic

Setting up linux-backports-modules-karmic-generic (2.6.31.15.28) ...
Setting up linux-backports-modules-karmic (2.6.31.15.28) ...
orion@orion-laptop:~$ sudo rmmod wl b43 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
orion@orion-laptop:~$ sudo depmod -
[B]FATAL: modules must be specified using absolute paths.
"-" is a relative path[/B]
orion@orion-laptop:~$ sudo modprobe b43 ssb
**FATAL: Error inserting b43 (/lib/modules/2.6.31-15-generic/updates/cw/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)**
orion@orion-laptop:~$ dmesg | tail
[ 1876.359935] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[ 1876.424587] ssb: Sonics Silicon Backplane found on PCI device 0000:04:00.0
[ 1876.430225] cfg80211: World regulatory domain updated:
[ 1876.430231]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1876.430236]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1876.430241]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1876.430245]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1876.430250]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1876.430254]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1876.439112] **b43: Unknown parameter `ssb'**

Still the  message b43 unknown parameter ssb, but the other output looks ok, it seems to be something with the ssb module and when i'm running

orion@orion-laptop:~$ lsmod
Module                  Size  Used by
ssb                    44868  0 
pcmcia                 36808  1 ssb
mac80211              210408  0 
cfg80211              130440  1 mac80211
pcmcia_core            35792  2 ssb,pcmcia
ppp_deflate             4732  0 
zlib_deflate           20088  1 ppp_deflate
bsd_comp                5436  0 '
...........

he d'ont found the b43. What can be wrong about ssb and b43 in the settings.

thanks georg

---

### Post by chenxiaolong on 2009-11-26
For the "sudo depmod -" error, that was a mistake on my part. It should be "sudo depmod -a". Sorry for the typo. Could you run "ls /lib/modules/2.6.31-15-generic/updates/cw" and make sure wl.ko is in it? Also, you post the output of "sudo cat /lib/modules/2.6.31-15-generic/modules.dep | grep b43", so I can see which ssb.ko is being loaded?

---

### Post by georg.65 on 2009-11-27
Here i'm again, 

orion@orion-laptop:~$ ls /lib/modules/2.6.31-15-generic/updates/cw
adm8211.ko       iwlagn.ko               mac80211.ko    rt61pci.ko
ar9170usb.ko     iwlcore.ko              mwl8k.ko       rt73usb.ko
at76c50x-usb.ko  iwmc3200wifi.ko         p54common.ko   rtl8180.ko
ath5k.ko         lib80211_crypt_ccmp.ko  p54pci.ko      rtl8187.ko
ath9k.ko         lib80211_crypt_tkip.ko  p54spi.ko      ssb.ko
ath.ko           lib80211_crypt_wep.ko   p54usb.ko      usb8xxx.ko
**b43.ko**           lib80211.ko             rndis_host.ko  usbnet.ko
b43legacy.ko     libertas_cs.ko          rndis_wlan.ko  wl1251.ko
b44.ko           libertas.ko             rt2400pci.ko   wl1251_sdio.ko
cdc_ether.ko     libertas_sdio.ko        rt2500pci.ko   wl1251_spi.ko
cfg80211.ko      libertas_spi.ko         rt2500usb.ko   wl1271.ko
eeprom_93cx6.ko  libertas_tf.ko          rt2800usb.ko   zd1211rw.ko
ipw2100.ko       libertas_tf_usb.ko      rt2x00lib.ko
ipw2200.ko       libipw.ko               rt2x00pci.ko
iwl3945.ko       mac80211_hwsim.ko       rt2x00usb.ko

don't found wl.ko ;) only some wl12....

orion@orion-laptop:~$ sudo cat /lib/modules/2.6.31-15-generic/modules.dep | grep b43
[sudo] password for orion: 
updates/cw/b43legacy.ko: updates/cw/ssb.ko kernel/drivers/pcmcia/pcmcia.ko kernel/drivers/pcmcia/pcmcia_core.ko updates/cw/mac80211.ko updates/cw/cfg80211.ko kernel/drivers/leds/led-class.ko
**updates/cw/b43.ko: updates/cw/ssb.ko **kernel/drivers/pcmcia/pcmcia.ko updates/cw/mac80211.ko updates/cw/cfg80211.ko kernel/drivers/leds/led-class.ko kernel/drivers/pcmcia/pcmcia_core.ko
orion@orion-laptop:~$ 

To much i don't understand but i've good feeling we can do it when seeing the result, wl.ko isn't there, when i look at network manager, the wl driver disappear can't connect anymore wireless with wl.

---

### Post by georg.65 on 2009-11-27
yes chenxiaolong it works, you do it for me 

at system->administration->hardware drivers i've activated the b43 driver and after rebooting the driver works.

The other one STA driver is still there at system->administration->hardware drivers but i'snt activated.

I think this was it, if there are some problems i'll come back to this great thread.

You can write me, if i need to run more commands to make it sure that it work fine, do you now i'm newcomer with linux and ubuntu every day understanding a little more.

many thanks from georg

---

### Post by chenxiaolong on 2009-11-27
You're welcome. Since you activated the b43 driver from the *Hardware Drivers* program, it will automatically make sure that everything is okay, even if you reboot.

---

### Post by wildbluefaerie on 2009-11-27
I have the Broadcom BCM4312 and Karmic (9.10) - I originally got the wireless driver to work by downloading the driver directly from Broadcom for linux, and installing it as follows:

```

lsmod | grep "b43\|ssb\|wl"
rmmod b43
rmmod ssb
rmmod wl
echo "blacklist ssb" | /etc/modprobe.d/blacklist.conf
echo "blacklist b43" | /etc/modprobe.d/blacklist.conf
make clean
make
modprobe lib80211
insmod wl.ko

```The wireless worked after this, but the driver disappeared every time I rebooted the system, and I had to repeat the last 4 commands each time to get it to work. So I tried the commands listed in the first post of this thread (after removing the blacklist entry for b43 and ssb). Not only did it not work at all, but now I can't get the other method to work either, and I can't get the wireless to work at all, even after removing the linux-backports-modules-karmic and b43-fwcutter and the blacklist files. Can anyone help????

edit: I was posting from windows (since obviously I couldn't from ubuntu since the wireless wasn't working), and I just booted back into ubuntu, and now it magically works, even after rebooting a second time. No idea why, but it does. As far as I can tell, only linux-backports-modules-karmic is installed - b43-fwcutter isn't, and the blacklist files aren't there either. Anyway, it works so I'm not going to question it too much.

---

### Post by accmpk on 2009-12-01
Tried this, did a reboot, got the following just before a system hang:

ACPI:  PDI Interrupt Link [APCH] enabled at IRQ 22
forecedeth 0000:00:0a.0: PCI INT A -> Link[ACPH] -> GSI 22 (level, low)
-> IRQ 22
b43-pci-bridge 0000:03:00.0:  PCI INT A -> Link[AX3A] -> GSI 16 16 
(Level, low) -> IRQ 16

(hang)

Tried recovery mode, no use.  Any help greatly appreciated.

Mark


> **chenxiaolong said:**
> This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.

1. Open up Terminal.

2. Install the "linux-backports-modules-karmic" (newer wireless drivers from compat-wireless) package and the "b43-fwcutter" package (wireless firmware). During installation, if it asks you to fetch the firmware automatically, make sure you select yes.

```
sudo apt-get install linux-backports-modules-karmic b43-fwcutter
```

3. Blacklist the ssb module.

```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
```

4. Blacklist the wl module.

```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
```

5. Reboot

6. Enjoy your wireless!!!

**[COLOR="Red"]----------------------------------------------------------------------------------------------------------------[/COLOR]**

First of all, I want to thank lwfinger at openSUSE forums for making the b43 driver work with the 14e4:4315

The post looks verrrrry long right? Well it's not. All the commands are "copy-n-paste-able" and I recommend that you do copy and paste them so you don't make any mistakes.

So first of all, you need to download the latest compat-wireless from 

You can't use wget for this because they have a hotlink prevention system. So just download the  file from that website and SAVE IT TO YOUR HOME DIRECTORY. 

Then open the terminal and run this command to extract the archive

```
tar xjf compat-wireless-2.6.tar.bz2
```

In order for the package to compile, you need to install the kernel headers, if not already installed. Run this in the terminal

```
sudo apt-get install linux-headers-$(uname -r)
```

Then change to the compat-wireless directory: 

```
cd compat-wireless
```

Then compile the source files:

```
sudo make
```

Then install the files:

```
sudo make install
```

Then unload the drivers

```
sudo make unload
```

Then install b43-fwcutter:
VERY IMPORTANT!!: Do NOT choose yes when it asks if you want to automatically fetch the firmware.

```
sudo apt-get install b43-fwcutter
```

Download the Broadcom firmware files

```
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```

Extract the archive

```
tar xjf broadcom-wl-4.150.10.5.tar.bz2
```

Change to the driver directory

```
cd broadcom-wl-4.150.10.5/driver
```

Install the firmware

```
b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

Then blacklist the proprietary driver

```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist.conf
```

And finally..............RESTART!!!




I hope this worked for you. It worked for me. 

By the way, I'm turning 14 on September 26, so wish me a happy birthday :)

---

### Post by chenxiaolong on 2009-12-01
Try booting with kernel option "... blacklist=b43". This will stop the driver from loading and you will be able to boot your system. You might want to try updating the computer after it boots. I've never seen that problem before (it doesn't even have an error message). I don't know much about error logs and what to look for, so maybe someone else can help you.

---

### Post by jsfour on 2009-12-02
Hey guys, I have everything loaded up correctly and have blacklisted the modules described in the first post.

I only have 1 problem:

```
modprobe b43
```
Starts the module and lets me wifi fine... But I need to do this every time I reboot....

Does anyone know how to fix this? There must be a way to have this load at boot.

---

### Post by chenxiaolong on 2009-12-02
Add the module to /etc/modules to make it load on startup.

```
echo "b43" | sudo tee -a /etc/modules
```

---

### Post by jsfour on 2009-12-02
> **chenxiaolong said:**
> Add the module to /etc/modules to make it load on startup.

```
echo "b43" | sudo tee -a /etc/modules
```

That worked...

Your the bomb...

---

### Post by leorolla on 2009-12-03
I have

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

I couldn't get b43 working in Karmic and I am using the proprietary  Broadcom STA wireless driver.

Is there any functional advantage of b43?

I don't have my LED working for instance. Does b43 fix that?

---

### Post by chenxiaolong on 2009-12-03
The b43 driver has the monitor mode feature, which isn't useful unless you go around the neighborhood cracking peoples' WEP networks:D. For the LED issue, are you using an HP? I'm pretty sure HP has a modification in the Windows driver for the wlan card because that was the case on my mom's HP laptop.

---

### Post by georg.65 on 2009-12-04
Hi chenxiaolong,

I'm here again, 

i've the same problem with my small netbook lenovo s10-2 to install the b43 driver, still the broadcom bcm4312.

Here is the output 

orion@orion-laptop:~$ lspci -vnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]

It looks a little different with the subsystem.

I'm runnig the command from your post  

sudo apt-get install linux-backports-modules-karmic b43-fwcutter
when I would like to activate the b43 driver i cant't do it, i'm doing the same commands, it must be something with this 

Subsystem: Broadcom Corporation Device [14e4:04b5] 

For my Compaq notebook where you do it for me everythink works very well.

thanks georg

---

### Post by leorolla on 2009-12-04
No, mine is an Acer Aspire One D 150.

You know how I can get LED working?

Thanks!

---

### Post by chenxiaolong on 2009-12-04
Georg.65, could you try running these command and then restart the computer?

sudo rmmod b43 ssb wl
sudo depmod -a

And leorolla, the wireless LED not working is a known problem in the latest linux kernel. According to some research, the only distros it worked on was Fedora 9 and Ubuntu 8.10 Intrepid.

---

### Post by georg.65 on 2009-12-04
Here is the output

orion@orion-laptop:~$ sudo rmmod b43 ssb wl
[sudo] password for orion: 
ERROR: Module wl does not exist in /proc/modules
orion@orion-laptop:~$ sudo depmod -a
orion@orion-laptop:~$ 

After i'm rebooting still can't activate b43 driver

---

### Post by chenxiaolong on 2009-12-04
Can you see if there is a :

blacklist b43

OR

blacklist ssb

in any of the files in /etc/modprobe.d/?

If so, comment it out.

---

### Post by georg.65 on 2009-12-04
In /etc/modprobe.d 

i d'ont found any  *blacklist b43 OR blacklist ssb* files 

only in the file *blacklist.conf* i found this command 

blacklist bcm43xx

need to comment it out ?

---

### Post by chenxiaolong on 2009-12-05
No, leave the *blacklist bcm43xx* blacklisted. What I meant by my previous post was to look inside all the files in /etc/modprobe.d for *blacklist b43* and *blacklist ssb*. If there isn't any line that says that, try running (and post the output here):

```

sudo modprobe b43
dmesg | grep b43

```

---

### Post by limaunion on 2009-12-05
hi all! I've just successfully switched from ndiswrapper to b43 after reading this thread. The only weird behaviour i'm having is that the transfer speed is quite low compared to ndiswrapper. I remenber having transfer speeds of around 20Mbps and now it hardly reaches 3Mbps under the same circunstances.

Here's some information about my network card:

04:00.0 0280: 14e4:4315 (rev 01)
	Subsystem: 103c:137c

For some reason I've found that wlan0 has switched its speed 
from: Bit Rate=48 Mb/s Tx-Power=20 dBm 
to: Bit Rate=1 Mb/s Tx-Power=20 dBm   

Does anyone know if this a known issue ? 
TIA

---

### Post by chenxiaolong on 2009-12-05
Limaunion, the speed issue is a known problem and it's going to be fixed by kernel 2.6.32. 

By the way, what Windows driver did you use for ndiswrapper? It never worked for me. Also, do you mean 20 megabytes or megabits per second? I can barely get 1.5 megabytes per second with any OS or driver :D

---

### Post by limaunion on 2009-12-05
> **chenxiaolong said:**
> Limaunion, the speed issue is a known problem and it's going to be fixed by kernel 2.6.32. 

By the way, what Windows driver did you use for ndiswrapper? It never worked for me. Also, do you mean 20 megabytes or megabits per second? I can barely get 1.5 megabytes per second with any OS or driver :D

Ok, glad to know that it's a known issue, but I'm already running 2.6.32 (I use to follow vanilla kernel), thus it seems that this issue it's not fixed yet. :(

I don't know precisely what ndiswrapper driver I was using but as far as I can remenber i donwloaded it from HP support website. Actually, today after I confirmed that this other alternative works I've uninstalled from my notebook all the ndiswrapper packages.

I mean 150 KBytes/s (~15Mbits/s) and 2 MBytes (~20Mbits/s).
Thanks.

---

### Post by georg.65 on 2009-12-05
today i'm looking one time more in /etc/modprobe.d in all the files for *blacklist b43* and *blacklist ssb* and i d'ont found them.

chenxiaolong here is the output, maybe now you now what is the problem

orion@orion-laptop:~$ sudo modprobe b43
[sudo] password for orion: 
orion@orion-laptop:~$ dmesg | grep b43
[    2.702224] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.702251] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   14.913052] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   15.261935] Registered led device: b43-phy0::tx
[   15.261996] Registered led device: b43-phy0::rx
[   15.262059] Registered led device: b43-phy0::radio
[   15.457410] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   15.858076] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   15.951294] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   15.951480] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   15.951651] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   16.164125] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   16.238466] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   16.300861] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   16.300874] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   16.300883] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
orion@orion-laptop:~$

thanks georg

---

### Post by chenxiaolong on 2009-12-05
Ohh. So it's missing the firmware files. Try running this command and choose yes when it asks you to fetch the firmware:

```
sudo dpkg-reconfigure b43-fwcutter
```

---

### Post by georg.65 on 2009-12-06
This was the problem chenxiaolong, 

i'm activated the driver and can see the networks at network manager now.

yes i forgot to fetch the firmware when i'm installing the b43-fwcutter the first time.

thanks again

> Limaunion, the speed issue is a known problem and it's going to be fixed by kernel 2.6.32. 
Yes when i'm using the wl driver the speed was a little better, but still is ok with b43.

I hope that other people that have the problem with b43 will found this thread that have now over 22 000 clicks.


thanks and see you, georg

---

### Post by shakty on 2009-12-06
I have a macbookpro 5.1 + Karmic. 

I had the problem described here: 

[http://ubuntuforums.org/showthread.php?p=8449681#post8449681](http://ubuntuforums.org/showthread.php?p=8449681#post8449681)

My network controller is Broadcom Corporation **BCM4322** 802.11a/b/g/n Wireless LAN Controller (rev 01), which is different from the **(Broadcom bcm4312 rev 01)**

If you try to update the firmware, not surprisingly, it does not work at all and moreover it created a conflict with the proprietary NVIDIA driver, and lead the system to instability. So don't do that! :)

Btw, can anybody suggest me anything? I am rather new to Ubuntu. Thanks!

---

### Post by limaunion on 2009-12-06
Today I've been testing the network speed using the b43 driver and in spite of the advertised speed by 'iwconfig wlan0' that is 'Bit Rate=1 Mb/s', I'm getting the following results:

$ iperf -c debian1 -t 30 -f K
------------------------------------------------------------
Client connecting to debian1, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.5 port 49592 connected with 192.168.1.2 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-30.1 sec  34888 KBytes  1161 KBytes/sec
 
It's not so bad but I hope that someone will fix this in the near future albeit that this problem has a long history: [https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/201225](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/201225)

---

### Post by chenxiaolong on 2009-12-06
Sorry shakty, but the b43 driver won't work with your wireless card as wireless N cards aren't supported yet. And from the thread that you linked to, the wl driver isn't working well either. The only thing I can suggest is to download and compile the Broadcom STA (wl) driver from Broadcom's website: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

BTW, if you need help, could you PM me instead of posting in this thread? It would nice to keep it on-topic.

---

### Post by stigb on 2009-12-06
Hi, I just posted this thread [http://ubuntuforums.org/showthread.php?p=8450418](http://ubuntuforums.org/showthread.php?p=8450418) and I followed this tutorial (on page 1) afterwards. There is no change at all, as far as I can see. At least the wireless still does not work. Info about my system is in my thread.

---

### Post by chenxiaolong on 2009-12-06
Stigb, you either want to use the driver in the other thread or the driver in this thread. You definitely don't want to use both. I posted instructions in the thread you linked to, so you can take a look at that.

---

### Post by daedalus317 on 2009-12-16
Damn, I'm having issues with this, my wireless card and the drivers are not talking talking nicely with each other. 

Let me start with I have a HP mini 311 and it has a bcm4312 wireless card and it is running ubuntu 9.10 with a kernel of 2.6.31-16. I can get it to connect fine using the broadcom-std drivers, but that leaves me without the ability to be able to place the card in "monitoring" or "injection" modes. 

I have study and tried what everyone in this thread has which it seems to be a hit or miss results. I really don't think I'm that dense to not get it, but google is not being my friend on this topic. 

As far as I can tell, the driver I need to get to play correctly is the b43 driver. I'll give another shot and post the results tonight.

Daedalus

[B][COLOR=Red]-------------------------------------------------------------------------------------------------------

[COLOR=Black]Please ignore the above I got the driver working.

Sorry about this.

Daedalus
[/COLOR][/COLOR][/B]

---

### Post by DarkAngel88 on 2009-12-18
Hi, following the instructions from the first post, I'm getting the following error after using the card for a bit (downloading a big file) or even when putting the card in monitor mode "sudo airmon-ng start wlan0"

```
[  387.405222] b43-phy0: Controller RESET (DMA error) ...
[  387.624315] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  393.137165] b43-phy0: Controller restarted
[  393.137348] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
```

And I have to reboot the machine to get wireless to work again...

Please help me!

Edit: Forgot to say, light turns orange when this is happenning...

---

### Post by msrk on 2009-12-20
Hi,
Thank you to all those that have contributed.

I have a Dell Inspiron 2200 with Ubuntu Karmic 9.10 kernel Linux 2.6.31-16-generic and followed the instructions on this thread. The b43 driver worked really well with my internal wireless card until last week.  On November 16th it stopped immediately following a reboot after running the Update Manager. I tried both the gnome manager and wicd.  With wicd it states "No wireless netorks found".

I tried removing the backports module and reinstalling it.  That did not work.  My theory is that the card is not getting turned on.  I'm pretty sure there were some kernel updates in the updates I got last week.

Please advise.

---

### Post by chenxiaolong on 2009-12-20
Could you post the output of these commands:?

dmesg | grep b43
ls /etc/modprobe.d | grep b43
ifconfig
iwconfig
sudo iwlist scan
lsmod | grep b43
lsmod | grep wl
lsmod | grep ssb

You might want to paste them into a text file and attach the text file here.

---

### Post by msrk on 2009-12-20
ms@ubuntubook:~$ dmesg | grep b43
[    1.757038] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   16.734452] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   16.813963] Registered led device: b43-phy0::tx
[   16.813986] Registered led device: b43-phy0::rx
[   16.814012] Registered led device: b43-phy0::radio
[   17.420127] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   17.721400] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   17.867545] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   17.925564] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   18.277091] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   18.360676] b43-phy0: Radio hardware status changed to DISABLED
[   18.384702] b43-phy0: Radio turned on by software
[   18.384710] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
ms@ubuntubook:~$ ls /etc/modprobe.d | grep b43
ms@ubuntubook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:05:99:c3  
          inet addr:192.168.1.26  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe05:99c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21984020 (21.9 MB)  TX bytes:526694 (526.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ms@ubuntubook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ms@ubuntubook:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ms@ubuntubook:~$ lsmod | grep b43
b43                   163812  0 
mac80211              210408  1 b43
cfg80211              130440  2 b43,mac80211
led_class               4096  1 b43
ssb                    44868  1 b43
pcmcia                 36808  2 b43,ssb
pcmcia_core            35792  5 b43,yenta_socket,rsrc_nonstatic,ssb,pcmcia
ms@ubuntubook:~$ lsmod | grep wl
ms@ubuntubook:~$ lsmod | grep ssb
ssb                    44868  1 b43
pcmcia                 36808  2 b43,ssb
pcmcia_core            35792  5 b43,yenta_socket,rsrc_nonstatic,ssb,pcmcia
ms@ubuntubook:~$

---

### Post by DarkAngel88 on 2009-12-20
> **DarkAngel88 said:**
> Hi, following the instructions from the first post, I'm getting the following error after using the card for a bit (downloading a big file) or even when putting the card in monitor mode "sudo airmon-ng start wlan0"

```
[  387.405222] b43-phy0: Controller RESET (DMA error) ...
[  387.624315] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  393.137165] b43-phy0: Controller restarted
[  393.137348] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
```

And I have to reboot the machine to get wireless to work again...

Please help me!

Edit: Forgot to say, light turns orange when this is happenning...

.... Am I the only one with this problem??  Can't anyone help?

---

### Post by chenxiaolong on 2009-12-20
Msrk, does your computer have a wireless switch or button? According to dmesg, the wireless card is turned off by the hardware: "The hardware RF-kill button still turns the radio physically off. Press the button to turn it on."

---

### Post by DarkAngel88 on 2009-12-20
chenxiaolong, didn't you had the same problem as mine before?  About the card going off by itself when downloading big files and intensive usage?  Only thing, my card is internal and I can't reset it...  Please advise.

---

### Post by msrk on 2009-12-20
chenxiaolong thank you.  From your postings I learned that iwconfig tells me if the net card is on or off.  Yes, the F2 toggle got it going, duh!  However, I was able to change a bios setting so that sofware applications can control the cards power rather than the F2 key.  Now it starts nicely on boot.

Thank you.

---

### Post by amigec on 2009-12-20
Hi, I have problems with BCM4312 driver, I followed your steps but it seems doesnt work. Im total linux noob so can somebody guide me what to do? I tried Broadcom STA drivers and then it works but i dont have monitor mode. When I activate BCM4312 fwcutter then after reboot OS wont load. Please help me, I have Broadcom b/g device.

---

### Post by chenxiaolong on 2009-12-20
You're welcome. 

DarkAngel88: Yes, I had the same problem before. Mine is an internal card also. To reset mine, I had to physically take out the card, touch all the pins to reset the card's RAM, and then put it back in.

---

### Post by amigec on 2009-12-20
Weird thing is that bluetooth works but wireless dont, and they are on same chip.

---

### Post by chenxiaolong on 2009-12-20
My Dell Studio 1555 has the bluetooth chip is in a different slot than my wireless card.

---

### Post by Hrcko2003 on 2009-12-20
Can someone HELP ???

I install Ubuntu 9.10 and falov your steps to install b43 drivers:

This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic. 
 
1. Open up Terminal. 
 
2. Install the "linux-backports-modules-karmic" (newer wireless drivers from compat-wireless) package and the "b43-fwcutter" package (wireless firmware). During installation, if it asks you to fetch the firmware automatically, make sure you select yes. 
       Code: 
       sudo apt-get install linux-backports-modules-karmic b43-fwcutter
3. 
      Blacklist the ssb module. 
      Code: 
      echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
4. 
      Blacklist the wl module. 
      Code: 
      echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
5. Reboot 
6. Enjoy your wireless!!!

End when I reset laptop everything vorks great. WICD show wireless networks and can conect,
I can put card in monitor mod and airodump-ng vorks great and can capture packages but THEN WHEN I RESTART LAPTOP THERE IS NO MORE WIRELESS CARD IN WICD ??

dmesg
00, 0x00000000, 0x00000000, 0x00000000
[  783.912763] b43-phy0: Controller RESET (DMA error) ...
[  784.128341] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  789.661266] b43-phy0: Controller restarted
[  789.661312] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  789.661320] b43-phy0: Controller RESET (DMA error) ...
[  789.876295] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  795.473379] b43-phy0: Controller restarted
[  795.484373] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  795.484383] b43-phy0: Controller RESET (DMA error) ...
[  795.700281] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  801.249353] b43-phy0: Controller restarted
[  801.249407] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  801.249415] b43-phy0: Controller RESET (DMA error) ...
[  801.464462] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  806.997224] b43-phy0: Controller restarted
[  807.008283] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  807.008294] b43-phy0: Controller RESET (DMA error) ...
[  807.224460] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  812.821157] b43-phy0: Controller restarted
[  812.821913] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000400, 0x00000000, 0x00000000
[  812.821922] b43-phy0: Controller RESET (DMA error) ...
[  813.044260] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  818.577347] b43-phy0: Controller restarted
[  818.588534] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  818.588544] b43-phy0: Controller RESET (DMA error) ...

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
pan0      no wireless extension


CAN SOMEONE HELP PLEASE ??

---

### Post by DarkAngel88 on 2009-12-21
> **chenxiaolong said:**
> You're welcome. 

DarkAngel88: Yes, I had the same problem before. Mine is an internal card also. To reset mine, I had to physically take out the card, touch all the pins to reset the card's RAM, and then put it back in.

Have u fixed this issue since u had this problem?

---

### Post by chenxiaolong on 2009-12-21
The only way to fix the DMA error is to physically take the card out of the computer, touch all the pins to reset the card's RAM, and then put it back in.

EDIT: DarkAngel88: No it hasn't been fixed yet. It should be fixed by kernel 2.6.32. The problem is caused by the firmware being incorrectly loaded on the card, therefore, the card's RAM has to be reset.

---

### Post by Hrcko2003 on 2009-12-21
Tnx for that.
 
But I still dont understand, sometimes everything works great.
 
I reset laptop and works and then reset it again and dont work... no roule...
 
Dont know why...
 
How can i translate ASCII code ??
 
The aircracker-ng if I am not wrong gives me the KEY in ASCII cod and when I put it in windows 7 I cant conect !
 
Any idea ??

---

### Post by chenxiaolong on 2009-12-21
Well, there's problems because the b43 driver is still is development stage. You can use the wl (Broadcom STA) driver if you want it stable. About the ASCII code: ASCII is plain text. This post is ASCII, for example. It should work if you typed it in correctly.

---

### Post by raikou on 2009-12-21
Hello everyone,

I have the 14e4:4315 card on my Lenovo G550 laptop.
It runs fine with the wl driver.
I can install the b43 driver, but it then stops seeing my device (eth1) which is a wireless card.
my kernel is 2.6.28-17 and i've tried installing compat-wireless-2.6 but it has problems when entering the header folders and i can't do a make.

Is there a possibility that the wireless card itself physically cannot support monitor mode/scanning?

---

### Post by chenxiaolong on 2009-12-21
3 things:

1. b43 sees the wireless card as wlan0
2. The new b43 driver requires kernel 2.6.31 or newer. The compat-wireless version is NOT the new version. If you scroll down on the b43 page, it will give you a chart of the versions --> the version you want is the one that supports LP-PHY cards.
3. The 14e4:4315 card definitely supports monitor mode. I've done it before.

---

### Post by raikou on 2009-12-21
Oh..
I have never had a wlan0 show up in my devices.
Yeah I think I might have to upgrade to karmic to get the newer kernel.

What do you mean the compat-wireless is not the new version?
on the b43 page on linuxwireless.org
if you go to this link: [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp)
it says compat-wireless-2.6

i'm relieved that the card supports monitoring. i will have to keep trying to fix this :(

---

### Post by chenxiaolong on 2009-12-22
Sorry, I misread that page. I guess the b43-fwcutter and the firmware is newer. Anyway, in Jaunty, I could never get compat-wireless to compile.

---

### Post by raikou on 2009-12-22
> **chenxiaolong said:**
> Sorry, I misread that page. I guess the b43-fwcutter and the firmware is newer. Anyway, in Jaunty, I could never get compat-wireless to compile.

I see.

Well lastnight I made some progress.
I upgraded to Karmic but my display was not working. 
This was fixed by adding i915.mode=0 onto the kernel line in one of the boot options in grub.

After booting into 9.10, 2.6.31-17, I managed to install the b43 driver and have wlan0 show up as my wireless device.
I can see networks in managed mode, however I cannot connect to them (it begins to connect but then disconnects).

As a side note, Kismet is also now working which means that I am able to switch my card into monitor mode, which is great.
However it can't pick up any networks including my own one at home, but a wired connection works.

Did you have the same problem?

---

### Post by chenxiaolong on 2009-12-22
No, mine is working fine (except when too much bandwith is being used). Are you installing the b43 driver that you compiled in the previous kernel, or did you recompile it. Right now, I'm using the Ubuntu-packaged version of compat-wireless (linux-backports-modules-karmic), but I'll test the linuxwireless.org version and see how it goes:D.

---

### Post by raikou on 2009-12-22
i used b43-fwcutter for the driver I think, if that is what it infact does :\

---

### Post by chenxiaolong on 2009-12-22
Which version of compat-wireless did you download? I downloaded the compat-wireless-2009-12-11.tar.gz version and it doesn't compile for me.

---

### Post by raikou on 2009-12-22
> **chenxiaolong said:**
> Which version of compat-wireless did you download? I downloaded the compat-wireless-2009-12-11.tar.gz version and it doesn't compile for me.

After installing Karmic I simply used the instructions at the top of the first post of this thread, I didn't get compat-wireless drivers involved (that I know of)
however I do have a compat-wireless-2009-12-11.tar.gz on my desktop that i was trying to use in Jaunty.
Does this now work in Karmic? If not, which version of compat-wireless should I go get?

---

### Post by chenxiaolong on 2009-12-22
The compat-wireless-2009-12-11.tar.gz does NOT work in either Jaunty or Karmic. If you followed my directions in my first post, you don't need compat-wireless at all. It should work.

---

### Post by raikou on 2009-12-22
> **chenxiaolong said:**
> The compat-wireless-2009-12-11.tar.gz does NOT work in either Jaunty or Karmic. If you followed my directions in my first post, you don't need compat-wireless at all. It should work.

Ah...
I think the reason it hasn't worked for me was because it never asked me "Do you want to fetch the firmware"
Because i've installed it before in Jaunty.
How do I get the fwcutter to run through the set up again to fetch the firmware?

---

### Post by chenxiaolong on 2009-12-22
You have to remove or rename these folders (apt-get will download them again):

[COLOR="DarkOrchid"]/lib/firmware/b43
/lib/firmware/b43legacy[/COLOR]

Then run [COLOR="Red"]sudo apt-get remove --purge b43-fwcutter[/COLOR] or select Completely Remove for [COLOR="SeaGreen"]b43-fwcutter[/COLOR] in Synaptic. 

Then install b43-fwcutter again and it will ask you if you want to fetch the firmware.

---

### Post by amigec on 2009-12-24
I installed Xubuntu 9.10 and b43-fwcutter package in Synaptic and it asked me to fetch a firmware, I selected yes and restarted. First time it couldn't boot so I reset my laptop and second time boot was successful. But when there's not wlan0 device in ifconfig and when i type lspci -v under BCM4312 it says 
Kernel driver in use: b43-pci-bridge 
Kernel Modules: ssb
I blacklisted ssb module but its always in use. What to do?

---

### Post by chenxiaolong on 2009-12-24
Don't blacklist the [COLOR="SeaGreen"]ssb[/COLOR] module. B43 uses it to determine which wlan card you have. Also, does [COLOR="SeaGreen"]iwconfig[/COLOR] show [COLOR="SeaGreen"]wlan0[/COLOR]?

And could you post the output of [COLOR="SeaGreen"]dmesg | grep b43[/COLOR]?

---

### Post by amigec on 2009-12-24
iwconfig doesnt show wlan0, and here is the output of dmesg | greb b43
[    3.049983] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.049998] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   10.650384] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   10.692903] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[   10.692947] b43: probe of ssb0:0 failed with error -95

---

### Post by chenxiaolong on 2009-12-24
You didn't install the package [COLOR="SeaGreen"]linux-backports-modules-karmic[/COLOR]. Install it by running:

[COLOR="SeaGreen"]sudo apt-get install linux-backport-modules-karmic
sudo depmod -a[/COLOR]

and then reboot.

---

### Post by The Glidd on 2009-12-24
I'm afraid my wireless is a mess.  I've tried many solutions (lately, the one at the beginning of this thread) with no result.

I Recently upgraded to 9.1.  Wireless worked for a bit, but after a restart it vanished. 

I Installed bcml.kernel, fw-cutter, etc.

Broadcom STA shows up under Admin>Drivers>Hardware Drivers, it reads:

"This driver is not activated"

I try and activate with no result.  No other drivers show up.

Along with all this, network manager detects no wireless at all.  I know the wireless is on; it works fine in the Vista partition.

Here are some terminal results:

**lspci:**

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

**iwconfig:**

lo        no wireless extensions.

eth0      no wireless extensions.

**ifconfig:**

eth0      Link encap:Ethernet  HWaddr 00:25:64:49:af:58  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe49:af58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1398660 (1.3 MB)  TX bytes:283242 (283.2 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1471354 (1.4 MB)  TX bytes:1471354 (1.4 MB)

Any help would be appreciated!

---

### Post by amigec on 2009-12-26
Merry Christmass to all. Thanks to [chenxiaolong]("http://ubuntuforums.org/member.php?u=724117") I succeeded to get my wireless half working, now i can see wlan0 in ifconfig. BUT when i want to scan it says device is busy. Output of dmesg | grep b43 says FATAL DMA ERROR. So i read that I must reset my wlan chipset, but I have button to turn wireless of and on, so can I reset it by that button? If not, then I must take out the card and touch all pins? How? Touch all pins with screwdriver to make short circuit of all pins?

---

### Post by chenxiaolong on 2009-12-26
Unfortunately, you can't reset the card with the wireless button. The wireless button controls whether the card is on or not, but to reset it, the firmware on the card has to be reset.

---

### Post by amigec on 2009-12-26
Ok, i removed wlan module and connected all pins with my screwdriver, is that enought or I must remove shielding on card and then touch some pins?

---

### Post by chenxiaolong on 2009-12-26
No, definitely don't remove the shielding. Touching the pins with the card out is good.

---

### Post by amigec on 2009-12-26
I did that, and problem is still here.:(

---

### Post by chenxiaolong on 2009-12-26
I don't what to say. That's all I had to do to fix it on my computer. :(:confused:

---

### Post by amigec on 2009-12-26
I dont know where is problem, I blacklisted b43 driver from loading on startup because sometimes it wont boot. When it boot I typed modprobe b43 to load driver. Driver loaded successfully and I can connect to my AP, I have IP adress but i cant access Internet. When I want to put card in monitor mode, it stops working after 10 seconds and dmesg | grep b43 says DMA error, then my system freeze. I tryed reset wlan module 3 times, I think I'll buy another wireless card.
EDIT: dmesg | grep b43 says 
[  812.821913] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000400, 0x00000000, 0x00000000
[  812.821922] b43-phy0: Controller RESET (DMA error) ...
[  813.044260] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  818.577347] b43-phy0: Controller restarted

Can I load some other firmware version? Maybe this is too old.

---

### Post by Kevinlittleton on 2009-12-26
Hi guys, I'm a total newbie to Ubuntu and Linux and I have a problem with my wireless connection. 

When I first installed Ubunutu 9.1 I had to play around with installing a driver for the wifi card. I went with Broadcom STA wireless card which is properitery. It worked for a few days but now it won't connect to a network. It will ask for the network key but after that it does nothing. 

I tried to disable and reinstall and now it's giving me this:

Please have a look at the log file for details: /var/log/jockey.log

Any ideas?

---

### Post by amigec on 2009-12-26
Here is something promising but I dont know how to patch that, can someone help me?
[http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html](http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html)

---

### Post by focwiz on 2009-12-26
> **The Glidd said:**
> I'm afraid my wireless is a mess.  I've tried many solutions (lately, the one at the beginning of this thread) with no result.

I Recently upgraded to 9.1.  Wireless worked for a bit, but after a restart it vanished. 

I Installed bcml.kernel, fw-cutter, etc.

Broadcom STA shows up under Admin>Drivers>Hardware Drivers, it reads:

"This driver is not activated"

I try and activate with no result.  No other drivers show up.



Glidd,

Have you tried activating the STA driver while connected to the internet (wired)?  That's what I had to do to activate it.

Kevin

---

### Post by chenxiaolong on 2009-12-28
Kevinlittleton, could you attach the [COLOR="DarkOrchid"]/var/log/jockey.log[/COLOR] file to a new post? I have no way to access your computer to get the file :).

---

### Post by emas80 on 2009-12-29
> **amigec said:**
> Here is something promising but I dont know how to patch that, can someone help me?
[http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html](http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html)

Hi, thank you, you find probably the cause of this problem! 

The bad news is that the problem is not (totally) solved.
[http://lists.berlios.de/pipermail/bcm43xx-dev/2009-December/006536.html](http://lists.berlios.de/pipermail/bcm43xx-dev/2009-December/006536.html)

That is the mailing list of driver's developer, they found the problem months ago and they finally half-fixed creating a patch that should be applied to driver's source code.

I said half-fixed because they really don't know what is causing the DMA problem, but, if you search througth the mailing list, you can discover that they isolated it and they could reproduce it (and solve! after a sequence of operations like reboot, loading wl driver, cold reboot.. ecc. ecc.. I got the wifi working by doing these apparently *random* things).

By now, the only way to get the card working is, as I wrote, to patch the source with that code, and then loading b43 module in PIO mode, slower than DMA mode (I don't really know what's the difference). The patch won't be included in 2.6.33 kernel, maybe in 2.6.34 kernel.

Maybe later this night I will try to do that stuff.

---

### Post by chenxiaolong on 2009-12-29
That's very good info you found! :D Could you post back with your results?

---

### Post by emas80 on 2009-12-29
Hi all!

I successfully patched b43 driver sources with info found on b43 developer's mailing list!
I'm writing using wireless connection :cool:. 
I loaded (and surfed with!) the new driver three times, and this time I booted directly with which will be my new default configuration and it seems to work.

To make the wifi card working, you should be able to recompile a linux kernel, and you should know what a kernel module is. Please take attention, read twice, and ALWAYS make backup before to modify something - if you don't know what you are doing, ask before doing damage to your system, someone will help.

I'm currently using b43 open source driver (shipped with linux "vanilla" kernel), with b43-fwcutter Ubuntu firmware. 

Here are my instructions to get things done:

[LIST=1]
[*]Patch driver's source files. I made a .tar with my driver's source file directory (<your kernel sources>/drivers/net/wireless/b43): in my .tar, there are source files *already patched* (that are to be compiled) together with a patch/ directory containing original files and all the patches. You can see patch-rejected results, changes have been merged by hand, I hope I didn't make too many mistakes.:)Take attention: I used vanilla kernel 2.6.32.2, currently Ubuntu kernel is 2.6.31-17, I'm really sorry but the patch, as far as I read on the mailing list, should be applied to 2.6.32 kernel. I didn't even try Ubuntu kernel, I like to have last vanilla kernel, and also I read on[ linuxwireless.org]("http://linuxwireless.org/en/users/Drivers/b43") that my Broadcom card *should* function with this kernel (it didn't). I don't know if the patch applies also to previous kernel, by reading the site probably NOT, but you can just try, remember ALWAYS to backup EVERYTHING that is supposed to be modified.
[*]Recompile the kernel - really safe - if you know what you are doing. Or ... why don't recompile only the module?!? Please take attention, this procedure is not difficult, but if you don't know what you are doing you can damage your running kernel, so TAKE THIS AT YOUR OWN RISK - and don't try this at work :)!  There is a simple instruction, go in your kernel source directory and type 
```
make modules SUBDIRS=drivers/net/wireless/b43
```                   This will recompile just b43 module, so in drivers/net/wireless/b43 directory you should found a shiny new b43 module. If you now type ```
modinfo drivers/net/wireless/b43/b43.ko
``` you should have a little different result than giving a simple ```
modinfo b43
``` (if you have a b43 module). Yes, the last line show a new parameter, a "pio" parameter, in the recompiled driver.
[*]If you recompiled the kernel, all is fine, just go to next step, kernel modules are already at the right place. Else, you should copy the new b43.ko in current kernel module directory. The fastest way is to simply copy the new file in /lib/modules/<your kernel>/kernel/drivers/net/wireless/b43, AFTER previous file was renamed (remember: BACKUP). After a reboot, the new module should be loaded instead of the old one - don't reboot right now, there is a last step.
[*]I said there is a new parameter, "pio" parameter. This param forces pio mode instead of dma mode, causing no more dma errors. Great! We should pass the new parameter to the new kernel module, when the module is loaded. In Ubuntu-boot, you can accomplish that by creating a new file, let's call b43.conf, in /etc/modprobe.d/ directory. While booting, Ubuntu will read that dir and will execute commands (= pass to kernel) contained in all found files. Our file will contain only a simple instruction: ```
options b43 pio=1
```. Take attention: after you created this file, whatever kernel you will use, "pio" parameter WILL ALWAYS be passed to b43 module. If the module cannot understand the parameter, simply it won't be loaded, causing an error message being displayed. e.g. If you boot with a kernel with an "old" (different?) version of b43 - 2.6.31-17. Remember the dir in which you "copied" b43.ko? Only that kernel will load b43 module, you should empty b43.conf file to make other kernel's b43 modules loading - other kernels modules are still intact in ther /lib/modules/<other kernel>/kernel/drivers/net/wireless/b43 directories!
[*]That's all. After a reboot your wifi should be activated and you could see wifi networks surrounding you. No more DMA problem. I read that probably the connection should be slower than DMA-normal one, but a slow connection is better than no connection. B43 guys have been busy for over 1 month on this problem, I hope they will solve it soon.
[/LIST]
Hope it helps, remember to ask for help if something is not clear.
I really thank Larry Finger and Michael Buesch, the work is definitely THEIR work, and of all b43 developer guys.

Bye!

Emanuele

---

### Post by chenxiaolong on 2009-12-29
Great news, emas80!!! :D:D:D May I paraphrase your HowTo in my first post (of course I'm going to credit you)? I'll also make a script for beginners if that's okay with you. I'll try recompiling the module with the patch tomorrow. I'm really tired right now (I've been trying to control my Lego Mindstorms NXT with a WiiMote, but NXT does not go well with Linux).

---

### Post by goslings on 2009-12-30
Brillant :):)
Every time i've upgraded Ubuntu the B43 NEVER works out of the box;
This solution above worked for me - Why o why is in not part of the upgrade facility ?!?!?!

> **stats said:**
> For those of you who use karmic, compat-wireless need not be compiled. 
```
sudo apt-get install linux-backports-modules-karmic linux-backports-modules-wireless-karmic-generic b43-fwcutter 
```
is enough. 
Then do 
```
sudo modprobe -r wl
sudo modprobe b43
```
and you're done. If it works and you want to make the change permanent :
First, blacklist the wl module
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Then
```
gksudo gedit /etc/modules
```
and add 
```
b43
```
to the end of the file

---

### Post by goslings on 2009-12-30
Ah - not quite - not permanent after reboot
also noticed that 
"sudo modprobe -r wl"
"sudo modprobe b43"
failed with 

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module wl not found.

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

I'll scan earlier in the post - but if anyone any ideas ...
thanks 
Ian

---

### Post by emas80 on 2009-12-30
Hi, 
This morning, I booted my note and wifi is still working! Great! 

Yes you can do whatever you think is good to share it, I spent two days looking for a solution and I really hope my work will help who is stuck with dma problem.
Unfortunately, your good how-to didn't work for me, not even with older kernel release, maybe because of my particular wifi card, as I read on linuxwireless.org.
I will write to b43 developer mailing list, telling their patch is working for me.

Lego Mindstorms.. I'm really going to try "playing" with them, sooner or later.. :-)

---

### Post by emas80 on 2009-12-30
Hi, what do you mean with "not permanent"?
Here is my explanation for errors you reported:

> **goslings said:**
> Ah - not quite - not permanent after reboot
also noticed that 
"sudo modprobe -r wl"
"sudo modprobe b43"
failed with 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


This is only a warning :), it tells you that ndiswrapper should be renamed to ndiswrapper.conf, otherwise future releases could ignore its content.
In Ubuntu, while booting kernel, all files in /etc/modprobe.d/ are read and "executed", and this is used to blacklist some modules, or to pass parameters to loaded modules.
You can see the content of the files in that directory to better understand what they are useful for.

> 
FATAL: Module wl not found.
This tells that no wl module was found as loaded, didn't you add it to blacklist :)? If so, obviously it has not been loaded!

What's the output of following command ```
lsmod | grep b43
``` after a reboot? Is b43 module loaded? ```
ifconfig
``` or ```
iwconfig
```?

Why do you have a "ndiswrapper" configuration file? Maybe in the past you tried to use ndiswrapper to make your card working? 
You shouldn't "mix" various howto's together, because you get confused, and your system gets confused too :).
I didn't try ndiswrapper, I don't know how to make it works, or how to remove it, maybe you can google for it, or someone could help you reinstalling or removing it.

---

### Post by goslings on 2009-12-30
> **emas80 said:**
> Hi, what do you mean with "not permanent"?
i.e after a reboot it looses all wireless 

> **emas80 said:**
>  What's the output of following command ```
lsmod | grep b43
``` after a reboot? Is b43 module loaded? ```
ifconfig
``` or ```
iwconfig
```? 

```
 Nothing from lsmod | grep b43
op from iconfig:

eth0      Link encap:Ethernet  HWaddr 00:0c:6e:12:71:f6  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe12:71f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3927342 (3.9 MB)  TX bytes:564320 (564.3 KB)
          Interrupt:17 Base address:0x9800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```
```
 op from iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

```
Seems not to being made permanent 
thanks for your help
Ian

---

### Post by goslings on 2009-12-30
got rid of ndiswrapper
lspci | grep BCM report 
```
 00:0e.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 
```

---

### Post by chenxiaolong on 2009-12-30
Emas80, I was able to create a working patch from by using [COLOR="DarkOrchid"]diff[/COLOR] between your patched files and my original files. I just did a test run on a copy of the original and it patched without errors. I'm writing a script right now and I'll edit my first post later on. Again, thanks for your help and testing.:D

---

### Post by emas80 on 2009-12-30
> **goslings said:**
> got rid of ndiswrapper
lspci | grep BCM report 
```
 00:0e.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 
```
Hi, so you are now in situation where you installed b43 module, b43 firmware and blacklisted wl module.
You said that wifi worked after following the procedure some posts ago, but after rebooting it stopped working. Probably this is because b43 module is not loaded, so if you try```
sudo modprobe b43
``` it should work, or at least ifconfig/iwconfig should show the new interface. 
If this is the case, please check that in /etc/modules the line about b43 module is present, and that no line about specifically "ssb" or "b43" is present in /etc/modprobe.d/blacklist.conf. When b43 module is loaded, it should load also ssb module, so if some error messages about module loading are shown try loading before ssb module and then b43.
Eventually type dmesg after module loading to look for log messages, or check kernel.log file to look for kernel error while loading modules (System->Administration->Log file viewer).

Which kernel are you using? I suppose the last Ubuntu kernel, 2.6.31-17.
Please go to this [site]("http://linuxwireless.org/en/users/Drivers/b43") to discover if your card could really work well with this revision of kernel, probably it does with no (known) problem but it is better to be sure.
I think that your card doesn't work after each upgrading because of some module conflict, the same conflict preventing you to use the card after a reboot, new Ubuntu revision = new kernel revision, if you use b43 module driver sources are in the kernel and the firmware is needed, other modules like nvidia or fglrx are "registered" with dkms so their sources are installed (look in /usr/src/) and the module is recompiled while booting if it is not found for running kernel.

---

### Post by chenxiaolong on 2009-12-30
Emas80, are you using the 2.6.32.2 kernel from the Ubuntu kernel PPA? I'm a little confused when you said kernel source directory. Is it /usr/src/linux-source-2.6.32 or is it /usr/src/linux-headers-2.6.32-*-generic? Thank you.

---

### Post by goslings on 2009-12-30
Hi Thanks for your help Emas80
uname -r report 
2.6.3.16-generic (upgrade from 9.04 via update manager)

lspci | grep BC
00:0e.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

according to site you suggested 
14e4:4306  supported  BCM4306  b43legacy? 
but below this states supported chipsets  
bcm4306 (Rev. 2 uses b43legacy, Rev. 3 uses b43)

so as per 9.04 as this is a REV 3 use b43-should be way forward
All working over wireless - as of now - before a reboot
See what happens on the other side 
thanks again 
Ian

---

### Post by goslings on 2009-12-30
> **goslings said:**
> See what happens on the other side 
thanks again 
Ian

grrr - No wireless after reboot 
network icon just has enable networking and no wireless
edit connection has 1 wired and strangle two wireless
BTvoyager - used 6hrs ago  
BTvoyager - used 1 yr ago
 
This is the kern.log file since the reboot - long sorry 
Hope there is some clues in here to the initiated 

```
 Dec 30 23:50:31 goslinux kernel: Kernel logging (proc) stopped.
Dec 30 23:51:21 goslinux kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 30 23:51:24 goslinux kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 30 23:51:24 goslinux kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 30 23:51:24 goslinux kernel: [    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
Dec 30 23:51:24 goslinux kernel: [    0.000000] KERNEL supported cpus:
Dec 30 23:51:24 goslinux kernel: [    0.000000]   Intel GenuineIntel
Dec 30 23:51:24 goslinux kernel: [    0.000000]   AMD AuthenticAMD
Dec 30 23:51:24 goslinux kernel: [    0.000000]   NSC Geode by NSC
Dec 30 23:51:24 goslinux kernel: [    0.000000]   Cyrix CyrixInstead
Dec 30 23:51:24 goslinux kernel: [    0.000000]   Centaur CentaurHauls
Dec 30 23:51:24 goslinux kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 30 23:51:24 goslinux kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 30 23:51:24 goslinux kernel: [    0.000000]   UMC UMC UMC UMC
Dec 30 23:51:24 goslinux kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 30 23:51:24 goslinux kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fffc000 (usable)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  BIOS-e820: 000000003fffc000 - 000000003ffff000 (ACPI data)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  BIOS-e820: 000000003ffff000 - 0000000040000000 (ACPI NVS)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000] DMI 2.3 present.
Dec 30 23:51:24 goslinux kernel: [    0.000000] last_pfn = 0x3fffc max_arch_pfn = 0x100000
Dec 30 23:51:24 goslinux kernel: [    0.000000] MTRR default type: uncachable
Dec 30 23:51:24 goslinux kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 30 23:51:24 goslinux kernel: [    0.000000]   00000-9FFFF write-back
Dec 30 23:51:24 goslinux kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 30 23:51:24 goslinux kernel: [    0.000000]   C0000-C7FFF write-protect
Dec 30 23:51:24 goslinux kernel: [    0.000000]   C8000-EFFFF uncachable
Dec 30 23:51:24 goslinux kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 30 23:51:24 goslinux kernel: [    0.000000] MTRR variable ranges enabled:
Dec 30 23:51:24 goslinux kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Dec 30 23:51:24 goslinux kernel: [    0.000000]   1 base 0E8000000 mask FFC000000 write-combining
Dec 30 23:51:24 goslinux kernel: [    0.000000]   2 disabled
Dec 30 23:51:24 goslinux kernel: [    0.000000]   3 disabled
Dec 30 23:51:24 goslinux kernel: [    0.000000]   4 disabled
Dec 30 23:51:24 goslinux kernel: [    0.000000]   5 disabled
Dec 30 23:51:24 goslinux kernel: [    0.000000]   6 disabled
Dec 30 23:51:24 goslinux kernel: [    0.000000]   7 disabled
Dec 30 23:51:24 goslinux kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 30 23:51:24 goslinux kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec 30 23:51:24 goslinux kernel: [    0.000000] modified physical RAM map:
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 0000000000100000 - 000000003fffc000 (usable)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 000000003fffc000 - 000000003ffff000 (ACPI data)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 000000003ffff000 - 0000000040000000 (ACPI NVS)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
Dec 30 23:51:24 goslinux kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Dec 30 23:51:24 goslinux kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Dec 30 23:51:24 goslinux kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Dec 30 23:51:24 goslinux kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Dec 30 23:51:24 goslinux kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Dec 30 23:51:24 goslinux kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Dec 30 23:51:24 goslinux kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Dec 30 23:51:24 goslinux kernel: [    0.000000] RAMDISK: 37816000 - 37fef821
Dec 30 23:51:24 goslinux kernel: [    0.000000] Allocated new RAMDISK: 008ad000 - 01086821
Dec 30 23:51:24 goslinux kernel: [    0.000000] Move RAMDISK from 0000000037816000 - 0000000037fef820 to 008ad000 - 01086820
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: RSDP 000f64e0 00014 (v00 ASUS  )
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: RSDT 3fffc000 00030 (v01 ASUS   P4S533VL 42302E31 MSFT 31313031)
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: FACP 3fffc0c0 00074 (v01 ASUS   P4S533VL 42302E31 MSFT 31313031)
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: DSDT 3fffc134 026B9 (v01   ASUS P4S533VL 00001000 MSFT 0100000B)
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: FACS 3ffff000 00040
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: BOOT 3fffc030 00028 (v01 ASUS   P4S533VL 42302E31 MSFT 31313031)
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: APIC 3fffc058 00068 (v01 ASUS   P4S533VL 42302E31 MSFT 31313031)
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 30 23:51:24 goslinux kernel: [    0.000000] 135MB HIGHMEM available.
Dec 30 23:51:24 goslinux kernel: [    0.000000] 887MB LOWMEM available.
Dec 30 23:51:24 goslinux kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Dec 30 23:51:24 goslinux kernel: [    0.000000]   low ram: 0 - 377fe000
Dec 30 23:51:24 goslinux kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Dec 30 23:51:24 goslinux kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Dec 30 23:51:24 goslinux kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Dec 30 23:51:24 goslinux kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 30 23:51:24 goslinux kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Dec 30 23:51:24 goslinux kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Dec 30 23:51:24 goslinux kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Dec 30 23:51:24 goslinux kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Dec 30 23:51:24 goslinux kernel: [    0.000000]   #5 [00008a9000 - 00008ac16c]              BRK ==> [00008a9000 - 00008ac16c]
Dec 30 23:51:24 goslinux kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Dec 30 23:51:24 goslinux kernel: [    0.000000]   #7 [00008ad000 - 0001086821]      NEW RAMDISK ==> [00008ad000 - 0001086821]
Dec 30 23:51:24 goslinux kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Dec 30 23:51:24 goslinux kernel: [    0.000000] Zone PFN ranges:
Dec 30 23:51:24 goslinux kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Dec 30 23:51:24 goslinux kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Dec 30 23:51:24 goslinux kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003fffc
Dec 30 23:51:24 goslinux kernel: [    0.000000] Movable zone start PFN for each node
Dec 30 23:51:24 goslinux kernel: [    0.000000] early_node_map[3] active PFN ranges
Dec 30 23:51:24 goslinux kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Dec 30 23:51:24 goslinux kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Dec 30 23:51:24 goslinux kernel: [    0.000000]     0: 0x00000100 -> 0x0003fffc
Dec 30 23:51:24 goslinux kernel: [    0.000000] On node 0 totalpages: 262039
Dec 30 23:51:24 goslinux kernel: [    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1087000
Dec 30 23:51:24 goslinux kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 30 23:51:24 goslinux kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 30 23:51:24 goslinux kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Dec 30 23:51:24 goslinux kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Dec 30 23:51:24 goslinux kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Dec 30 23:51:24 goslinux kernel: [    0.000000]   HighMem zone: 272 pages used for memmap
Dec 30 23:51:24 goslinux kernel: [    0.000000]   HighMem zone: 34542 pages, LIFO batch:7
Dec 30 23:51:24 goslinux kernel: [    0.000000] Using APIC driver default
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 30 23:51:24 goslinux kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 128, address 0xfec00000, GSI 0-23
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 30 23:51:24 goslinux kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 30 23:51:24 goslinux kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 30 23:51:24 goslinux kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 30 23:51:24 goslinux kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Dec 30 23:51:24 goslinux kernel: [    0.000000] nr_irqs_gsi: 24
Dec 30 23:51:24 goslinux kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Dec 30 23:51:24 goslinux kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 30 23:51:24 goslinux kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec 30 23:51:24 goslinux kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec 30 23:51:24 goslinux kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
Dec 30 23:51:24 goslinux kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Dec 30 23:51:24 goslinux kernel: [    0.000000] PERCPU: Embedded 14 pages at c188c000, static data 35612 bytes
Dec 30 23:51:24 goslinux kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259991
Dec 30 23:51:24 goslinux kernel: [    0.000000] Kernel command line: root=UUID=37e33de3-a10e-485e-902e-8db860896b49 ro vga=795 quiet 
Dec 30 23:51:24 goslinux kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 30 23:51:24 goslinux kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 30 23:51:24 goslinux kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 30 23:51:24 goslinux kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 30 23:51:24 goslinux kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 30 23:51:24 goslinux kernel: [    0.000000] Initializing CPU#0
Dec 30 23:51:24 goslinux kernel: [    0.000000] allocated 5242800 bytes of page_cgroup
Dec 30 23:51:24 goslinux kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 30 23:51:24 goslinux kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003fffc)
Dec 30 23:51:24 goslinux kernel: [    0.000000] Memory: 1017640k/1048560k available (4566k kernel code, 30164k reserved, 2142k data, 540k init, 139256k highmem)
Dec 30 23:51:24 goslinux kernel: [    0.000000] virtual kernel memory layout:
Dec 30 23:51:24 goslinux kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Dec 30 23:51:24 goslinux kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 30 23:51:24 goslinux kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Dec 30 23:51:24 goslinux kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Dec 30 23:51:24 goslinux kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Dec 30 23:51:24 goslinux kernel: [    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
Dec 30 23:51:24 goslinux kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
Dec 30 23:51:24 goslinux kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 30 23:51:24 goslinux kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Dec 30 23:51:24 goslinux kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Dec 30 23:51:24 goslinux kernel: [    0.000000] Fast TSC calibration using PIT
Dec 30 23:51:24 goslinux kernel: [    0.000000] Detected 3059.046 MHz processor.
Dec 30 23:51:24 goslinux kernel: [    0.000046] Console: colour dummy device 80x25
Dec 30 23:51:24 goslinux kernel: [    0.000051] console [tty0] enabled
Dec 30 23:51:24 goslinux kernel: [    0.000105] Calibrating delay loop (skipped), value calculated using timer frequency.. 6118.09 BogoMIPS (lpj=12236184)
Dec 30 23:51:24 goslinux kernel: [    0.000138] Security Framework initialized
Dec 30 23:51:24 goslinux kernel: [    0.000169] AppArmor: AppArmor initialized
Dec 30 23:51:24 goslinux kernel: [    0.000179] Mount-cache hash table entries: 512
Dec 30 23:51:24 goslinux kernel: [    0.000381] Initializing cgroup subsys ns
Dec 30 23:51:24 goslinux kernel: [    0.000388] Initializing cgroup subsys cpuacct
Dec 30 23:51:24 goslinux kernel: [    0.000393] Initializing cgroup subsys memory
Dec 30 23:51:24 goslinux kernel: [    0.000403] Initializing cgroup subsys freezer
Dec 30 23:51:24 goslinux kernel: [    0.000407] Initializing cgroup subsys net_cls
Dec 30 23:51:24 goslinux kernel: [    0.000428] CPU: Trace cache: 12K uops, L1 D cache: 8K
Dec 30 23:51:24 goslinux kernel: [    0.000432] CPU: L2 cache: 512K
Dec 30 23:51:24 goslinux kernel: [    0.000435] CPU: Physical Processor ID: 0
Dec 30 23:51:24 goslinux kernel: [    0.000437] CPU: Processor Core ID: 0
Dec 30 23:51:24 goslinux kernel: [    0.000442] mce: CPU supports 4 MCE banks
Dec 30 23:51:24 goslinux kernel: [    0.000455] CPU0: Thermal monitoring enabled (TM1)
Dec 30 23:51:24 goslinux kernel: [    0.000470] Performance Counters: no PMU driver, software counters only.
Dec 30 23:51:24 goslinux kernel: [    0.000479] Checking 'hlt' instruction... OK.
Dec 30 23:51:24 goslinux kernel: [    0.018975] ACPI: Core revision 20090521
Dec 30 23:51:24 goslinux kernel: [    0.024497]   alloc irq_desc for 20 on node 0
Dec 30 23:51:24 goslinux kernel: [    0.024500]   alloc kstat_irqs on node 0
Dec 30 23:51:24 goslinux kernel: [    0.024635] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 30 23:51:24 goslinux kernel: [    0.064325] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 07
Dec 30 23:51:24 goslinux kernel: [    0.068001] Booting processor 1 APIC 0x1 ip 0x6000
Dec 30 23:51:24 goslinux kernel: [    0.004000] Initializing CPU#1
Dec 30 23:51:24 goslinux kernel: [    0.004000] Calibrating delay using timer specific routine.. 6118.24 BogoMIPS (lpj=12236486)
Dec 30 23:51:24 goslinux kernel: [    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Dec 30 23:51:24 goslinux kernel: [    0.004000] CPU: L2 cache: 512K
Dec 30 23:51:24 goslinux kernel: [    0.004000] CPU: Physical Processor ID: 0
Dec 30 23:51:24 goslinux kernel: [    0.004000] CPU: Processor Core ID: 0
Dec 30 23:51:24 goslinux kernel: [    0.004000] mce: CPU supports 4 MCE banks
Dec 30 23:51:24 goslinux kernel: [    0.004000] CPU1: Thermal monitoring enabled (TM1)
Dec 30 23:51:24 goslinux kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Dec 30 23:51:24 goslinux kernel: [    0.152870] CPU1: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 07
Dec 30 23:51:24 goslinux kernel: [    0.152893] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 30 23:51:24 goslinux kernel: [    0.156050] Brought up 2 CPUs
Dec 30 23:51:24 goslinux kernel: [    0.156056] Total of 2 processors activated (12236.33 BogoMIPS).
Dec 30 23:51:24 goslinux kernel: [    0.156100] CPU0 attaching sched-domain:
Dec 30 23:51:24 goslinux kernel: [    0.156105]  domain 0: span 0-1 level SIBLING
Dec 30 23:51:24 goslinux kernel: [    0.156109]   groups: 0 1
Dec 30 23:51:24 goslinux kernel: [    0.156117] CPU1 attaching sched-domain:
Dec 30 23:51:24 goslinux kernel: [    0.156120]  domain 0: span 0-1 level SIBLING
Dec 30 23:51:24 goslinux kernel: [    0.156124]   groups: 1 0
Dec 30 23:51:24 goslinux kernel: [    0.156233] Booting paravirtualized kernel on bare hardware
Dec 30 23:51:24 goslinux kernel: [    0.156266] regulator: core version 0.5
Dec 30 23:51:24 goslinux kernel: [    0.156266] Time: 23:50:49  Date: 12/30/09
Dec 30 23:51:24 goslinux kernel: [    0.156266] NET: Registered protocol family 16
Dec 30 23:51:24 goslinux kernel: [    0.156298] EISA bus registered
Dec 30 23:51:24 goslinux kernel: [    0.156311] ACPI: bus type pci registered
Dec 30 23:51:24 goslinux kernel: [    0.157834] PCI: PCI BIOS revision 2.10 entry at 0xf2520, last bus=1
Dec 30 23:51:24 goslinux kernel: [    0.157837] PCI: Using configuration type 1 for base access
Dec 30 23:51:24 goslinux kernel: [    0.160942] bio: create slab <bio-0> at 0
Dec 30 23:51:24 goslinux kernel: [    0.160942] ACPI: EC: Look up EC in DSDT
Dec 30 23:51:24 goslinux kernel: [    0.167868] ACPI: Interpreter enabled
Dec 30 23:51:24 goslinux kernel: [    0.167876] ACPI: (supports S0 S1 S3 S4 S5)
Dec 30 23:51:24 goslinux kernel: [    0.168022] ACPI: Using IOAPIC for interrupt routing
Dec 30 23:51:24 goslinux kernel: [    0.181925] ACPI: No dock devices found.
Dec 30 23:51:24 goslinux kernel: [    0.182061] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 30 23:51:24 goslinux kernel: [    0.182124] pci 0000:00:00.0: reg 10 32bit mmio: [0xe8000000-0xebffffff]
Dec 30 23:51:24 goslinux kernel: [    0.182302] pci 0000:00:02.0: Enabling SiS 96x SMBus
Dec 30 23:51:24 goslinux kernel: [    0.182360] pci 0000:00:02.1: reg 20 io port: [0xe600-0xe61f]
Dec 30 23:51:24 goslinux kernel: [    0.182412] pci 0000:00:02.5: reg 10 io port: [0xd800-0xd807]
Dec 30 23:51:24 goslinux kernel: [    0.182422] pci 0000:00:02.5: reg 14 io port: [0xd400-0xd403]
Dec 30 23:51:24 goslinux kernel: [    0.182431] pci 0000:00:02.5: reg 18 io port: [0xd000-0xd007]
Dec 30 23:51:24 goslinux kernel: [    0.182440] pci 0000:00:02.5: reg 1c io port: [0xb800-0xb803]
Dec 30 23:51:24 goslinux kernel: [    0.182449] pci 0000:00:02.5: reg 20 io port: [0xb400-0xb40f]
Dec 30 23:51:24 goslinux kernel: [    0.182510] pci 0000:00:02.6: reg 10 io port: [0xb000-0xb0ff]
Dec 30 23:51:24 goslinux kernel: [    0.182520] pci 0000:00:02.6: reg 14 io port: [0xa800-0xa87f]
Dec 30 23:51:24 goslinux kernel: [    0.182575] pci 0000:00:02.6: supports D1 D2
Dec 30 23:51:24 goslinux kernel: [    0.182578] pci 0000:00:02.6: PME# supported from D3hot D3cold
Dec 30 23:51:24 goslinux kernel: [    0.182584] pci 0000:00:02.6: PME# disabled
Dec 30 23:51:24 goslinux kernel: [    0.182629] pci 0000:00:02.7: reg 10 io port: [0xa400-0xa4ff]
Dec 30 23:51:24 goslinux kernel: [    0.182638] pci 0000:00:02.7: reg 14 io port: [0xa000-0xa07f]
Dec 30 23:51:24 goslinux kernel: [    0.182694] pci 0000:00:02.7: supports D1 D2
Dec 30 23:51:24 goslinux kernel: [    0.182697] pci 0000:00:02.7: PME# supported from D3hot D3cold
Dec 30 23:51:24 goslinux kernel: [    0.182702] pci 0000:00:02.7: PME# disabled
Dec 30 23:51:24 goslinux kernel: [    0.182746] pci 0000:00:03.0: reg 10 32bit mmio: [0xe6800000-0xe6800fff]
Dec 30 23:51:24 goslinux kernel: [    0.182805] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Dec 30 23:51:24 goslinux kernel: [    0.182811] pci 0000:00:03.0: PME# disabled
Dec 30 23:51:24 goslinux kernel: [    0.182856] pci 0000:00:03.1: reg 10 32bit mmio: [0xe6000000-0xe6000fff]
Dec 30 23:51:24 goslinux kernel: [    0.182916] pci 0000:00:03.1: PME# supported from D0 D3hot D3cold
Dec 30 23:51:24 goslinux kernel: [    0.182921] pci 0000:00:03.1: PME# disabled
Dec 30 23:51:24 goslinux kernel: [    0.182965] pci 0000:00:03.2: reg 10 32bit mmio: [0xe5800000-0xe5800fff]
Dec 30 23:51:24 goslinux kernel: [    0.183024] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
Dec 30 23:51:24 goslinux kernel: [    0.183030] pci 0000:00:03.2: PME# disabled
Dec 30 23:51:24 goslinux kernel: [    0.183073] pci 0000:00:03.3: reg 10 32bit mmio: [0xe5000000-0xe5000fff]
Dec 30 23:51:24 goslinux kernel: [    0.183133] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
Dec 30 23:51:24 goslinux kernel: [    0.183139] pci 0000:00:03.3: PME# disabled
Dec 30 23:51:24 goslinux kernel: [    0.183194] pci 0000:00:0e.0: reg 10 32bit mmio: [0xe4800000-0xe4801fff]
Dec 30 23:51:24 goslinux kernel: [    0.183278] pci 0000:00:0f.0: reg 10 32bit mmio: [0xe4000000-0xe40003ff]
Dec 30 23:51:24 goslinux kernel: [    0.183339] pci 0000:00:0f.0: supports D1 D2
Dec 30 23:51:24 goslinux kernel: [    0.183387] pci 0000:00:10.0: reg 10 32bit mmio: [0x000000-0x000fff]
Dec 30 23:51:24 goslinux kernel: [    0.183412] pci 0000:00:10.0: supports D1 D2
Dec 30 23:51:24 goslinux kernel: [    0.183415] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 23:51:24 goslinux kernel: [    0.183420] pci 0000:00:10.0: PME# disabled
Dec 30 23:51:24 goslinux kernel: [    0.183467] pci 0000:00:12.0: reg 10 io port: [0x9800-0x98ff]
Dec 30 23:51:24 goslinux kernel: [    0.183477] pci 0000:00:12.0: reg 14 32bit mmio: [0xe3800000-0xe38000ff]
Dec 30 23:51:24 goslinux kernel: [    0.183532] pci 0000:00:12.0: supports D1 D2
Dec 30 23:51:24 goslinux kernel: [    0.183535] pci 0000:00:12.0: PME# supported from D1 D2 D3hot D3cold
Dec 30 23:51:24 goslinux kernel: [    0.183541] pci 0000:00:12.0: PME# disabled
Dec 30 23:51:24 goslinux kernel: [    0.183585] pci 0000:00:13.0: reg 10 32bit mmio: [0xe3000000-0xe3000fff]
Dec 30 23:51:24 goslinux kernel: [    0.183645] pci 0000:00:13.0: supports D1 D2
Dec 30 23:51:24 goslinux kernel: [    0.183648] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 23:51:24 goslinux kernel: [    0.183654] pci 0000:00:13.0: PME# disabled
Dec 30 23:51:24 goslinux kernel: [    0.183727] pci 0000:01:00.0: reg 10 32bit mmio: [0xe7000000-0xe7ffffff]
Dec 30 23:51:24 goslinux kernel: [    0.183736] pci 0000:01:00.0: reg 14 32bit mmio: [0xf0000000-0xf7ffffff]
Dec 30 23:51:24 goslinux kernel: [    0.183744] pci 0000:01:00.0: reg 18 32bit mmio: [0xef800000-0xef87ffff]
Dec 30 23:51:24 goslinux kernel: [    0.183765] pci 0000:01:00.0: reg 30 32bit mmio: [0xef7e0000-0xef7fffff]
Dec 30 23:51:24 goslinux kernel: [    0.183844] pci 0000:00:01.0: bridge 32bit mmio: [0xe7000000-0xe7ffffff]
Dec 30 23:51:24 goslinux kernel: [    0.183850] pci 0000:00:01.0: bridge 32bit mmio pref: [0xef700000-0xfebfffff]
Dec 30 23:51:24 goslinux kernel: [    0.183882] pci_bus 0000:00: on NUMA node 0
Dec 30 23:51:24 goslinux kernel: [    0.183888] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 30 23:51:24 goslinux kernel: [    0.184063] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Dec 30 23:51:24 goslinux kernel: [    0.276095] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec 30 23:51:24 goslinux kernel: [    0.276230] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Dec 30 23:51:24 goslinux kernel: [    0.276359] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
Dec 30 23:51:24 goslinux kernel: [    0.276489] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 30 23:51:24 goslinux kernel: [    0.276618] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
Dec 30 23:51:24 goslinux kernel: [    0.276747] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
Dec 30 23:51:24 goslinux kernel: [    0.276873] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
Dec 30 23:51:24 goslinux kernel: [    0.277003] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
Dec 30 23:51:24 goslinux kernel: [    0.277272] SCSI subsystem initialized
Dec 30 23:51:24 goslinux kernel: [    0.277345] libata version 3.00 loaded.
Dec 30 23:51:24 goslinux kernel: [    0.277345] usbcore: registered new interface driver usbfs
Dec 30 23:51:24 goslinux kernel: [    0.277345] usbcore: registered new interface driver hub
Dec 30 23:51:24 goslinux kernel: [    0.277345] usbcore: registered new device driver usb
Dec 30 23:51:24 goslinux kernel: [    0.277345] ACPI: WMI: Mapper loaded
Dec 30 23:51:24 goslinux kernel: [    0.277345] PCI: Using ACPI for IRQ routing
Dec 30 23:51:24 goslinux kernel: [    0.288013] Bluetooth: Core ver 2.15
Dec 30 23:51:24 goslinux kernel: [    0.288045] NET: Registered protocol family 31
Dec 30 23:51:24 goslinux kernel: [    0.288045] Bluetooth: HCI device and connection manager initialized
Dec 30 23:51:24 goslinux kernel: [    0.288045] Bluetooth: HCI socket layer initialized
Dec 30 23:51:24 goslinux kernel: [    0.288045] NetLabel: Initializing
Dec 30 23:51:24 goslinux kernel: [    0.288045] NetLabel:  domain hash size = 128
Dec 30 23:51:24 goslinux kernel: [    0.288045] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 30 23:51:24 goslinux kernel: [    0.288053] NetLabel:  unlabeled traffic allowed by default
Dec 30 23:51:24 goslinux kernel: [    0.300021] pnp: PnP ACPI init
Dec 30 23:51:24 goslinux kernel: [    0.300056] ACPI: bus type pnp registered
Dec 30 23:51:24 goslinux kernel: [    0.305606] pnp: PnP ACPI: found 15 devices
Dec 30 23:51:24 goslinux kernel: [    0.305610] ACPI: ACPI bus type pnp unregistered
Dec 30 23:51:24 goslinux kernel: [    0.305615] PnPBIOS: Disabled by ACPI PNP
Dec 30 23:51:24 goslinux kernel: [    0.305631] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Dec 30 23:51:24 goslinux kernel: [    0.305636] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
Dec 30 23:51:24 goslinux kernel: [    0.305640] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
Dec 30 23:51:24 goslinux kernel: [    0.305645] system 00:00: iomem range 0xfec00000-0xfecfffff could not be reserved
Dec 30 23:51:24 goslinux kernel: [    0.305649] system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
Dec 30 23:51:24 goslinux kernel: [    0.305659] system 00:02: ioport range 0xe400-0xe47f has been reserved
Dec 30 23:51:24 goslinux kernel: [    0.305663] system 00:02: ioport range 0xe480-0xe4ff has been reserved
Dec 30 23:51:24 goslinux kernel: [    0.305667] system 00:02: ioport range 0xe600-0xe61f has been reserved
Dec 30 23:51:24 goslinux kernel: [    0.305670] system 00:02: ioport range 0x480-0x48f has been reserved
Dec 30 23:51:24 goslinux kernel: [    0.305674] system 00:02: iomem range 0xffee0000-0xffefffff has been reserved
Dec 30 23:51:24 goslinux kernel: [    0.305683] system 00:03: iomem range 0xfffe0000-0xffffffff could not be reserved
Dec 30 23:51:24 goslinux kernel: [    0.305692] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
Dec 30 23:51:24 goslinux kernel: [    0.305705] system 00:0d: ioport range 0x295-0x296 has been reserved
Dec 30 23:51:24 goslinux kernel: [    0.340443] AppArmor: AppArmor Filesystem Enabled
Dec 30 23:51:24 goslinux kernel: [    0.340493] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Dec 30 23:51:24 goslinux kernel: [    0.340497] pci 0000:00:01.0:   IO window: disabled
Dec 30 23:51:24 goslinux kernel: [    0.340504] pci 0000:00:01.0:   MEM window: 0xe7000000-0xe7ffffff
Dec 30 23:51:24 goslinux kernel: [    0.340510] pci 0000:00:01.0:   PREFETCH window: 0xef700000-0xfebfffff
Dec 30 23:51:24 goslinux kernel: [    0.340517] pci 0000:00:10.0: CardBus bridge, secondary bus 0000:02
Dec 30 23:51:24 goslinux kernel: [    0.340520] pci 0000:00:10.0:   IO window: 0x001000-0x0010ff
Dec 30 23:51:24 goslinux kernel: [    0.340526] pci 0000:00:10.0:   IO window: 0x001400-0x0014ff
Dec 30 23:51:24 goslinux kernel: [    0.340532] pci 0000:00:10.0:   PREFETCH window: 0x40000000-0x43ffffff
Dec 30 23:51:24 goslinux kernel: [    0.340538] pci 0000:00:10.0:   MEM window: 0x44000000-0x47ffffff
Dec 30 23:51:24 goslinux kernel: [    0.340555] pci 0000:00:01.0: setting latency timer to 64
Dec 30 23:51:24 goslinux kernel: [    0.340575]   alloc irq_desc for 19 on node -1
Dec 30 23:51:24 goslinux kernel: [    0.340578]   alloc kstat_irqs on node -1
Dec 30 23:51:24 goslinux kernel: [    0.340586] pci 0000:00:10.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 30 23:51:24 goslinux kernel: [    0.340595] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Dec 30 23:51:24 goslinux kernel: [    0.340599] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Dec 30 23:51:24 goslinux kernel: [    0.340602] pci_bus 0000:01: resource 1 mem: [0xe7000000-0xe7ffffff]
Dec 30 23:51:24 goslinux kernel: [    0.340606] pci_bus 0000:01: resource 2 pref mem [0xef700000-0xfebfffff]
Dec 30 23:51:24 goslinux kernel: [    0.340609] pci_bus 0000:02: resource 0 io:  [0x1000-0x10ff]
Dec 30 23:51:24 goslinux kernel: [    0.340612] pci_bus 0000:02: resource 1 io:  [0x1400-0x14ff]
Dec 30 23:51:24 goslinux kernel: [    0.340616] pci_bus 0000:02: resource 2 pref mem [0x40000000-0x43ffffff]
Dec 30 23:51:24 goslinux kernel: [    0.340619] pci_bus 0000:02: resource 3 mem: [0x44000000-0x47ffffff]
Dec 30 23:51:24 goslinux kernel: [    0.340673] NET: Registered protocol family 2
Dec 30 23:51:24 goslinux kernel: [    0.340812] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 30 23:51:24 goslinux kernel: [    0.341334] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 30 23:51:24 goslinux kernel: [    0.342487] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 30 23:51:24 goslinux kernel: [    0.343245] TCP: Hash tables configured (established 131072 bind 65536)
Dec 30 23:51:24 goslinux kernel: [    0.343251] TCP reno registered
Dec 30 23:51:24 goslinux kernel: [    0.343444] NET: Registered protocol family 1
Dec 30 23:51:24 goslinux kernel: [    0.343573] Trying to unpack rootfs image as initramfs...
Dec 30 23:51:24 goslinux kernel: [    0.581926] Freeing initrd memory: 8038k freed
Dec 30 23:51:24 goslinux kernel: [    0.592800] Simple Boot Flag at 0x3a set to 0x1
Dec 30 23:51:24 goslinux kernel: [    0.592954] cpufreq-nforce2: No nForce2 chipset.
Dec 30 23:51:24 goslinux kernel: [    0.592992] Scanning for low memory corruption every 60 seconds
Dec 30 23:51:24 goslinux kernel: [    0.593145] audit: initializing netlink socket (disabled)
Dec 30 23:51:24 goslinux kernel: [    0.593171] type=2000 audit(1262217049.592:1): initialized
Dec 30 23:51:24 goslinux kernel: [    0.600550] highmem bounce pool size: 64 pages
Dec 30 23:51:24 goslinux kernel: [    0.600558] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec 30 23:51:24 goslinux kernel: [    0.602486] VFS: Disk quotas dquot_6.5.2
Dec 30 23:51:24 goslinux kernel: [    0.602577] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 30 23:51:24 goslinux kernel: [    0.603325] fuse init (API version 7.12)
Dec 30 23:51:24 goslinux kernel: [    0.603436] msgmni has been set to 1731
Dec 30 23:51:24 goslinux kernel: [    0.603799] alg: No test for stdrng (krng)
Dec 30 23:51:24 goslinux kernel: [    0.603821] io scheduler noop registered
Dec 30 23:51:24 goslinux kernel: [    0.603824] io scheduler anticipatory registered
Dec 30 23:51:24 goslinux kernel: [    0.603827] io scheduler deadline registered
Dec 30 23:51:24 goslinux kernel: [    0.603898] io scheduler cfq registered (default)
Dec 30 23:51:24 goslinux kernel: [    0.603990] pci 0000:01:00.0: Boot video device
Dec 30 23:51:24 goslinux kernel: [    0.604125] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 30 23:51:24 goslinux kernel: [    0.604158] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 30 23:51:24 goslinux kernel: [    0.604332] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Dec 30 23:51:24 goslinux kernel: [    0.604338] ACPI: Power Button [PWRF]
Dec 30 23:51:24 goslinux kernel: [    0.604403] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Dec 30 23:51:24 goslinux kernel: [    0.604407] ACPI: Power Button [PWRB]
Dec 30 23:51:24 goslinux kernel: [    0.604583] ACPI: Invalid PBLK length [5]
Dec 30 23:51:24 goslinux kernel: [    0.604631] processor LNXCPU:00: registered as cooling_device0
Dec 30 23:51:24 goslinux kernel: [    0.604691] processor LNXCPU:01: registered as cooling_device1
Dec 30 23:51:24 goslinux kernel: [    0.615359] isapnp: Scanning for PnP cards...
Dec 30 23:51:24 goslinux kernel: [    0.840937] Switched to high resolution mode on CPU 1
Dec 30 23:51:24 goslinux kernel: [    0.844006] Switched to high resolution mode on CPU 0
Dec 30 23:51:24 goslinux kernel: [    0.969050] isapnp: No Plug & Play device found
Dec 30 23:51:24 goslinux kernel: [    0.970618] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 30 23:51:24 goslinux kernel: [    0.971071]   alloc irq_desc for 18 on node -1
Dec 30 23:51:24 goslinux kernel: [    0.971075]   alloc kstat_irqs on node -1
Dec 30 23:51:24 goslinux kernel: [    0.971085] serial 0000:00:02.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 30 23:51:24 goslinux kernel: [    0.971094] serial 0000:00:02.6: PCI INT C disabled
Dec 30 23:51:24 goslinux kernel: [    0.972432] brd: module loaded
Dec 30 23:51:24 goslinux kernel: [    0.973077] loop: module loaded
Dec 30 23:51:24 goslinux kernel: [    0.973202] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Dec 30 23:51:24 goslinux kernel: [    0.974091] pata_sis 0000:00:02.5: version 0.5.2
Dec 30 23:51:24 goslinux kernel: [    0.974109]   alloc irq_desc for 16 on node -1
Dec 30 23:51:24 goslinux kernel: [    0.974112]   alloc kstat_irqs on node -1
Dec 30 23:51:24 goslinux kernel: [    0.974121] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 30 23:51:24 goslinux kernel: [    0.974421] scsi0 : pata_sis
Dec 30 23:51:24 goslinux kernel: [    0.974570] scsi1 : pata_sis
Dec 30 23:51:24 goslinux kernel: [    0.975304] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xb400 irq 14
Dec 30 23:51:24 goslinux kernel: [    0.975308] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xb408 irq 15
Dec 30 23:51:24 goslinux kernel: [    0.975824] Fixed MDIO Bus: probed
Dec 30 23:51:24 goslinux kernel: [    0.975871] PPP generic driver version 2.4.2
Dec 30 23:51:24 goslinux kernel: [    0.976045] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 30 23:51:24 goslinux kernel: [    0.976083]   alloc irq_desc for 23 on node -1
Dec 30 23:51:24 goslinux kernel: [    0.976086]   alloc kstat_irqs on node -1
Dec 30 23:51:24 goslinux kernel: [    0.976094] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Dec 30 23:51:24 goslinux kernel: [    0.976118] ehci_hcd 0000:00:03.3: EHCI Host Controller
Dec 30 23:51:24 goslinux kernel: [    0.976192] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
Dec 30 23:51:24 goslinux kernel: [    0.976231] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
Dec 30 23:51:24 goslinux kernel: [    0.976251] ehci_hcd 0000:00:03.3: irq 23, io mem 0xe5000000
Dec 30 23:51:24 goslinux kernel: [    0.985013] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
Dec 30 23:51:24 goslinux kernel: [    0.985120] usb usb1: configuration #1 chosen from 1 choice
Dec 30 23:51:24 goslinux kernel: [    0.985165] hub 1-0:1.0: USB hub found
Dec 30 23:51:24 goslinux kernel: [    0.985178] hub 1-0:1.0: 6 ports detected
Dec 30 23:51:24 goslinux kernel: [    0.985272] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 30 23:51:24 goslinux kernel: [    0.985304] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 30 23:51:24 goslinux kernel: [    0.985322] ohci_hcd 0000:00:03.0: OHCI Host Controller
Dec 30 23:51:24 goslinux kernel: [    0.985372] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
Dec 30 23:51:24 goslinux kernel: [    0.985392] ohci_hcd 0000:00:03.0: irq 20, io mem 0xe6800000
Dec 30 23:51:24 goslinux kernel: [    1.042085] usb usb2: configuration #1 chosen from 1 choice
Dec 30 23:51:24 goslinux kernel: [    1.042122] hub 2-0:1.0: USB hub found
Dec 30 23:51:24 goslinux kernel: [    1.042133] hub 2-0:1.0: 2 ports detected
Dec 30 23:51:24 goslinux kernel: [    1.042212]   alloc irq_desc for 21 on node -1
Dec 30 23:51:24 goslinux kernel: [    1.042216]   alloc kstat_irqs on node -1
Dec 30 23:51:24 goslinux kernel: [    1.042223] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec 30 23:51:24 goslinux kernel: [    1.042236] ohci_hcd 0000:00:03.1: OHCI Host Controller
Dec 30 23:51:24 goslinux kernel: [    1.042281] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
Dec 30 23:51:24 goslinux kernel: [    1.042306] ohci_hcd 0000:00:03.1: irq 21, io mem 0xe6000000
Dec 30 23:51:24 goslinux kernel: [    1.098087] usb usb3: configuration #1 chosen from 1 choice
Dec 30 23:51:24 goslinux kernel: [    1.098126] hub 3-0:1.0: USB hub found
Dec 30 23:51:24 goslinux kernel: [    1.098138] hub 3-0:1.0: 2 ports detected
Dec 30 23:51:24 goslinux kernel: [    1.098207]   alloc irq_desc for 22 on node -1
Dec 30 23:51:24 goslinux kernel: [    1.098211]   alloc kstat_irqs on node -1
Dec 30 23:51:24 goslinux kernel: [    1.098217] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Dec 30 23:51:24 goslinux kernel: [    1.098232] ohci_hcd 0000:00:03.2: OHCI Host Controller
Dec 30 23:51:24 goslinux kernel: [    1.098276] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
Dec 30 23:51:24 goslinux kernel: [    1.098301] ohci_hcd 0000:00:03.2: irq 22, io mem 0xe5800000
Dec 30 23:51:24 goslinux kernel: [    1.137142] ata1.00: ATA-6: WDC WD1600BB-22DAA0, 65.13G65, max UDMA/100
Dec 30 23:51:24 goslinux kernel: [    1.137147] ata1.00: 312581808 sectors, multi 16: LBA48 
Dec 30 23:51:24 goslinux kernel: [    1.153172] ata1.00: configured for UDMA/100
Dec 30 23:51:24 goslinux kernel: [    1.153341] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BB-22D 65.1 PQ: 0 ANSI: 5
Dec 30 23:51:24 goslinux kernel: [    1.153546] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 30 23:51:24 goslinux kernel: [    1.153606] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Dec 30 23:51:24 goslinux kernel: [    1.153681] sd 0:0:0:0: [sda] Write Protect is off
Dec 30 23:51:24 goslinux kernel: [    1.153685] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 30 23:51:24 goslinux kernel: [    1.153724] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 30 23:51:24 goslinux kernel: [    1.154131] usb usb4: configuration #1 chosen from 1 choice
Dec 30 23:51:24 goslinux kernel: [    1.154179] hub 4-0:1.0: USB hub found
Dec 30 23:51:24 goslinux kernel: [    1.154196] hub 4-0:1.0: 2 ports detected
Dec 30 23:51:24 goslinux kernel: [    1.154294] uhci_hcd: USB Universal Host Controller Interface driver
Dec 30 23:51:24 goslinux kernel: [    1.154455] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 30 23:51:24 goslinux kernel: [    1.154810] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 30 23:51:24 goslinux kernel: [    1.154820] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 30 23:51:24 goslinux kernel: [    1.154935] mice: PS/2 mouse device common for all mice
Dec 30 23:51:24 goslinux kernel: [    1.155079] rtc_cmos 00:06: RTC can wake from S4
Dec 30 23:51:24 goslinux kernel: [    1.155142] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Dec 30 23:51:24 goslinux kernel: [    1.155170] rtc0: alarms up to one month, 242 bytes nvram
Dec 30 23:51:24 goslinux kernel: [    1.155345] device-mapper: uevent: version 1.0.3
Dec 30 23:51:24 goslinux kernel: [    1.155558] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Dec 30 23:51:24 goslinux kernel: [    1.155725]  sda:
Dec 30 23:51:24 goslinux kernel: [    1.155855] device-mapper: multipath: version 1.1.0 loaded
Dec 30 23:51:24 goslinux kernel: [    1.155862] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 30 23:51:24 goslinux kernel: [    1.156116] EISA: Probing bus 0 at eisa.0
Dec 30 23:51:24 goslinux kernel: [    1.156126] Cannot allocate resource for EISA slot 1
Dec 30 23:51:24 goslinux kernel: [    1.156156] EISA: Detected 0 cards.
Dec 30 23:51:24 goslinux kernel: [    1.156328] cpuidle: using governor ladder
Dec 30 23:51:24 goslinux kernel: [    1.156331] cpuidle: using governor menu
Dec 30 23:51:24 goslinux kernel: [    1.157118] TCP cubic registered
Dec 30 23:51:24 goslinux kernel: [    1.157285] NET: Registered protocol family 10
Dec 30 23:51:24 goslinux kernel: [    1.157925] lo: Disabled Privacy Extensions
Dec 30 23:51:24 goslinux kernel: [    1.158405] NET: Registered protocol family 17
Dec 30 23:51:24 goslinux kernel: [    1.158435] Bluetooth: L2CAP ver 2.13
Dec 30 23:51:24 goslinux kernel: [    1.158437] Bluetooth: L2CAP socket layer initialized
Dec 30 23:51:24 goslinux kernel: [    1.158441] Bluetooth: SCO (Voice Link) ver 0.6
Dec 30 23:51:24 goslinux kernel: [    1.158443] Bluetooth: SCO socket layer initialized
Dec 30 23:51:24 goslinux kernel: [    1.158526] Bluetooth: RFCOMM TTY layer initialized
Dec 30 23:51:24 goslinux kernel: [    1.158533] Bluetooth: RFCOMM socket layer initialized
Dec 30 23:51:24 goslinux kernel: [    1.158537] Bluetooth: RFCOMM ver 1.11
Dec 30 23:51:24 goslinux kernel: [    1.158594] Using IPI No-Shortcut mode
Dec 30 23:51:24 goslinux kernel: [    1.158705] PM: Resume from disk failed.
Dec 30 23:51:24 goslinux kernel: [    1.158724] registered taskstats version 1
Dec 30 23:51:24 goslinux kernel: [    1.158868]   Magic number: 5:521:859
Dec 30 23:51:24 goslinux kernel: [    1.158968] rtc_cmos 00:06: setting system clock to 2009-12-30 23:50:50 UTC (1262217050)
Dec 30 23:51:24 goslinux kernel: [    1.158973] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 30 23:51:24 goslinux kernel: [    1.158975] EDD information not available.
Dec 30 23:51:24 goslinux kernel: [    1.175781]  sda1 sda2 <
Dec 30 23:51:24 goslinux kernel: [    1.180183] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Dec 30 23:51:24 goslinux kernel: [    1.187536]  sda5 sda6 sda7 > sda3
Dec 30 23:51:24 goslinux kernel: [    1.211613] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 30 23:51:24 goslinux kernel: [    1.324256] ata2.00: ATAPI: SONY    DVD RW DW-U12A, 2.0b, max UDMA/33
Dec 30 23:51:24 goslinux kernel: [    1.324297] ata2.01: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-120, 1.20, max UDMA/66
Dec 30 23:51:24 goslinux kernel: [    1.324330] ata2.01: limited to UDMA/33 due to 40-wire cable
Dec 30 23:51:24 goslinux kernel: [    1.340274] ata2.00: configured for UDMA/33
Dec 30 23:51:24 goslinux kernel: [    1.356305] ata2.01: configured for UDMA/33
Dec 30 23:51:24 goslinux kernel: [    1.359120] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DW-U12A   2.0b PQ: 0 ANSI: 5
Dec 30 23:51:24 goslinux kernel: [    1.362918] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
Dec 30 23:51:24 goslinux kernel: [    1.362924] Uniform CD-ROM driver Revision: 3.20
Dec 30 23:51:24 goslinux kernel: [    1.363063] sr 1:0:0:0: Attached scsi CD-ROM sr0
Dec 30 23:51:24 goslinux kernel: [    1.363144] sr 1:0:0:0: Attached scsi generic sg1 type 5
Dec 30 23:51:24 goslinux kernel: [    1.363787] scsi 1:0:1:0: CD-ROM            PIONEER  DVD-ROM DVD-120R 1.20 PQ: 0 ANSI: 5
Dec 30 23:51:24 goslinux kernel: [    1.367157] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
Dec 30 23:51:24 goslinux kernel: [    1.367275] sr 1:0:1:0: Attached scsi CD-ROM sr1
Dec 30 23:51:24 goslinux kernel: [    1.367339] sr 1:0:1:0: Attached scsi generic sg2 type 5
Dec 30 23:51:24 goslinux kernel: [    1.367382] Freeing unused kernel memory: 540k freed
Dec 30 23:51:24 goslinux kernel: [    1.368152] Write protecting the kernel text: 4568k
Dec 30 23:51:24 goslinux kernel: [    1.368219] Write protecting the kernel read-only data: 1836k
Dec 30 23:51:24 goslinux kernel: [    1.542428] Linux agpgart interface v0.103
Dec 30 23:51:24 goslinux kernel: [    1.548266] agpgart-sis 0000:00:00.0: SiS chipset [1039/0651]
Dec 30 23:51:24 goslinux kernel: [    1.573117] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
Dec 30 23:51:24 goslinux kernel: [    1.595273] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Dec 30 23:51:24 goslinux kernel: [    1.595333] 8139cp 0000:00:12.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Dec 30 23:51:24 goslinux kernel: [    1.600736] 8139too Fast Ethernet driver 0.9.28
Dec 30 23:51:24 goslinux kernel: [    1.600841]   alloc irq_desc for 17 on node -1
Dec 30 23:51:24 goslinux kernel: [    1.600846]   alloc kstat_irqs on node -1
Dec 30 23:51:24 goslinux kernel: [    1.600861] 8139too 0000:00:12.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 30 23:51:24 goslinux kernel: [    1.602830] eth0: RealTek RTL8139 at 0x9800, 00:0c:6e:12:71:f6, IRQ 17
Dec 30 23:51:24 goslinux kernel: [    1.696809] Floppy drive(s): fd0 is 1.44M
Dec 30 23:51:24 goslinux kernel: [    1.757077] ohci1394 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 30 23:51:24 goslinux kernel: [    1.760633] reset set in interrupt, calling f80db170
Dec 30 23:51:24 goslinux kernel: [    1.760670] floppy0: no floppy controllers found
Dec 30 23:51:24 goslinux kernel: [    1.815036] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[e3000000-e30007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Dec 30 23:51:24 goslinux kernel: [    2.761336] vesafb: framebuffer at 0xf0000000, mapped to 0xf8180000, using 10240k, total 131072k
Dec 30 23:51:24 goslinux kernel: [    2.761342] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
Dec 30 23:51:24 goslinux kernel: [    2.761344] vesafb: protected mode interface info at c000:f060
Dec 30 23:51:24 goslinux kernel: [    2.761348] vesafb: pmi: set display start = c00cf0a5, set palette = c00cf12a
Dec 30 23:51:24 goslinux kernel: [    2.761351] vesafb: pmi: ports = b4c3 b503 ba03 c003 c103 c403 c503 c603 c703 c803 c903 cc03 ce03 cf03 d003 d103 d203 d303 d403 d503 da03 ff03 
Dec 30 23:51:24 goslinux kernel: [    2.761380] vesafb: scrolling: redraw
Dec 30 23:51:24 goslinux kernel: [    2.761385] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Dec 30 23:51:24 goslinux kernel: [    2.761464] fb0: VESA VGA frame buffer device
Dec 30 23:51:24 goslinux kernel: [    2.770280] Console: switching to colour frame buffer device 160x64
Dec 30 23:51:24 goslinux kernel: [    3.100704] xor: automatically using best checksumming function: pIII_sse
Dec 30 23:51:24 goslinux kernel: [    3.101257] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301543ecf]
Dec 30 23:51:24 goslinux kernel: [    3.120008]    pIII_sse  :  3879.000 MB/sec
Dec 30 23:51:24 goslinux kernel: [    3.120012] xor: using function: pIII_sse (3879.000 MB/sec)
Dec 30 23:51:24 goslinux kernel: [    3.123261] device-mapper: dm-raid45: initialized v0.2594b
Dec 30 23:51:24 goslinux kernel: [    3.402738] PM: Starting manual resume from disk
Dec 30 23:51:24 goslinux kernel: [    3.402744] PM: Resume from partition 8:5
Dec 30 23:51:24 goslinux kernel: [    3.402746] PM: Checking hibernation image.
Dec 30 23:51:24 goslinux kernel: [    3.402972] PM: Resume from disk failed.
Dec 30 23:51:24 goslinux kernel: [    3.428347] kjournald starting.  Commit interval 5 seconds
Dec 30 23:51:24 goslinux kernel: [    3.428366] EXT3-fs: mounted filesystem with writeback data mode.
Dec 30 23:51:24 goslinux kernel: [    4.219229] type=1505 audit(1262217053.557:2): operation="profile_load" pid=415 name=/usr/share/gdm/guest-session/Xsession
Dec 30 23:51:24 goslinux kernel: [    4.233368] type=1505 audit(1262217053.573:3): operation="profile_load" pid=416 name=/sbin/dhclient3
Dec 30 23:51:24 goslinux kernel: [    4.233916] type=1505 audit(1262217053.573:4): operation="profile_load" pid=416 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 30 23:51:24 goslinux kernel: [    4.234219] type=1505 audit(1262217053.573:5): operation="profile_load" pid=416 name=/usr/lib/connman/scripts/dhclient-script
Dec 30 23:51:24 goslinux kernel: [    4.277625] type=1505 audit(1262217053.618:6): operation="profile_load" pid=417 name=/usr/bin/evince
Dec 30 23:51:24 goslinux kernel: [    4.286926] type=1505 audit(1262217053.626:7): operation="profile_load" pid=417 name=/usr/bin/evince-previewer
Dec 30 23:51:24 goslinux kernel: [    4.292398] type=1505 audit(1262217053.630:8): operation="profile_load" pid=417 name=/usr/bin/evince-thumbnailer
Dec 30 23:51:24 goslinux kernel: [    4.316992] type=1505 audit(1262217053.654:9): operation="profile_load" pid=418 name=/usr/lib/cups/backend/cups-pdf
Dec 30 23:51:24 goslinux kernel: [    4.317642] type=1505 audit(1262217053.658:10): operation="profile_load" pid=418 name=/usr/sbin/cupsd
Dec 30 23:51:24 goslinux kernel: [   28.277388] udev: starting version 147
Dec 30 23:51:24 goslinux kernel: [   28.288084] Adding 1020088k swap on /dev/sda5.  Priority:-1 extents:1 across:1020088k 
Dec 30 23:51:24 goslinux kernel: [   28.318325] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
Dec 30 23:51:24 goslinux kernel: [   28.343124] lp: driver loaded but no devices found
Dec 30 23:51:24 goslinux kernel: [   28.387017] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 30 23:51:24 goslinux kernel: [   28.399873] yenta_cardbus 0000:00:10.0: CardBus bridge found [104d:8139]
Dec 30 23:51:24 goslinux kernel: [   28.527595] yenta_cardbus 0000:00:10.0: ISA IRQ mask 0x06b8, PCI irq 19
Dec 30 23:51:24 goslinux kernel: [   28.527603] yenta_cardbus 0000:00:10.0: Socket status: 30000006
Dec 30 23:51:24 goslinux kernel: [   28.629621] Linux video capture interface: v2.00
Dec 30 23:51:24 goslinux kernel: [   28.750430] parport_pc 00:0a: reported by Plug and Play ACPI
Dec 30 23:51:24 goslinux kernel: [   28.750507] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Dec 30 23:51:24 goslinux kernel: [   28.775927] saa7130/34: v4l2 driver version 0.2.15 loaded
Dec 30 23:51:24 goslinux kernel: [   28.779528] Floppy drive(s): fd0 is 1.44M
Dec 30 23:51:24 goslinux kernel: [   28.805840] reset set in interrupt, calling f815e170
Dec 30 23:51:24 goslinux kernel: [   28.805873] floppy0: no floppy controllers found
Dec 30 23:51:24 goslinux kernel: [   28.826208] ppdev: user-space parallel port driver
Dec 30 23:51:24 goslinux kernel: [   28.833436] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 30 23:51:24 goslinux kernel: [   28.845420] lp0: using parport0 (interrupt-driven).
Dec 30 23:51:24 goslinux kernel: [   28.867100] b43-pci-bridge 0000:00:0e.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 30 23:51:24 goslinux kernel: [   28.870686] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0e.0
Dec 30 23:51:24 goslinux kernel: [   28.871207] saa7134 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 30 23:51:24 goslinux kernel: [   28.871222] saa7134[0]: found at 0000:00:0f.0, rev: 1, irq: 18, latency: 32, mmio: 0xe4000000
Dec 30 23:51:24 goslinux kernel: [   28.871238] saa7134[0]: subsystem: 1043:4830, board: ASUS TV-FM 7134 [card=16,autodetected]
Dec 30 23:51:24 goslinux kernel: [   28.871276] saa7134[0]: board init: gpio is 0
Dec 30 23:51:24 goslinux kernel: [   28.871287] IRQ 18/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
Dec 30 23:51:24 goslinux kernel: [   28.889401] cfg80211: Calling CRDA to update world regulatory domain
Dec 30 23:51:24 goslinux kernel: [   28.932671] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
Dec 30 23:51:24 goslinux kernel: [   29.026897] saa7134[0]: i2c eeprom 00: 43 10 30 48 ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.026925] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.026951] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.026974] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.026998] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027021] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027045] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027069] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027092] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027116] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027139] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027163] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027186] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027209] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027232] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027255] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Dec 30 23:51:24 goslinux kernel: [   29.027285] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
Dec 30 23:51:24 goslinux kernel: [   29.070656] phy0: Selected rate control algorithm 'minstrel'
Dec 30 23:51:24 goslinux kernel: [   29.071764] Registered led device: b43-phy0::tx
Dec 30 23:51:24 goslinux kernel: [   29.071789] Registered led device: b43-phy0::rx
Dec 30 23:51:24 goslinux kernel: [   29.071814] Registered led device: b43-phy0::radio
Dec 30 23:51:24 goslinux kernel: [   29.071905] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]
Dec 30 23:51:24 goslinux kernel: [   29.080146] tuner 1-0043: chip found @ 0x86 (saa7134[0])
Dec 30 23:51:24 goslinux kernel: [   29.088670] tda9887 1-0043: creating new instance
Dec 30 23:51:24 goslinux kernel: [   29.088677] tda9887 1-0043: tda988[5/6/7] found
Dec 30 23:51:24 goslinux kernel: [   29.098100] psmouse serio1: ID: 10 00 64
Dec 30 23:51:24 goslinux kernel: [   29.120014] All bytes are equal. It is not a TEA5767
Dec 30 23:51:24 goslinux kernel: [   29.120151] tuner 1-0060: chip found @ 0xc0 (saa7134[0])
Dec 30 23:51:24 goslinux kernel: [   29.136028] tuner-simple 1-0060: creating new instance
Dec 30 23:51:24 goslinux kernel: [   29.136035] tuner-simple 1-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
Dec 30 23:51:24 goslinux kernel: [   29.148386] udev: renamed network interface wlan0 to eth1
Dec 30 23:51:24 goslinux kernel: [   29.165970] cfg80211: World regulatory domain updated:
Dec 30 23:51:24 goslinux kernel: [   29.165976] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 30 23:51:24 goslinux kernel: [   29.165980] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 30 23:51:24 goslinux kernel: [   29.165984] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 30 23:51:24 goslinux kernel: [   29.165987] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 30 23:51:24 goslinux kernel: [   29.165991] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 30 23:51:24 goslinux kernel: [   29.165994] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 30 23:51:24 goslinux kernel: [   29.166740] logips2pp: Detected unknown logitech mouse model 14
Dec 30 23:51:24 goslinux kernel: [   29.196349] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x240-0x247
Dec 30 23:51:24 goslinux kernel: [   29.198146] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
Dec 30 23:51:24 goslinux kernel: [   29.198888] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Dec 30 23:51:24 goslinux kernel: [   29.199544] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
Dec 30 23:51:24 goslinux kernel: [   29.200209] saa7134[0]: registered device video0 [v4l2]
Dec 30 23:51:24 goslinux kernel: [   29.200225]  clean.
Dec 30 23:51:24 goslinux kernel: [   29.200266] saa7134[0]: registered device vbi0
Dec 30 23:51:24 goslinux kernel: [   29.200324] saa7134[0]: registered device radio0
Dec 30 23:51:24 goslinux kernel: [   29.200605] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Dec 30 23:51:24 goslinux kernel: [   29.202058] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 30 23:51:24 goslinux kernel: [   29.209240] saa7134 ALSA driver for DMA sound loaded
Dec 30 23:51:24 goslinux kernel: [   29.209264] IRQ 18/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
Dec 30 23:51:24 goslinux kernel: [   29.209324] saa7134[0]/alsa: saa7134[0] at 0xe4000000 irq 18 registered as card -2
Dec 30 23:51:24 goslinux kernel: [   29.636721] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input4
Dec 30 23:51:24 goslinux kernel: [   29.953050] EXT3 FS on sda3, internal journal
Dec 30 23:51:24 goslinux kernel: [   30.024030] intel8x0_measure_ac97_clock: measured 55413 usecs (2665 samples)
Dec 30 23:51:24 goslinux kernel: [   30.024035] intel8x0: clocking to 48000
Dec 30 23:51:24 goslinux kernel: [   32.144390] kjournald starting.  Commit interval 5 seconds
Dec 30 23:51:24 goslinux kernel: [   32.144620] EXT3 FS on sda6, internal journal
Dec 30 23:51:24 goslinux kernel: [   32.144629] EXT3-fs: mounted filesystem with writeback data mode.
Dec 30 23:51:24 goslinux kernel: [   32.562938] __ratelimit: 6 callbacks suppressed
Dec 30 23:51:24 goslinux kernel: [   32.562943] type=1505 audit(1262217081.901:13): operation="profile_replace" pid=1058 name=/usr/share/gdm/guest-session/Xsession
Dec 30 23:51:24 goslinux kernel: [   32.566793] type=1505 audit(1262217081.905:14): operation="profile_replace" pid=1059 name=/sbin/dhclient3
Dec 30 23:51:24 goslinux kernel: [   32.567362] type=1505 audit(1262217081.905:15): operation="profile_replace" pid=1059 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 30 23:51:24 goslinux kernel: [   32.567663] type=1505 audit(1262217081.905:16): operation="profile_replace" pid=1059 name=/usr/lib/connman/scripts/dhclient-script
Dec 30 23:51:24 goslinux kernel: [   32.576401] type=1505 audit(1262217081.917:17): operation="profile_replace" pid=1060 name=/usr/bin/evince
Dec 30 23:51:24 goslinux kernel: [   32.586462] type=1505 audit(1262217081.925:18): operation="profile_replace" pid=1060 name=/usr/bin/evince-previewer
Dec 30 23:51:24 goslinux kernel: [   32.592692] type=1505 audit(1262217081.933:19): operation="profile_replace" pid=1060 name=/usr/bin/evince-thumbnailer
Dec 30 23:51:24 goslinux kernel: [   32.601231] type=1505 audit(1262217081.941:20): operation="profile_replace" pid=1061 name=/usr/lib/cups/backend/cups-pdf
Dec 30 23:51:24 goslinux kernel: [   32.602295] type=1505 audit(1262217081.941:21): operation="profile_replace" pid=1061 name=/usr/sbin/cupsd
Dec 30 23:51:24 goslinux kernel: [   32.606254] type=1505 audit(1262217081.945:22): operation="profile_replace" pid=1062 name=/usr/sbin/mysqld-akonadi
Dec 30 23:51:25 goslinux kernel: [   35.766113] b43-pci-bridge 0000:00:0e.0: PCI INT A disabled
Dec 30 23:51:25 goslinux kernel: [   35.866466] eth0: link down
Dec 30 23:51:25 goslinux kernel: [   35.866741] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 30 23:51:28 goslinux kernel: [   39.300896] CPU0 attaching NULL sched-domain.
Dec 30 23:51:28 goslinux kernel: [   39.300906] CPU1 attaching NULL sched-domain.
Dec 30 23:51:28 goslinux kernel: [   39.313090] CPU0 attaching sched-domain:
Dec 30 23:51:28 goslinux kernel: [   39.313096]  domain 0: span 0-1 level SIBLING
Dec 30 23:51:28 goslinux kernel: [   39.313101]   groups: 0 1
Dec 30 23:51:28 goslinux kernel: [   39.313110] CPU1 attaching sched-domain:
Dec 30 23:51:28 goslinux kernel: [   39.313113]  domain 0: span 0-1 level SIBLING
Dec 30 23:51:28 goslinux kernel: [   39.313116]   groups: 1 0
Dec 30 23:53:52 goslinux kernel: [  183.356821] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Dec 30 23:53:52 goslinux kernel: [  183.356978] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 30 23:54:03 goslinux kernel: [  194.156010] eth0: no IPv6 routers present

```

---

### Post by chenxiaolong on 2009-12-30
Goslings, does your wireless work if you run [COLOR="DarkOrchid"]sudo modprobe b43[/COLOR]? If it does, you can add [COLOR="DarkOrchid"]modprobe b43[/COLOR] right above the [COLOR="SeaGreen"]exit 0[/COLOR] line in [COLOR="Sienna"]/etc/rc.local[/COLOR].

Also (to everyone), I've updated my original post with the links to my script. You can change them however you want, but please let me know what changes you made.

---

### Post by TironN on 2009-12-31
I've been trying to get this b43 stuff working for ages now!
Trying your kernel script now, hopefully this and your help I will be able to have everything going!

---

### Post by goslings on 2009-12-31
Does this not mean i would have enter root passwd every time 
+It worked in 9.04 without workarounds 
I love the odd tinker with Ubuntu, but there are limits, every time it is a pain with wireless 

> **chenxiaolong said:**
> Goslings, does your wireless work if you run [COLOR="DarkOrchid"]sudo modprobe b43[/COLOR]? If it does, you can add [COLOR="DarkOrchid"]modprobe b43[/COLOR] right above the [COLOR="SeaGreen"]exit 0[/COLOR] line in [COLOR="Sienna"]/etc/rc.local[/COLOR].


---

### Post by chenxiaolong on 2009-12-31
Goslings: No, you will not have to enter your root password every time it boots because all the lines in [COLOR="DarkOrchid"]/etc/rc.local[/COLOR] are run as root. So, no password :D.

---

### Post by TironN on 2009-12-31
Hey I'm using a dell mini 9 so its not Amd 64 or i386. Its i686.
So do I use the amd or i386 .debs for this?

---

### Post by chenxiaolong on 2009-12-31
i386.

By the way, debs for what?

---

### Post by DarkAngel88 on 2009-12-31
Multiple problems with your script.  The script downloads the amd files if uname -m == i686.  Had to do the download manually.  Also, problem at line 239 in your script, missing a "esac" or something similar (tried changing the first case from "if uname -m == i386" to "if uname -m == i686").  In that particular case, the new kernel wasn't installed at all as it downloads and tries to install the amd version of the kernel into a Intel Atom cpu, you get the idea I'm pretty sure ;)

Also, your script should check if "patch" is installed prior to execute the patch command.  In my case (fresh system), "patch" wasn't installed and the b43 sources weren't patched at all.

Other than that, thanks for the script.  Will continue to see if this fixes my issue!

---

### Post by chenxiaolong on 2009-12-31
Ahh, I see. Thanks for the info. I was using the amd64 version of Ubuntu so the script worked fine for me. Also, I used "if [ "$(uname -m) == "i386" ]" because I thought Ubuntu x86 was i386 based; the LiveCD and the kernel debs end with i386. Oh well, I fixed the scripts.

---

### Post by goslings on 2009-12-31
> **chenxiaolong said:**
> Goslings: No, you will not have to enter your root password every time it boots because all the lines in [COLOR="DarkOrchid"]/etc/rc.local[/COLOR] are run as root. So, no password :D.

cheers works thanks very much 
Would like to find out why have to do this tweak, 
but that is for another year

Happy New Year

---

### Post by The Glidd on 2009-12-31
> **focwiz said:**
> Glidd,

Have you tried activating the STA driver while connected to the internet (wired)?  That's what I had to do to activate it.

Kevin


I tried that without any result.  I did put this into the terminal: 

[COLOR=DarkOrchid]modprobe b43

[COLOR=Black]And at least now I'm getting an option for wireless networks under network manager.  Simultaneously, the Broadcom B43 showed up under Hardware Drivers.  When I activate it though, (it says it's activated) nothing happens, either in network manager or with the wireless.

Did I blacklist or something somewhere in this process?
[/COLOR][/COLOR]

---

### Post by TironN on 2010-01-01
So I ran your shell scripts and the final result is this:

after a restart running 'sudo modprobe b43' I get:

```
FATAL: Error inserting b43 (/lib/modules/2.6.32-02063202-generic/updates/drivers/net/wireless/b43/b43.ko): Invalid module format

```

Whats going on here? Also dmesg has no DMA errors, lshw -c network is saying its using the b43 driver and modinfo b43 has this: "parm:           pio:enable(1) / disable(0) PIO mode (int)" at the bottom

Thanks, Fergus

---

### Post by The Glidd on 2010-01-01
> **The Glidd said:**
> I tried that without any result.  I did put this into the terminal: 

[COLOR=DarkOrchid]modprobe b43

[COLOR=Black]And at least now I'm getting an option for wireless networks under network manager.  Simultaneously, the Broadcom B43 showed up under Hardware Drivers.  When I activate it though, (it says it's activated) nothing happens, either in network manager or with the wireless.

Did I blacklist or something somewhere in this process?
[/COLOR][/COLOR]

Also, I just had a few moments of wireless signals being detected.  Network Manager even said I was connected to my router (just like old times!)  No pages loaded, though.  After a restart, no networks are being detected.
 
Also, under System > Administration > Hardware Drivers, both STA and b43 show up.  If I try and activate STA I get this:
[COLOR=Blue]
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log[/COLOR] 

And then if I go and activate b43, the dialog at the bottom of the Hardware Driver info screen says:
[COLOR=Blue]
A different version of this driver is in use.
[COLOR=Black]
Then I activate with the only change being that network manager has an option for wireless which didn't exist when I tried to install STA.[/COLOR]
[/COLOR]

---

### Post by goslings on 2010-01-02
> **goslings said:**
> cheers works thanks very much 
chenxiaolong 

Just whem I I though was all solved ....
Now on every boot up network wireless asks for wireless passwd 
and sudo modprobe b43 just hangs 

Luv Linux but for a couple of months after EVERY upgrade I always have problem

---

### Post by chenxiaolong on 2010-01-02
Wow, a lot of problems :(.

TironN: Could you post the output of [COLOR="DarkOrchid"]dmesg | tail[/COLOR] after running [COLOR="DarkOrchid"]sudo modprobe b43[/COLOR]. This will give me a look at why b43 isn't loading.

The Glidd: You definitely don't want to try and activate the STA driver and the b43 driver together. They fight for control over the wireless card and as a result, nothing works. Since you've been having problems, I suggest you to use the STA driver because it's stable (although proprietary). Here's how:

1. [COLOR="DarkOrchid"]sudo rmmod b43 ssb wl[/COLOR]
   Unloads the two wireless drivers.

2. [COLOR="DarkOrchid"]sudo apt-get --purge remove b43-fwcutter bcmwl-kernel-source[/COLOR]

3. Check the files in [COLOR="SeaGreen"]/etc/modprobe.d[/COLOR] and make sure that there ISN'T

[COLOR="SeaGreen"]blacklist wl[/COLOR]

in any of the files. Also make sure that there IS

[COLOR="SeaGreen"]blacklist b43
blacklist bcm43xx
blacklist ssb
blacklist b43legacy[/COLOR]

in one of the files. You can create a new one if you want to be more organized (file has to end in .conf).

4. Open [COLOR="SeaGreen"]/etc/modules[/COLOR] as root and check the file and make sure that there isn't a line with

[COLOR="SeaGreen"]b43[/COLOR]

and that there is a line with

[COLOR="SeaGreen"]wl[/COLOR]

5. [COLOR="DarkOrchid"]sudo apt-get install bcmwl-kernel-source[/COLOR]
   Reinstall bcmwl-kernel-source

Goslings: Could you post the output of [COLOR="DarkOrchid"]modinfo b43[/COLOR]?

---

### Post by goslings on 2010-01-02
> **chenxiaolong said:**
> Wow, a lot of problems :(.

Goslings: Could you post the output of [COLOR="DarkOrchid"]modinfo b43[/COLOR]?

It seems to be working again after a reboot (using Kino a lot at the moment)

```

ian@goslinux:~$ modinfo b43
filename:       /lib/modules/2.6.31-16-generic/updates/cw/b43.ko
firmware:       FW13
license:        GPL
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     3C72AF37EF2A8FE86721372
alias:          pcmcia:m02D0c0476f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m02D0c0448f*fn*pfn*pa*pb*pc*pd*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        pcmcia,ssb,mac80211,led-class,cfg80211,pcmcia_core
vermagic:       2.6.31-16-generic SMP mod_unload modversions 586 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)

```

---

### Post by emas80 on 2010-01-03
Hi! And happy new year :-) 
Sorry I was away during the last days

> **chenxiaolong said:**
> Emas80, are you using the 2.6.32.2 kernel from the Ubuntu kernel PPA? I'm a little confused when you said kernel source directory. Is it /usr/src/linux-source-2.6.32 or is it /usr/src/linux-headers-2.6.32-*-generic? Thank you.

I'm not using Ubuntu kernel, I downloaded kernel sources directly from [www.kernel.org]("http://www.kernel.org"), so when I untarred the file, usually in /usr/src/, it created a dir called linux-2.6.32.2. Ubuntu kernels instead when untarred create directory called linux-***source***-2.6.xxxx.
I think that that patches should apply with no many problems on Ubuntu version of 2.6.32 kernel.

---

### Post by emas80 on 2010-01-03
> **goslings said:**
> Just whem I I though was all solved ....
Now on every boot up network wireless asks for wireless passwd 
and sudo modprobe b43 just hangs 

Luv Linux but for a couple of months after EVERY upgrade I always have problem

Hi, your *modinfo*s looks right, if wifi keeps asking for password, your card is detected and driver is already loaded, maybe this is causing the hangs on modprobe b43.
About the password, I'm not sure, maybe it lost the "remember pwd", or the connect automatically, or couldn't connect because some sort of problem occurred.. I had the same problem on Windows, with another notebook, sometime wifi is not detected on boot time and I should connect manually, and I should try many times before it worked.
But I think that looking at the output of dmesg when this error occurs (e.g. just after boot) should help us identifying the problem,
After a correct boot with wifi found, enabled and connected my last dmesg lines are
```
[  988.371533] wlan0: deauthenticating from 00:1d:6a:ec:18:45 by local choice (reason=3)
[  988.373729] wlan0: direct probe to AP 00:1d:6a:ec:18:45 (try 1)
[  988.376187] wlan0: direct probe responded
[  988.376197] wlan0: authenticate with AP 00:1d:6a:ec:18:45 (try 1)
[  988.378502] wlan0: authenticated
[  988.378553] wlan0: associate with AP 00:1d:6a:ec:18:45 (try 1)
[  988.382002] wlan0: RX AssocResp from 00:1d:6a:ec:18:45 (capab=0x431 status=0 aid=1)
[  988.382033] wlan0: associated
[  988.384550] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  988.385491] cfg80211: Calling CRDA for country: IT
[  988.389714] cfg80211: Received country IE:
[  988.389721] cfg80211: Regulatory domain: IT
[  988.389725]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  988.389733]     (2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[  988.389737] cfg80211: CRDA thinks this should applied:
[  988.389741] cfg80211: Regulatory domain: IT
[  988.389745]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  988.389751]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  988.389757]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  988.389763]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  988.389769]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  988.389773] cfg80211: We intersect both of these and get:
[  988.389777] cfg80211: Regulatory domain: 98
[  988.389781]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  988.389787]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  988.389797] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[  988.389804] cfg80211: Current regulatory domain updated by AP to: IT
[  988.389808]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  988.389814]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  998.601110] wlan0: no IPv6 routers present
```I agree with you about Ubuntu problems after EACH upgrade, maybe Ubuntu is too user friendly so everyone (me too!) upgrades without reading the changelogs and readmes, and just after everything stops working they realizes that developers changed that and added those, so *maybe this could possibly cause some problems on people who use <yes, it is really your card/pc here>*. 
I have been using Ubuntu for 3 years, and I made the last 3 upgrades over one month after they released the OS, after browsed forums and discovered possible problems and workarounds. I work with my pc and I really cannot stay without my video card because someone changed something that WAS ALREADY WORKING PRETTY WELL and *forgot* to test it with my hardware. Yes I know it is not easy, and it's quite impossible, I'm a software engineer too :-) .
I've always fixed everything is important to me (I gave up with hibernate, after EACH kernel revision it works, if before didn't, or it stops working, if before it did), so I can go on with this, and I've no time to try Gentoo, but one day I will :-)

---

### Post by The Glidd on 2010-01-03
> **chenxiaolong said:**
> Wow, a lot of problems :(.
The Glidd: You definitely don't want to try and activate the STA driver and the b43 driver together. They fight for control over the wireless card and as a result, nothing works. Since you've been having problems, I suggest you to use the STA driver because it's stable (although proprietary). Here's how:

1. [COLOR=DarkOrchid]sudo rmmod b43 ssb wl[/COLOR]
   Unloads the two wireless drivers.

2. [COLOR=DarkOrchid]sudo apt-get --purge remove b43-fwcutter bcmwl-kernel-source[/COLOR]

3. Check the files in [COLOR=SeaGreen]/etc/modprobe.d[/COLOR] and make sure that there ISN'T

[COLOR=SeaGreen]blacklist wl[/COLOR]

in any of the files. Also make sure that there IS

[COLOR=SeaGreen]blacklist b43
blacklist bcm43xx
blacklist ssb
blacklist b43legacy[/COLOR]

in one of the files. You can create a new one if you want to be more organized (file has to end in .conf).

4. Open [COLOR=SeaGreen]/etc/modules[/COLOR] as root and check the file and make sure that there isn't a line with


[COLOR=SeaGreen]b43[/COLOR]

and that there is a line with

[COLOR=SeaGreen]wl[/COLOR]

5. [COLOR=DarkOrchid]sudo apt-get install bcmwl-kernel-source[/COLOR]
   Reinstall bcmwl-kernel-source
[COLOR=Blue]
Thanks, I'm following each of these as we speak.  Incidentally, the wireless inexplicably tried to connect last night.  It won't accept my WPA password, though.  So I'm proceeding with the above, anyway.
[/COLOR] 
1. [COLOR=DarkOrchid]sudo rmmod b43 ssb wl[/COLOR]
   Unloads the two wireless drivers.

[COLOR=Blue]-I get:[/COLOR] **[COLOR=Blue]ERROR: Module wl does not exist in /proc/modules[/COLOR]**

2. [COLOR=DarkOrchid]sudo apt-get --purge remove b43-fwcutter bcmwl-kernel-source[/COLOR]

[COLOR=Blue]-ok[/COLOR]

3. Check the files in [COLOR=SeaGreen]/etc/modprobe.d[/COLOR] and make sure that there ISN'T

[COLOR=SeaGreen]blacklist wl[/COLOR]

in any of the files. Also make sure that there IS

[COLOR=SeaGreen]blacklist b43
blacklist bcm43xx
blacklist ssb
blacklist b43legacy[/COLOR]

in one of the files. You can create a new one if you want to be more organized (file has to end in .conf).

[COLOR=Blue]i get:
[B]
 alsa-base.conf           blacklist-framebuffer.conf  blacklist-wl.conf
blacklist-ath_pci.conf   blacklist-modem.conf        libpisock9.conf
blacklist.conf           [COLOR=Cyan]blacklist-oss.conf          oss-compat.conf[/COLOR]
blacklist-firewire.conf  blacklist-watchdog.conf
[/B] 
The ones in aqua blue appear as such in the terminal.
[/COLOR] 
4. Open [COLOR=SeaGreen]/etc/modules[/COLOR] as root and check the file and make sure that there isn't a line with


[COLOR=SeaGreen]b43[/COLOR]

and that there is a line with

[COLOR=SeaGreen]wl
[COLOR=Blue]
- sorry, I don't know how open that as root, exactly.  I'm still fairly new to ubuntu!
[/COLOR][/COLOR]
5. [COLOR=DarkOrchid]sudo apt-get install bcmwl-kernel-source[/COLOR]
   Reinstall bcmwl-kernel-source
[COLOR=SeaGreen][COLOR=Blue]
-ok, I'll restart now.

Upon restart, there's no option for wireless under network manager.  Broadcom STA shows up under hardware drivers (no b43!) but when I try to activate, I get:
[B]
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log[/B]

I don't know how to look at this log file.  When I put this into terminal, it tell me I don't have permission.

I have a hunch this has something to do with what's blacklisted above, but I have no idea how to resolve this!
[/COLOR] [/COLOR]

---

### Post by chenxiaolong on 2010-01-03
Can you post the contents of /var/log/jockey.log?

You can open the file by running:

sudo cat /var/log/jockey.log

Whenever you run a command with sudo *command*, the command runs with root privileges; it means **S**uper **U**ser **DO**es *command* :D.

EDIT: About the blacklists: What I meant by that step was to open each of the files in /etc/modprobe.d to check for the lines. An easier was to open the folder as root, where you can double click the files to open them:

gksu nautilus /etc/modprobe.d

GKSU is the graphical version of sudo, which is better for running graphical programs.

Good luck. I hope this works for you.

---

### Post by The Glidd on 2010-01-03
> **chenxiaolong said:**
> Wow, a lot of problems :(.

TironN: Could you post the output of [COLOR=DarkOrchid]dmesg | tail[/COLOR] after running [COLOR=DarkOrchid]sudo modprobe b43[/COLOR]. This will give me a look at why b43 isn't loading.

The Glidd: You definitely don't want to try and activate the STA driver and the b43 driver together. They fight for control over the wireless card and as a result, nothing works. Since you've been having problems, I suggest you to use the STA driver because it's stable (although proprietary). Here's how:

1. [COLOR=DarkOrchid]sudo rmmod b43 ssb wl[/COLOR]
   Unloads the two wireless drivers.

2. [COLOR=DarkOrchid]sudo apt-get --purge remove b43-fwcutter bcmwl-kernel-source[/COLOR]

3. Check the files in [COLOR=SeaGreen]/etc/modprobe.d[/COLOR] and make sure that there ISN'T

[COLOR=SeaGreen]blacklist wl[/COLOR]

in any of the files. Also make sure that there IS

[COLOR=SeaGreen]blacklist b43
blacklist bcm43xx
blacklist ssb
blacklist b43legacy[/COLOR]

in one of the files. You can create a new one if you want to be more organized (file has to end in .conf).

4. Open [COLOR=SeaGreen]/etc/modules[/COLOR] as root and check the file and make sure that there isn't a line with

[COLOR=SeaGreen]b43[/COLOR]

and that there is a line with

[COLOR=SeaGreen]wl[/COLOR]

5. [COLOR=DarkOrchid]sudo apt-get install bcmwl-kernel-source[/COLOR]
   Reinstall bcmwl-kernel-source

Goslings: Could you post the output of [COLOR=DarkOrchid]modinfo b43[/COLOR]?

Here are the contents of the log file:

2010-01-03 19:15:30,215 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-01-03 19:15:30,248 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-01-03 19:15:30,249 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-01-03 19:15:30,252 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-01-03 19:15:30,255 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-71
2010-01-03 19:15:30,256 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-01-03 19:15:30,258 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-01-03 19:15:30,258 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-01-03 19:15:31,553 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-01-03 19:15:31,560 DEBUG: Software modem not available
2010-01-03 19:15:31,561 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-01-03 19:15:31,572 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-01-03 19:15:31,572 DEBUG: Firmware for DVB cards not available
2010-01-03 19:15:31,572 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-01-03 19:15:31,582 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-01-03 19:15:31,582 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-01-03 19:15:31,582 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-01-03 19:15:31,587 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-03 19:15:31,588 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-01-03 19:15:31,589 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-01-03 19:15:31,589 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-01-03 19:15:31,593 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-01-03 19:15:31,594 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-01-03 19:15:31,594 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-01-03 19:15:31,594 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-01-03 19:15:31,604 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-01-03 19:15:31,604 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-01-03 19:15:31,607 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-01-03 19:15:31,607 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-01-03 19:15:31,607 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-01-03 19:15:31,611 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-01-03 19:15:31,613 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-01-03 19:15:31,619 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-01-03 19:15:31,619 DEBUG: all custom handlers loaded
2010-01-03 19:15:31,620 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-01-03 19:15:31,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-01-03 19:15:31,979 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:31,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-01-03 19:15:31,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-01-03 19:15:31,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:)NP0800:')
2010-01-03 19:15:31,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:)NP0303:')
2010-01-03 19:15:31,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:31,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-03 19:15:31,989 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:31,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-03 19:15:31,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-03 19:15:32,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-01-03 19:15:32,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-03 19:15:32,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:)NP0C01:')
2010-01-03 19:15:32,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'platform:dcdbas')
2010-01-03 19:15:32,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-01-03 19:15:32,043 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,043 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'platform:eisa')
2010-01-03 19:15:32,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-01-03 19:15:32,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,047 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-01-03 19:15:32,049 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-01-03 19:15:32,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:)NP0000:')
2010-01-03 19:15:32,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-01-03 19:15:32,052 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:)NP0F13:')
2010-01-03 19:15:32,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-03 19:15:32,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-03 19:15:32,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:)NP0C02:')
2010-01-03 19:15:32,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc02ip00')
2010-01-03 19:15:32,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-01-03 19:15:32,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-01-03 19:15:32,058 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-01-03 19:15:32,058 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,058 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-01-03 19:15:32,059 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-01-03 19:15:32,059 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-01-03 19:15:32,059 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,059 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA07:bd05/13/2009:svnDellInc.:)nInspiron1545:)vr:rvnDellInc.:rn0G848F:rvr:cvnDellInc.:ct8:cvr:')
2010-01-03 19:15:32,077 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,077 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,077 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:)NP0200:')
2010-01-03 19:15:32,077 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-01-03 19:15:32,078 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-03 19:15:32,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-01-03 19:15:32,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:)NP0103:)NP0C01:')
2010-01-03 19:15:32,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-01-03 19:15:32,084 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:)NP0C04:')
2010-01-03 19:15:32,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-01-03 19:15:32,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-03 19:15:32,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:)NP0B00:')
2010-01-03 19:15:32,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc01ip00')
2010-01-03 19:15:32,095 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-01-03 19:15:32,147 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-03 19:15:32,147 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-01-03 19:15:32,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,147 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-03 19:15:32,147 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-01-03 19:15:32,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'platform:)cspkr')
2010-01-03 19:15:32,148 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,148 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-03 19:15:32,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-01-03 19:15:32,159 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-01-03 19:15:32,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'input:b0003v05CAp180Ae8730-e0,1,kD4,ramlsfw')
2010-01-03 19:15:32,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-03 19:15:32,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x97fe80c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-03 19:15:32,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-01-03 19:15:32,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-01-03 19:15:32,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-01-03 19:15:32,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-01-03 19:15:32,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-03 19:15:32,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-01-03 19:15:32,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-03 19:15:32,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-03 19:15:32,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-03 19:15:32,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-01-03 19:15:32,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-03 19:15:32,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-03 19:15:32,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'platform:dcdbas')
2010-01-03 19:15:32,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-01-03 19:15:32,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'platform:eisa')
2010-01-03 19:15:32,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-01-03 19:15:32,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-01-03 19:15:32,165 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-01-03 19:15:32,165 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-03 19:15:32,165 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-01-03 19:15:32,165 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-01-03 19:15:32,165 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-03 19:15:32,165 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-03 19:15:32,165 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-03 19:15:32,165 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc02ip00')
2010-01-03 19:15:32,165 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-01-03 19:15:32,165 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-01-03 19:15:32,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-01-03 19:15:32,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-01-03 19:15:32,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-01-03 19:15:32,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-01-03 19:15:32,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA07:bd05/13/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn0G848F:rvr:cvnDellInc.:ct8:cvr:')
2010-01-03 19:15:32,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-03 19:15:32,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-01-03 19:15:32,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-03 19:15:32,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-01-03 19:15:32,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-01-03 19:15:32,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-01-03 19:15:32,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-03 19:15:32,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-01-03 19:15:32,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-03 19:15:32,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-03 19:15:32,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc01ip00')
2010-01-03 19:15:32,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-01-03 19:15:32,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'platform:pcspkr')
2010-01-03 19:15:32,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-03 19:15:32,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-01-03 19:15:32,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-01-03 19:15:32,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-01-03 19:15:32,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'input:b0003v05CAp180Ae8730-e0,1,kD4,ramlsfw')
2010-01-03 19:15:32,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b45fac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-03 19:15:32,217 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-03 19:15:32,378 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-03 19:15:32,409 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-03 19:15:34,948 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-03 19:15:39,331 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-01-03 19:15:39,342 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-03 19:15:45,906 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-03 19:15:45,919 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-03 19:15:45,942 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

And I just opened up Nautilus:

Here are the contents of modprobe.d:

blacklist-wl
alsa-base.conf
blacklist.conf
blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf (has an arrow shooting off the icon)
blacklist-watchdog.conf
libpisock9.conf
oss-compat.conf (has an arrow shooting off the icon)

Thanks!

---

### Post by k3Rn on 2010-01-03
Hi chenxiaolong,

i've been trying hard to get the b43 driver to work on my dell mini 10 - =/
what a mess!

I now manually installed the 2.6.32 kernel (2.6.32-02063202-generic).

Your b43_compile script prompts some errors.

Here is the output of your script:

```

b43 Kernel Source Patcher: The exciting part 2!
-------------------------------------------------
Remember, you must me booted in your 2.6.32.2 kernel before you continue.
Do you want to continue?
(yes/no):
yes
The b43 driver will be unloaded before the script continues.

ERROR: Module b43 does not exist in /proc/modules
[: 120: !=: unexpected operator
Compiling the modules needed for compiling the kernel module b43 (hmmm...needs rewording :D). [Might need password for sudo]
scripts/kconfig/conf -s arch/x86/Kconfig
***
*** You have not yet configured your kernel!
*** (missing kernel config file ".config")
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `modules_prepare'.  Stop.

Now for what we've been waiting for...the b43 compilation!!! YAY!!! [Also might need password for sudo]


  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


  WARNING: Symbol version dump /usr/src/linux-source-2.6.32/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
/usr/src/linux-source-2.6.32/scripts/Makefile.modpost:42: include/config/auto.conf: No such file or directory
make[1]: *** No rule to make target `include/config/auto.conf'.  Stop.
make: *** [modules] Error 2
Please enter your password if asked.
The commands being run are:
--------------------------------------
sudo mkdir /lib/modules/2.6.32-02063202-generic/updates/drivers > /dev/null
sudo mkdir /lib/modules/2.6.32-02063202-generic/updates/drivers/net > /dev/null
sudo mkdir /lib/modules/2.6.32-02063202-generic/updates/drivers/net/wireless > /dev/null
sudo mkdir /lib/modules/2.6.32-02063202-generic/updates/drivers/net/wireless/b43 > /dev/null
mkdir: cannot create directory `/lib/modules/2.6.32-02063202-generic/updates/drivers': No such file or directory
mkdir: cannot create directory `/lib/modules/2.6.32-02063202-generic/updates/drivers/net': No such file or directory
mkdir: cannot create directory `/lib/modules/2.6.32-02063202-generic/updates/drivers/net/wireless': No such file or directory
mkdir: cannot create directory `/lib/modules/2.6.32-02063202-generic/updates/drivers/net/wireless/b43': No such file or directory

Please enter your password is asked (again :( ).
The command being run is: "sudo depmod -a"

Enabling PIO Mode
options b43 pio=1

Loading b43 module... (ARGH, PASSWORDS!!!)
FATAL: Error inserting b43 (/lib/modules/2.6.32-02063202-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

YAY!!! EVERYTHING IS DONE!!! :D:D:D
Now, just check the files in "/etc/modprobe.d/" and make sure they don't contain:

blacklist b43
blacklist ssb

Now that was easy wasn't it? :) Enjoy your wireless!

```Output of modprobe b43:

```

k3rn@kernkraft:~$ sudo modprobe b43
FATAL: Error inserting b43 (/lib/modules/2.6.32-02063202-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```Here the dmesg output:

```

  733.221499] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  733.221521] b43-phy0: Controller RESET (DMA error) ...
[  733.221534] Controller restarted
[  733.464455] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  738.985499] b43-phy0: Controller restarted
[  738.986504] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  738.986539] b43-phy0: Controller RESET (DMA error) ...
[  739.216428] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  744.733448] b43-phy0: 
[  744.733460] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  744.733481] b43-phy0: Controller RESET (DMA error) ...
[  744.733494] Controller restarted
[  744.972443] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  750.489450] b43-phy0: 
[  750.489461] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  750.489482] b43-phy0: Controller RESET (DMA error) ...
[  750.489495] Controller restarted
[  750.645367] b43-pci-bridge 0000:03:00.0: PCI INT A disabled
[  754.773778] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  754.773814] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[  754.840602] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[  754.867234] b43: Unknown parameter `pio'
[  754.915106] b43: Unknown parameter `pio'
[ 1352.172081] b43: Unknown parameter `pio'
[ 2107.124385] b43-pci-bridge 0000:03:00.0: PCI INT A disabled
[ 2111.811660] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2111.811942] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[ 2111.876795] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 2111.901145] b43: Unknown parameter `pio'
[ 2111.933204] b43: Unknown parameter `pio'

```I hope you can help me to get it to work - in the end.

Greetings,
Markus

---

### Post by chenxiaolong on 2010-01-03
Delete the blacklist-wl file in /etc/modprobe.d (as root). Then restart and try again. If it still doesn't work, try plugging in your wired internet, then reactivating the STA Driver in the *Hardware Drivers*.

---

### Post by howcanireachthesekids on 2010-01-04
**Chienxialong, **first of all i want to thank you for taking your time to make this guide that i am sure it helped many Broadcom users.
I would like to ask you some questions if you could possibly help me with this issue.
I have a HP Pavilion DV6-1020el laptop which uses Broadcom BCM4312 (rev 01) card.
[CENTER][LEFT]It is **14e4:4315.  **I have installed Ubuntu 9.04 using the option "Inside Windows" and given it a 17 GB harddisk. 
[CENTER][LEFT]So the driver **wl** is loaded to get my card working.But as you know, this driver does not support monitor mode. I want to try monitor mode with injection, which i herd works with [B]14e4:4315. 
[FONT=Arial]I think i know what to do.I should blacklist the wl driver and get b43 driver to work.But to do this i am a little stuck.I am not that good with Linux.[/FONT][/B][FONT=Arial]
**[COLOR=Black]So i am asking you, [/COLOR]which options of your guide should i use ?**
**Can you guide me with specifics into getting my card ( which is the same as yours) **
**to work in monitor mode with injection.I want to learn about WEP cracking for EDUCATIONAL PURPOSES ONLY !!!!**[/FONT]
Also, if i would be using Ubuntu 9.10 on full hard disk installation, which part of your guide should i use ?
and do i need internet connection to make the card work ? because the only way i can get internet is by wireless but since the card would not work in 9.10 ( i have tried it ) i dont think i can get internet other ways. i can just download the neccessary files and put them in USB.
or will try connecting in 9.10 via using the wireless in my nokia E71 using bluetooth connection with the laptop then...
[/LEFT]
[/CENTER]
[B]
Thank you in advance.
[/B][/LEFT]
[/CENTER]

---

### Post by chenxiaolong on 2010-01-04
Yesssss, snow day, no school!

Anyway,

howcanireachthesekids: Unfortunately, you need kernel 2.6.32, which can only be installed on Ubuntu 9.10, not Ubuntu 9.04. The wireless doesn't work by default in Ubuntu 9.10 because the Ubuntu developers decided not to include the wl driver for the standard install, unlike Ubuntu 8.04-9.04. You should install Ubuntu 9.10 first, then come back to this thread. I'll give you some steps later because I'll still trying to fix this problem. There's no fool-proof solution yet :(.

K3rn: could you try running these commands:

```

cd /usr/src/linux-source-2.6.32       #Change to source directory
sudo make oldconfig                   #Use the default (I think) settings for make
sudo make prepare                     #Prepares make to compile kernel
sudo make modules_prepare             #Prepares make to compile kernel modules
sudo make modules SUBDIRS=drivers/net/wireless/b43 #Compiles b43
sudo rmmod b43 ssb wl                 #Unload in-use modules
cd /lib/modules/`uname -r`/kernel/drivers/net/wireless/b43 #Change to b43 directory of current kernel
sudo mv b43.ko b43.ko.backup          #Backup current b43 module
sudo cp /usr/src/linux-source-2.6.32/drivers/net/wireless/b43/b43.ko ./ #Copies new b43 driver to the kernel modules directory (where the drivers are)
sudo modprobe ssb                    # 0R REBOOT
sudo modprobe b43 pio=1              # OR REBOOT

```

Hope that helps

---

### Post by howcanireachthesekids on 2010-01-04
> **chenxiaolong said:**
> Yesssss, snow day, no school!

Anyway,

howcanireachthesekids: Unfortunately, you need kernel 2.6.32, which can only be installed on Ubuntu 9.10, not Ubuntu 9.04. The wireless doesn't work by default in Ubuntu 9.10 because the Ubuntu developers decided not to include the wl driver for the standard install, unlike Ubuntu 8.04-9.04. You should install Ubuntu 9.10 first, then come back to this thread. I'll give you some steps later because I'll still trying to fix this problem. There's no fool-proof solution yet :(.


Well i appreciate your quick reply :)
Ok i will install Ubuntu 9.10 with kernel 2.6.32 on fresh installation in the entire HDD. I will try to get internet access to download any necessary packages/files via ethernet cable or somehow using my Nokia E71 with bluetooth connection and the laptop.
Then what do you suggest ? Which guide steps ?

Thanks

---

### Post by k3Rn on 2010-01-04
Hi chenxiaolong,

thank you for the fast reply.

I did run the commands, here is the complete log/output:

```

k3rn@kernkraft:~$ cd /usr/src/linux-source-2.6.3
linux-source-2.6.31/ linux-source-2.6.32/ 
k3rn@kernkraft:~$ cd /usr/src/linux-source-2.6.32
k3rn@kernkraft:/usr/src/linux-source-2.6.32$ sudo make oldconfig
[sudo] password for k3rn: 
scripts/kconfig/conf -o arch/x86/Kconfig
#
# using defaults found in /boot/config-2.6.32-02063202-generic
#
#
# configuration written to .config
#
k3rn@kernkraft:/usr/src/linux-source-2.6.32$ sudo make prepare
scripts/kconfig/conf -s arch/x86/Kconfig
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
  CC      kernel/bounds.s
  GEN     include/linux/bounds.h
  CC      arch/x86/kernel/asm-offsets.s
  GEN     include/asm/asm-offsets.h
  CALL    scripts/checksyscalls.sh
k3rn@kernkraft:/usr/src/linux-source-2.6.32$ sudo make modules_prepare
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
  CALL    scripts/checksyscalls.sh
  HOSTCC  scripts/genksyms/genksyms.o
  SHIPPED scripts/genksyms/lex.c
  SHIPPED scripts/genksyms/parse.h
  SHIPPED scripts/genksyms/keywords.c
  HOSTCC  scripts/genksyms/lex.o
  SHIPPED scripts/genksyms/parse.c
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
scripts/mod/modpost.c: In function ‘get_markers’:
scripts/mod/modpost.c:1562: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
scripts/mod/modpost.c: In function ‘add_marker’:
scripts/mod/modpost.c:1982: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/selinux/mdp/mdp
  HOSTCC  scripts/kallsyms
scripts/kallsyms.c: In function ‘read_symbol’:
scripts/kallsyms.c:112: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/conmakehash

---

k3rn@kernkraft:/usr/src/linux-source-2.6.32$ ls drivers/net/wireless/b43
b43.h                        dma.c    lo.h           pcmcia.h      phy_g.h   pio.h     sysfs.h         tables_nphy.h
b43_kernel_2.6.32.2.patch    dma.h    main.c         phy_a.c       phy_lp.c  rfkill.c  tables.c        wa.c
b43_kernel_2.6.32.2.patch.1  Kconfig  main.h         phy_a.h       phy_lp.h  rfkill.h  tables.h        wa.h
b43_kernel_2.6.32.2.patch.2  leds.c   Makefile       phy_common.c  phy_n.c   sdio.c    tables_lpphy.c  xmit.c
debugfs.c                    leds.h   modules.order  phy_common.h  phy_n.h   sdio.h    tables_lpphy.h  xmit.h
debugfs.h                    lo.c     pcmcia.c       phy_g.c       pio.c     sysfs.c   tables_nphy.c
k3rn@kernkraft:/usr/src/linux-source-2.6.32$ sudo make modules SUBDIRS=drivers/net/wireless/b43

  WARNING: Symbol version dump /usr/src/linux-source-2.6.32/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  drivers/net/wireless/b43/main.o
  CC [M]  drivers/net/wireless/b43/tables.o
  CC [M]  drivers/net/wireless/b43/phy_common.o
  CC [M]  drivers/net/wireless/b43/phy_g.o
  CC [M]  drivers/net/wireless/b43/phy_a.o
  CC [M]  drivers/net/wireless/b43/phy_lp.o
drivers/net/wireless/b43/phy_lp.c:382: warning: ‘lpphy_restore_dig_flt_state’ defined but not used
drivers/net/wireless/b43/phy_lp.c:890: warning: ‘lpphy_disable_rx_gain_override’ defined but not used
  CC [M]  drivers/net/wireless/b43/tables_lpphy.o
  CC [M]  drivers/net/wireless/b43/sysfs.o
  CC [M]  drivers/net/wireless/b43/xmit.o
  CC [M]  drivers/net/wireless/b43/lo.o
  CC [M]  drivers/net/wireless/b43/wa.o
  CC [M]  drivers/net/wireless/b43/dma.o
  CC [M]  drivers/net/wireless/b43/pio.o
  CC [M]  drivers/net/wireless/b43/rfkill.o
  CC [M]  drivers/net/wireless/b43/leds.o
  LD [M]  drivers/net/wireless/b43/b43.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      drivers/net/wireless/b43/b43.mod.o
  LD [M]  drivers/net/wireless/b43/b43.ko
k3rn@kernkraft:/usr/src/linux-source-2.6.32$ sudo rmmod b43 ssb wl
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module wl does not exist in /proc/modules

```When trying to load the b43 module i get the following error now:

```

sudo modprobe b43 pio=1
[sudo] password for k3rn: 
FATAL: Error inserting b43 (/lib/modules/2.6.32-02063202-generic/kernel/drivers/net/wireless/b43/b43.ko): Invalid module format

```

dmesg prompts:

```
 b43: no symbol version for module_layout

```

I don't know what to try else - please have a second look at it. 

Thank you in advance!

---

### Post by The Glidd on 2010-01-04
> **chenxiaolong said:**
> Delete the blacklist-wl file in /etc/modprobe.d (as root). Then restart and try again. If it still doesn't work, try plugging in your wired internet, then reactivating the STA Driver in the *Hardware Drivers*.

I deleted the blacklist-wl file in /etc/modprobe.d using nautilus.  When I return via nautilus, there's no blacklist-wl anywhere to be seen.  I then tried to activate the STA driver (while wired) and restarted.  Then I get:

This driver is activated but not currently in use.  

There's no wireless dialog to speak of in network manager.

---

### Post by TironN on 2010-01-05
Ok. After a mod probe dmesg gives me:

```
[   659.512320] b43: no symbol version for module_layout
```

> **k3Rn said:**
> dmesg prompts:

 	Code:
 	 b43: no symbol version for module_layout 
I don't know what to try else - please have a second look at it. 

Thank you in advance! 		                   		  		  		  		  		 		

Same as me!

---

### Post by emas80 on 2010-01-06
To [TironN]("http://ubuntuforums.org/member.php?u=934510") and [k3Rn]("http://ubuntuforums.org/member.php?u=936978"):
Which kernel are you using? It seems that is trying to insert a wrong module in running kernel, or something is missing with inserted module.
What's the result of
```
uname -a
``` and ```
modinfo b43
``` ?

The first command prints kernel actual version, while the second prints information about current b43 module version.

Maybe I just found this solution from another post:

Just copy the file Module.symversion from /lib/modules/your-kernel-name into the kernel source location (=/usr/src/linux-source-2.6.32).

I don't know why this file is missing, but [k3Rn]("http://ubuntuforums.org/member.php?u=936978") do you remember the warning about "Symbol version dump missing" when running [chenxiaolong]("http://ubuntuforums.org/member.php?u=724117")'s script? I think that is related.

If it still doesn't work, I think that recompiling (and of course installing) all the kernel, and not only modules, should work, fixing all these little problems.

---

### Post by howcanireachthesekids on 2010-01-07
bump, i need help :(

---

### Post by k3Rn on 2010-01-07
@emas80: i couldn't find any modules.symversion file in my system.

for now i give up on this topic, i don't have enough time at the moment.

i'll keep track on this thread here and will try it again with a fresh ubuntu install when i find the time.

anyway thank you guys for the help so far - i'll be back sometime :)

greetz,

k3rn

---

### Post by gfa on 2010-01-08
**[COLOR="Red"][SOLVED] View next post :)[/COLOR]**

Hi chenxiaolong... I've run your commands, and got the same errors as K3rn... As I can see in his last message, he has no time to help you, but I really would like to get B43 in 2.6.32 so if you have any idea I could test ;)

After rebooting in new kernel, applying the patch and trying to insert the new kernel module I get:

```

FATAL: Error inserting b43 (/lib/modules/2.6.32-02063203-generic/updates/drivers/net/wireless/b43/b43.ko): Invalid module format
```

In dmesg I get:

```
b43: no symbol version for module_layout
```

I have tried stripping symbols in kernel, but then I get another error stating there're no symbols :S

Any help will be great :)

Thanks
gFa


> **chenxiaolong said:**
> 
K3rn: could you try running these commands:

```

cd /usr/src/linux-source-2.6.32       #Change to source directory
sudo make oldconfig                   #Use the default (I think) settings for make
sudo make prepare                     #Prepares make to compile kernel
sudo make modules_prepare             #Prepares make to compile kernel modules
sudo make modules SUBDIRS=drivers/net/wireless/b43 #Compiles b43
sudo rmmod b43 ssb wl                 #Unload in-use modules
cd /lib/modules/`uname -r`/kernel/drivers/net/wireless/b43 #Change to b43 directory of current kernel
sudo mv b43.ko b43.ko.backup          #Backup current b43 module
sudo cp /usr/src/linux-source-2.6.32/drivers/net/wireless/b43/b43.ko ./ #Copies new b43 driver to the kernel modules directory (where the drivers are)
sudo modprobe ssb                    # 0R REBOOT
sudo modprobe b43 pio=1              # OR REBOOT

```

Hope that helps

---

### Post by gfa on 2010-01-08
I have successfully compiled b43 module, just needed one more command:

```
cd /usr/src/linux-source-2.6.32       #Change to source directory
[COLOR="Red"]**sudo cp /usr/src/linux-headers-`uname -r`/Module.symvers ./  #Copy symbols dependencies**[/COLOR]
sudo make oldconfig                   #Use the default (I think) settings for make
sudo make prepare                     #Prepares make to compile kernel
sudo make modules_prepare             #Prepares make to compile kernel modules
sudo make modules SUBDIRS=drivers/net/wireless/b43 #Compiles b43
sudo rmmod b43 ssb wl                 #Unload in-use modules
cd /lib/modules/`uname -r`/kernel/drivers/net/wireless/b43 #Change to b43 directory of current kernel
sudo mv b43.ko b43.ko.backup          #Backup current b43 module
sudo cp /usr/src/linux-source-2.6.32/drivers/net/wireless/b43/b43.ko ./ #Copies new b43 driver to the kernel modules directory (where the drivers are)
[COLOR="Red"]**sudo depmod -a                       # Refresh modules**[/COLOR]
sudo modprobe ssb                    # 0R REBOOT
sudo modprobe b43 pio=1              # OR REBOOT
```

Now, I can insert the module... but my system freezes after few seconds (about 10 secs), any clue?

Thanks
gFa

---

### Post by TironN on 2010-01-08
> **gfa said:**
> I have successfully compiled b43 module, just needed one more command:

```
cd /usr/src/linux-source-2.6.32       #Change to source directory
[COLOR=Red]**sudo cp /usr/src/linux-headers-`uname -r`/Module.symvers ./  #Copy symbols dependencies**[/COLOR]
sudo make oldconfig                   #Use the default (I think) settings for make
sudo make prepare                     #Prepares make to compile kernel
sudo make modules_prepare             #Prepares make to compile kernel modules
sudo make modules SUBDIRS=drivers/net/wireless/b43 #Compiles b43
sudo rmmod b43 ssb wl                 #Unload in-use modules
cd /lib/modules/`uname -r`/kernel/drivers/net/wireless/b43 #Change to b43 directory of current kernel
sudo mv b43.ko b43.ko.backup          #Backup current b43 module
sudo cp /usr/src/linux-source-2.6.32/drivers/net/wireless/b43/b43.ko ./ #Copies new b43 driver to the kernel modules directory (where the drivers are)
[COLOR=Red]**sudo depmod -a                       # Refresh modules**[/COLOR]
sudo modprobe ssb                    # 0R REBOOT
sudo modprobe b43 pio=1              # OR REBOOT
```Now, I can insert the module... but my system freezes after few seconds (about 10 secs), any clue?

Thanks
gFa

I was getting the same errors and did the same thing (the header version) and got the same system freeze. It got so bad I have done a fresh installation (off a nikon camera no less (I'm overseas)) so hopefully it will work now!

---

### Post by chenxiaolong on 2010-01-08
Thanks for the information about the symbols dependencies. I've added that to the script and I reattached the script on my first post.

Sorry for the long wait. I've been studying for my midterms (I'm only a High School freshman. I have to take midterms :(). Anyway, I'll try and figure out why it freezes after ten seconds. If you want to remove the driver, you can always boot into an older kernel and delete /lib/modules/YOUR_KERNEL/updates/drivers/net/wireless/b43/b43.ko.

---

### Post by gfa on 2010-01-08
Thank you... If you need some kind of log or something like that, I could try again... i'm still using karmic default kernel (2.6.31) as primary but I can reboot to test whenever you need...

By the way, I downloaded the latests packages from Kernel PPA, version:

2.6.32-02063203

I think they're different than the one that downloads your script, does this affect?


> **chenxiaolong said:**
> Thanks for the information about the symbols dependencies. I've added that to the script and I reattached the script on my first post.

Sorry for the long wait. I've been studying for my midterms (I'm only a High School freshman. I have to take midterms :(). Anyway, I'll try and figure out why it freezes after ten seconds. If you want to remove the driver, you can always boot into an older kernel and delete /lib/modules/YOUR_KERNEL/updates/drivers/net/wireless/b43/b43.ko.

---

### Post by chenxiaolong on 2010-01-08
Actually, it does. The script is written for kernel 2.6.32.2, but you have kernel 2.6.32.3. I'll upload a new script in addition to the one for 2.6.32.2. I didn't know that kernel 2.6.32.3 is out already :confused::D.

---

### Post by gfa on 2010-01-08
> **chenxiaolong said:**
> Actually, it does. The script is written for kernel 2.6.32.2, but you have kernel 2.6.32.3. I'll upload a new script in addition to the one for 2.6.32.2. I didn't know that kernel 2.6.32.3 is out already :confused::D.

Maybe this is the freezes cause :o

I think I'll wait until you submit the new patch instead of downloading the old kernel packages...

Thanks
gFa

---

### Post by chenxiaolong on 2010-01-08
I just uploaded it.

---

### Post by gfa on 2010-01-08
> **chenxiaolong said:**
> I just uploaded it.

I don't see any diff between the old and the newest patch file :S

---

### Post by chenxiaolong on 2010-01-08
The patch file will be the same until 2.6.33 because the coding in the 2.6.32 "series" is the same. I just fixed the script so it would recognize that you're running kernel 2.6.32.3.

---

### Post by gfa on 2010-01-08
> **chenxiaolong said:**
> The patch file will be the same until 2.6.33 because the coding in the 2.6.32 "series" is the same. I just fixed the script so it would recognize that you're running kernel 2.6.32.3.

Yes :) what I wanted to say is that as the patch is the same and installed manually the new kernel I still have the freezes... As long as I get into my home I will try again and post the logs here...

---

### Post by chenxiaolong on 2010-01-08
Crap.   Double crap.   Triple crap.   I just noticed that I've been using the wl driver the whole time and not b43 :(:(. I'm such an idiot. I just tried loading the b43 driver under the new kernel 2.6.32.3 and I'm getting the same 10-seconds-waiting-then-kernel-panic error. I'm going to try compiling the b43 driver from the wireless-testing git tree. It already has the files prepatched, so that eliminates some work.

I would be glad if emas80 could give some help on this. He's the only one who's got it working so far.

---

### Post by gfa on 2010-01-08
> **chenxiaolong said:**
> Crap.   Double crap.   Triple crap.   I just noticed that I've been using the wl driver the whole time and not b43 :(:(. I'm such an idiot...

LOL :S

Good luck
gFa

---

### Post by emas80 on 2010-01-09
> **chenxiaolong said:**
> Crap.   Double crap.   Triple crap.   I just noticed that I've been using the wl driver the whole time and not b43. I'm such an idiot. I just tried loading the b43 driver under the new kernel 2.6.32.3 and I'm getting the same 10-seconds-waiting-then-kernel-panic error. I'm going to try compiling the b43 driver from the wireless-testing git tree. It already has the files prepatched, so that eliminates some work.

I would be glad if emas80 could give some help on this. He's the only one who's got it working so far.

LOL :)

So you are saying that using patched-kernel.org (and not Ubuntu) kernel 2.6.32.**3** instead of 2.6.32.**2** locks the system in kernel panic?
I had a kernel panic too, the very first time I booted Ubuntu 9.10 with its 2.6.31 kernel, when I checked wireless card driver (I really don't remember which one, if wl or b43) in Admnistration>Hardware drivers. I didn't care, because I was at work, I was full of to-dos and I had a wired connection, I simply rebooted and then nothing strange happened since then, simply my wifi was not working. So I think now that kernel panic was caused by this driver ;)

But, by the way, I really don't know what to do.. :(
A kernel panic is a bad thing.. I just suggest to check log files (system>log file viewer) for error messages, maybe there is something useful..
All that I did was patch with the right patch the right kernel. I usually recompile my own kernel, after downloading the last version from kernel.org, I'm a little maniac with this ;). 
So my system was totally "clean", headers compiled and installed, kernel compiled and installed and _running_, modules compiled and installed, all in right directories, dkms autorecompiled correctly (and still now checks on every boot) nvidia and virtualbox modules.. This is just to say that I did the things in the way the things are to be done, a coherent way, I KNOW what I was doing.
I'm not telling YOU don't know :D, I'm trying to describe my totally _clean_ situation.

What I don't undestand is... 
Which kernel are you using? Is the kernel recompiled? Has it been totally recompiled and installed together with its kernel headers? I don't totally agree with copying that "Module.symvers" file, just because in my ignorance I don't know what "Module.symvers" file is (I can wonder it, but I'm not totally sure), and I'm not sure about things I ignore ;).
In particular, 
```

sudo cp /usr/src/linux-headers-`uname -r`/Module.symvers

```what's "uname -r"? I hope that it is 2.6.32 (but I frankly don't believe so.. ;)) , because else you are copying a file from current running kernel to a complete different one!
Maybe it could work, maybe not.. 
What that I know, is that there is a kernel panic, and a possibly mix of modules from possible different kernels...
So, [chenxiaolong]("http://ubuntuforums.org/member.php?u=724117"), what's your current situation?
What's the changelog between 2.6.32.**2** and 2.6.32.**3**?
I'm really NOT going to install new kernel (until 2.6.33 revision comes out ;)) I need my notebook for my job and now, after Christmas' holidays are over, I have no time to recompile and rechecks everything, right now everything works and I'm happy with this.

---

### Post by llamafier on 2010-01-10
This thread looks very promising in solving my issues with b43. I tried using the 2.6.32 script to update the kernel and it seems to be attempting to install the amd64 version on accident. I've tried manually updating to the newer kernel but I always mess it up somehow.

I have an HP Mini 311 with an Atom processor so that would require the i386 kernel right?

Thanks for making that script chenxiaolong it got me very excited, even though it hasn't worked yet. :D

---

### Post by hypergeek14 on 2010-01-11
Perhaps the all-knowing chenxiaolong can help me with my b43 problem?  

[http://ubuntuforums.org/showthread.php?t=1373877](http://ubuntuforums.org/showthread.php?t=1373877)

---

### Post by saewelo on 2010-01-15
This bit worked for me 
[COLOR=Red]----------------------------------------------------------------------------------------------[/COLOR]
This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.

1. Open up Terminal.

2. Install the "linux-backports-modules-karmic" (newer wireless drivers from compat-wireless) package and the "b43-fwcutter" package (wireless firmware). During installation, if it asks you to fetch the firmware automatically, make sure you select yes.

     Code:
     sudo apt-get install linux-backports-modules-karmic b43-fwcutter 
3. Blacklist the ssb module.

     Code:
     echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf 
4. Blacklist the wl module.

     Code:
     echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf 
5. Reboot

6. Enjoy your wireless!!!

**[COLOR=Red]----------------------------------------------------------------------------------------------------------------[/COLOR]**
Compaq Mini 110C-1100

---

### Post by chenxiaolong on 2010-01-15
I am soo sorry for the late response. VBulletin didn't send email notifications for any of my fifty some subscribed threads :(. Anyway, I'm back now :). 

Emas80: I am actually running the Ubuntu version of the 2.6.32.3 kernel from the Ubuntu Kernel PPA. I am not running a self compiled version of the 2.6.32.3 kernel. I do have the headers and the kernel source installed. The modules.symvers file contains information about the symbol versions for the kernel modules. I really have no idea what symbols (in this case) are. About "uname -r": It's actually a command that tells you what kernel version you are booted into and are running. When you use " ` " in a script or a command, it runs the command inside the " ` " and replaces " `blahblah` " with the output of the command "blahblah." It essentially does the same thing as "$(blahblah)." Here's the changelog of kernel 2.6.32.3: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/CHANGES). It doesn't fix anything for b43, except a error on the PPC platform.
I'll try compiling a kernel from kernel.org and hopefully it will finally work :D.

llamafier: I'm sorry my script installed the amd64 version of the kernel on your computer. You can remove the kernel using Synaptic or apt-get. Could you post the output of the command "uname -a" so I can improve the detection of my script (I don't have a computer running Ubuntu i386)? Also, my script doesn't work quite right yet :( because the Ubuntu version of the kernel isn't cooperating with the new, patched b43 driver. I'll let you know when I get it working :D.

saewelo: I suggest that you do NOT use that method as it will eventually cause a DMA error, which will cause the wireless card to stop working until you manually take out the wireless card and touch all the pins (pretty annoying).


Anyway, I'll be compiling the latest kernel from [http://kernel.org](http://kernel.org) and I'll let you guys know how it goes :D.

Chen Xiao-Long

---

### Post by Alacrity on 2010-01-15
chenxiaolong,

Could you please list the 50 subsribed threads?  Your b43 thread subscribers will all want to subsribe to their thread facilitor's recommended threads.

Alacrity

---

### Post by chenxiaolong on 2010-01-15
Well, I haven't subscribed to many useful software threads. Most of them are threads on hardware issues (because I've had past experience). I'll list some threads you guys might find useful:

[http://ubuntuforums.org/showthread.php?t=1352270](http://ubuntuforums.org/showthread.php?t=1352270)
[http://ubuntuforums.org/showthread.php?t=1317801](http://ubuntuforums.org/showthread.php?t=1317801)
[http://ubuntuforums.org/showthread.php?t=1361657](http://ubuntuforums.org/showthread.php?t=1361657)
[http://ubuntuforums.org/showthread.php?t=1009404](http://ubuntuforums.org/showthread.php?t=1009404)
[http://ubuntuforums.org/showthread.php?t=1361108](http://ubuntuforums.org/showthread.php?t=1361108)
[http://ubuntuforums.org/showthread.php?t=1360732](http://ubuntuforums.org/showthread.php?t=1360732)
[http://ubuntuforums.org/showthread.php?t=1362237](http://ubuntuforums.org/showthread.php?t=1362237)
[http://ubuntuforums.org/showthread.php?t=1361594](http://ubuntuforums.org/showthread.php?t=1361594)
[http://ubuntuforums.org/showthread.php?t=1318953](http://ubuntuforums.org/showthread.php?t=1318953)
[http://ubuntuforums.org/showthread.php?t=1347483](http://ubuntuforums.org/showthread.php?t=1347483)
[http://ubuntuforums.org/showthread.php?t=1352964](http://ubuntuforums.org/showthread.php?t=1352964)
[http://ubuntuforums.org/showthread.php?t=1350865](http://ubuntuforums.org/showthread.php?t=1350865)
[http://ubuntuforums.org/showthread.php?t=978212](http://ubuntuforums.org/showthread.php?t=978212)
[http://ubuntuforums.org/showthread.php?t=1352665](http://ubuntuforums.org/showthread.php?t=1352665)
[http://ubuntuforums.org/showthread.php?t=1215686](http://ubuntuforums.org/showthread.php?t=1215686)
[http://ubuntuforums.org/showthread.php?t=1338775](http://ubuntuforums.org/showthread.php?t=1338775)
[http://ubuntuforums.org/showthread.php?t=1311826](http://ubuntuforums.org/showthread.php?t=1311826)
[http://ubuntuforums.org/showthread.php?t=1308235](http://ubuntuforums.org/showthread.php?t=1308235)
[http://ubuntuforums.org/showthread.php?t=1052602](http://ubuntuforums.org/showthread.php?t=1052602)

And I modified the Gnometris code for my brother a while ago so he could get a high score: 

[http://ubuntuforums.org/showthread.php?t=1064445](http://ubuntuforums.org/showthread.php?t=1064445)

---

### Post by chenxiaolong on 2010-01-15
Also, could someone tell me how to cross compile a kernel for i386 (from amd64) or point out a link to a HowTo? Google isn't very helpful :( I'm planning on creating a PPA at Launchpad for a prepatched version of the latest kernel at [http://kernel.org](http://kernel.org) for an easy install.

---

### Post by gfa on 2010-01-16
I have just downloaded new Lucid Lynx alpha2 and b43 driver for 14e4:4315 **works great!!!! =) I could even change to monitor mode :o**

I will try again using Kernels PPA's for Karmic as this Lucid release is still in early dev and I use this notebook as main system.

By the way, the kernel version in Lucid was 2.6.32.10...

---

### Post by chenxiaolong on 2010-01-16
Thanks for the information! It's nice to know that the next Ubuntu release will support the wireless card natively :D:D.

---

### Post by llamafier on 2010-01-16
> **chenxiaolong said:**
> llamafier: I'm sorry my script installed the amd64 version of the kernel on your computer. You can remove the kernel using Synaptic or apt-get. Could you post the output of the command "uname -a" so I can improve the detection of my script (I don't have a computer running Ubuntu i386)? Also, my script doesn't work quite right yet :( because the Ubuntu version of the kernel isn't cooperating with the new, patched b43 driver. I'll let you know when I get it working :D.

Here is the output of uname -a

```
Linux myhostname 2.6.32-7-generic #10-Ubuntu SMP Sun Dec 6 13:43:20 UTC 2009 **i686** GNU/Linux
```

(this was from Ubuntu 10.04 Alpha 1, but I think the part you needed to see should be the same right?)



I tried 10.04 Alpha 1 since it had the newer kernel, but I couldn't get the wireless working. I think there was issues in the b43 package.

Looks like that was fixed in Alpha 2 unless I just screwed something up before. Thanks for pointing that out **gfa**! I'm gonna give it a try now. :D

---

### Post by chenxiaolong on 2010-01-16
Does anyone know a free reliable web hosting company (free only; I'm 14; can't make money yet :()? I have the kernel with the b43 patch packaged as debs (amd64 version -- native compile; i386 version -- chroot 32bit compile). I just need a reliable web host for an apt repository. My server is running on a ADSL connection, which is waaaay too slow for more than one user. 

Also: If you ever need to compile anything, use Distcc. It can use any computer in your network to help compiling whatever you need to compile :D.

---

### Post by rivensky on 2010-01-17
I had to register just so I could tell you THANK YOU! I'm still a Linux n00b and just wiped Vista off my Dell XPS laptop and was not happy to find my wireless wasn't working. Problem solved! And so easy! Thanks again!

---

### Post by Indolence on 2010-01-17
The b43 driver in lucid lynx alpha2 gives me dma errors

> **chenxiaolong said:**
> Does anyone know a free reliable web hosting company (free only; I'm 14; can't make money yet :()? I have the kernel with the b43 patch packaged as debs (amd64 version -- native compile; i386 version -- chroot 32bit compile). I just need a reliable web host for an apt repository. My server is running on a ADSL connection, which is waaaay too slow for more than one user. 

Also: If you ever need to compile anything, use Distcc. It can use any computer in your network to help compiling whatever you need to compile :D.

zymic.com maybe?

---

### Post by chenxiaolong on 2010-01-17
Indolence: Unfortunately, zymic doesn't allow a file hosting site (apparently, an apt repository falls under this category).

---

### Post by voxsim on 2010-01-17
Hello everyone,

I read this thread beacause and i download the b43_kernel_2.6.32.3.sh script, first i run the third option beacause i have the kernel 2.6.31-18 on Ubuntu 9.10, after i run the first option of this script and finally i have to run the second option, but this don't work :(

When i type

```
sudo sh b43_kernel_2.6.32.3.sh /usr/src/linux-source-2.6.32
```

i have this result

```

/usr/src/linux-source-2.6.32
The path you set isn't valid (or you typed it wrong). (Man, I have to type the path again, darn it :D) It has to be the full path name.

```

I modified the script and i added an "echo $@" and seems the if[$@=="/*"] don't work, please help me :P

---

### Post by voxsim on 2010-01-17
I already try only third option of kernel script and i finally read XD 

```
You must now boot into the new 2.6.32.3 kernel to build the b43 driver.
After reboot, you will need to run part 2 of this script.
You can get it at http://software.6368.co.cc/linux/b43/patches/b43_compile_2.6.32.3.sh
The link is also in my first post on my b43 HowTo thread on UbuntuForums

I have to reboot now?? Awwwwwwww. Oh, well. (After all, it's Linux. Who cares about rebooting :D)
```

Excuse me for my first post :P but when i reboot in grub i didn't see the new kernel, but i see only the kernel 2.6.31-18

---

### Post by Indolence on 2010-01-18
> **chenxiaolong said:**
> Indolence: Unfortunately, zymic doesn't allow a file hosting site (apparently, an apt repository falls under this category).

Well... I rent a part of a webserver. If you can get yourself a domain name (for which you can change the name servers/dns servers) I can give you some space for free. The server is running everything you're likely to need, php, mysql, etc.

---

### Post by chenxiaolong on 2010-01-18
Indolence: I've already found a host that suits my needs: cxr.cc. Thanks anyway though :D. 

Emas80:

I just recompiled the newest stable kernel (2.6.32.3) from kernel.org and the b43 driver loads fine, but it won't connect to any networks.

Did you compile your kernel using the Ubuntu/Debian way or the traditional way?

I compiled mine by running:

sudo su
cd /usr/src
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.3.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.3.tar.bz2)
tar jxvf linux-2.6.32.3.tar.bz2
cd linux-2.6.32.3
cp /boot/config-`uname -r` ./.config
make oldconfig
make-kpkg clean
CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd --append-to-version=-cxl kernel_image kernel_headers modules_image
dpkg -i ../linux-*.deb

Is that basically what you did? The kernel I compiled can boot perfectly fine and can load any of my other modules (wl,nvidia,virtualbox,etc) and b43, but b43 won't connect to any networks. Dmesg doesn't give any errors either.:( By the way, this is my first time compiling a kernel.

Thanks.

---

### Post by voxsim on 2010-01-18
_[chenxiaolong]("http://ubuntuforums.org/member.php?u=724117")_: Did you [SIZE=2]enable your wireless drivers in the kernel?

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
[/SIZE]

---

### Post by chenxiaolong on 2010-01-18
I actually followed that thread to compile the kernel. I read that post about 10 times before I started compiling. Yet, I still missed it.

> THIS#IS#     NOT    THE#1ST#  ##    ## TIME I'VE MADE 
##     ##   ## ##   ##     ## ###   ## #### #### #### 
##     ##  ##   ##  ##     ## ####  ## #### #### #### 
##     ## ##  A  ## MISTAKE#  ## ## ##  ##   ##   ##  
##     ## ######### ##   ##   ##  ####                
##     ## ##     ## ##    ##  ##   ### #### #### #### 
########  ##     ## ##     ## ##    ## #### #### #### 

EDIT: Darn, the ascii didn't turn out right

---

### Post by hypergeek14 on 2010-01-19
> **saewelo said:**
> 2. Install the "linux-backports-modules-karmic" (newer wireless drivers from compat-wireless) package and the "b43-fwcutter" package (wireless firmware). During installation, if it asks you to fetch the firmware automatically, make sure you select yes.

     Code:
     sudo apt-get install linux-backports-modules-karmic b43-fwcutter 

It turned out that I did in fact not have linux-backports-modules-karmic installed, but sadly installing it has not changed my situation.  Any further help?

---

### Post by Hiro2k on 2010-01-19
Any updates? I got as far as you guys and when the system would freeze there would be no errors in the syslog. The last line mentioned loading the firmware so I tried using the newer 4.174.64.19 firmware like it says over at [http://linuxwireless.org/en/users/Drivers/b43#device_firmware]("http://linuxwireless.org/en/users/Drivers/b43#device_firmware"), but that also failed.

I have clue what else to try :(

---

### Post by chenxiaolong on 2010-01-20
I have no time to try anything. I have midterms all week.

---

### Post by chenxiaolong on 2010-01-21
The b43 driver is already enabled because I'm using the Ubuntu version of ".config" to compile. I have no idea why b43 loads but won't connect. Any suggestions?

---

### Post by MarioHaddad on 2010-01-21
good luck with the Midterms !! 

i just reinstalled Ubuntu 9.10 ( havent even booted it yet !! :D ) i've went through all 34 pages of this thread but still have a couple of questions... 

1) will your script 100% work ? ( i'll manually update the kernel to 2.6.32.3 )
2) is the b43 driver the same  thing as that b43-fwcutter? ( if i apt-get that does that mean i'll have the b43 driver ? ) 
3) should i or should i not install the broadcom STA driver ? ( that worked on previous installs of 9.10 but without monitor mode) 
4) is your 2 part script all i need to get it working ? or do i have to download something before running it other than the kernel ? 
5) might it need me to hard reset my network card ? :\ 

THANK YOU :D

---

### Post by chenxiaolong on 2010-01-21
Thanks !!

1) No, it causes a kernel panic. I have no idea why, but I'm trying to figure it out.
2) B43 is not the same thing as b43-fwcutter. B43 is already installed on every Ubuntu installation. B43-fwcutter downloads the firmware, which tells the b43 driver how to send and receive signals from your wireless card.
3) If you want wireless internet, then yes. You can always uninstall it (or disable it).
4) Yes. The second part of my script should (in theory) get it working; but it doesn't. The driver loads fine, but it crashes after 10 seconds.
5) No. The purpose of the script was to enable PIO mode because DMA mode causes the card to need a hard reset.

I'll let you know when (yes, when, not if) I get it working :D.

---

### Post by chenxiaolong on 2010-01-21
I just compiled the lastest kernel: 2.6.32.4 --> still has the same kernel panic problem, except now it panics right after loading the module. Crap. I'm going to try to compile the latest kernel from the Lucid git tree as someone reported success in the Lucid Alpha 2 release. Other than that, I'm running out of ideas. AHHHH!!!

---

### Post by chenxiaolong on 2010-01-21
OMWG (oh my windoze god), I'm about to rip my hair out ](*,)](*,)! Compiling the Lucid kernel from its git tree didn't work either. It makes a kernel panic as soon as the module loads, just like kernel 2.6.32.4. By the way, the latest Lucid kernel in the git tree is 2.6.32.11. I've compiled a total of 17 kernels with different versions and configurations ](*,). I really have no idea of what I should do. It causes a kernel panic in every single kernel I've compiled. In the 2.6.33-RC kernels, everything was screwed up. My ATI modules, wl module, and b43 module didn't load. I'm really, really confused about why this is happening :confused::confused::confused:. Tomorrow, I'm going to try compiling the Lucid kernel debs under Lucid Alpha 2 and install them under Karmic. I could bet money that there's a very simple command or changing of a configuration file that will make this magically work :D.

Where is the great Emas80? We need your steps on compiling the kernel and your .config file for your kernel :).

Oh yeah, one more thing: After some research online, I found out that make-kpkg is not the recommended way of compiling the kernel in Karmic.

---

### Post by Hiro2k on 2010-01-22
You are using the newest firmware and fwcutter like the Linux Wireless page says to right?

> You are using the b43 driver with an LP-PHY card (e.g. BCM4312)

Follow these instructions if you are using the b43 driver from linux-2.6.32 and newer or compat-wireless-2.6, or from any current GIT tree, and have a device with a low-power PHY.

Use the current Git version of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

git clone [http://git.bu3sch.de/git/b43-tools.git](http://git.bu3sch.de/git/b43-tools.git)
cd b43-tools/fwcutter
make
cd ..

Use version 4.174.64.19 of Broadcom's proprietary driver. (The tarball is mislabeled as "4.178.10.4", but it is actually 4.174.64.19.)
Download and extract the firmware from this driver tarball:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../fwcutter/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place. 

I'm 100% sure that you won't get it working without that firmware. I tried it using the precompiled 2.6.32 kernels but it never worked. I didn't try compiling my own kernel in Ubuntu and switched to gentoo for some odd reason. I managed to get it work in gentoo! :D So there is hope. 

But I don't know how much of a difference there is between the two kernel sources, of it had anything to do with my success.

---

### Post by chenxiaolong on 2010-01-22
Well, I knew there was going to be a simple solution. I wasn't using that new firmware. DARN IT!!! Thanks you so much for the information :D. I'll try this tomorrow and see how it goes :D. 

(I feel embarrassed when someone types a really long post or a post with really useful information and all I have to say is Thank You :))

---

### Post by Hiro2k on 2010-01-23
I thought I'd share this in case anyone ran into this little problem.
> airodump-ng wlan0
ioctl(SIOCSIWMODE) failed: Device or resource busy

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.


First you have to use ```
airmon-ng start wlan0 <channel>
``` which creates an interface called mon0. And then you use that interface for all the rest of the stuff. ```
airodump-ng mon0
```

---

### Post by MarioHaddad on 2010-01-23
hey.. is there an easy way to get kernel 2.32.X on ubuntu 9.10 running 2.31.14-17 ? i tried downloading and configuring the kernel then compiling, but i dont know what all the settings do in the config and i managed to screw up ubuntu :P so i formatted the drive and got a fresh install :D 

i need 2.32 to be able to follow the guide from linux wireless right ?... 

THANKS !! :popcorn:

---

### Post by single29 on 2010-01-23
It is backports caused the problem. I have fixed it. type these commands in terminal you should be able to have it fixed in minutes.

root@ubuntu:apt-get remove linux-ubuntu-modules-2.6.31-17-generic \
           linux-backports-modules-2.6.31-17-generic
root@ubuntu:apt-get install --reinstall bcmwl-kernel-source

Then click on your network manager icon in your launch panel you should see all available wireless services.

---

### Post by hypergeek14 on 2010-01-25
I can't say why, but the first script that upgrades my kernel has never worked.  Can someone tell/link me how to do it manually?

---

### Post by chenxiaolong on 2010-01-25
All the Ubuntu Kernel's are at the PPA: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by MarioHaddad on 2010-01-25
i just had to try it................... -.-"...

got my self a DMA error :| crap :|:(

EDIT: fixed it without removing the card !!... dont know what exactly did it but here's what i did :
1) disconnected power cord and took out the battery
2) pressed the power button with the lid OPENED for 30+ seconds, 
3) then pressed the wifi catcher on the left of my 1537 studio With the power button for 30 seconds.
4) kept pressing the power button like crazy on and off
5) returned the battery and wen into bios, turned off everything about wireless including that WPAN+WLAN thingy... but left bluetooth on.. save settings
6) restarted
7) turned everything in the bios about wireless back on :D 

and voila !! it worked :P just a little something for whoever gets a DMA error and doesnt want to take the card out manually...

---

### Post by k3Rn on 2010-01-25
omg - so frustrating, spend couple of hours again!

you scripts just don't work probperly. tryed to execute the commands by hand, but errors over errors. 

i hope you once redo em properly (especially for i386 systems).

p.s.: when i did the commands from script 1 by hand (i need the i386 kernel, the script would download amd64) - i can boot into 2.6.32-02063203-generic. 
but compiling the patch give me various errors. i posted the output on pastbin: [http://pastebin.com/f379bf961](http://pastebin.com/f379bf961)

---

### Post by Ferdemidu on 2010-01-26
Dear chenxiaolong,
I'm just a beginner with Ubuntu.
My problem is that I do not know how to follow after the Part1 of your script.
I have my machine with two operating systems, Windows 7 an Ubuntu 9.10 and I have GRUB 1 to select from each one.
My kernel is 2.6.31-17-generic-pae
I don't know how to reboot from the new 2.6.32.2 because I don't know how to put it in the GRUB
Could you  help me?
 
Regards,
 
Ferdemidu
 
> **chenxiaolong said:**
> Unfortunately, only patching the b43 driver will not work because it causes a kernel panic after ten seconds. You have to compile a new kernel with the b43 module patched. But..........that's not so bad. I already patched and compiled it for you :D. I'm just trying to find a free reliable web hosting company to host an apt repository for the patched kernels. I can't afford any paid webhosts--I'm only 14. Please PM any suggestions to me (doesn't need PHP or MySQL, just hosting). 
 
 
----------------------
 
**2.6.32.3 Script**
 
[COLOR=orange]New Script for kernel 2.6.32.3 (b43_compile_2.6.32.3.sh & b43_kernel_2.6.32.3.sh): Attached below; also at my website: [http://software.6368.co.cc/linux/b43/patches](http://software.6368.co.cc/linux/b43/patches).[/COLOR]
 
----------------------
 
**2.6.32.2 Script**
 
[COLOR=red]Script Update 4 (b43_kernel_2.6.32.2.sh): Backs up and renames /usr/src/linux-source-2.6.32 so there is a clean copy of the source to work with.[/COLOR]
 
[COLOR=red]Script Update 3 (b43_compile_2.6.32.2.sh): Fixed error about modules.symversions.[/COLOR]
 
[COLOR=red]Script Update 2 (b43_kernel_2.6.32.2.sh): Fixed kernel download part (i386 --> i686); added checking for "patch" package.[/COLOR]
 
[COLOR=red]Script Update 1 (b43_compile_2.6.32.2.sh): Included the enabling of PIO mode; stupid mistake on my part.[/COLOR]
 
---------------------
 
Great news for everyone!! The b43 driver can now be run in Ubuntu 9.10 Karmic WITHOUT any DMA errors!!:D I created a script this time that will install it for you. :D I couldn't have done it without [COLOR=mediumturquoise]emas80[/COLOR] (page 26), O-Hatta ([http://www.incentivespro.com/forum/viewtopic.php?t=222](http://www.incentivespro.com/forum/viewtopic.php?t=222)), and of course, the b43 developers ([http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html](http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html)). 
 
Unfortunately, it only works on kernel 2.6.32. BUT, the first shell script that I created will automatically download and install kernel 2.6.32.2 from the Ubuntu Kernel PPA and patch the b43 driver to get rid of the DMA problems. If you compiled the 2.6.32 kernel or downloaded it from a third party source, the script also works, but you will have to run it with a parameter (see below). Also, if you already have the 2.6.32.* kernel installed from the Ubuntu Kernel PPA, you can just run the script normally. This script can be run as root or as your regular user. It uses sudo commands, so running the script as root might save you from typing your password a million times. Now lets put this paragraph into action :).
 
PART 1 (described above) of the script can be downloaded here (also attached to this post as b43_kernel_2.6.32.2.sh): [http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.2.sh](http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.2.sh)
 
IF YOU WANT TO USE THE 2.6.32.2 KERNEL, USE "2.6.32.2" INSTEAD OF "2.6.32.3", INCLUDING LINKS.
 
Cases:
 
1. You are using a 2.6.31 kernel (default in Ubuntu 9.10 Karmic)
Run [COLOR=red]sudo sh b43_kernel_2.6.32.3.sh[/COLOR]
 
2. You are running a third party or self-compiled version of kernel 2.6.32
Run [COLOR=red]sudo sh b43_kernel_2.6.32.3.sh /path/to/kernel/sources[/COLOR]
 
3. You already have kernel 2.6.32 installed from the Ubuntu Kernel PPA
Run [COLOR=red]sudo sh b43_kernel_2.6.32.3.sh[/COLOR]
 
Part 1 of the script makes sure that you are using the 2.6.32 kernel and patches the b43 script for compilation during part 2 of the script. If you were running kernel 2.6.31* and the script installed 2.6.32, you MUST boot into the new kernel for b43 to compile (a.k.a. just reboot). Part 2 will prepare the kernel sources to compile the b43 driver and then compile and install b43. After running the script, you will have to make sure that there IS a "[COLOR=darkorchid]b43[/COLOR]" line in [COLOR=darkorchid]/etc/modules[/COLOR] and make sure that there ISN"T a "[COLOR=darkorchid]blacklist b43[/COLOR]" or "[COLOR=darkorchid]blacklist ssb[/COLOR]" line in any of the files in "[COLOR=darkorchid]/etc/modprobe.d[/COLOR]." You run the second script basically like the same way above.
 
PART 2 (described above) of the script can be downloaded here (also attached to this post as b43_compile_2.6.32.3.sh): [http://software.6368.co.cc/linux/b43/patches/b43_compile_2.6.32.3.sh](http://software.6368.co.cc/linux/b43/patches/b43_compile_2.6.32.3.sh)
 
Cases:
 
1. You are (now) running kernel 2.6.32 from the Ubuntu Kernel PPA
Run [COLOR=red]sudo sh b43_compile_2.6.32.3.sh[/COLOR]
 
2. You are running a third party or self-compiled version of kernel 2.6.32
Run [COLOR=red]sudo sh b43_compile_2.6.32.3.sh /path/to/kernel/sources[/COLOR]
 
[COLOR="Red"]Again, after running part 2 of the script, you will need to make sure that in "[COLOR=darkorchid]/etc/modules[/COLOR]," there IS a "[COLOR=darkorchid]b43[/COLOR]" line and that there ISN'T a "[COLOR=darkorchid]blacklist b43[/COLOR]" or "[COLOR=darkorchid]blacklist ssb[/COLOR]" line in any of the files in "[COLOR=darkorchid]/etc/modprobe.d[/COLOR]."
 
Then reboot and enjoy your wireless!! :D
 
Notes:
 
The patch file from my website (also attached to this post) is NOT the same as the patch at [http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html](http://lists.opensuse.org/opensuse-kernel/2009-12/msg00047.html), although the patch results ARE the same. Emas80 took the time to read the patch file line-by-line and patch the files manually. I downloaded his patched version of the b43 source files (page 26 of this thread) and ran the [COLOR=darkorchid]diff[/COLOR] command between my unmodified b43 source and his patched source, saving the output to a new patch. The new patch is at [http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.3.patch](http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.3.patch).
 
If you have any doubts about my scripts, you can open them up and check it. I commented (in the script) what every command does. If there's any typos or problems please PM me so I can fix them. They should be okay; I tested the scripts on my computer.
 
Again, thanks to anyone who helped me with the script and the developers of the b43 driver. 
 
[COLOR=red]----------------------------------------------------------------------------------------------[/COLOR]
This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.
 
1. Open up Terminal.
 
2. Install the "linux-backports-modules-karmic" (newer wireless drivers from compat-wireless) package and the "b43-fwcutter" package (wireless firmware). During installation, if it asks you to fetch the firmware automatically, make sure you select yes.
 
```
sudo apt-get install linux-backports-modules-karmic b43-fwcutter
```
 
3. Blacklist the ssb module.
 
```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
```
 
4. Blacklist the wl module.
 
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
```
 
5. Reboot
 
6. Enjoy your wireless!!!
 
**[COLOR=red]----------------------------------------------------------------------------------------------------------------[/COLOR]**
 
First of all, I want to thank lwfinger at openSUSE forums for making the b43 driver work with the 14e4:4315
 
The post looks verrrrry long right? Well it's not. All the commands are "copy-n-paste-able" and I recommend that you do copy and paste them so you don't make any mistakes.
 
So first of all, you need to download the latest compat-wireless from 
 
You can't use wget for this because they have a hotlink prevention system. So just download the file from that website and SAVE IT TO YOUR HOME DIRECTORY. 
 
Then open the terminal and run this command to extract the archive
 
```
tar xjf compat-wireless-2.6.tar.bz2
```
 
In order for the package to compile, you need to install the kernel headers, if not already installed. Run this in the terminal
 
```
sudo apt-get install linux-headers-$(uname -r)
```
 
Then change to the compat-wireless directory: 
 
```
cd compat-wireless
```
 
Then compile the source files:
 
```
sudo make
```
 
Then install the files:
 
```
sudo make install
```
 
Then unload the drivers
 
```
sudo make unload
```
 
Then install b43-fwcutter:
VERY IMPORTANT!!: Do NOT choose yes when it asks if you want to automatically fetch the firmware.
 
```
sudo apt-get install b43-fwcutter
```
 
Download the Broadcom firmware files
 
```
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```
 
Extract the archive
 
```
tar xjf broadcom-wl-4.150.10.5.tar.bz2
```
 
Change to the driver directory
 
```
cd broadcom-wl-4.150.10.5/driver
```
 
Install the firmware
 
```
b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```
 
Then blacklist the proprietary driver
 
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist.conf
```
 
And finally..............RESTART!!!
 
 
 
 
I hope this worked for you. It worked for me. 
 
By the way, I'm turning 14 on September 26, so wish me a happy birthday :)

---

### Post by chenxiaolong on 2010-01-26
Awesome new, everyone: B43 FINALLY WORKS!!! Really, it works now. No crashes. No DMA errors. No kernel panics. And best of all, very easy to get working :D. I'll update my first post with more info after I do my homework. Time ~ 1 hour (for homework). Time ~ 20 minutes (to get working).

---

### Post by leorolla on 2010-01-27
They should release Lucid Alpha2 with Wubi, so we can make disposable fresh installations to make tests all the time.

One suggestion: keep the 1st post more clear, separating what is the state-or-art and what is just history.

---

### Post by MarioHaddad on 2010-01-27
awesome ! :D tried it ! works !! :D atleast the normal surfing mode.. but when i tried ifconfig down then iwconfig wlan0 mode monitor... it said something about busy.. dont really remember... is there another way im missing ?

---

### Post by chenxiaolong on 2010-01-27
I'll separate the first post to make it more clear.

---

### Post by jensbodal on 2010-01-27
Was going to say I ran into an error when running the 'make' command but I didn't install all 3 kernel debs.

---

### Post by jensbodal on 2010-01-27
Hey I tried your directions and followed them to the T... I didn't receive any errors but after I rebooted my computer nothing changed.  Wireless still not working, or even showing up for that matter.  I tried the drivers from the hardware manager and the Broadcom STA shows up, but I cannot install those drivers as it just says installation of driver fails...

---

### Post by chenxiaolong on 2010-01-27
You have to install all three debs (for your system architecture). The kernel-headers packages allow you to compile kernel modules.

---

### Post by jensbodal on 2010-01-27
Would just installing the ubuntu 10.0.04 beta do the same thing?  I had this card working with Ubuntu 8.04 like 2 years ago and was able to run Aircrack just fine, but I cannot seem to find any guide or tip that works for me.

---

### Post by leorolla on 2010-01-27
> **chenxiaolong said:**
> ....then add these lines to /etc/rc.local (thanks to Muti for this information)

```
modprobe -r b43
sleep 3
modprobe b43
```...

Mine isn't working... and I did it with a nearly fresh wubi install (though I had installed and uninstalled kernel 2.32.10 and had been playing with ndiswrapper as well).

Did you test it on fresh installs?

I will try the above trick and report tomorrow.

---

### Post by leorolla on 2010-01-27
> **jensbodal said:**
> Would just installing the ubuntu 10.0.04 beta do the same thing?  I had this card working with Ubuntu 8.04 like 2 years ago and was able to run Aircrack just fine, but I cannot seem to find any guide or tip that works for me.

You had this card working with a different driver... whose well-functioning Ubuntu unfortunately keeps breaking.

---

### Post by leorolla on 2010-01-27
**Firmware missing?**

Driver was not even present:
```
leorolla@ubuntu:~$ sudo lshw -C network
[sudo] password for leorolla: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:55100000-55103fff
  *-network
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:5a:57:47:ed
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:53000000-5303ffff ioport:1000(size=128)

```Then I did:
```
leorolla@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8736  0 
snd_hda_codec_realtek   202637  1 
snd_hda_intel          21530  2 
snd_hda_codec          74209  2 snd_hda_codec_realtek,snd_hda_intel
iptable_filter          2271  0 
ip_tables              10219  1 iptable_filter
x_tables               14299  1 ip_tables
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35304  0 
snd_mixer_oss          13774  1 snd_pcm_oss
snd_pcm                70894  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            27055  0 
snd_seq_midi            4557  0 
snd_rawmidi            19084  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47231  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19333  2 snd_pcm,snd_seq
snd_seq_device          5762  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57402  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54416  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7124  0 
led_class               2864  0 
parport                32603  2 ppdev,lp
soundcore               6620  1 snd
psmouse                62398  0 
serio_raw               3978  0 
snd_page_alloc          7340  2 snd_hda_intel,snd_pcm
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47919  1 vfat
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7589  1 fbcon
bitblit                 4675  1 fbcon
softcursor              1189  1 bitblit
i915                  282634  3 
drm_kms_helper         27478  1 i915
usbhid                 36048  0 
drm                   156437  4 i915,drm_kms_helper
i2c_algo_bit            4964  1 i915
intel_agp              24246  2 i915
atl1e                  28866  0 
agpgart                31703  2 drm,intel_agp
video                  17491  1 i915
output                  1871  1 video

``````
leorolla@ubuntu:~$ sudo modprobe b43
```

Now the icon at the panel says "device not ready". Doesn't see any network. New output:
```
leorolla@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:55100000-55103fff
  *-network
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:5a:57:47:ed
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:53000000-5303ffff ioport:1000(size=128)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:2b:a2:1a:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.32-11-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

```My suspect of firmware is due to:
```
leorolla@ubuntu:~$ dmesg | grep b43
[  113.461069] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  113.461094] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[  113.579322] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  113.692501] Registered led device: b43-phy0::tx
[  113.692623] Registered led device: b43-phy0::rx
[  113.699752] Registered led device: b43-phy0::radio
[  113.765173] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[  113.804840] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[  113.818433] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[  113.818459] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[  113.818479] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  113.864130] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[  113.870022] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[  113.879531] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[  113.879546] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[  113.879556] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```When you tested this solution, had you previosly installed the firmwares from some other driver etc, or was it in a fresh install?

---

### Post by chenxiaolong on 2010-01-27
Quote [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp:](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp:)

> You are using the b43 driver with an LP-PHY card (e.g. BCM4312)

Follow these instructions if you are using the b43 driver from linux-2.6.32 and newer or compat-wireless-2.6, or from any current GIT tree, and have a device with a low-power PHY.

Use the current Git version of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

git clone [http://git.bu3sch.de/git/b43-tools.git](http://git.bu3sch.de/git/b43-tools.git)
cd b43-tools/fwcutter
make
cd ..

Use version 4.174.64.19 of Broadcom's proprietary driver. (The tarball is mislabeled as "4.178.10.4", but it is actually 4.174.64.19.)
Download and extract the firmware from this driver tarball:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../fwcutter/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

---

### Post by jensbodal on 2010-01-28
> **leorolla said:**
> You had this card working with a different driver... whose well-functioning Ubuntu unfortunately keeps breaking.

I'm not sure what you mean by this but I read in another post that someone had used the latest Ubuntu install and said that the driver works fine in there.  Are you saying that the Ubuntu versions keep changing/breaking the driver?

Do you think just clearing my current install and trying 10.04 will do anything?

---

### Post by leorolla on 2010-01-28
> **jensbodal said:**
> I'm not sure what you mean by this but I read in another post that someone had used the latest Ubuntu install and said that the driver works fine in there.  Are you saying that the Ubuntu versions keep changing/breaking the driver?

Yes. Ubuntu autmoatically loads the correct proprietary driver and you wireless just works out of the box. This was true in 8.04, 8.10, 9.04 but suddenly not quint with 9.10.
A few months ago you had to update your installation (with wired connection of course) to get it working. Since a few weeks ago even that was again not working. I don't know if has been fixed again, I'm getting sick of it.

> **jensbodal said:**
> Do you think just clearing my current install and trying 10.04 will do anything?

Maybe. But I guess it is safer to install it to a USB stick, just to check if it works.

> **chenxiaolong said:**
> Quote [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp:")

You are using the b43 driver with an LP-PHY card (e.g. BCM4312)

Follow these instructions if you are using the b43 driver from linux-2.6.32 and newer or compat-wireless-2.6, or from any current GIT tree, and have a device with a low-power PHY.

Use the current Git version of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

git clone [http://git.bu3sch.de/git/b43-tools.git](http://git.bu3sch.de/git/b43-tools.git)
cd b43-tools/fwcutter
make
cd ..

Use version 4.174.64.19 of Broadcom's proprietary driver. (The tarball is mislabeled as "4.178.10.4", but it is actually 4.174.64.19.)
Download and extract the firmware from this driver tarball:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../fwcutter/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o                      

So, in summary, you mean something like this?

```
cd ~/Desktop
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-11-generic_2.6.32-11.15_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-11-generic_2.6.32-11.15_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-11_2.6.32-11.15_all.deb
sudo dpkg -i linux*2.6.*.deb
sudo reboot
``````
cd ~/Desktop
git clone http://git.bu3sch.de/git/b43-tools.git
cd b43-tools/fwcutter
make
cd ..
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../fwcutter/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
sudo reboot
``````
cd ~/Desktop
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2010-01-26.tar.bz2
tar jxvf compat-wireless-2010-01-26.tar.bz2
cd compat-wireless-2010-01-26
make
sudo make install
sudo make unload
sudo depmod
sudo depmod -a
echo "options b43 pio=1" | sudo tee -a "/etc/modprobe.d/b43-thingy.conf"
sudo reboot

```

---

### Post by leorolla on 2010-01-28
It works!!!

:KS:KS:KS:KS:KS

I also had to check for the blacklist and remove b43.

So I guess you should add:
- the firmware installation,
- un-blacklisting of b43,
- blacklisting of the other drivers,
and you will finally have your HowTo :P

---

### Post by DarkAngel88 on 2010-01-28
> **leorolla said:**
> It works!!!

:KS:KS:KS:KS:KS

I also had to check for the blacklist and remove b43.

So I guess you should add:
- the firmware installation,
- un-blacklisting of b43,
- blacklisting of the other drivers,
and you will finally have your HowTo :P

What he said!!  Thanks dude!  Adding "modprobe b43 into /etc/rc.local" did the work for me!

---

### Post by chenxiaolong on 2010-01-28
leorolla: Sure thing. Anything to make the guide easier :D.

DarkAngel88: I'm glad you got it working :D.

Also, I'll update the first post whenever a new kernel comes out and I'll let you guys know whether it works or not :P:P.

---

### Post by Oly0909 on 2010-01-28
OK. I'm trying to get this card working under BackTrack 4 Final Release. As soon as I start, I get this:
> root@bt:~/kernel2632# sudo dpkg -i linux*2.6.*.deb

Selecting previously deselected package linux-headers-2.6.32-11.

(Reading database ... 225594 files and directories currently installed.)

Unpacking linux-headers-2.6.32-11 (from linux-headers-2.6.32-11_2.6.32-11.15_all
.deb) ...

Selecting previously deselected package linux-headers-2.6.32-11-generic.

Unpacking linux-headers-2.6.32-11-generic (from linux-headers-2.6.32-11-generic_2.6.32-11.15_i386.deb) ...

Selecting previously deselected package linux-image-2.6.32-11-generic.

Unpacking linux-image-2.6.32-11-generic (from linux-image-2.6.32-11-generic_2.6.32-11.15_i386.deb) ...

Done.

Setting up linux-headers-2.6.32-11 (2.6.32-11.15) ...

dpkg: dependency problems prevent configuration of linux-headers-2.6.32-11-generic:

 linux-headers-2.6.32-11-generic depends on libc6 (>= 2.8); however:

  Version of libc6 on system is 2.8~20080505-0ubuntu9.
dpkg:
 error processing linux-headers-2.6.32-11-generic (--install):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of linux-image-2.6.32-11-generic:

 linux-image-2.6.32-11-generic depends on wireless-crda; however:

  Package wireless-crda is not installed.

dpkg: error processing linux-image-2.6.32-11-generic (--install):

 dependency problems - leaving unconfigured

Errors were encountered while processing:

 linux-headers-2.6.32-11-generic

 linux-image-2.6.32-11-generic

I'm totaly new to linux. Can somebody help me?

---

### Post by DarkAngel88 on 2010-01-28
chenxiaolong: good idea about the regular updates about new kernels.

Also, am I the only one with the issue that sometimes, my laptop simply won't go beyond the grub menu?  I mean, it seems to hang *sometimes* just after the grub menu.  A reboot sometimes fixes the issue but still, pretty weird.  Hangs after the "b43-pci-bridge" thing... One solution is to blacklist b43 and use STA instead.  We all know here that this is not the solution we want... now I'm wondering if anyone knows another solution to this issue.

---

### Post by eric512 on 2010-01-29
Finally got Kismet working on my Dell 1537 with the new tutorial on the first page. 

Had to use the firmware instructions for the 4.174.64.19 firmware.

Airodump and Kismet both run with mon0,

but both die after about 2-3 mins. 

I have to modprobe -r to restart the mon0.

Then it dies again after 2-3 mins.

Getting very close............

---

### Post by nbcmayhem on 2010-01-29
i just got this running under fedora with current kernel. no drops so far. (dell mini 10 2nd gen)
but i only get 1mb/s and some weird jumping between transferrates from time to time. 

i'll wait til 2.6.32.xx is pushed through the pipes and compile compat-wl again, maybe that's causing odd behavior. 

is there a newer driver then broadcom's 4.178.10.4 ? let me know

---

### Post by chenxiaolong on 2010-01-29
DarkAngel88: Well, we can't expect too much from a beta kernel :D. I rather reboot once or twice than to use the STA driver :D.

Eric512: I have that problem sometimes, but not too frequently. I'm guessing that it will be fixed in the coming kernels and compat-wireless releases.

Nbcmayhem: I have no idea why it's that slow. I know it's a wireless-g card, but I get about 1.7-2.0 megabytes per second using the b43 driver. PIO mode is also slower than DMA, but it shouldn't be half the speed :(. By the way, the 4.178.10.4 package is NOT a driver. It has the firmware files that tell the b43 driver (and wl driver) how to communicate with the Broadcom cards.

EDIT: Sorry Oly0909, I didn't see your post :(. You will have to compile your own kernel or use a kernel from the Debian experimental repository (sorry, no link. I have no idea how to access the experimental repo online). The kernels mentioned in this post are for Ubuntu ONLY.

---

### Post by leorolla on 2010-01-29
I have one problem with this kernel:
I'm running on battery and it's totally unaware of it. It even thinks my laptop only runs on AC power.
Should I file a bug to the devs? How is it?

---

### Post by chenxiaolong on 2010-01-29
Try booting with the option "acpi=force". If that doesn't work, then, yes, file a bug report.

---

### Post by leorolla on 2010-01-29
> **chenxiaolong said:**
> Try booting with the option "acpi=force". If that doesn't work, then, yes, file a bug report.

I'm more newbie than you think. How do you "boot with the option xyz" ?

---

### Post by chenxiaolong on 2010-01-29
That's okay, Ubuntu is "Linux for [all] humanity" :D. Anyway, when you start up the computer and get to the list of kernels (it says Grub at the top), press "E"; go to the second line (or the longest line) and add "acpi=force" to the end; then, press escape and "Control X" boot. Hopefully that will work :P.

---

### Post by hypergeek14 on 2010-01-29
I must say the latest update is working perfectly.  Thanks all!

---

### Post by chenxiaolong on 2010-01-30
Well, I really didn't do much except creating a HowTo article. We really should be thanking Larry Finger at the OpenSUSE forums for making the b43 code :D.

---

### Post by nbcmayhem on 2010-02-01
still only 1mbit transferrate and i can't connect to ttls networks. bummer.

---

### Post by chenxiaolong on 2010-02-01
The 1MB transfer rate will remain until the developers fix DMA mode for this card or improve PIO mode. I have no idea what TTLS is, so I can't help you there :D.

---

### Post by nbcmayhem on 2010-02-02
[http://en.wikipedia.org/wiki/Extensible_Authentication_Protocol#EAP-TTLS](http://en.wikipedia.org/wiki/Extensible_Authentication_Protocol#EAP-TTLS)

---

### Post by leorolla on 2010-02-02
I haven't tested the transfer rate.

Does it also work with 2.6.32-12?

With 2.6.32-11 I have the power problem.

---

### Post by chenxiaolong on 2010-02-02
I'll try kernel 2.6.32.12 tomorow and let you guys know.

---

### Post by Xantar on 2010-02-02
I followed this HOW TO step by step.  Unfortunately my wireless card is still not working.

Any trouble shooting tips to assist me?  I've tried both the ndiswrapper how to and this to no avail.

---

### Post by leorolla on 2010-02-02
> **Xantar said:**
> I followed this HOW TO step by step.  Unfortunately my wireless card is still not working.

Any trouble shooting tips to assist me?  I've tried both the ndiswrapper how to and this to no avail.

Show us:

```
lsmod
dmesg
grep b43 /etc/modprobe.d/*
grep wl /etc/modprobe.d/*
grep ndiswrapper /etc/modprobe.d/*
uname -r
apt-cache policy ndiswrapper-common
apt-cache policy bcmwl-kernel-source
sudo lshw -C network

```

---

### Post by Xantar on 2010-02-02
lsmod
```
Module                  Size  Used by
aes_i586                7268  471 
aes_generic            26863  1 aes_i586
b44                    25647  0 
mii                     4349  1 b44
ssb                    37914  1 b44
ndiswrapper           185354  0 
mac80211              205832  0 
cfg80211              127190  1 mac80211
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      51397  1 
snd_hda_intel          21530  2 
snd_hda_codec          74209  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35304  0 
snd_mixer_oss          13774  1 snd_pcm_oss
dm_crypt               11307  0 
snd_pcm                70894  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            27055  0 
snd_seq_midi            4557  0 
snd_rawmidi            19084  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47231  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19333  2 snd_pcm,snd_seq
joydev                  8736  0 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
iptable_filter          2271  0 
ip_tables              10219  1 iptable_filter
ricoh_mmc               2992  0 
snd_seq_device          5762  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
x_tables               14299  1 ip_tables
snd                    54416  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               5470  0 
vfat                    8901  1 
soundcore               6620  1 snd
sdhci                  15462  1 sdhci_pci
snd_page_alloc          7340  2 snd_hda_intel,snd_pcm
led_class               2864  1 sdhci
psmouse                62398  0 
fat                    47919  1 vfat
dell_wmi                1697  0 
serio_raw               3978  0 
dell_laptop             6688  0 
dcdbas                  5550  1 dell_laptop
lp                      7124  0 
parport                32603  2 ppdev,lp
ohci1394               27174  0 
usbhid                 36048  0 
video                  17491  0 
output                  1871  1 video
ieee1394               81465  1 ohci1394
e1000e                120970  0 
intel_agp              24246  0 
agpgart                31703  1 intel_agp

```

dmesg
```

[    0.564891] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0e
[    0.564894] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff
[    0.564901] pci 0000:00:1c.3:   MEM window: 0xf1c00000-0xf1efffff
[    0.564906] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.564913] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.564915] pci 0000:00:1e.0:   IO window: disabled
[    0.564921] pci 0000:00:1e.0:   MEM window: 0xf1b00000-0xf1bfffff
[    0.564926] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.564945]   alloc irq_desc for 16 on node -1
[    0.564948]   alloc kstat_irqs on node -1
[    0.564955] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.564960] pci 0000:00:01.0: setting latency timer to 64
[    0.564969] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.564975] pci 0000:00:1c.0: setting latency timer to 64
[    0.564985]   alloc irq_desc for 17 on node -1
[    0.564987]   alloc kstat_irqs on node -1
[    0.564990] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.564995] pci 0000:00:1c.1: setting latency timer to 64
[    0.565006]   alloc irq_desc for 18 on node -1
[    0.565007]   alloc kstat_irqs on node -1
[    0.565011] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.565016] pci 0000:00:1c.2: setting latency timer to 64
[    0.565026]   alloc irq_desc for 19 on node -1
[    0.565028]   alloc kstat_irqs on node -1
[    0.565031] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.565037] pci 0000:00:1c.3: setting latency timer to 64
[    0.565045] pci 0000:00:1e.0: setting latency timer to 64
[    0.565050] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.565052] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.565055] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.565057] pci_bus 0000:01: resource 1 mem: [0xf2000000-0xf6efffff]
[    0.565060] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.565062] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
[    0.565065] pci_bus 0000:0b: resource 1 mem: [0x80000000-0x801fffff]
[    0.565067] pci_bus 0000:0b: resource 2 pref mem [0x80200000-0x803fffff]
[    0.565069] pci_bus 0000:0c: resource 0 io:  [0x3000-0x3fff]
[    0.565072] pci_bus 0000:0c: resource 1 mem: [0xf1f00000-0xf1ffffff]
[    0.565074] pci_bus 0000:0c: resource 2 pref mem [0x80400000-0x805fffff]
[    0.565077] pci_bus 0000:0d: resource 0 io:  [0x4000-0x4fff]
[    0.565079] pci_bus 0000:0d: resource 1 mem: [0x80600000-0x807fffff]
[    0.565081] pci_bus 0000:0d: resource 2 pref mem [0x80800000-0x809fffff]
[    0.565084] pci_bus 0000:0e: resource 0 io:  [0xc000-0xcfff]
[    0.565086] pci_bus 0000:0e: resource 1 mem: [0xf1c00000-0xf1efffff]
[    0.565089] pci_bus 0000:0e: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.565091] pci_bus 0000:03: resource 1 mem: [0xf1b00000-0xf1bfffff]
[    0.565093] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.565096] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.565139] NET: Registered protocol family 2
[    0.565242] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.565546] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.566043] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.566271] TCP: Hash tables configured (established 131072 bind 65536)
[    0.566273] TCP reno registered
[    0.566339] NET: Registered protocol family 1
[    0.566523] pci 0000:01:00.0: Boot video device
[    0.566712] cpufreq-nforce2: No nForce2 chipset.
[    0.566737] Scanning for low memory corruption every 60 seconds
[    0.566840] audit: initializing netlink socket (disabled)
[    0.566849] type=2000 audit(1265141428.563:1): initialized
[    0.576481] highmem bounce pool size: 64 pages
[    0.576486] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.577899] VFS: Disk quotas dquot_6.5.2
[    0.577952] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.578480] fuse init (API version 7.13)
[    0.578561] msgmni has been set to 1705
[    0.578753] alg: No test for stdrng (krng)
[    0.578763] io scheduler noop registered
[    0.578765] io scheduler anticipatory registered
[    0.578767] io scheduler deadline registered
[    0.578805] io scheduler cfq registered (default)
[    0.578943]   alloc irq_desc for 24 on node -1
[    0.578945]   alloc kstat_irqs on node -1
[    0.578953] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.578959] pcieport 0000:00:01.0: setting latency timer to 64
[    0.579087]   alloc irq_desc for 25 on node -1
[    0.579089]   alloc kstat_irqs on node -1
[    0.579097] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.579108] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.579255]   alloc irq_desc for 26 on node -1
[    0.579257]   alloc kstat_irqs on node -1
[    0.579265] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.579276] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.579427]   alloc irq_desc for 27 on node -1
[    0.579428]   alloc kstat_irqs on node -1
[    0.579437] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.579447] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.579596]   alloc irq_desc for 28 on node -1
[    0.579598]   alloc kstat_irqs on node -1
[    0.579607] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.579632] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.579732] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.579870] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.579990] ACPI: AC Adapter [AC] (on-line)
[    0.580063] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.581708] ACPI: Lid Switch [LID]
[    0.581749] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.581756] ACPI: Power Button [PBTN]
[    0.581797] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.581800] ACPI: Sleep Button [SBTN]
[    0.582515] ACPI: SSDT 7f450999 00281 (v01  PmRef   BspIst 00003000 INTL 20050624)
[    0.582981] ACPI: SSDT 7f450df1 005C6 (v01  PmRef   BspCst 00003001 INTL 20050624)
[    0.583316] Monitor-Mwait will be used to enter C-1 state
[    0.583339] Monitor-Mwait will be used to enter C-2 state
[    0.583361] Monitor-Mwait will be used to enter C-3 state
[    0.583367] Marking TSC unstable due to TSC halts in idle
[    0.583422] processor LNXCPU:00: registered as cooling_device0
[    0.583838] ACPI: SSDT 7f450c1a 001D7 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.584175] ACPI: SSDT 7f4513b7 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.584498] Switching to clocksource hpet
[    0.584826] processor LNXCPU:01: registered as cooling_device1
[    0.616909] thermal LNXTHERM:01: registered as thermal_zone0
[    0.616917] ACPI: Thermal Zone [THM] (51 C)
[    0.616961] ACPI: Battery Slot [BAT0] (battery present)
[    0.616970] ACPI: Battery Slot [BAT1] (battery absent)
[    0.617075] isapnp: Scanning for PnP cards...
[    0.621244] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.621396] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.621779] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.622779] brd: module loaded
[    0.623216] loop: module loaded
[    0.623283] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.623364] ahci 0000:00:1f.2: version 3.0
[    0.623377] ahci 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.623408]   alloc irq_desc for 29 on node -1
[    0.623410]   alloc kstat_irqs on node -1
[    0.623419] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.623464] ahci: SSS flag set, parallel bus scan disabled
[    0.623501] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl RAID mode
[    0.623504] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
[    0.623510] ahci 0000:00:1f.2: setting latency timer to 64
[    0.648052] scsi0 : ahci
[    0.648120] scsi1 : ahci
[    0.648169] scsi2 : ahci
[    0.648220] scsi3 : ahci
[    0.648270] scsi4 : ahci
[    0.648321] scsi5 : ahci
[    0.648735] ata1: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c900 irq 29
[    0.648739] ata2: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c980 irq 29
[    0.648741] ata3: DUMMY
[    0.648742] ata4: DUMMY
[    0.648745] ata5: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb00 irq 29
[    0.648748] ata6: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb80 irq 29
[    0.649602] Fixed MDIO Bus: probed
[    0.649633] PPP generic driver version 2.4.2
[    0.649664] tun: Universal TUN/TAP device driver, 1.6
[    0.649666] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.649747] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.649765]   alloc irq_desc for 22 on node -1
[    0.649767]   alloc kstat_irqs on node -1
[    0.649771] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.649781] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.649785] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.649822] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.649849] ehci_hcd 0000:00:1a.7: debug port 1
[    0.653751] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.653778] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.672013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.672090] usb usb1: configuration #1 chosen from 1 choice
[    0.672119] hub 1-0:1.0: USB hub found
[    0.672125] hub 1-0:1.0: 6 ports detected
[    0.672183]   alloc irq_desc for 20 on node -1
[    0.672184]   alloc kstat_irqs on node -1
[    0.672189] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.672198] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.672201] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.672231] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.672256] ehci_hcd 0000:00:1d.7: debug port 1
[    0.676153] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.676165] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.692012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.692088] usb usb2: configuration #1 chosen from 1 choice
[    0.692112] hub 2-0:1.0: USB hub found
[    0.692117] hub 2-0:1.0: 6 ports detected
[    0.692171] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.692187] uhci_hcd: USB Universal Host Controller Interface driver
[    0.692205] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.692211] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.692215] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.692242] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.692268] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
[    0.692347] usb usb3: configuration #1 chosen from 1 choice
[    0.692372] hub 3-0:1.0: USB hub found
[    0.692377] hub 3-0:1.0: 2 ports detected
[    0.692420]   alloc irq_desc for 21 on node -1
[    0.692422]   alloc kstat_irqs on node -1
[    0.692426] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.692432] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.692435] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.692462] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.692494] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
[    0.692573] usb usb4: configuration #1 chosen from 1 choice
[    0.692596] hub 4-0:1.0: USB hub found
[    0.692602] hub 4-0:1.0: 2 ports detected
[    0.692644] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.692651] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.692655] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.692685] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.692710] uhci_hcd 0000:00:1a.2: irq 22, io base 0x00006fa0
[    0.692791] usb usb5: configuration #1 chosen from 1 choice
[    0.692814] hub 5-0:1.0: USB hub found
[    0.692820] hub 5-0:1.0: 2 ports detected
[    0.692864] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.692870] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.692874] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.692900] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.692926] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
[    0.693003] usb usb6: configuration #1 chosen from 1 choice
[    0.693026] hub 6-0:1.0: USB hub found
[    0.693032] hub 6-0:1.0: 2 ports detected
[    0.693077] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.693083] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.693087] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.693114] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.693139] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
[    0.693223] usb usb7: configuration #1 chosen from 1 choice
[    0.693246] hub 7-0:1.0: USB hub found
[    0.693252] hub 7-0:1.0: 2 ports detected
[    0.693296] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.693302] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.693306] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.693337] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.693361] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.693441] usb usb8: configuration #1 chosen from 1 choice
[    0.693464] hub 8-0:1.0: USB hub found
[    0.693470] hub 8-0:1.0: 2 ports detected
[    0.693562] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.694138] i8042.c: Warning: Keylock active.
[    0.697332] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.697337] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.697441] mice: PS/2 mouse device common for all mice
[    0.697566] rtc_cmos 00:03: RTC can wake from S4
[    0.697600] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.697629] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.697718] device-mapper: uevent: version 1.0.3
[    0.697804] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.697871] device-mapper: multipath: version 1.1.0 loaded
[    0.697874] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.697970] EISA: Probing bus 0 at eisa.0
[    0.697973] EISA: Cannot allocate resource for mainboard
[    0.697975] Cannot allocate resource for EISA slot 1
[    0.697977] Cannot allocate resource for EISA slot 2
[    0.697979] Cannot allocate resource for EISA slot 3
[    0.697980] Cannot allocate resource for EISA slot 4
[    0.697997] EISA: Detected 0 cards.
[    0.698134] cpuidle: using governor ladder
[    0.698241] cpuidle: using governor menu
[    0.698662] TCP cubic registered
[    0.698800] NET: Registered protocol family 10
[    0.699226] lo: Disabled Privacy Extensions
[    0.699541] NET: Registered protocol family 17
[    0.700258] Using IPI No-Shortcut mode
[    0.700314] PM: Resume from disk failed.
[    0.700324] registered taskstats version 1
[    0.701117]   Magic number: 14:860:193
[    0.701151] acpi device:1f: hash matches
[    0.701190] rtc_cmos 00:03: setting system clock to 2010-02-02 20:10:28 UTC (1265141428)
[    0.701193] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.701194] EDD information not available.
[    0.702688] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.973243] isapnp: No Plug & Play device found
[    1.140069] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.141298] ata1.00: ATA-7: ST9160823ASG, 3.ADE, max UDMA/133
[    1.141302] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.142842] ata1.00: configured for UDMA/133
[    1.156192] scsi 0:0:0:0: Direct-Access     ATA      ST9160823ASG     3.AD PQ: 0 ANSI: 5
[    1.156309] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.156329] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.156369] sd 0:0:0:0: [sda] Write Protect is off
[    1.156372] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.156392] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.156508]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.205276] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.384063] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    1.561843] usb 5-1: configuration #0 chosen from 1 choice
[    1.561847] usb 5-1: config 0 descriptor??
[    1.808098] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    1.982069] usb 6-2: configuration #1 chosen from 1 choice
[    2.044070] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.046083] ata2.00: ATAPI: MATSHITA DVD+/-RW UJ862A, 1.02, max UDMA/33
[    2.048448] ata2.00: configured for UDMA/33
[    2.065949] scsi 1:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ862A   1.02 PQ: 0 ANSI: 5
[    2.069760] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.069764] Uniform CD-ROM driver Revision: 3.20
[    2.069851] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.069903] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.388107] ata5: SATA link down (SStatus 0 SControl 300)
[    2.724070] ata6: SATA link down (SStatus 0 SControl 300)
[    2.740132] Freeing unused kernel memory: 660k freed
[    2.740483] Write protecting the kernel text: 4780k
[    2.740534] Write protecting the kernel read-only data: 1916k
[    2.867578] Linux agpgart interface v0.103
[    2.891182] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    2.891185] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.891232] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.891241] e1000e 0000:00:19.0: setting latency timer to 64
[    2.891337]   alloc irq_desc for 30 on node -1
[    2.891339]   alloc kstat_irqs on node -1
[    2.891351] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[    2.935962] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.935979] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    2.976930] usbcore: registered new interface driver hiddev
[    2.989352] ohci1394 0000:03:01.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.992574] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input5
[    2.992656] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1d.0-2/input0
[    2.992676] usbcore: registered new interface driver usbhid
[    2.992679] usbhid: v2.6:USB HID core driver
[    3.006051] acpi device:35: registered as cooling_device2
[    3.007182] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:33/LNXVIDEO:00/input/input6
[    3.007216] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    3.020347] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    3.033547] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:21:70:b8:fa:7a
[    3.033550] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.033577] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1004ff-0ff
[    3.050063] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f1bff800-f1bfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.188268] PM: Starting manual resume from disk
[    4.188272] PM: Resume from partition 8:5
[    4.188274] PM: Checking hibernation image.
[    4.188440] PM: Error -22 checking image file
[    4.188441] PM: Resume from disk failed.
[    4.225035] kjournald starting.  Commit interval 5 seconds
[    4.225043] EXT3-fs: mounted filesystem with writeback data mode.
[    4.324173] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[444fc00012494de1]
[    4.824367] type=1505 audit(1265141432.622:2):  operation="profile_load" pid=489 name="/usr/share/gdm/guest-session/Xsession"
[    4.831655] type=1505 audit(1265141432.626:3):  operation="profile_load" pid=490 name="/sbin/dhclient3"
[    4.832315] type=1505 audit(1265141432.630:4):  operation="profile_load" pid=490 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    4.832651] type=1505 audit(1265141432.630:5):  operation="profile_load" pid=490 name="/usr/lib/connman/scripts/dhclient-script"
[    4.913448] type=1505 audit(1265141432.710:6):  operation="profile_load" pid=491 name="/usr/bin/evince"
[    4.922876] type=1505 audit(1265141432.718:7):  operation="profile_load" pid=491 name="/usr/bin/evince-previewer"
[    4.928527] type=1505 audit(1265141432.726:8):  operation="profile_load" pid=491 name="/usr/bin/evince-thumbnailer"
[    4.941640] type=1505 audit(1265141432.738:9):  operation="profile_load" pid=493 name="/usr/lib/cups/backend/cups-pdf"
[    4.942381] type=1505 audit(1265141432.738:10):  operation="profile_load" pid=493 name="/usr/sbin/cupsd"
[    5.904963] Adding 4104568k swap on /dev/sda5.  Priority:-1 extents:1 across:4104568k 
[    6.273162] EXT3 FS on sda3, internal journal
[    6.398169] udev: starting version 147
[    8.918762] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.990002] input: Dell WMI hotkeys as /devices/virtual/input/input7
[    9.191472] lp: driver loaded but no devices found
[    9.406085] sdhci: Secure Digital Host Controller Interface driver
[    9.406088] sdhci: Copyright(c) Pierre Ossman
[    9.489219] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 21)
[    9.489238] sdhci-pci 0000:03:01.1: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    9.491310] Registered led device: mmc0::
[    9.492380] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    9.492397] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0843] (rev 11)
[    9.492411] sdhci-pci 0000:03:01.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    9.493416] mmc1: Hardware doesn't specify base clock frequency.
[    9.493425] sdhci-pci 0000:03:01.2: PCI INT C disabled
[    9.839343] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input8
[    9.856334] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input9
[   10.012308] Disabling lock debugging due to kernel taint
[   10.019566] ricoh-mmc: Ricoh MMC Controller disabling driver
[   10.019569] ricoh-mmc: Copyright(c) Philip Langdale
[   10.019597] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 11)
[   10.019613] ricoh-mmc: Controller is now disabled.
[   10.020145] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   10.049081] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.227872] usbcore: registered new interface driver ndiswrapper
[   10.363752] cfg80211: Calling CRDA to update world regulatory domain
[   10.448633] b43: Unknown parameter `pio'
[   10.601798] cfg80211: World regulatory domain updated:
[   10.601801]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.601804]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.601806]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.601808]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.601810]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.601812]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.657036] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.657077] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.082597] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   12.181272] __ratelimit: 3 callbacks suppressed
[   12.181275] type=1505 audit(1265159439.978:12):  operation="profile_replace" pid=1087 name="/usr/share/gdm/guest-session/Xsession"
[   12.182731] type=1505 audit(1265159439.978:13):  operation="profile_replace" pid=1088 name="/sbin/dhclient3"
[   12.183383] type=1505 audit(1265159439.978:14):  operation="profile_replace" pid=1088 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.183745] type=1505 audit(1265159439.978:15):  operation="profile_replace" pid=1088 name="/usr/lib/connman/scripts/dhclient-script"
[   12.187866] type=1505 audit(1265159439.982:16):  operation="profile_replace" pid=1089 name="/usr/bin/evince"
[   12.198073] type=1505 audit(1265159439.994:17):  operation="profile_replace" pid=1089 name="/usr/bin/evince-previewer"
[   12.204436] type=1505 audit(1265159440.002:18):  operation="profile_replace" pid=1089 name="/usr/bin/evince-thumbnailer"
[   12.214255] type=1505 audit(1265159440.010:19):  operation="profile_replace" pid=1091 name="/usr/lib/cups/backend/cups-pdf"
[   12.215042] type=1505 audit(1265159440.010:20):  operation="profile_replace" pid=1091 name="/usr/sbin/cupsd"
[   12.217577] type=1505 audit(1265159440.014:21):  operation="profile_replace" pid=1092 name="/usr/sbin/tcpdump"
[   12.977204] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[   13.033113] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[   13.033370] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.100011] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x00df0700
[   13.100314] input: HDA Intel Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.100441] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.100551] input: HDA Intel Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.100659] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   14.661795] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   14.661799] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   14.661987] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   15.240250] ppdev: user-space parallel port driver
[   18.267127] dell-wmi: Unknown key ffd0 pressed
[   18.658033] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[   19.577828] dell-wmi: Unknown key ffd0 pressed
[   20.851736] dell-wmi: Unknown key ffd1 pressed
[   21.724524] cfg80211: Calling CRDA to update world regulatory domain
[   21.729558] cfg80211: World regulatory domain updated:
[   21.729561]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.729564]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.729566]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.729569]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.729571]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.729573]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.772486] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.772505] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   21.840301] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[   21.846105] b43: Unknown parameter `pio'
[   21.901130] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[   21.902855] usbcore: deregistering interface driver ndiswrapper
[   21.911526] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   21.920386] usbcore: registered new interface driver ndiswrapper
[   21.926726] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.926747] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   21.996293] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[   24.784203] eth0: no IPv6 routers present
[   40.165794] padlock: VIA PadLock not detected.
[ 2403.632017] CE: hpet increasing min_delta_ns to 15000 nsec
[ 2565.688296] CE: hpet increasing min_delta_ns to 22500 nsec
[ 2565.752095] CE: hpet increasing min_delta_ns to 33750 nsec
[ 3456.452215] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 5
[ 3456.453562] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 3456.461118] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 - driver resynched.
[ 3457.168219] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 5
[ 3457.169417] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 3457.176263] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 - driver resynched.

```

```
/etc/modprobe.d/b43-thingy.conf:options b43 pio=1
/etc/modprobe.d/blacklist:blacklist b43
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.

```

```
/etc/modprobe.d/blacklist:blacklist wl
/etc/modprobe.d/blacklist:blacklist wl
/etc/modprobe.d/blacklist:blacklist wl
/etc/modprobe.d/blacklist~:blacklist wl
/etc/modprobe.d/blacklist~:blacklist wl
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
/etc/modprobe.d/ndiswrapper:alias wlan0 ndiswrapper
/etc/modprobe.d/wedontneednonossdrivers.conf:blacklist wl

```

```
/etc/modprobe.d/ndiswrapper:alias wlan0 ndiswrapper

```

```
2.6.32-11-generic

```

```
ndiswrapper-common:
  Installed: 1.54-2ubuntu1
  Candidate: 1.54-2ubuntu1
  Version table:
 *** 1.54-2ubuntu1 0
        500 http://us.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

```

```
ndiswrapper-common:
  Installed: 1.54-2ubuntu1
  Candidate: 1.54-2ubuntu1
  Version table:
 *** 1.54-2ubuntu1 0
        500 http://us.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status
xantar@xantar-laptop:~$ apt-cache policy bcmwl-kernel-source
bcmwl-kernel-source:
  Installed: (none)
  Candidate: 5.10.91.9+bdcom-0ubuntu4
  Version table:
     5.10.91.9+bdcom-0ubuntu4 0
        500 http://us.archive.ubuntu.com karmic/restricted Packages

```

```

  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:b8:fa:7a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.7-7 ip=192.168.1.108 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f6fe0000-f6ffffff memory:f6fdb000-f6fdbfff ioport:efe0(size=32)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f1ffc000-f1ffffff

```

---

### Post by leorolla on 2010-02-03
Check:
```
cat /etc/modules

```There should be a line with "b43".

Backup:```

cp /etc/modprobe.d/ndiswrapper ~

```Now
```

sudo gedit /etc/modprobe.d/blacklist
```and remove the line
```

blacklist b43

```Remove ndiswrapper:```

sudo rm /etc/modprobe.d/ndiswrapper
sudo apt-get purge ndiswrapper-common
```Reboot and see if it works.

---

### Post by Xantar on 2010-02-03
```
cat /etc/modules
```Contains

```

lp
ndiswrapper
ndiswrapper
b43

```

```
sudo gedit /etc/modprobe.d/blacklist
```Produces

```

blacklist bcm43xx
blacklist wl
blackist bcm43xx
blacklist wl
blacklist bcm43xx
blacklist b43
blacklist bcm43xx
blacklist wl
```Aren't the multiple blacklists redundant?  Anyway, removed b43 and

After

```
sudo apt-get purge ndiswrapper-common
```It said

```
dpkg: warning: while removing ndiswrapper-common, directory '/etc/ndiswrapper' not empty so not removed.
```And afterward still nothing.

Under Network Connections the Wireless tab is completely empty (although I am right next to a wireless router + others around campus)

and the antenna next to the speaker and the mail icon in the upper right produces only the options

Wired Netork

Anything else I can try?

EDIT - 

Also

```
cat /etc/modules
```

Still contains

```

lp
ndiswrapper
ndiswrapper
b43

```

---

### Post by chenxiaolong on 2010-02-03
Did you reboot after making the changes? I know it's a stupid question, but I forget to reboot all the time :D.

Also, about the 2.6.32.12 kernel: I don't have time to test it yet. I have to use Premier Pro CS4 for my world history project, so I've been using Windoze lately ](*,)](*,)](*,):D.

---

### Post by Xantar on 2010-02-03
Hehe yes I reboot after every set of instructions to check.  Unfortunately still nothing :(

I have this laptop on loan from school.  It had a Windows partition on it already.  I added another partition because when I give the computer back I want to be able to just delete the partition and it'd be like I never had it (hopefully).  I decided on Ubuntu because I wanted more practice in a Unix command line because one of my classes this semester has us SSH into our school's Solaris server.  Everything went well except for the wireless card :C

---

### Post by chenxiaolong on 2010-02-03
If you need stability with your wireless connection for your classes, then I recommend that you use the Broadcom STA driver simply because:

1) Easy to install
2) No connection drops
3) Stable

The b43 driver is still in development with this wireless card and you never know if it will work or not.

From the output of "dmesg" a few posts ago, it looks like you didn't install the new kernel (2.6.32.11) and/or you didn't compile and install compat-wireless (indicated by "Unknown parameter: pio," which only occurs with the current/non-beta version of b43). Make sure you're running and booted into the latest kernel mentioned on my first post and make sure that you run "sudo depmod" & "sudo depmod -a" after you compile and install compat-wireless.

Anyway, good luck with this!

---

### Post by leorolla on 2010-02-03
```
cd /etc
cp -r ndiswrapper ~            # backup that you probably will never need
sudo rm -r ndiswrapper
sudo gedit modules             # then remove lines containing ndiswrapper
sudo reboot                    # but close important programs before!

```As Chen said, maybe you didn't really compile the latest compat. It takes ages to compile... Did you really do the HowTo steps one-by-one in the right order?

---

### Post by tcrowter on 2010-02-04
I have a problem - I have got to the part about installing the new kernel - the links are down, but I can find a similar file in the index of that link you posted. I was scared to do ANYTHING differently (whenever I do, it goes wrong) from the instructions, so I thought I would post and ask:

**Would it still work if I used different kernel image and headers to the ones linked to?**

and how come the links are suddenly down - yesterday they worked for me :-s

Thanks very much for the guide -- I felt really close to getting there yesterday, but it seemed my Ubuntu installation was too cluttered with all my attempts - I decided to reinstall from scratch and JUST try your method, as it seems to work for everyone else.

---

### Post by leorolla on 2010-02-04
> **tcrowter said:**
> I have a problem - I have got to the part about installing the new kernel - the links are down, but I can find a similar file in the index of that link you posted. I was scared to do ANYTHING differently (whenever I do, it goes wrong) from the instructions, so I thought I would post and ask:

**Would it still work if I used different kernel image and headers to the ones linked to?**

and how come the links are suddenly down - yesterday they worked for me :-s

Thanks very much for the guide -- I felt really close to getting there yesterday, but it seemed my Ubuntu installation was too cluttered with all my attempts - I decided to reinstall from scratch and JUST try your method, as it seems to work for everyone else.

Weird that 2.6.32-11 was just vaporized from repositories.

Try with these and tell us if it works.
[http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-image-2.6.32-12-generic_2.6.32-12.16_i386.deb](http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-image-2.6.32-12-generic_2.6.32-12.16_i386.deb)
[http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-headers-2.6.32-12_2.6.32-12.16_all.deb](http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-headers-2.6.32-12_2.6.32-12.16_all.deb)
[http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-headers-2.6.32-12-generic_2.6.32-12.16_i386.deb](http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-headers-2.6.32-12-generic_2.6.32-12.16_i386.deb)

Note that I am assuming you have an ordinary 32-bit installation.

---

### Post by tcrowter on 2010-02-04
> **leorolla said:**
> Weird that 2.6.32-11 was just vaporized from repositories.

Try with these and tell us if it works.
[http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-image-2.6.32-12-generic_2.6.32-12.16_i386.deb](http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-image-2.6.32-12-generic_2.6.32-12.16_i386.deb)
[http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-headers-2.6.32-12_2.6.32-12.16_all.deb](http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-headers-2.6.32-12_2.6.32-12.16_all.deb)
[http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-headers-2.6.32-12-generic_2.6.32-12.16_i386.deb](http://mirrors.kernel.org///ubuntu/pool/main/l/linux/linux-headers-2.6.32-12-generic_2.6.32-12.16_i386.deb)

Note that I am assuming you have an ordinary 32-bit installation.

Sorry, I have a 64-bit laptop. Hate to be difficult.

Thanks for your quick reply!

---

### Post by leorolla on 2010-02-04
> **tcrowter said:**
> Sorry, I have a 64-bit laptop. Hate to be difficult.

Thanks for your quick reply!

Try these then:
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.12.12_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.12.12_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-12-generic_2.6.32-12.16_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-12-generic_2.6.32-12.16_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-12_2.6.32-12.16_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-12_2.6.32-12.16_all.deb)

I have tested on a fresh install and it seems* to work.

Actually after installing the firmware, it seemed* to be working even without compiling and installing compat.

So if it doesn't work for you, you may want to try installing Ubuntu 32 bits just to be sure that this is not a 64-bit-specific isssue.

* the network here is refusing to give me an IP, but it is not because of my drivers.

---

### Post by chenxiaolong on 2010-02-04
Ubuntu does not keep minor revisions of development (ing?) packages in the repository, which is why the 2.6.32.11 files are gone. I think it's safe to try out kernel 2.6.32.12 from leorolla's post. I'll update my first post with the links.

leorolla: The default b43 module that comes with the 2.6.32.12 works, but you will eventually get the DMA error because it's not patched with the PIO mode patch, which is included in compat-wireless.

Also, it's definitely not a 64 bit issue. I've been running 64 bit the whole time (mainly because I have 8GB of RAM and it would be really slow to run 32 bit Ubuntu :D).

---

### Post by tcrowter on 2010-02-04
> **leorolla said:**
> Try these then:
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.12.12_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.12.12_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-12-generic_2.6.32-12.16_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-12-generic_2.6.32-12.16_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-12_2.6.32-12.16_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-12_2.6.32-12.16_all.deb)

I have tested on a fresh install and it seems* to work.

Actually after installing the firmware, it seemed* to be working even without compiling and installing compat.

So if it doesn't work for you, you may want to try installing Ubuntu 32 bits just to be sure that this is not a 64-bit-specific isssue.

* the network here is refusing to give me an IP, but it is not because of my drivers.

I'll download those onto a fresh installation, thanks :)

> **chenxiaolong said:**
> Ubuntu does not keep minor revisions of development (ing?) packages in the repository, which is why the 2.6.32.11 files are gone. I think it's safe to try out kernel 2.6.32.12 from leorolla's post. I'll update my first post with the links.

leorolla: The default b43 module that comes with the 2.6.32.12 works, but you will eventually get the DMA error because it's not patched with the PIO mode patch, which is included in compat-wireless.

Also, it's definitely not a 64 bit issue. I've been running 64 bit the whole time (mainly because I have 8GB of RAM and it would be really slow to run 32 bit Ubuntu :D).

Is the DMA error serious? I'll try and follow the instructions through as well as I can - most linux instructions never seem to work for me -- there's always some technicality!

Thanks for your help, I'll get back to you when I find out the results.

---

### Post by chenxiaolong on 2010-02-04
I don't know what you consider serious, but if you get that error (shown in dmesg), then you won't be able to use the wireless card until you physically take out the card, touch the pins, and put it back in.

---

### Post by tcrowter on 2010-02-04
> **chenxiaolong said:**
> I don't know what you consider serious, but if you get that error (shown in dmesg), then you won't be able to use the wireless card until you physically take out the card, touch the pins, and put it back in.
 
I decided to follow through the instructions - I noticed my wifi was working when I installed the new kernel, but I went right ahead, and now it seems I have no wireless interfaces. Anything I can do to fix it?

---

### Post by chenxiaolong on 2010-02-04
Can you post the output of "dmesg"? I need it to see what's happening when your computer boots.

---

### Post by leorolla on 2010-02-04
What the heck is the DMA error?

Mine seemed to be working fine after the kernel and fwcutter.

I haven't installed compat yet.

---

### Post by chenxiaolong on 2010-02-04
> What the heck is the DMA error?

I have no idea.

> Mine seemed to be working fine after the kernel and fwcutter.

You'll find out after downloading a large file.

---

### Post by tcrowter on 2010-02-05
> **chenxiaolong said:**
> Can you post the output of "dmesg"? I need it to see what's happening when your computer boots.

Okay, I only just got your message(s) - after my last post I ran dmesg on a hunch, and then added those lines mentioned in the first post, and now it works! 

The only problem is with the GUI I'm trying out, but that's separate from this thread.

Thanks VERY much for your help!

---

### Post by drumin90 on 2010-02-05
Hello, thanks for the tutorial.  I can now succesfully get my BCM4312 into monitor mode but it brings up another problem.  My wireless card can detect netowrks but absolutely cannot connect to any of them.  Any ideas?

---

### Post by tcrowter on 2010-02-05
Sorry to be difficult again, but I now have another issue, which has popped up since restarting. When I click on the network applet, the 'Enable Wireless' option is greyed out. When I 'modprobe -r b43', the option disappears. When I 'modprobe b43', the option returns, but still ghosted.

EDIT: Sorry, this turned out to be a separate issue.

Sorry for posting so much!

---

### Post by chenxiaolong on 2010-02-05
tcrowter: That's okay. Do you still have the problem? I you do, can you start a new thread on it, so I can help you there?

drumin90: Can you post the output of "uname -a"? That command tells me what kernel you are booted into. The pre-2.6.32-11 kernels have this error.

---

### Post by drumin90 on 2010-02-05
Output from uname -a:

```
2.6.32-12-generic #16-Ubuntu SMP Wed Jan 27 18:34:19 UTC 2010 i686 GNU/Linux
```

The netbook can see wireless networks fine, it just cannot connect to any of them.

Thank you for the help
-drumin90

---

### Post by tcrowter on 2010-02-06
> **chenxiaolong said:**
> tcrowter: That's okay. Do you still have the problem? I you do, can you start a new thread on it, so I can help you there?


It turned out to be related to the network manager applet, which I replaced with the Wicd Network Manager, which works okay. The only problem now is related to the GUI I'm using for aircrack, which I'm asking about on the aircrack-ng forum.

Thanks!

---

### Post by chenxiaolong on 2010-02-06
drumin90: Hmmmm... I'm also running kernel 2.6.32-12 with compat-wireless-2010-02-01 with no problems. I don't know what might be causing this :(.

---

### Post by drumin90 on 2010-02-06
OK.  Well if this helps at all, the NIC is the LP version.  (14e4:14315) I assume this is ok since that is the same as in the title of this post.  Also,  in your tutorial, before setting up the new kernel, for installing b43-fwcutter, should I just use the standard Ubuntu command to install b43-fwcutter or should I do the option listed for the LP cards?

---

### Post by chenxiaolong on 2010-02-06
You should use the option for LP cards.

---

### Post by drumin90 on 2010-02-06
Ok I figured.  So should I only do that or should I go through the entire tutorial again and redo all of the steps?

---

### Post by chenxiaolong on 2010-02-06
You can backup and remove the current firmware so you can redo the steps on installing the LP firmware. You don't need to do everything over again.

To backup the firmware

```
sudo rmmod b43 ssb
sudo mv /lib/firmware/b43 /lib/firmware/b43.backup
```

---

### Post by drumin90 on 2010-02-06
So basically backup the old firmware, and then follow the steps for the LP cards?  And should I completely remove the current b43-fwcutter first?

---

### Post by chenxiaolong on 2010-02-06
Sorry for the slow response. So, you should remove the current b43-fwcutter package, backup the firmware, and follow the firmware for LP cards.

Good luck. I hope this works out for you :D.

---

### Post by drumin90 on 2010-02-07
Ok thank you for all the help.  I will most likely do all of this after the game today and report the results back to here.  Thanks again for everything.

---

### Post by tcrowter on 2010-02-07
> **tcrowter said:**
> It turned out to be related to the network manager applet, which I replaced with the Wicd Network Manager, which works okay. The only problem now is related to the GUI I'm using for aircrack, which I'm asking about on the aircrack-ng forum.

Thanks!

I hate to keep coming back and annoying you all with my problems, but here I am. 

Sorry in advance.

Okay, so using the Wicd Network Manager, I can see all the APs fine. When I try and connect to my own with what is definitely the correct password, the program keeps saying it is getting an IP address. I checked with my router, and DHCP is working fine, and it does for all my other devices.

I'm now unsure what is causing this issue! Please help!

Thanks muchly in advance.

---

### Post by drumin90 on 2010-02-07
> **tcrowter said:**
> I hate to keep coming back and annoying you all with my problems, but here I am. 

Sorry in advance.

Okay, so using the Wicd Network Manager, I can see all the APs fine. When I try and connect to my own with what is definitely the correct password, the program keeps saying it is getting an IP address. I checked with my router, and DHCP is working fine, and it does for all my other devices.

I'm now unsure what is causing this issue! Please help!

Thanks muchly in advance.


This actually sounds like the same problem I am having.  BTW, reinstalling fwcutter and the firmware decribed for LP cards did not work for me.  I'm still having the same issue.  I try to connect to my router with the correct wpa key and it continually tries to connect.  After about a minute or so, it asks me for my wpa key again.  It never actually makes a connection to the router though.

If it helps at all, I tried using aircrack to see if it could establish a connection that way.  It originally found the router when using airodump the first time (for finding the bssid) but could not even see the router when using airodump for dumping on the target or in aireplay.

Thanks again for all the help.

---

### Post by chenxiaolong on 2010-02-07
I'll try everything out myself today to make sure that everything is working. I've been using Vista (Premier Pro CS4) for a school project and was also messing around with my parent's digital keyboard & PropellerHeads Reason 4 :D. Anyway, I'm going back to Linux now to see what exactly the problem is. 

I'll post my results whether I get it working or not (hopefully it will work fine......).

---

### Post by leorolla on 2010-02-07
> **tcrowter said:**
> I hate to keep coming back and annoying you all with my problems, but here I am. 

Sorry in advance.

Okay, so using the Wicd Network Manager, I can see all the APs fine. When I try and connect to my own with what is definitely the correct password, the program keeps saying it is getting an IP address. I checked with my router, and DHCP is working fine, and it does for all my other devices.

I'm now unsure what is causing this issue! Please help!

Thanks muchly in advance.

Sometimes I have this problem. Once it went away just by itself.

I noticed that when it happens, it's independent of Compat, BCM, or Ndiswrapper. It is even independent of the OS, and with other OSes I don't get an IP either.

When googling, I found out that it may be a problem with our hardware:
[http://www.google.com/search?q=acer+aspire+one+dhcp+problems+wireless&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=acer+aspire+one+dhcp+problems+wireless&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

When you had this DHCP problem, did you try with other releases like Jaunty, and with Windows?

---

### Post by drumin90 on 2010-02-07
> **chenxiaolong said:**
> I'll try everything out myself today to make sure that everything is working. I've been using Vista (Premier Pro CS4) for a school project and was also messing around with my parent's digital keyboard & PropellerHeads Reason 4 :D. Anyway, I'm going back to Linux now to see what exactly the problem is. 

I'll post my results whether I get it working or not (hopefully it will work fine......).


Way off topic: Propellarhead Reason 4 is amazing.  Great piece of software.

Back on topic, as far as I know, this wireless card works fine in windows.

---

### Post by chenxiaolong on 2010-02-07
BAD NEWS: B43 won't connect in either 2.6.32-12.17 or 2.6.33-RC7.

BUT, I found some interesting info from dmesg:

```
[ 1526.290758] wlan0: direct probe to 00:21:27:46:94:da (try 1)
[ 1526.500123] wlan0: direct probe to 00:21:27:46:94:da (try 2)
[ 1526.690129] wlan0: direct probe to 00:21:27:46:94:da (try 3)
[ 1526.890156] wlan0: direct probe to 00:21:27:46:94:da timed out
[ 1537.723698] wlan0: direct probe to 00:21:27:46:94:da (try 1)
[ 1537.728609] wlan0: direct probe responded
[ 1537.760066] wlan0: authenticate with 00:21:27:46:94:da (try 1)
[ 1537.762726] wlan0: authenticated
[ 1537.762986] wlan0: associate with 00:21:27:46:94:da (try 1)
[ 1537.766827] wlan0: RX AssocResp from 00:21:27:46:94:da (capab=0x431 status=0 aid=1)
[ 1537.766833] wlan0: associated
[B][ 1537.769207] cfg80211: Calling CRDA for country: US
[ 1537.773261] cfg80211: Received country IE:
[ 1537.773266] cfg80211: Regulatory domain: US
[ 1537.773269]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1537.773274]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 2700 mBm)
[ 1537.773277] cfg80211: CRDA thinks this should applied:
[ 1537.773280] cfg80211: Regulatory domain: US
[ 1537.773282]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1537.773287]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1537.773291]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1537.773295]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1537.773300]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1537.773304]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1537.773307] cfg80211: We intersect both of these and get:
[ 1537.773309] cfg80211: Regulatory domain: 98[/B]
[ 1537.773312]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[B][ 1537.773316]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1537.773323] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[ 1537.773327] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[ 1537.773330] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[ 1537.773334] cfg80211: Current regulatory domain updated by AP to: US
[ 1537.773337]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1537.773341]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)[/B]
[ 1542.540162] No probe response from AP 00:21:27:46:94:da after 500ms, disconnecting.
[ 1543.673914] wlan0: direct probe to 00:21:27:46:94:da (try 1)
[ 1543.874452] wlan0: direct probe to 00:21:27:46:94:da (try 2)
[ 1544.070049] wlan0: direct probe to 00:21:27:46:94:da (try 3)
[ 1544.270056] wlan0: direct probe to 00:21:27:46:94:da timed out
chenxiaolong@d6657k1:~$ 

```

Would cfg80211 be blocking a attempt to connect? I'll try connecting to another router and a neighbor's router and see how it goes.

---

### Post by chenxiaolong on 2010-02-07
Hmm... I tried connecting to my other router after the first one failed and, of course, it failed to connect. But interestingly, dmesg didn't show any errors or debug messages. Afterwards, I tried to connect again, but neither network-manager nor "sudo iwlist scan" could show any networks ](*,).

---

### Post by chenxiaolong on 2010-02-07
Could you guys try loading b43 with this: ? It seems to be working for one of my routers.

```
sudo rmmod b43
sudo modprobe b43 pio=1 nohwcrypt=1 verbose=3
```

---

### Post by drumin90 on 2010-02-08
> **chenxiaolong said:**
> Could you guys try loading b43 with this: ? It seems to be working for one of my routers.

```
sudo rmmod b43
sudo modprobe b43 pio=1 nohwcrypt=1 verbose=3
```

It didnt work for my router.  Airodump was able to see the router this time however, so it seems to have gotten closer.  As far as connecting, it still just times out every time.

---

### Post by tcrowter on 2010-02-09
> **chenxiaolong said:**
> Could you guys try loading b43 with this: ? It seems to be working for one of my routers.

```
sudo rmmod b43
sudo modprobe b43 pio=1 nohwcrypt=1 verbose=3
```


I can see my AP, but when connecting it just times out when fetching an IP address.

---

### Post by chenxiaolong on 2010-02-09
I wonder if it's because compat-wireless never got installed properly: .

```
chenxiaolong@d6657k1:/lib/modules/2.6.32-12-generic/updates$ find
./drivers
./drivers/misc
./drivers/misc/eeprom
./drivers/bluetooth
./drivers/bluetooth/btsdio.ko
./drivers/bluetooth/btusb.ko
./drivers/bluetooth/bluecard_cs.ko
./drivers/bluetooth/bt3c_cs.ko
./drivers/bluetooth/btmrvl.ko
./drivers/bluetooth/btmrvl_sdio.ko
./drivers/bluetooth/bcm203x.ko
./drivers/bluetooth/bpa10x.ko
./drivers/bluetooth/bfusb.ko
./drivers/bluetooth/btuart_cs.ko
./drivers/bluetooth/hci_vhci.ko
./drivers/bluetooth/dtl1_cs.ko
./drivers/bluetooth/hci_uart.ko
./drivers/net
./drivers/net/atl1e
./drivers/net/atl1e/atl1e.ko
./drivers/net/atlx
./drivers/net/atlx/atl1.ko
./drivers/net/atlx/atl2.ko
./drivers/net/atl1c
./drivers/net/atl1c/atl1c.ko
./dkms
./dkms/vboxnetadp.ko
./dkms/wl.ko
./dkms/vboxdrv.ko
./dkms/vboxnetflt.ko
./compat
./compat/compat_firmware_class.ko
./compat/compat.ko
./net
./net/bluetooth
./net/bluetooth/bluetooth.ko
./net/bluetooth/bnep
./net/bluetooth/bnep/bnep.ko
./net/bluetooth/hidp
./net/bluetooth/hidp/hidp.ko
./net/bluetooth/rfcomm
./net/bluetooth/rfcomm/rfcomm.ko
./net/bluetooth/sco.ko
./net/bluetooth/cmtp
./net/bluetooth/cmtp/cmtp.ko
./net/bluetooth/l2cap.ko
```

I'll try compiling compat-wireless, then manually copying b43 and it's dependencies to /lib/modules/2.6.32-12-generic/updates.

---

### Post by drumin90 on 2010-02-09
> **chenxiaolong said:**
> I wonder if it's because compat-wireless never got installed properly: .

```
chenxiaolong@d6657k1:/lib/modules/2.6.32-12-generic/updates$ find
./drivers
./drivers/misc
./drivers/misc/eeprom
./drivers/bluetooth
./drivers/bluetooth/btsdio.ko
./drivers/bluetooth/btusb.ko
./drivers/bluetooth/bluecard_cs.ko
./drivers/bluetooth/bt3c_cs.ko
./drivers/bluetooth/btmrvl.ko
./drivers/bluetooth/btmrvl_sdio.ko
./drivers/bluetooth/bcm203x.ko
./drivers/bluetooth/bpa10x.ko
./drivers/bluetooth/bfusb.ko
./drivers/bluetooth/btuart_cs.ko
./drivers/bluetooth/hci_vhci.ko
./drivers/bluetooth/dtl1_cs.ko
./drivers/bluetooth/hci_uart.ko
./drivers/net
./drivers/net/atl1e
./drivers/net/atl1e/atl1e.ko
./drivers/net/atlx
./drivers/net/atlx/atl1.ko
./drivers/net/atlx/atl2.ko
./drivers/net/atl1c
./drivers/net/atl1c/atl1c.ko
./dkms
./dkms/vboxnetadp.ko
./dkms/wl.ko
./dkms/vboxdrv.ko
./dkms/vboxnetflt.ko
./compat
./compat/compat_firmware_class.ko
./compat/compat.ko
./net
./net/bluetooth
./net/bluetooth/bluetooth.ko
./net/bluetooth/bnep
./net/bluetooth/bnep/bnep.ko
./net/bluetooth/hidp
./net/bluetooth/hidp/hidp.ko
./net/bluetooth/rfcomm
./net/bluetooth/rfcomm/rfcomm.ko
./net/bluetooth/sco.ko
./net/bluetooth/cmtp
./net/bluetooth/cmtp/cmtp.ko
./net/bluetooth/l2cap.ko
```I'll try compiling compat-wireless, then manually copying b43 and it's dependencies to /lib/modules/2.6.32-12-generic/updates.


When I was compiling compat wireless, there were a few warnings that came up.  It would list them as it was compiling.  If I remember correctly, none of them had to do with a broadcom driver.  I don't know if this would have anything to do with it or not.

---

### Post by leorolla on 2010-02-10
> **chenxiaolong said:**
> [COLOR=Red]2010-02-07: Not working under any kernel, except 2.6.32-11-generic, which does not exist under the Ubuntu Lucid alpha testing repo anymore[/COLOR]

[COLOR=Orange]2010-02-07: Changed links for 2.6.32-12.17-generic[/COLOR]

[COLOR=Orange]2010-02-03: Changed links for 2.6.32-12.16-generic; Untested[/COLOR]

[COLOR=Green]2010-01-29: Working kernel: 2.6.32-11-generic; Working compat-wireless: compat-wireless-2010-01-24[/COLOR]


Isn't it the case of filing a regression bug?

---

### Post by steven6991 on 2010-02-14
Thnx man soooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo much u rock
u can't imagine how much days i've spend trying to make this driver work!
Thnx you so much keep up the good work 
ubuntu

---

### Post by sirsycho on 2010-02-14
I tried with the new linux-2.6.32-13 and the new compat-wireless (2010-02-13) with no luck.  I followed the guide in the first post and I can see the wireless networks but continually get prompted for the password after I enter it (it never completely negotiates the connection).

I see there's a new compat-wireless out there (2010-02-14), anyone have any luck with a particular combination... that is still downloadable?

Thanks!

---

### Post by sirsycho on 2010-02-15
well I got it to work once but it stops working after the reboot... here are my steps:

Install Karmic
Full Update - Reboot
Install 2.6.32-13 headers and image - Reboot
Install git-core and follow instructions here: [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp)
Reboot
.
.
I can now see wireless networks and join them (do not reboot again yet)
.
.
Install Aircrack-ng via apt-get
airmon-ng start wlan0
airodump-ng mon0 (I now see networks and injection works as well)
Test as much as you like... everything seems to work
.
.
Reboot
.
.
Nothing works anymore, I can no longer see networks and dmesg shows it loading the firmware so I'm not sure what's up.  

I've tried: modprobe -r b43 && sleep 3 && modprobe b43 

no dice.

any ideas or help would be greatly apprecaited.

Thanks!!

[EDIT]  dmesg is now showing the following errors repeatedly


```
[   91.008467] b43-phy0: Controller RESET (DMA error) ...
[   91.236385] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   96.749302] b43-phy0: Controller restarted
[   96.749844] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000

```

I am not running compat-wireless... not yet at least.

---

### Post by Loader009 on 2010-02-15
Hello,
I've got a Dell 1555 with the same Wireless NIC.
I'm having the same error as above.
And if I'm trying the tutorial in the first post, I get a "*b43*-phy0 ERROR: *MAC* suspend failed" (in PIO mode).

As the error looks to come in all kernels except the 2.6.32-11, so somebody should look at the changelog.
I would, but I'm very new in linux/ubuntu and wouldn't understand or find anything.
Greetings

PS: Sorry for bad english
<--- german

---

### Post by chenxiaolong on 2010-02-16
sirsycho: You have to use compat-wireless for the card to work. The DMA error occurs when the card is in DMA mode, which crashes the card under high bandwidth. The compat-wireless b43 driver supports PIO mode, which doesn't have this error. BUT, the b43 driver from compat-wireless is not working with the newest kernel :(.

Loader009: I get the same error with one of my routers too (in PIO mode). I'll take a look at the kernel changelog to see what happened after kernel 2.6.32-11. The latest compat-wireless package isn't even compiling anymore :(. (By the way, you're english is great!)

I'm going to try compiling the latest compat-wireless (2010-02-16) on development kernel 2.6.32-13 and stable kernel 2.6.32.8 and see how it goes.

---

### Post by sirsycho on 2010-02-16
chenxiaolong:  Thanks for the reply.  I actually compiled compat-wireless and I don't get the errors anymore but it never completes the handshake, I get prompted for the WPA2-AES password but it just times out.  That was with the 2.6.32-13 and compat-wireless 2010-2-14.  Oh and for what it's worth... I'm using an Airport Extreme router.

Let us know how your testing goes.  If I get a chance I'll try as well tonight.

---

### Post by sirsycho on 2010-02-16
well I tried compat-wireless (2010-02-16) and it wouldn't compile so I switched to (2010-02-15) and still no dice.

I'm still getting the:

```

[   48.772629] wlan0: authenticate with 00:25:bc:XX:XX:XX (try 1)
[   48.972052] wlan0: authenticate with 00:25:bc:XX:XX:XX (try 2)
[   49.172105] wlan0: authenticate with 00:25:bc:XX:XX:XX (try 3)
[   49.372102] wlan0: authentication with 00:25:XX:XX:XX:XX timed out

```

:(

I'm still running 2.6.32-13.

---

### Post by rlelliott on 2010-02-17
Hi guys,

I'm running the fully updated 2.6.32-13 lucid kernel on a Lenovo G550 (4312 14e4:4315) with b43 installed. This card and driver together create a pretty nasty mon mode aircracker, but i am also getting the:

```

[   48.772629] wlan0: authenticate with 00:25:bc:XX:XX:XX (try 1)
[   48.972052] wlan0: authenticate with 00:25:bc:XX:XX:XX (try 2)
[   49.172105] wlan0: authenticate with 00:25:bc:XX:XX:XX (try 3)
[   49.372102] wlan0: authentication with 00:25:XX:XX:XX:XX timed out

```

What i figured out is if you remove the crda package it will not give you this problem. Thing is when you remove that it also removes your kernel!!!! I did it for sh*ts and giggles and it worked great until reboot and no kernel was listed in grub. Does anyone know how to remove crda and still keep the new kernel????

Im using vmware to access the partition in windows 7 to download updates and what not. Had to add rootdelay=10 to make this possible. But it does work.

So for now, linux for "educational purposes". Windows 7 for internet.

ow, and this thread is epic, true story.


also, when injecting, i am able to get about 330-350pps. not bad, def not the best. but injection does work without any patching involved using the svn version of aircrack.

---

### Post by leorolla on 2010-02-18
> **rlelliott said:**
> 
So for now, linux for "educational purposes". Windows 7 for internet.


I know exactly what this feeling is.

You can try jockey or ndiswrapper.

I am running ndiswrapper. Once I got it working it just continued working forever, no breaks.

Jockey works out of the box for Hardy and Jaunty, for Karmic you need to update/upgrade and then it works fine. But it was broken again a month ago and I don't (want to) know if it has been fixed.

For b43, I congratulate brave people who want to get it working, I even want to help, but right now I will just wait for Lucid and see how it will be then.

---

### Post by Loader009 on 2010-02-18
I'm running Lucid beta, w/ 2.6.32-13.18 kernel (updated today from 2.6.32-13) and it don't want to work.
I'll compile the 2.6.32-8 kernel and try it then.
Another thing. Could it be that wireless-crda make broken wifi connection?
Don't know about that package, but I know that earlier was used wireless-regdb instead of wireless-crda.
Greetz

---

### Post by leorolla on 2010-02-18
Maybe you want to try this: [http://ubuntuforums.org/showthread.php?t=1410259](http://ubuntuforums.org/showthread.php?t=1410259)

Chen, feel free if you want to put this link at the first post, so that the poor victims of Ubuntu unstability can get their wireless working.

---

### Post by Loader009 on 2010-02-18
With this you can use nearly every Wireless NIC.
But with that you can't use the Monitor mode, promiscues (or something like this)...

Also I tried the STA driver and everytime the PC hangs. Now the PC hangs if gdm want to have privilegies in Xorg.

This driver can all of this (if it supports the device).
Greetz

---

### Post by leorolla on 2010-02-19
> **Loader009 said:**
> With this you can use nearly every Wireless NIC.
But with that you can't use the Monitor mode, promiscues (or something like this)...

Also I tried the STA driver and everytime the PC hangs. Now the PC hangs if gdm want to have privilegies in Xorg.

This driver can all of this (if it supports the device).
Greetz

What is Monitor mode?

Some people reported not being able to find a Windows driver that works with ndiswrapper, so you can find the linked I have used.

In any case, better with ndiswrapper than having one OS for internet and another OS for other purposes :)

---

### Post by Loader009 on 2010-02-19
Monitor Mode -> [http://en.wikipedia.org/wiki/Monitor_mode](http://en.wikipedia.org/wiki/Monitor_mode)

I've compiled a custom kernel based on the official stable 2.6.32.8 kernel.
Installed and it worked.
Now the driver (b43) works too, but I want to test, if it was only one time.

The STA driver are not open source and I've got problems with it (as already told, ubuntu hangs if the driver is loaded -- found nothing in logs).

ndiswrapper is surely nice but I want "true" WLAN with all WLAN features, include Monitor Mode.
Greetz

---

### Post by chenxiaolong on 2010-02-19
DARN VBULLETIN for not sending me reply emails :o:o. Anyway, I'll see if I can do something about wireless-crda. For now, if you want to remove wireless-cdra, you will have to use videbcontrol (attached to this post) and modify the dependencies line on the linux-image*.deb file. If you don't know what you're doing, then don't do this because when you remove wireless-cdra, it will remove any unmodified (with videbcontrol) kernels.

By the way, videbcontrol works with any deb file.

---

### Post by chenxiaolong on 2010-02-19
I wonder what would happen if I renamed /sbin/crda to /sbin/crda2 and created a script as /sbin/crda that just echoed hi.

---

### Post by rlelliott on 2010-02-19
I downloaded the newest compat-wireless tar and it seems as tho ssb and b43 are broken... :( 

As far as ndis goes..... umm if i wanted to use windows drivers i would boot into Win7 and load up Commview for Wifi..

My goal here is to be able to use the b43 driver without any problems.

Crash course in writing drivers? I think so :)

---

### Post by Loader009 on 2010-02-20
I don't know if it is the driver or the kernel.
With official stable 2.6.32.8 kernel it works fine. (Compiled with make oldconfig then make-kpkg --initrd)

I don't know how to remove depencies, so I will not test videbcontrol.
I have very little linux knowledge.
Only some basics, some compiling things and the "build kernel" thing is not really what for me. (Because of this I used "make oldconfig")
Greetz

---

### Post by chenxiaolong on 2010-02-20
Are you using PIO mode for the driver? In other words, did you compile compat-wireless and run "echo "options b43 pio=1" | sudo tee -a /etc/modprobe.d/b43.conf"? I know DMA mode works normally on the 2.6.32.* kernels, but it will eventually give the Fatal DMA Error.

---

### Post by Loader009 on 2010-02-20
Nope, I'm using the DMA mode.
But as I noticed, the connection is lost randomly (does such a word exist?) and won't connect.
It even doesn't scan (iwlist scan --- no scan result (or something like that)). <- Sounds like that the device crashed ->

Looks like my kernel is crap...

But it works for a few minutes...

Since my rsyslogd is taking much of CPU load, I had to turn it of.
So I haven't (yet) any usefull log.

I'm working on that rsyslog problem but it may take a while.
Greetz

---

### Post by rlelliott on 2010-02-20
BCM 4312 LP Phy compat-wireless stack on (Ubuntu) Linux kernel 2.6.32.14-20 w/ monitor mode & full IPv4 connectivity write up coming soon!!! 10+ cold boots and no breakage with DMA mode!! Thanks goes out to the creator of this thread. Ow and a huge shout out to the compat-wireless team!

---

### Post by chenxiaolong on 2010-02-20
rlelliott: That's great news :D! Could you test to see if the card crashes when downloading a large file, like the Ubuntu CD image? That's usually when the Fatal DMA Error occurs. 

Loader009: Most log messages are shown in dmesg (command: dmesg), so you don't need rsyslogd. By the way, randomly is a word :D.

---

### Post by rlelliott on 2010-02-20
Man I haven't slept in weeks and I have no idea what food is for anymore. I'll start the download and let you know what I find. Its so weird, I had to have bcmwl sta driver auto load, then unload the sta driver load the b43.. Full details soon. :)


I know that sound like a pain in the *****, but if you build launchers its no more than a few double clicks to either be in mon mode or connect to the internet. The injection rate is something like 600-750 pps with a tuned svn aircrack and airoscript compile :)


UPDATE: Downloading Ubuntu 9.10 now. If this download is successful without any fatal DMA errors i will start my write up on the process used to get this working. **crosses fingers**

---

### Post by rlelliott on 2010-02-20
alright guys, Im working with a wireless broadband internet connection from sprint.... and im sharing it with my roommates also, sooooooooo it's extremely slow. I have no way to currently test a high speed 10mbit+ wifi connection.. :(

The download is going to take about 2 hrs..

---

### Post by chenxiaolong on 2010-02-20
That's fine. I don't have a very high speed connection either.

---

### Post by rlelliott on 2010-02-20
** UPDATE: ** 640mb downloaded without any errors of any kind. while this finishes i will go ahead and start typing the steps i took to get this working, i will leave out the 20 or more "let's format and try again's".....

Once again thanks go out to chenxiaolong for all the help and hand holding that has been done though out this 46 page thread. your the man. Also lets not forget the hard work that the compat-wireless team has done to get us this far.




If anyone would like to chat while im testing you can reach me @

yahoo: killin1a4

msn: [email]killin1a4@hotmail.com[/email]

dmesg so far after 300mb and 3 or 4 svn downloads and compiles is...




[ 1534.932456] wlan0: direct probe to AP 00:1c:df:61:xx:xx (try 1)
[ 1535.132058] wlan0: direct probe to AP 00:1c:df:61:xx:xx (try 2)
[ 1535.134655] wlan0: direct probe responded
[ 1535.134659] wlan0: authenticate with AP 00:1c:df:61:xx:xx (try 1)
[ 1535.136629] wlan0: authenticated
[ 1535.136646] wlan0: associate with AP 00:1c:df:61:xx:xx (try 1)
[ 1535.139284] wlan0: RX AssocResp from 00:1c:df:61:xx:xx (capab=0x411 status=0 aid=3)
[ 1535.139287] wlan0: associated
[ 2157.161282] Skipping EDID probe due to cached edid
[ 2157.197199] Skipping EDID probe due to cached edid
[ 2158.172164] Skipping EDID probe due to cached edid
[ 2158.204123] Skipping EDID probe due to cached edid
[ 2158.240140] Skipping EDID probe due to cached edid
[ 2167.644154] Skipping EDID probe due to cached edid
[ 2167.676140] Skipping EDID probe due to cached edid
[ 2167.716137] Skipping EDID probe due to cached edid
[ 2168.328121] Skipping EDID probe due to cached edid
[ 2173.649090] Skipping EDID probe due to cached edid
[ 2297.984160] Skipping EDID probe due to cached edid
[ 2298.641207] Skipping EDID probe due to cached edid
[ 2298.673186] Skipping EDID probe due to cached edid
[ 2299.704155] Skipping EDID probe due to cached edid
[ 2299.736221] Skipping EDID probe due to cached edid
[ 2299.768146] Skipping EDID probe due to cached edid
[ 2305.420159] Skipping EDID probe due to cached edid
[ 2305.925366] Skipping EDID probe due to cached edid
[ 2335.729124] Skipping EDID probe due to cached edid
[ 2344.284151] Skipping EDID probe due to cached edid
[ 2345.008153] Skipping EDID probe due to cached edid
[ 3900.724033] CE: hpet increasing min_delta_ns to 15000 nsec
[ 4016.949132] Skipping EDID probe due to cached edid
[ 4021.480127] Skipping EDID probe due to cached edid
[ 4060.024128] Skipping EDID probe due to cached edid
[

---

### Post by northd_tech on 2010-02-20
Hi rlelliott,

There has been a rash of recent slowness with ubuntu internet related to IPv6, OpenDNS, etc. (esp. under Karmic 9.10).

You might want to take a look at this/these threads:

[http://ubuntuforums.org/showpost.php?p=8849219&postcount=4](http://ubuntuforums.org/showpost.php?p=8849219&postcount=4)

---

### Post by rlelliott on 2010-02-20
just a quick summary of what I have done to get the b43 driver and firmware working. 

Downloaded last nights "nightly" build of lucid. Installed from usb.

After the system was up I proceeded to install bcmwl kernel source that came with the build under the pool dir.

after i had internet i made sure the build was fully updated and installed kernel image 2.6.32.14-20 with matching headers.

I then followed the directions to the letter to install firmware  @ 

[http://wireless.kernel.org/en/users/Drivers/b43#device_firmware_installation](http://wireless.kernel.org/en/users/Drivers/b43#device_firmware_installation)

under the 

"You are using the b43 driver with an LP-PHY card (e.g. BCM4312)"

section.

I then downloaded the "compat-wireless-2009-10-14" tar file @ 

[http://www.orbit-lab.org/kernel/compat-wireless-2.6/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/)

followed the directions to build and install @ 

[http://wireless.kernel.org/en/users/Download#Building_and_installing](http://wireless.kernel.org/en/users/Download#Building_and_installing)

after the install I ran "rmmod wl" to unbind the wl driver from my wireless card. Then ran while still in the compat dir "make unload" to unload anything else pertaining to wireless. I then ran "modprobe b43" to bind the b43 driver to my wireless nic. after that it was smooth sailing.

After the first cold boot the wl driver re-binds to the wifi's nic, so all that needs to be done is to run rmmod wl and the cd to the compat dir and run make unload. bind the b43 driver back with modprobe... this has worked flawlessly without any DMA errors or timeouts. ow and yea and your favorite wireless pen testing programs work like a charm after a quick compile of iw source (this allows programs to control your wifi nic..... 

I'll post a full command for command write up soon. If you have questions about this process before i finish the write, just post them here, Im sure either me or the owner if this thread "chenxiaolong" will be able to help you.


I will not pretend to know why this works, but it does. I have even went as far as starting a download and then flipping the hard switch in the front of my Lenovo G550 off and had no hang ups at all. and yes the switch works and turns the led off.



Enjoy!

---

### Post by chenxiaolong on 2010-02-20
rlelliott: Thanks for the guide :D. I'll be doing a complete system format probably tomorrow, so I'll try this out and see how it goes :D.

Again, thank you soo much for the testing.

---

### Post by avilella on 2010-02-21
Great howto! I've added the link to the Lenovo G550/G450/G560 website ([http://launchpad.net/~lenovo-g550](http://launchpad.net/~lenovo-g550)).

---

### Post by rlelliott on 2010-02-21
I have completed a written guide including term entries and hyper-linked download locations. It can be found @ [http://docs.google.com/View?id=dhkq5635_11f3hjxdp6](http://docs.google.com/View?id=dhkq5635_11f3hjxdp6)

If any finds any errors in the code posted, please email me @ [email]rlelliott@gmail.com[/email] with your findings and fixes.

---

### Post by sirsycho on 2010-02-21
rlelliott:  I haven't looked at your full write-up yet but your abbreviated notes worked like a charm ... so far at least :).  I've been up for about 3 reboots and just started downloading the current lucid build just to see.

Out of curiosity, have you tried a more recent release of compat-wireless?  if so, I'm assuming there were problems?  Just trying to avoid testing something you've already tried.

Thanks!!

---

### Post by rlelliott on 2010-02-21
The bleeding edge builds of compat will not build without 2.6.33.xx kernel and headers.

---

### Post by rlelliott on 2010-02-21
> **sirsycho said:**
> rlelliott:  I haven't looked at your full write-up yet but your abbreviated notes worked like a charm ... so far at least :).  I've been up for about 3 reboots and just started downloading the current lucid build just to see.

Out of curiosity, have you tried a more recent release of compat-wireless?  if so, I'm assuming there were problems?  Just trying to avoid testing something you've already tried.

Thanks!!

2 weeks with no sleep and 20+ formats later.... geezz what a task this was.

---

### Post by sirsycho on 2010-02-23
> **rlelliott said:**
> 2 weeks with no sleep and 20+ formats later.... geezz what a task this was.

Indeed... I had all but given up until I saw your post.  

I meant to post yesterday but I did want to say that I finally got Lucid (10.04) running in triple boot on my Dell Mini 10v, though it was no trivial task with the Ubiquity installer being quite buggy in the latest daily builds (only when you do manual partitioning or want to put the bootloader on a partition).

If anyone is really interested I can write something up but for those more adventurous... I just did a normal triple boot with 9.10 Karmic and then did an install of 10.04 on top of it without reformatting or installing the bootloader.

You will have to go in and reinstall chameleon (I used Netbook Installer) and may need to repair grub afterward (YMMV with that one).  Once you've reinstalled 10.04, you have to do all the steps over again for fixing your bootloaders (chameleon and windows and then linux will work from the chameleon menu).

Basic Triple boot howto here: [http://www.youtube.com/user/anguish79#p/u/3/UiI-AxL4RBU](http://www.youtube.com/user/anguish79#p/u/3/UiI-AxL4RBU)

Good luck and thanks again to all who have contributed to this thread.

---

### Post by leorolla on 2010-02-24
**Good that it works! This is really nice news.

In the Installation Guide, is there any reason for installing bcmwl-kernel-source beforehand, other than having internet connection for the next steps?

Why can't you just uninstall wl and have b43 being loaded automatically during boot?[I]

[/I]

---

### Post by MarioHaddad on 2010-02-24
thnx relliott!!!!!... btw i still have the  [COLOR=Green] 2.6.32-11-generic kernel files on my laptop... i can upload them if you need them !... btw where is the best place to upload them ?... rapidshare has a limit on the number of downloads right ?... (for FREE.. )[/COLOR]

---

### Post by mikeioannina on 2010-02-24
Thanks! I had the wireless working on my Acer Aspire One D250 before two months but after a kernel update it stopped working. I did 5 reformats since then, trying to fix it with many methods, but finally made it work again! I just did everything that the first post says, except i used kernel [color=blue]2.6.32-14-20[/color]. I also had to do this:
> then add these lines to /etc/rc.local (thanks to Muti for this information)

```
modprobe -r b43
sleep 3
modprobe b43
```

Everything works good, monitor mode works also when connected to my wlan.:D

---

### Post by chenxiaolong on 2010-02-24
MarioHaddad: You can use mediafire.com. There's no download limit (as far as I know).

mikeioannina: Are you running Ubuntu Karmic or Lucid. If you are running Karmic with b43 working, I'll update my first post with the info.

---

### Post by mikeioannina on 2010-02-24
> **chenxiaolong said:**
> mikeioannina: Are you running Ubuntu Karmic or Lucid. If you are running Karmic with b43 working, I'll update my first post with the info.

I am running Karmic with updated kernel 2.6.32-14-20 and b43 working.

The steps I followed were these. It is from the first post, slightly changed some things:
> **chenxiaolong said:**
> Download and install the b43 device firmware. Make sure you have the package "[COLOR="SeaGreen"]git-core[/COLOR]" installed then follow the instructions at this link: [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp). It's very easy to follow. They're copy and paste commands.

First of all, download and install the new kernel 2.6.32-14-20:

i386 (32 bit)
---------------
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic_2.6.32-14.20_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic_2.6.32-14.20_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic_2.6.32-14.20_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic_2.6.32-14.20_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb)


i386-PAE (32 bit with _>_ 4 GB of RAM)
---------------------------------------------
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic-pae_2.6.32-14.20_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic-pae_2.6.32-14.20_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic-pae_2.6.32-14.20_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic-pae_2.6.32-14.20_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb)


amd64 (64 bit)
----------------
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic_2.6.32-14.20_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-2.6.32-14-generic_2.6.32-14.20_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic_2.6.32-14.20_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14-generic_2.6.32-14.20_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-2.6.32-14_2.6.32-14.20_all.deb)

Then run: 

```
sudo dpkg -i linux*2.6.*.deb
```

in the folder.

Boot into the new kernel by choosing it from the GRUB boot menu.

Then, head on over here: [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and download the latest compat-wireless-2010-**-**.tar.gz package to anywhere, preferably an easy to remember location. The package as of now is, compat-wireless-2010-02-24.tar.bz2. I will be using this version for the commands below. Adjust the commands below based on the file you downloaded.

Open up a Terminal and change to the directory you downloaded the file to:

```
cd /your/path/to/the/directory
```

Extract the file you downloaded:

```
tar jxvf compat-wireless-2010-02-24.tar.bz2
```

Change to the extracted directory:

```
cd compat-wireless-2010-02-24
```

Compile the drivers:

```
make
```

Install the drivers:

```
sudo make install
```

Unload the current drivers: (if you are using the Broadcom STA Driver, run "sudo rmmod wl" first)

```
sudo make unload
```

Refresh the drivers/modules for the current kernel:

```
sudo depmod
sudo depmod -a
```

Enable PIO mode:

```
echo "options b43 pio=1" | sudo tee -a "/etc/modprobe.d/b43-thingy.conf"
```

Remove the package "[COLOR="SeaGreen"]bcmwl-kernel-source[/COLOR]." It's the easiest way to ensure that the b43 driver isn't blacklisted. 

Blacklist the wl driver (STA driver):

```
echo "blacklist wl" | sudo tee "/etc/modprobe.d/blacklist.conf"
echo "blacklist ssb" | sudo tee "/etc/modprobe.d/blacklist.conf"
```

Add b43 to /etc/modules so it will load at bootup:

```
echo "b43" | sudo tee -a "/etc/modules"
```

After reboot, I got errors in dmesg like:

```
[   11.788669] b43: Unknown symbol ssb_pcicore_dev_irqvecs_enable
[   11.789575] b43: disagrees about version of symbol ssb_bus_may_powerdown
[   11.789586] b43: Unknown symbol ssb_bus_may_powerdown
[   11.790340] b43: disagrees about version of symbol ssb_dma_free_consistent
[   11.790351] b43: Unknown symbol ssb_dma_free_consistent
[   11.792008] b43: disagrees about version of symbol ssb_bus_suspend
[   11.792020] b43: Unknown symbol ssb_bus_suspend
[   11.793154] b43: disagrees about version of symbol ssb_bus_unregister
[   11.793166] b43: Unknown symbol ssb_bus_unregister
[   11.795081] b43: disagrees about version of symbol ssb_bus_resume
[   11.795093] b43: Unknown symbol ssb_bus_resume
[   11.795509] b43: disagrees about version of symbol ssb_set_devtypedata
[   11.795520] b43: Unknown symbol ssb_set_devtypedata
[   11.796959] b43: disagrees about version of symbol ssb_device_disable
[   11.796972] b43: Unknown symbol ssb_device_disable
[   11.797411] b43: disagrees about version of symbol ssb_pmu_set_ldo_voltage
[   11.797422] b43: Unknown symbol ssb_pmu_set_ldo_voltage
[   11.798340] b43: disagrees about version of symbol ssb_dma_alloc_consistent
[   11.798350] b43: Unknown symbol ssb_dma_alloc_consistent
[   11.799029] b43: disagrees about version of symbol ssb_dma_set_mask
[   11.799042] b43: Unknown symbol ssb_dma_set_mask
[   11.801861] b43: disagrees about version of symbol ssb_device_enable
[   11.801874] b43: Unknown symbol ssb_device_enable
[   11.802820] b43: disagrees about version of symbol ssb_driver_unregister
[   11.802833] b43: Unknown symbol ssb_driver_unregister
[   11.804095] b43: disagrees about version of symbol __ssb_driver_register
[   11.804109] b43: Unknown symbol __ssb_driver_register
[   11.821841] b43: Unknown symbol ssb_bus_pcmciabus_register
[   11.822234] b43: disagrees about version of symbol ssb_bus_powerup
[   11.822243] b43: Unknown symbol ssb_bus_powerup
[   11.826522] b43: disagrees about version of symbol ssb_dma_translation
[   11.826535] b43: Unknown symbol ssb_dma_translation
```

then added these lines to /etc/rc.local (thanks to Muti for this information)

```
modprobe -r b43
sleep 3
modprobe b43
```

And everything works ok after several reboots, the driver loads itself automatically on boot with no problems


---

### Post by chenxiaolong on 2010-02-24
Thanks :D. I'll update my first post with the new info.

---

### Post by MarioHaddad on 2010-02-24
i just tried this with 32.14-20 about 3 times :( this is what i did the last time : freshly installed karmic that comes with 31-14,installed bcmwl-kernel-source from karmic cd ,updated to 31-19, downloaded the firmware as instructed, upgraded to 32.14-20 PAE >= 4GB, followed instructions, but when i finish and reboot, i get nothing.. no wireless... the wifi light on my dell studio doesnt even turn on... i tried adding the 3 lines in the end..... but didnt help... when i try sudo modprobe b43 it just hangs.. its like it goes into an endless loop or something.. i can stop it with CTRL C... 
and there isnt a DMA error...
so... :( what can i do ? :(

---

### Post by chenxiaolong on 2010-02-24
Could you post the output of "dmesg | tail" from a separate terminal while "sudo modprobe b43" hangs?

---

### Post by MarioHaddad on 2010-02-25
ok, i got it fixed, dunno why.... when i removed those three lines from rc.local everything worked... 

and thats my dmesg, 

[  424.598681] evbug.c: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[  424.726884] evbug.c: Event. Dev: input5, Type: 4, Code: 4, Value: 38
[  424.726905] evbug.c: Event. Dev: input5, Type: 1, Code: 38, Value: 1
[  424.726915] evbug.c: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[  424.815096] evbug.c: Event. Dev: input5, Type: 4, Code: 4, Value: 38
[  424.815117] evbug.c: Event. Dev: input5, Type: 1, Code: 38, Value: 0
[  424.815127] evbug.c: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[  425.007393] evbug.c: Event. Dev: input5, Type: 4, Code: 4, Value: 28
[  425.007414] evbug.c: Event. Dev: input5, Type: 1, Code: 28, Value: 1
[  425.007424] evbug.c: Event. Dev: input5, Type: 0, Code: 0, Value: 0


it just keeps going like this.. i dont know what input5 is..

---

### Post by Bradicus on 2010-02-25
I recently bought a Lenovo S10-3t, and have been having a few issues with getting some of the hardware to work, most importantly the wifi card. It is the bcm4313. It worked fine with the windows install the device came with. Does anyone have any experience with this card? I'm running the netbook remix, which is 9.10 I believe, and I'm not able to see the card. Any info would be appreciated, if I'm leaving anything out that is needed please let me know.

---

### Post by chenxiaolong on 2010-02-25
MarioHaddad: Input5 is the fifth input device you plug in, such as a mouse, keyboard, or tablet. 

Bradicus: You might have better luck finding help if you start a new thread, so other people can help you. I don't have this card, so I can't help you very much. Sorry :(.

---

### Post by MarioHaddad on 2010-02-25
> **chenxiaolong said:**
> MarioHaddad: Input5 is the fifth input device you plug in, such as a mouse, keyboard, or tablet. 



im on my laptop with no external devices... u know where i could find a list of connected devices with their numbering ?

---

### Post by chenxiaolong on 2010-02-25
If you want to list your:

PCICMA/Expresscard/PCI cards: "lspci"
USB: "lsusb"
Network hardware: "lshw -C Network"
Input devices: "xinput --list"     ----   I think :D

---

### Post by rlelliott on 2010-02-25
chromium is a beast on lucid... that is all

---

### Post by chenxiaolong on 2010-02-25
Way off topic, but I love chromium too.

---

### Post by rlelliott on 2010-02-25
Sorry about going off topic, i just popped in to see what was going on in here.

---

### Post by leorolla on 2010-02-26
> **leorolla said:**
> Good that it works! This is really nice news.

In the Installation Guide, is there any reason for installing bcmwl-kernel-source beforehand, other than having internet connection for the next steps?

Why can't you just uninstall wl and have b43 being loaded automatically during boot?

I'm wondering if it can be installed directly, without installing first the bcmwl-kernel-source...

---

### Post by rlelliott on 2010-02-27
On a Lenovo G550 R6U, after putting notebook in hibernation, when it came back up, dmesg shows that the the card is having dma errors. I powered down the machine. After sitting for about 20 seconds, powered on the machine. I rmmod wl, then modprobe b43. No DMA errors. I have not tried to load b43 without first loading the wl driver. Has anyone tested this?

---

### Post by dalga999 on 2010-02-27
I have been trying to make packet injection work under ubuntu 9.04, in pio mode with no success. I tried it under linux 2.6.32.14.20 and compat-wireless2-24. 
Internet works, but packet injection/monitor mode only works for 5-10 seconds then it doesnt work, and connections fail. I need to do modprobe -r b43 and modprobe b43 to make the internet work again. I also upgraded to 9.10 ubuntu, but things didnt change.
 
 I have a question? What is a DMA error, and is there a way to recover from that error?
 
Thanks

---

### Post by MarioHaddad on 2010-02-27
> **dalga999 said:**
> I have been trying to make packet injection work under ubuntu 9.04, in pio mode with no success. I tried it under linux 2.6.32.14.20 and compat-wireless2-24. 
Internet works, but packet injection/monitor mode only works for 5-10 seconds then it doesnt work, and connections fail. I need to do modprobe -r b43 and modprobe b43 to make the internet work again. I also upgraded to 9.10 ubuntu, but things didnt change.
 
 I have a question? What is a DMA error, and is there a way to recover from that error?
 
Thanks


i dont know what a DMA error is, but these are the ways to recover from it:
1) a simple turn off wait 30 seconds then turn on might work ( worked for me sometimes )
2) if you're on a laptop: turn off. remove power cord, remove battery, while screen opened press the power button for 30 seconds + .... then return everything and turn on. this might work on a desktop by removing power cord and pressing the power button for 30 secs... but didnt try it ;) 
3) if none works, you have to TAKE OUT the card, and make contact between all of the pins of the card.. ( using something metal of course ) that should reset it. 
4) if none worked, then you're in trouble.....

hope that helps

---

### Post by rlelliott on 2010-02-27
If you follow the guide I have posted, internet and injection works with out a problem using svn aircrack-ng and airoscript.

---

### Post by dalga999 on 2010-03-01
I did not activate the DMA mode because I dont want to risk my laptop right now, I need to be connected to the internet. I tried the instructions on the first page, kernel 2.6.32.14 with compat-wireless and pio mode, the injection do not work on karmic: when I do airodump after airmon, it works for 5 seconds then stops working. I stopped networkmanager before doing it, but nothing changed.
 
Does it really matter that we use karmic, lucid or other releases? Shouldnt it depend only on the kernel, compat-wireless version and b43 ?

---

### Post by Loader009 on 2010-03-02
I have now installed kubuntu karmic koala (9.10) and getting the DMA error.
I tried the tutorial on the first page and the link... nothing worked neither on lucid nor on karmic...
Any idea?
I also tried the newest and the 2009-10-14 driver, nothing... Don't work either.
Greetz

PS: kernel was/is 2.6.32-14.20

---

### Post by rlelliott on 2010-03-02
> **Loader009 said:**
> I have now installed kubuntu karmic koala (9.10) and getting the DMA error.
I tried the tutorial on the first page and the link... nothing worked neither on lucid nor on karmic...
Any idea?
I also tried the newest and the 2009-10-14 driver, nothing... Don't work either.
Greetz

PS: kernel was/is 2.6.32-14.20

-----------------------------------------------------------------




You may want to take a look at this ------->>


[https://docs.google.com/ViewdocID=0ASbhSfPvr6pZZGhrcTU2MzVfMTFmM2hqeGRwNg&revision=_latest&hgd=1]("https://docs.google.com/View?docID=0ASbhSfPvr6pZZGhrcTU2MzVfMTFmM2hqeGRwNg&revision=_latest&hgd=1")

---

### Post by Loader009 on 2010-03-03
Yes, with "I tried the tutorial on the first page and **the link**..." I ment your link.
I skipped the installation of bcmwl cause it made me problems from the first day. (The os hangs.)
I haven't tried bcmwl with my actual (kubuntu karmic koala) distribution.

I installed the build-essentials, the compiled and installed compat wireless and then (cause I forgot) I installed b43-fwcutter.
Now I'm getting all the time the DMA error.

Is it because I don't use bcmwl and doesnt rmmod it?
Maybe b43 doesn't load the NIC right and so the DMA error comes?
Greetz

---

### Post by m1lkman on 2010-03-05
Got this to work on Acer Aspire One (D250) with a few hurdles involving grub hacks for booting new kernel and manually having to load the b43 driver.

Unfortunately it's got some quirks.  I cant get the b43 to load at startup (as instructed by the guide ).  No missing symbol errors in dmesg although I do get a missing parameter error:

```
m1lkman@shorepoint:~/b43/compat-wireless/compat-wireless-2010-03-04$ dmesg | grep b43
[    2.071920] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.071950] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[   13.765167] b43: Unknown parameter `pio'
[   14.345117] b43: Unknown parameter `pio'

```

Not sure what to make of that, anyway, after following the guide and rebooting I was not able to get the b43 driver to load.  sudo modprobe, as correctly stated in the guide, does not work nothing.

On a hunch I tried:

```
sudo insmod /lib/modules/2.6.32-14-generic/kernel/drivers/net/wireless/b43/b43.ko

```

Couple seconds later, the wireless LED lit up, along with a wlan0 interface, yay!!!

I'm not even sure if this b43.ko was created by me or came with this install as this is a new install, anyways:

The physical radio hardware switch works as well.  

"iwlist scan" and the gnome network manager applet both detect and show wireless networks.

Also I can connect to open networks ( but that's it )

Unfortunately, upon trying to connect to my local WEP network I get:

```
[ 3397.596848] wlan0: associate with AP 00:23:75:02:00:e0 (try 1)
[ 3397.598899] wlan0: RX AssocResp from 00:23:75:02:00:e0 (capab=0x451 status=0 aid=1)
[ 3397.598915] wlan0: associated
[ 3397.624121] wlan0: deauthenticating from 00:23:75:02:00:e0 by local choice (reason=3)

```

After trying to connect to my local WEP AP.  I'm not sure why but if I had to guess,  it would be because I need to load some b43 crypto/authentication modules as my local AP uses WEP.  I have no clue as to the name of these modules so I cant test it.

If anyone knows what these modules are named that would be great as I can just manually load them and make a script, I don't care if it's hackish.  Unless, of course someone has a better solution or explanation as to why the drivers may have failed to load.

---

### Post by chenxiaolong on 2010-03-05
I feel bad writing a short post after you wrote such a long one :(. I also don't want to burst your bubble, but you are still using the stock b43.ko from the kernel, which doesn't support PIO mode (the point of this guide was to have b43 working in PIO mode). The b43.ko from compat-wireless will be in a subfolder in /lib/modules/2.6.32-14-generic/updates (sorry, I don't know the exact folder), not /lib/modules/2.6.32-14-generic/kernel/drivers/net/wireless/b43/b43.ko. 

You can find out if it was correctly installed by running:

cd /lib/modules/2.6.32-14-generic/updates
find | grep b43.ko

Good Luck

---

### Post by m1lkman on 2010-03-05
Yeah I gave it a closer look this morning and realized what I actually did.  I don't know how basic something like that is but I might as well just give up after that. doh!  Screw it, I'll just use my alfa card.

---

### Post by TironN on 2010-03-05
I had given up on this for too long but now I'm back home (you know with good internet and a decent computer at the side), I'm ready to lend my failures to the fray!

---

### Post by chenxiaolong on 2010-03-05
It's nice to see that people haven't given up :D:D. Can anybody test to see if the compat-wireless b43 driver works on kernel 2.6.33? The latest version of compat-wireless should work and the kernel can be downloaded from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/). Unfortunately, I can't test because I inadvertently deleted my Ubuntu partition while I installed another distro to see if the b43 errors are only in Ubuntu kernels :(.

---

### Post by m1lkman on 2010-03-06
> **chenxiaolong said:**
> It's nice to see that people haven't given up :D:D. Can anybody test to see if the compat-wireless b43 driver works on kernel 2.6.33? The latest version of compat-wireless should work and the kernel can be downloaded from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/). Unfortunately, I can't test because I inadvertently deleted my Ubuntu partition while I installed another distro to see if the b43 errors are only in Ubuntu kernels :(.

I got an error when I tried to install that kernel, looks like its due to a broadcom module or something?  btw - I'm running a clean install of UNR updated to "Linux version 2.6.31-20-generic"

```
m1lkman@shorepoint:~/kernel$ sudo dpkg -i linux*2.6.*.deb
Selecting previously deselected package linux-headers-2.6.33-020633.
(Reading database ... 135208 files and directories currently installed.)
Unpacking linux-headers-2.6.33-020633 (from linux-headers-2.6.33-020633_2.6.33-020633_all.deb) ...
Selecting previously deselected package linux-headers-2.6.33-020633-generic.
Unpacking linux-headers-2.6.33-020633-generic (from linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb) ...
Selecting previously deselected package linux-image-2.6.33-020633-generic.
Unpacking linux-image-2.6.33-020633-generic (from linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb) ...
Done.
Setting up linux-headers-2.6.33-020633 (2.6.33-020633) ...
Setting up linux-headers-2.6.33-020633-generic (2.6.33-020633) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.33-020633-generic                                                   
 *  bcmwl (5.10.91.9+bdcom)...                                                                                               bcmwl (5.10.91.9+bdcom): Installing module.
........(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                                                                      [fail]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-image-2.6.33-020633-generic (2.6.33-020633) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.33-020633-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.33-020633-generic
Found initrd image: /boot/initrd.img-2.6.33-020633-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 8.10 (8.10) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.33-020633-generic                                                   
 *  bcmwl (5.10.91.9+bdcom)...                                                                                               bcmwl (5.10.91.9+bdcom): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                                                                      [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

m1lkman@shorepoint:~/kernel$ 

```

Any ideas?  Edit: n/m It looks like it worked, I was able to boot it from grub and /proc/version list it as current, should I continue to try and test it or did I screw something up?

---

### Post by rlelliott on 2010-03-06
i downloaded  yesterdays daily lucid build. It installed perfectly. bcmwl drivers would not install correctly for me me, but because i have already followed the steps for cutting my firmware, i already had the files on a thumb drive. The first reboot was fine with the stock b43 drivers that came with the build. After a reboot received a fatal dma error almost instantly. I then proceeded to compile the compat-wireless package i have been using with success "compat-wireless-2009-10-14". A few warning durring make but nothing serious or have to do with the b43 drivers i was after. make unload then reboot. rmmod ssb, modprobe b43..... and there we have it, full wireless capabilities. And just so everyone knows the bleeding edge compat package will not compile under 2.6.33.xx  :(


But progress IS being made. I now no long have to load the wl driver at boot the unload it and load b43. I am booting strait in. Unloading ssb, and loading b43. I have rebooted 4 or 5 time and it is stiff working!

---

### Post by TironN on 2010-03-06
Ok well heres what Ive got at the moment:
Followed all the steps using compat-wireless-2010-03-04.
Its connected fine and all but is timing out. Turns out I'm getting the fatal dma errors. I think I may be running the wrong b43 version

---

### Post by m1lkman on 2010-03-06
I'm still playing with it but, short of reinstalling a fresh distribution on a partition.  What's the best way to go about uninstalling some of these old and test kernels and remove them from grub menu to clean thing up?

---

### Post by chenxiaolong on 2010-03-06
TironN: You will have to take out your card, touch all the pins (at the same time) to short out the RAM circuit and put the card back in.

m1lkman: You can remove the old kernels using Synaptic or apt-get by running: (purge means remove package along with configuration files)

sudo apt-get purge linux-image-2.6.3*.*-generic
sudo apt-get purge linux-headers-2.6.3*.*-generic

Ubuntu tweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)) also has a tab in the program which lets you remove old kernels.

---

### Post by rlelliott on 2010-03-06
The drivers that come with the newest daily builds are giving me DMA errors. But if i load the wl driver @ boot, then load the compat b43 driver after login, everything works great..... very weird>

---

### Post by Loader009 on 2010-03-06
Due to this fact (that b43 only works right after loading and unloading bcmwl) I think that b43 either doesn't load the NIC right or there is a firmware conflict.
Only an idea that I thougt.
Greetz

---

### Post by chenxiaolong on 2010-03-06
rlelliott: The compat-wireless build definitely should not give DMA errors because they are patched to use PIO mode. Are you sure you are the compat-wireless b43 driver and not the native kernel driver? The newest compat-wireless builds (actually, since February) don't compile under kernsl 2.6.32, only 2.6.33.

Loader009: I really have no idea at all. You might be right :).

---

### Post by rlelliott on 2010-03-07
> **chenxiaolong said:**
> rlelliott: The compat-wireless build definitely should not give DMA errors because they are patched to use PIO mode. Are you sure you are the compat-wireless b43 driver and not the native kernel driver? The newest compat-wireless builds (actually, since February) don't compile under kernsl 2.6.32, only 2.6.33.

Loader009: I really have no idea at all. You might be right :).


I was using the b43 driver that comes with the daily lucid builds without pio mode enabled. I would rather not use pio mode because it kills the overall output of the nic. Basicly i loaded the os, threw the bcm4312 firmware in the needed dir and rebooted the system. When it came back up, i had instant DMA errors. The only solution to this problem I have found is to install bcmwl, let it auto-load with the os, after log on, unload wl and load the compat wireless b43 driver with DMA mode enabled. I installed kde 4.4 on my latest lucid build, and man is it sweet. With my current Gnome/KDE hybrid Ubuntu Lucid build, wireless is functioning as intended and with vmware workstation installed I have no need to ever boot directly back into Windows 7 again. Wow... :)

---

### Post by chenxiaolong on 2010-03-07
Ohhhh. That's awesome. Can you see if it still works if you have the unloading and loading done automatically by putting this in /etc/rc.local (before "exit 0"):

rmmod wl
modprobe b43

By the way, KDE 4.4 is amazing :D.

---

### Post by rlelliott on 2010-03-07
> **chenxiaolong said:**
> Ohhhh. That's awesome. Can you see if it still works if you have the unloading and loading done automatically by putting this in /etc/rc.local (before "exit 0"):

rmmod wl
modprobe b43

By the way, KDE 4.4 is amazing :D.




I added the two entries above to rc.local and it worked! So those 2 commands automated the release and rebind of the nic and made the launchers i created obsolete.... good stuff. ty :)

---

### Post by chenxiaolong on 2010-03-07
Great! It's nice to know that it will work on the next Ubuntu version...one and a half months before the actual release :D.

---

### Post by boesl on 2010-03-08
Hello,

I've a HP 615, the same problem with wireless connection. I tried to follow the steps in the first post, but I've problems with updating the kernel.

Here's the log:
```
Richte linux-image-2.6.32-14-generic ein (2.6.32-14.20) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-14-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.32-14-generic
Found initrd image: /boot/initrd.img-2.6.32-14-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.32-14-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Installing module.
........(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

```

Seems that the fglrx driver makes problems with update.


Here are other facts of my laptop:


**cat /etc/lsb-release **

```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=8
RELEASE_NOTES_URL=http://www.linuxmint.com/rel_helena.php
DISTRIB_CODENAME=helena
DISTRIB_DESCRIPTION="Linux Mint 8 Helena - x64 Edition"
```


**iwconfig**

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```


**ifconfig**

```
eth0      Link encap:Ethernet  Hardware Adresse 18:a9:05:d4:70:09  
          inet Adresse:192.168.1.11  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::1aa9:5ff:fed4:7009/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:3922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3088 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:3816852 (3.8 MB)  TX bytes:456611 (456.6 KB)
          Interrupt:10 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```


**lspci -nn | grep -i net**

```
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4357] (rev 10)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```


Don't know what to do. Would be fine, if anybody can help me.

---

### Post by chenxiaolong on 2010-03-08
The fglrx module is the driver for your ATI graphics card. I'm afraid the current Karmic version won't work with the new kernel. You will need the Lucid version from: [http://packages.ubuntu.com/lucid/fglrx-kernel-source](http://packages.ubuntu.com/lucid/fglrx-kernel-source)

You need to remove your current "fglrx-kernel-source" package and install the Lucid one. If you need more help, please start a new threead or PM me (about fglrx).

Good Luck :).

---

### Post by rlelliott on 2010-03-09
> **rlelliott said:**
> I added the two entries above to rc.local and it worked! So those 2 commands automated the release and rebind of the nic and made the launchers i created obsolete.... good stuff. ty :)


after two days of using rc.local to auto unload wl and load b43, it has now started to cause DMA errors. I have moved back to manual unloading and loading. It seems that the wl driver needs to stay loaded for a set amount of time before it gets unloaded. The good thing about this Lenovo G550 is that it has a hardware switch in the front that physically cuts the power to the card, so i don't need to take the card out every time. Is there a way to add a wait statement to rc.local?

---

### Post by murasan on 2010-03-09
Hi, I'am spanish nood in Ubuntu... I have my machine working with Ubuntu 9.10 Netbook Remix..it has Broadcom 4315...I follow the "how to" step by step(i like this kernel .14) but finally don't work for my....my broadcom isn't..i make iwconfig and it'isnt....i lost it in the system follow this "how to"..

I also tryed this spanish "how to"..[http://foro.seguridadwireless.net/zona-linux/%28tuto%29chipset-broadcom-4312-%2814e44315%29-en-ubuntu/](http://foro.seguridadwireless.net/zona-linux/%28tuto%29chipset-broadcom-4312-%2814e44315%29-en-ubuntu/) and work well in the first time(i capture packets with airodump) but not work after the first reboot...signal off for always but the there is Broadcom making iwconfig ..

sorry for my bad english...

---

### Post by rlelliott on 2010-03-09
The key to getting your card to work is have the latest kernel for Ubuntu Lucid Lynx (2.6.32-16.25) is the latest i believe. Installing the bcmwl package and letting it auto load. Cutting the firmware with the git repo fwcutter and specified driver. Installing the specified compat-wireless package. And finally unloading the wl driver and loading the b43 driver manually after boot. If all the steps are followed correctly you will have a working wireless card capable of connecting from much farther distances than possible any other way along with other features that may also be helpful ;)

---

### Post by chenxiaolong on 2010-03-10
rlelliott: Sorry for the slow response. My high school blocks UbuntuForums and I didn't feel like using a proxy :D. The command to wait is "sleep." It accepts parameters in seconds. I.e. Wait for 3 seconds = "sleep 3." Hope this helps.

murasan: Like rlelliott said, you have to be running the latest Alpha build of Ubuntu 10.04 Lucid Lynx. If you just want to use the internet in 9.10 without Aircrack-ng, then you can use the Broadcom STA driver --> package "bcmwl-kernel-source."

---

### Post by leorolla on 2010-03-11
> **murasan said:**
> Hi, I'am spanish nood in Ubuntu... I have my machine working with Ubuntu 9.10 Netbook Remix..it has Broadcom 4315...I follow the "how to" step by step(i like this kernel .14) but finally don't work for my....my broadcom isn't..i make iwconfig and it'isnt....i lost it in the system follow this "how to"..

I also tryed this spanish "how to"..[http://foro.seguridadwireless.net/zona-linux/%28tuto%29chipset-broadcom-4312-%2814e44315%29-en-ubuntu/](http://foro.seguridadwireless.net/zona-linux/%28tuto%29chipset-broadcom-4312-%2814e44315%29-en-ubuntu/) and work well in the first time(i capture packets with airodump) but not work after the first reboot...signal off for always but the there is Broadcom making iwconfig ..

sorry for my bad english...

If you just want wireless try these
[http://ubuntuforums.org/showthread.php?t=1312603](http://ubuntuforums.org/showthread.php?t=1312603)
[http://ubuntuforums.org/showthread.php?t=1410259](http://ubuntuforums.org/showthread.php?t=1410259)

---

### Post by ish01 on 2010-03-11
hi guys, some months ago I read the issue related to DMA would be fixed in the 2.6.34 kernel... is that correct? does somebody has tried it already?

---

### Post by rlelliott on 2010-03-11
Adding the lines below to rc.local is working great as an automatic unload and loader. I will keep testing this to see if DMA errors result in the coming days.

sleep 2
rmmod wl
sleep 4
modprobe b43

exit 0

Thank you Chenxiaolong, your help has been instrumental in the success of the many people that have visited this thread.

---

### Post by chenxiaolong on 2010-03-11
ish01: That is correct. The 2.6.34 kernel will fix the DMA issues.

Kernel 2.6.34 RC1 is out already: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc1/) if you want to test it.

rlelliott: You're welcome :D. I'm glad it's working out so far :D. By the way, this is the longest thread in any forum I've seen where each post is meaningful.

---

### Post by murasan on 2010-03-11
Special thanks for yours answers...I try to tell(in my bad english) how is my situation now for if it can help to others...STA work very,very well but not is free and it don't like me, perhaps i don't use my broadcom in mode monitor never but i like can make it if i want..
I install b43 from synaptic and put new kernel from here(it work well and like me) after follow the spanish "how to" for install the driver..all ok and i can put my broadcom in mode managed,monitor and ad-hoc with
sudo ifconfig wlan0 down 
sudo iwconfig wlan0 mode monitor,managed or ad-hoc
sudo ifconfig wlan0 up
Only some times after reboot don't find signals..for this i removed Networkmanager and put 
wicd and rutilt,this two works better than networkmanager but not well of all.

The great problem came, i think, for use airmon for know if broadcom realy was in mode monitor...with sudo airmon-ng wlan0 it make other mon0 and think it no is good for me after reebot...with:
sudo ifconfig wlan0 down 
sudo iwconfig wlan0 mode monitor,managed or ad-hoc
sudo ifconfig wlan0 up
I work ok and not need mon0....I remove aimon and try with Kismet, it work fine...

This sound well:
"The key to getting your card to work is have the latest kernel for Ubuntu Lucid Lynx (2.6.32-16.25) is the latest i believe. Installing the bcmwl package and letting it auto load. Cutting the firmware with the git repo fwcutter and specified driver. Installing the specified compat-wireless package. And finally unloading the wl driver and loading the b43 driver manually after boot. If all the steps are followed correctly you will have a working wireless card capable of connecting from much farther distances than possible any other way along with other features that may also be helpful :wink:"

Read this for over with my bad english sound well..i wil translate it and will try but i am very very nood...thanks thanks

---

### Post by gstanden on 2010-03-18
Sweeeet!  Worked perfectly for me - Dell Latitude e6400 with card:

(output from lspci):

0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

running Ubuntu 9.10 Karmic Koala, kernel:

(output from uname -a)

Linux africa.cv.com 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

nice - thank you Bigadada_saba - thanks!!!

fyi - i used this from much earlier in this thread from poster Bigadada_saba:

1) i did a fresh install from the live cd
2) after the installation in made sure and turn on the wireless even-though is not detected.
3) then load the the live cd as a source in synaptic
4) then search for broadcom
5) install the drivers
6) got to system/administration/hardware drivers
7) install the STA driver
restart your computer then it should be working perfectly 

...and it did work perfectly....on my system as spec'd above

---

### Post by chenxiaolong on 2010-03-18
gstanden: Are you sure you posted in the right thread :D?

---

### Post by rlelliott on 2010-03-18
> **gstanden said:**
> Sweeeet!  Worked perfectly for me - Dell Latitude e6400 with card:

(output from lspci):

0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

running Ubuntu 9.10 Karmic Koala, kernel:

(output from uname -a)

Linux africa.cv.com 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

nice - thank you Bigadada_saba - thanks!!!

fyi - i used this from much earlier in this thread from poster Bigadada_saba:

1) i did a fresh install from the live cd
2) after the installation in made sure and turn on the wireless even-though is not detected.
3) then load the the live cd as a source in synaptic
4) then search for broadcom
5) install the drivers
6) got to system/administration/hardware drivers
7) install the STA driver
restart your computer then it should be working perfectly 

...and it did work perfectly....on my system as spec'd above


Just to clarify; Are you using the wl driver from the STA package or the open source b43 driver?

---

### Post by gstanden on 2010-03-18
chenxiaolong, yea I know what you mean, but - yea - it's a looooong thread, ...  check out post #204 in this thread, i.e.

 December 6th, 2009   	   #204

it's back on page 21 of this thread...user with handle of "Bigadada_saba" posted the solution I referenced.

---

### Post by gstanden on 2010-03-18
rlelliott - loaded up my ubuntu 9.10 install disk, then chose the following 2 packages in synaptic from the install cd as source:

Description column:  Broadcom 802.11 Linux STA wireless driver source
package name:  bcmwl-kernel-source

and also this package:

Description:  Modaliases for the Broadcom 802.11 Linux STA driver
package name:  bcmwl-modaliases

(note 2nd package was a dependency of the STA driver)

hit "apply" in synaptic, then rebooted..and voila, wireless was working perfectly - it's been up for hours now no hiccups, and working fully with WPA2-AES - when i connected it prompted with a dialog box for the passphrase, then connected perfectly.  thank god I didn't have to go through working with wpa config file again...

---

### Post by chenxiaolong on 2010-03-19
Ahh...I see. That was a while back :).

---

### Post by chenxiaolong on 2010-03-25
After testing distro to distro, I can finally conclude that b43 WILL WORK PERFECTLY in DMA mode with any Linux system running kernel 2.6.33. Is that great or what?

---

### Post by piratesmack on 2010-03-26
> **chenxiaolong said:**
> [COLOR="Green"]2010-03-25: After testing distro to distro, I can finally conclude that b43 WILL WORK PERFECTLY in DMA mode with any Linux system running kernel 2.6.33. Is that great or what?[/COLOR]


That is great, but is that with compat-wireless? Because I'm running Slackware-Current with 2.6.33 (vanilla kernel) and still get DMA errors with the b43 driver.

b43 only works if I load and unload wl first like in that lucid howto.

---

### Post by chenxiaolong on 2010-03-26
Sorry, I wasn't very clear in my previous post. I got it working without compat-wireless and for some distros, it would work without loading and unloading wl, while in others, I had to.

---

### Post by piratesmack on 2010-03-26
> **chenxiaolong said:**
> Sorry, I wasn't very clear in my previous post. I got it working without compat-wireless and for some distros, it would work without loading and unloading wl, while in others, I had to.

Thanks for clarifying.

Can you name a distro  that didn't need wl loaded first?
I want to check out their kernel patches.

EDIT:
btw, looks like the kernel 2.6.32-14-generic deb links are dead :(

---

### Post by chenxiaolong on 2010-03-26
Works without loading wl
--------------------------

Fedora -- Self-compiled kernel with exactly the same configuration as the default kernel
Debian -- Using the Ubuntu 2.6.33 kernel from the Ubuntu Kernel PPA
Sabayon -- Using default kernel from version 5.1 upgraded to 5.2 branch

Not working without loading wl
--------------------------------

Mandriva -- Don't remember what kernel I used (sorry)
OpenSuSE -- Self-compiled kernel with exactly the same configuration as the default kernel
Arch Linux -- Self-compiled kernel with exactly the same configuration as the default kernel

Good luck on your quest for the working kernel config :D!

---

### Post by piratesmack on 2010-03-26
Thanks man :)

---

### Post by chenxiaolong on 2010-03-26
You're welcome :D! Could you also check Ubuntu's kernel configuration? Ubuntu 9.10 is the only distro that I couldn't get working, even with kernel 2.6.33.

---

### Post by piratesmack on 2010-03-26
I still haven't checked out any of those distros, but I decided to give 2.6.33.1 a compile.

B43 still isn't working, but at least I can boot into my native resolution with Intel KMS :cool:

---

### Post by chenxiaolong on 2010-03-26
Could you tell me what error message "dmesg | grep b43" gives you? And also, are you using compat-wireless? Compat-wireless w/kernel 2.6.33 gives me a kernel panic.

---

### Post by piratesmack on 2010-03-26
> **chenxiaolong said:**
> Could you tell me what error message "dmesg | grep b43" gives you? And also, are you using compat-wireless? Compat-wireless w/kernel 2.6.33 gives me a kernel panic.

Sorry, I'm recompiling 2.6.33.1 right now; it might take a while with this Intel Atom.
This time I've enabled bcm43xx debugging and bcm43xx force pio to see if it works in PIO mode.

No, I wasn't using compat-wireless. I was also getting a kernel panic when I tried it with 2.6.33.

---

### Post by chenxiaolong on 2010-03-26
That might take a while :D. I'm compiling two kernels at the same time (wasn't a good idea): 2.6.33.1 from kernel.org and the latest Lucid kernel from git.

Darn, you got the kernel panic too? I hoped it was only my computer :D.

---

### Post by piratesmack on 2010-03-27
No errors in PIO mode, but it won't connect to my router. :(

---

### Post by chenxiaolong on 2010-03-27
PIO mode has never worked for me --> only DMA mode. What's funny is that, in Debian (Sid/Unstable), I could use the Ubuntu 2.6.33 kernel from the kernel PPA and it work just fine in DMA mode with DMA fatal errors. Now, in Ubuntu, when I use the exact same kernel, it doesn't work. This really bums me --> Ubuntu is based on Debian Sid/Unstable.

---

### Post by leorolla on 2010-03-27
I'm using Lucid Beta 1 for (general) testing.

All I need to do on the Live Session is install firmware and load b43 (no reboot required)... wireless is working very well.

How can check if it is running PIO/DMA?

By the way, what is the practical difference between these?

---

### Post by chenxiaolong on 2010-03-27
leorolla: I'm not sure how to determine whether your version of b43 is using PIO or DMA mode, but if you run "modinfo b43 | grep pio" and it gives an output, then PIO mode is supported, although probably not on (argh, run-on sentence). Here's the pros and cons of PIO:

Pros
-----
No DMA errors

Cons
-----
Not working in Ubuntu
Slower than DMA mode

Also, could you tell me what kernel version you're running so I can see if I can get it to work in Ubuntu 9.10 (uname -a)?

---

### Post by leorolla on 2010-03-27
kernel:             2.6.32-16-generic

I searched a little about pio/dma... and it seems that having a dma error depends on more than just the kernel/driver/device.

So a computer with 14e3:4315 may give this error and another one with the same distro/version may not.

You can make a live USB out of Lucid Beta 1 and try as well, it's quick.

---

### Post by chenxiaolong on 2010-03-27
I sort of expected that. I'm thinking it's either a conflict between a package and b43 or a conflict of a new kernel using old packages. The distros that b43 worked with were the distros that had both new versions packages and a new kernel.

---

### Post by chenxiaolong on 2010-03-27
Kernel 2.6.32-17 from Lucid repo works great with b43 on Ubuntu 9.10.

EDIT: Nevermind --> gives DMA Fatal Errors + Kernel Panic

---

### Post by piratesmack on 2010-03-28
I'm downloading the Lucid beta right now

chenxiaolong, what kind of processor do you have?
I read that only people with Atom and Core Duo CPU's are having this problem.

EDIT:
Also getting DMA errors in Lucid

---

### Post by chenxiaolong on 2010-03-28
I have a Core 2 Duo T6500 2.1GHZ.

---

### Post by leorolla on 2010-03-28
Mine is working so perfectly that maybe I am wrong.

How do I get to know if I'm having DMA errors?

I can't see any error here.

You guys should file a bug.

---

### Post by chenxiaolong on 2010-03-28
You can run "dmesg | tail" to see if you get the Fatal DMA errors. I doubt you're getting them though because the computer freezes for about a second when that happens.

---

### Post by chenxiaolong on 2010-03-28
Bug reported: [https://bugzilla.kernel.org/show_bug.cgi?id=15642](https://bugzilla.kernel.org/show_bug.cgi?id=15642)

---

### Post by leorolla on 2010-03-28
So, DMA is Direc Memory Access and there are too many thing that can be conflicting to it, like too many devices running on DMA etc... so even though we all share exacly the same device 14e4:4315, use same kernel with the same configurations and firmware, etc, still it may work for some of us and not for others.

To reproduce what I did is extremely simple:

Download Lucid Beta 1 32bit Desktop ISO. Use USB creator and burn it with persistent memory.

Start the Live session and follow the instructions of [https://wiki.ubuntu.com/Testing/Laptop/Reports/AcerAspireOneD150](https://wiki.ubuntu.com/Testing/Laptop/Reports/AcerAspireOneD150) to install the firmware and load b43.

That's it. Wireless works. If you have persistent memory it will work seemlessly next time you boot.

Some information:
```
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:55100000-55103fff
  *-network
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:5a:57:47:ed
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 multicast=yes
       resources: irq:28 memory:53000000-5303ffff ioport:1000(size=128)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:24:2b:a2:1a:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.52 multicast=yes wireless=IEEE 802.11bg
ubuntu@ubuntu:~$ modinfo b43
filename:       /lib/modules/2.6.32-16-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
firmware:       b43/pcm5.fw
firmware:       b43/n0initvals11.fw
firmware:       b43/n0bsinitvals11.fw
firmware:       b43/n0absinitvals11.fw
firmware:       b43/lp0initvals15.fw
firmware:       b43/lp0initvals14.fw
firmware:       b43/lp0initvals13.fw
firmware:       b43/lp0bsinitvals15.fw
firmware:       b43/lp0bsinitvals14.fw
firmware:       b43/lp0bsinitvals13.fw
firmware:       b43/b0g0initvals9.fw
firmware:       b43/b0g0initvals5.fw
firmware:       b43/b0g0initvals13.fw
firmware:       b43/b0g0bsinitvals9.fw
firmware:       b43/b0g0bsinitvals5.fw
firmware:       b43/b0g0bsinitvals13.fw
firmware:       b43/a0g1initvals9.fw
firmware:       b43/a0g1initvals5.fw
firmware:       b43/a0g1initvals13.fw
firmware:       b43/a0g1bsinitvals9.fw
firmware:       b43/a0g1bsinitvals5.fw
firmware:       b43/a0g1bsinitvals13.fw
firmware:       b43/a0g0initvals9.fw
firmware:       b43/a0g0initvals5.fw
firmware:       b43/a0g0bsinitvals9.fw
firmware:       b43/a0g0bsinitvals5.fw
license:        GPL
author:         G??bor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     F74D61070FAF674C1A39F95
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,led-class,cfg80211
vermagic:       2.6.32-16-generic SMP mod_unload modversions 586 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
ubuntu@ubuntu:~$ 

```

---

### Post by piratesmack on 2010-03-28
EDIT: nevermind

EDIT2: Got nothing better to do, so I'm compiling 2.6.34-rc2

---

### Post by piratesmack on 2010-03-30
Just noticed this on the compat-wireless git changelog
> 29 hours ago 	Paul Fertser	compat-wireless: driver-select: add b43 to the list

We'll soon be able to run 'scripts/driver_select b43' and not have to build all the other drivers.

---

### Post by rlelliott on 2010-03-31
That sure would be great... Im tired of seeing driver-select return "Unsupported"

---

### Post by leorolla on 2010-04-01
What's the difference between compat-wireless and the b43 module that comes with the kernel?

Chen, did you try the 32bit version? It could help isolating the source of trouble.

---

### Post by rlelliott on 2010-04-01
Using the auto-load "wl" unload "wl" then load "b43" method with compat-wireless drivers installed, Backtrack4 is fully operational. Im sure there is an easier way, but what i have done is added the restricted intrepid repo, then edited the sources file and changed "intrepid" to "lucid". I then downloaded the meta package "linux" along with "bcmwl-kernel-source" package. As usual i created load and unload shortcuts on the desktop, updated each package section manually (bt4 doesn't like to overwrite some packages for some odd reason) and now have fully working and updated backtrack4. I probably won't write a tut on this one, as the guys over at backtrack frown upon about 98% of what it takes to get this card working in their distro. If anyone needs further information, please feel free to email me @ [email]rlelliott@gmail.com[/email]

---

### Post by tcrowter on 2010-04-03
I followed the guide by leorolla a few posts up, and wireless started working. 

Later, it stopped.

I ran dmesg, and got something about a DMA error (I would have copied it here, but my ubuntu wifi isn't working, so I'm in Win7)

Even when I booted into Win7 to try wifi after that, it wouldn't work. 

I shut down the computer, took out the battery, and held the power button for 30secs, and when I started up it worked again. 

This has happened twice now. Am I doing it wrong? Do I need to set the mode to PIO or something?

And is the info in the first post accurate? It doesn't seem up-to-date.

Sorry for these stupid questions...

---

### Post by rlelliott on 2010-04-03
As Chenxiaolong has proven, there are a few different ways to get the b43 driver working. What you do to get yours working might be different than what someone else does. For instance, I must install bcmwl-kernel-source and allow the wl drivers to load at boot then rmmod the wl drive and modprobe the b43 driver in order not to have DMA errors. This Thread is so massive, that you can see a driver/kernel combo working one month and not the next.

---

### Post by mikeioannina on 2010-04-03
My wireless just stopped working before a week. I can't get it to work. I think I'll install lucid and do what rlelliott says to see if it works for me that way.

---

### Post by MyChaOS on 2010-04-04
I'm also trying to gett my Dell mini 9 to work with the b43, but like anyone else I get these errors.

I'm running lucid beta
cant get it working by the solution on first page.
No Function in Standard lucid Kernel using compat-wireless-2010-03-28, neither DMA or PIO mode.
Under Kernel 2.26.33 from mainline PPA no wireless in DMA Mode nor in PIO. 
With PIO mode i first get these ssb errors, but unloading and reloading b43 via modprobe results in a bad paging request

```

[  513.537653] b43-pci-bridge 0000:03:00.0: PCI INT A disabled
[  521.552214] cfg80211: Calling CRDA to update world regulatory domain
[  521.588206] cfg80211: World regulatory domain updated:
[  521.588218]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  521.588229]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  521.588239]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  521.588249]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  521.588258]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  521.588268]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  521.686138] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  521.686174] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[  521.704984] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[  521.705211] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[  521.705241] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[  521.705271] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[  521.752475] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[  521.791546] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  521.889580] phy0: Selected rate control algorithm 'minstrel'
[  521.891351] Registered led device: b43-phy0::tx
[  521.891418] Registered led device: b43-phy0::rx
[  521.891487] Registered led device: b43-phy0::radio
[  521.891689] Broadcom 43xx driver loaded [ Features: PMNLS, Firmware-ID: FW13 ]
[  521.923176] BUG: unable to handle kernel paging request at 31323038
[  521.923195] IP: [<31323038>] 0x31323038
[  521.923221] *pde = 00000000 
[  521.923231] Oops: 0000 [#1] SMP 
[  521.923240] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0/ifindex
[  521.923251] Modules linked in: arc4 b43 ssb pcmcia pcmcia_core mac80211 cfg80211 nls_iso8859_1 nls_cp437 vfat fat binfmt_misc ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss fbcon tileblit font snd_mixer_oss bitblit softcursor joydev snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq bridge stp snd_timer mmc_block bnep snd_seq_device i915 uvcvideo snd drm_kms_helper dell_laptop videodev jmb38x_ms sdhci_pci intel_agp drm sdhci soundcore dcdbas psmouse v4l1_compat btusb serio_raw i2c_algo_bit led_class memstick agpgart snd_page_alloc video output lp parport r8169 mii [last unloaded: cfg80211]
[  521.923408] 
[  521.923420] Pid: 3127, comm: NetworkManager Not tainted 2.6.33-020633-generic #020633 CN0J14/Inspiron 910
[  521.923432] EIP: 0060:[<31323038>] EFLAGS: 00010282 CPU: 1
[  521.923452] EIP is at 0x31323038
[  521.923461] EAX: f26a6800 EBX: ffffffa1 ECX: ef601f20 EDX: ef601eec
[  521.923470] ESI: 00008b01 EDI: c05fc90c EBP: ef601e94 ESP: ef601e70
[  521.923480]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[  521.923491] Process NetworkManager (pid: 3127, ti=ef600000 task=f68058d0 task.ti=ef600000)
[  521.923499] Stack:
[  521.923504]  c0579da1 00000000 ef601f10 ef601e94 f26a6800 ef601f20 f26a6800 00008b01
[  521.923527] <0> ef601f10 ef601eb4 c0579560 ef601eec 31323038 00000000 00000000 00008b01
[  521.923551] <0> ef601f10 ef601ed8 c05795e2 ef601eec c0579d50 c057a6d0 c090b4c0 00008b01
[  521.923577] Call Trace:
[  521.923596]  [<c0579da1>] ? ioctl_standard_call+0x51/0xd0
[  521.923610]  [<c0579560>] ? wireless_process_ioctl+0xd0/0x100
[  521.923622]  [<c05795e2>] ? wext_ioctl_dispatch+0x52/0x70
[  521.923635]  [<c0579d50>] ? ioctl_standard_call+0x0/0xd0
[  521.923647]  [<c057a6d0>] ? ioctl_private_call+0x0/0x80
[  521.923659]  [<c057963a>] ? wext_handle_ioctl+0x3a/0x70
[  521.923671]  [<c0579d50>] ? ioctl_standard_call+0x0/0xd0
[  521.923683]  [<c057a6d0>] ? ioctl_private_call+0x0/0x80
[  521.923698]  [<c04beb54>] ? dev_ioctl+0x244/0x250
[  521.923713]  [<c04ab2ed>] ? sock_ioctl+0x9d/0x220
[  521.923726]  [<c04ab250>] ? sock_ioctl+0x0/0x220
[  521.923740]  [<c020bfc8>] ? vfs_ioctl+0x28/0xa0
[  521.923752]  [<c04ad782>] ? sys_socketcall+0x92/0x2c0
[  521.923765]  [<c020c744>] ? do_vfs_ioctl+0x64/0x1c0
[  521.923779]  [<c02e1ac0>] ? security_file_ioctl+0x10/0x20
[  521.923792]  [<c020c8f3>] ? sys_ioctl+0x53/0x70
[  521.923806]  [<c0102d23>] ? sysenter_do_call+0x12/0x28
[  521.923815] Code:  Bad EIP value.
[  521.923824] EIP: [<31323038>] 0x31323038 SS:ESP 0068:ef601e70
[  521.923850] CR2: 0000000031323038
[  521.923890] ---[ end trace eded2e36b04177cb ]---

```

---

### Post by MyChaOS on 2010-04-04
Testing Kernel 2.6.34 rc1 from mainline PPA works in Lucid Beta 1 (i686) with wireless in DMA mode. Nevertheless dmesg states an DMA Error, followed by a controller reset, but then it works!

---

### Post by leorolla on 2010-04-04
Each hardware is different, and these erros have to do deep with low-level kernel-hardware issues.

If you have time to contribute, you can go to the bug that Chen filed directly to the kernel developpers, that is linked a couple of pages before the present post.

---

### Post by pcstalljr on 2010-04-05
Hey guys, i have a weird problem, well its only weird because i had it working 4 days ago before a system re-install.

ok so heres the deal, I got the urge to try ubuntu (again) about a week ago and upgraded to Linux kernel 2.6.33 so i can use the new b43 driver for th 14e4:4315 version of my Broadcom bcm4312 rev 01 wifi card (im on a dell studio 1555). and everything went fine! About 3 days later I decided to wipe it so i could put it on my larger partition of my drive, and i did the same install, but when i try to install the generic linux headers for Linux kernel 2.6.33 i get this error.

```
 *  bcmwl (5.10.91.9+bdcom)...
bcmwl (5.10.91.9+bdcom): Installing module.
.......(bad exit status: 10)

```

the compiler error is: (from /var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/make.log)

```
DKMS make.log for bcmwl-5.10.91.9+bdcom for kernel 2.6.33-020633-generic (i686)
Sun Apr  4 23:06:43 MDT 2010
make: Entering directory `/usr/src/linux-headers-2.6.33-020633-generic'
  LD      /var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_free’:
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.c:702: error: implicit declaration of function ‘schedule’
make[1]: *** [/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.33-020633-generic'
```

the thing that confuses me, is that i installed this same package 3 days before and it was working find. any ideas anyone?

---

### Post by chenxiaolong on 2010-04-05
Hey, I have the same laptop too! Anyway, all you have to do is to remove the Broadcom STA driver. Package: bcmwl-kernel-source

---

### Post by pcstalljr on 2010-04-05
> **chenxiaolong said:**
> Hey, I have the same laptop too! Anyway, all you have to do is to remove the Broadcom STA driver. Package: bcmwl-kernel-source

haha i love this laptop. perfict for everything i can do. lol. so it should compile currectly if i remove the sta drive?

---

### Post by chenxiaolong on 2010-04-05
Yes. The STA driver does not work on kernel 2.6.33, so just remove it and everything should be fine.

---

### Post by revelationman on 2010-04-05
I did get b43 driver working now the strangest thing is occurring,every now and then I loose complete network connection. 
The wireless looks connected but no internet no network connection I have to reboot always. This is very strange because the other laptop has ubuntu and no issues but it does not use b43 driver.
The other machine is Windows and that is hard wired into the cable router. 
 
Here is the wireless card information, I hope someone can figure this out it is driving me nuts

   description: Wireless interface 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:16:44:7f:cf:92 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.0.15 latency=0 multicast=yes wireless=IEEE 802.11 
       resources: irq:17 memory:fe8fc000-fe8fffff 
  *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1d:09:c8:50:5e 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes 
       resources: irq:17 memory:fe5fe000-fe5fffff 
:guitar:

---

### Post by chenxiaolong on 2010-04-05
Actually, you are currently using the Broadcom STA driver (wl), not b43.

> configuration: broadcast=yes **driver=wl0** driverversion=5.10.91.9 ip=192.168.0.15 latency=0 multicast=yes wireless=IEEE 802.11 

I really don't know what to do to help. I never use the Broadcom STA driver.

---

### Post by pcstalljr on 2010-04-05
[s]Hmm. it sucessfully installed the kernel. but when i run ifconfig wlan0 up. i get this error:[/s]
```
ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
```

Fixed it, the problem was a faulty driver install. for those that get the same error:
```

sudo apt-get remove b43-fwcutter
sudo apt-get install b43-fwcutter
``` when promped if you want to fetch and install drivers select yes.

---

### Post by chenxiaolong on 2010-04-05
Could you post the output of "dmesg | tail" so I can see the error?

---

### Post by El_Chamo_Ve on 2010-04-05
Hi there, i'm follow this post for a few days,

I got the 4312 rev01 (14e4:4315), i have installed 2.6.33 from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/"), all great, except a few things with ati driver but fixed already..

But i'm not able to make b43 work, the diferents compat-wirlees 2xxx-xx-xx due a compiling or unknown symbols or anything else. So i decided to make it clean from begining, i clean up my system from every wl or b43(from compat-wireless) and now i'm triying with the new releases of compat-wireless, i mean [compat-wirless-20010-04-05]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2"). Ok, when i'm in make step it gave me this error: 
```
/home/rafa/Descargas/compat-wireless-2010-04-05/drivers/net/wireless/ath/ath9k/xmit.c: In function &#8216;ath_tx_complete_buf&#8217;:
/home/rafa/Descargas/compat-wireless-2010-04-05/drivers/net/wireless/ath/ath9k/xmit.c:1880: error: too many arguments to function &#8216;ath_debug_stat_tx&#8217;
```
 I think the clue start's here:
```

/home/rafa/Descargas/compat-wireless-2010-04-05/drivers/net/wireless/ath/ath9k/recv.c: In function &#8216;ath_rx_tasklet&#8217;:
/home/rafa/Descargas/compat-wireless-2010-04-05/drivers/net/wireless/ath/ath9k/recv.c:572: warning: passing argument 2 of &#8216;ath_debug_stat_rx&#8217; from incompatible pointer type
/home/rafa/Descargas/compat-wireless-2010-04-05/drivers/net/wireless/ath/ath9k/debug.h:211: note: expected &#8216;struct ath_buf *&#8217; but argument is of type &#8216;struct ath_rx_status *&#8217;
  CC [M]  /home/rafa/Descargas/compat-wireless-2010-04-05/drivers/net/wireless/ath/ath9k/xmit.o
/home/rafa/Descargas/compat-wireless-2010-04-05/drivers/net/wireless/ath/ath9k/xmit.c: In function &#8216;ath_tx_complete_buf&#8217;:
/home/rafa/Descargas/compat-wireless-2010-04-05/drivers/net/wireless/ath/ath9k/xmit.c:1880: error: too many arguments to function &#8216;ath_debug_stat_tx&#8217;

```

Same history with compat-wirless-20010-04-04.

So what i'm doing wrong?

Thx

(sorry for my bad english)

edit1: I forget it, i'm using karmic 9.10

edit2: With release 2010-03-23 it gave me the same error of MyChaos in [Page 57]("http://ubuntuforums.org/showthread.php?t=1266620&page=57") and then my pc die! :'(

---

### Post by pcstalljr on 2010-04-06
> **chenxiaolong said:**
> Could you post the output of "dmesg | tail" so I can see the error?

interesting, after a reboot my driver broke and the dmesg | tail is:
```
[  523.228072] b43-phy0 ERROR: MAC suspend failed
[  526.092316] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  531.624428] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  531.624439] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[  531.624444] b43-phy0 ERROR: CONFIG_B43_FORCE_PIO must be set in your kernel configuration.
[  531.624493] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  531.624500] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[  531.624505] b43-phy0 ERROR: CONFIG_B43_FORCE_PIO must be set in your kernel configuration.
[  531.645853] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  734.880072] CE: hpet increasing min_delta_ns to 22500 nsec

```

---

### Post by El_Chamo_Ve on 2010-04-06
I found solution for my issue:

I downloaded a release from [www.orbit-lab.org]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.33/") for the 2.6.33 kernel.. Guess what.. 'till now everything ok. Injects & connect (there was no neccesary the PIO mode options, it says unknowm parameter, but i verify it was using from de ../update/ folder.

I hope this can help anyone like you help me

PD: I follow the original post step's to install in karmic running on 2.6.33 kernel

---

### Post by chenxiaolong on 2010-04-06
pcstalljr: Hmmm...I've only seen that happen when compat-wireless is installed. Did you try using PIO mode by running:

```
echo "options b43 pio=1" | sudo tee /etc/modprobe.d/b43.conf
```

(undo by removing /etc/modprobe.d/b43.conf)

El_Chamo_Ve. First of all, welcome to Ubuntu Forums! I've never heard of Orbit Labs, but I'll try their release of compat-wireless when I have time.

---

### Post by piratesmack on 2010-04-06
> **chenxiaolong said:**
> Yes. The STA driver does not work on kernel 2.6.33, so just remove it and everything should be fine.

I'm using the STA driver with 2.6.33.2 (it's the only one that works for me right now.)

Just needs to be patched
```

--- src/include/linuxver.h.orig	2010-04-07 02:53:55.203642287 -0600
+++ src/include/linuxver.h	2010-04-07 02:54:29.922895653 -0600
@@ -20,7 +20,7 @@
 #if (LINUX_VERSION_CODE < KERNEL_VERSION(2, 6, 0))
 #include <linux/config.h>
 #else
-#include <linux/autoconf.h>
+#include <generated/autoconf.h>
 #endif
 #include <linux/module.h>

```

---

### Post by chenxiaolong on 2010-04-06
piratesmack: Thanks for the info. I was too lazy to look at the code. It's basically the same patch as the one needed for VirtualBox :D. 

Anyway, I'm back to Ubuntu now and on Ubuntu's 2.6.33 kernel, b43 works OOTB for me in DMA mode.

---

### Post by piratesmack on 2010-04-06
> **chenxiaolong said:**
> Anyway, I'm back to Ubuntu now and on Ubuntu's 2.6.33 kernel, b43 works OOTB for me in DMA mode.

Does the Lucid daily image come with 2.6.33?

---

### Post by chenxiaolong on 2010-04-06
I'm running Karmic. I'm not sure whether Lucid is using 2.6.33 now.

---

### Post by DarkAngel88 on 2010-04-07
> **piratesmack said:**
> Does the Lucid daily image come with 2.6.33?

Unfortunately no, Lucid has kernel 2.6.32-19 as of now... and I haven't been able to make it work with latest compat-wireless driver.  Even Lucid using kernel 2.6.33 does not work for me with compat-wireless.. so no injection under 10.04,for now.

---

### Post by drumin90 on 2010-04-07
I have tried switching to 2.6.33 and wlan0 does not show up in network devices. Any ideas?

---

### Post by chenxiaolong on 2010-04-07
```
sudo rmmod b43
sudo modprobe b43
```

?

Does "dmesg | grep b43" show any errors?

---

### Post by drumin90 on 2010-04-07
When running "sudo rmmod b43" I get "ERROR: Module b43 does not exist in /proc/modules"

and here is the output of dmesg:

```
[    8.895965] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17  (level, low) -> IRQ 17
[    8.895992] b43-pci-bridge 0000:03:00.0:  setting latency timer to 64
[    9.635131] b43: Unknown parameter  `pio'
[  347.843628] b43-pci-bridge 0000:03:00.0: PCI INT A disabled
[   350.267658] b43-pci-bridge 0000:03:00.0: restoring config space at  offset 0xf (was 0x100, writing 0x10b)
[  350.267729] b43-pci-bridge  0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing  0xf0100004)
[  350.267748] b43-pci-bridge 0000:03:00.0: restoring config space at  offset 0x3 (was 0x0, writing 0x10)
[  350.267773] b43-pci-bridge  0000:03:00.0: restoring config space at offset 0x1 (was 0x100000,  writing 0x100006)
[  350.723816] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17  (level, low) -> IRQ 17
[  392.585717] b43: Unknown parameter `pio'

```

---

### Post by piratesmack on 2010-04-07
> **drumin90 said:**
> When running "sudo rmmod b43" I get "ERROR: Module b43 does not exist in /proc/modules"

and here is the output of dmesg:

```
[    8.895965] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17  (level, low) -> IRQ 17
[    8.895992] b43-pci-bridge 0000:03:00.0:  setting latency timer to 64
[    9.635131] b43: Unknown parameter  `pio'
[  347.843628] b43-pci-bridge 0000:03:00.0: PCI INT A disabled
[   350.267658] b43-pci-bridge 0000:03:00.0: restoring config space at  offset 0xf (was 0x100, writing 0x10b)
[  350.267729] b43-pci-bridge  0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing  0xf0100004)
[  350.267748] b43-pci-bridge 0000:03:00.0: restoring config space at  offset 0x3 (was 0x0, writing 0x10)
[  350.267773] b43-pci-bridge  0000:03:00.0: restoring config space at offset 0x1 (was 0x100000,  writing 0x100006)
[  350.723816] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17  (level, low) -> IRQ 17
[  392.585717] b43: Unknown parameter `pio'

```

Try removing /etc/modprobe.d/b43-thingy.conf
That's for the compat-wireless b43 module, PIO is not a recognized option in 2.6.33's b43

---

### Post by drumin90 on 2010-04-07
I did that and now I can see wireless networks but cannot connect to them

---

### Post by drumin90 on 2010-04-07
Ok this is bizarre but I rebooted without changing anything and its working now.  I'm gonna do some more testing and post back

---

### Post by drumin90 on 2010-04-07
After attempting a wpa crack and a reboot, it no longer works on Ubuntu 9.10 (kernel 2.6.33)

---

### Post by chenxiaolong on 2010-04-08
I attempted to do a WPA crack and it still worked after reboot ("attempted" because no clients were online for the deauth hack). 

EDIT: Are you sure you're running the SVN (development) version of aircrack-ng?

EDIT_2: I'm downloading the new Ubuntu 10.04 Beta 2 to test b43 tomorrow (so no more Karmic testing for me). For now, I have a Social Studies project to do :(.

---

### Post by drumin90 on 2010-04-08
I don't know how much this will help but here we go:

Occasionally, the wireless card will work correctly in Ubuntu (not sure what causes this).

Both times it has worked correctly, I attempted a wireless crack (like you, I didn't have any APs available to crack so I only enabled monitor mode and ran airodump-ng)

After this, I reboot into windows and windows does not even detect the wireless card.

Then when I boot into Ubuntu, I cannot even see any APs, although I can see the wireless card in Network Tools.

I am currently attempting to get the card working in windows again.

---

### Post by chenxiaolong on 2010-04-08
Hmmm...Maybe aircrack also causes the same thing that the DMA error does (if that makes sense). Try the take-out-wlan-card-and-touch-pins trick. That always works for me when my wireless card isn't detected properly.

---

### Post by drumin90 on 2010-04-08
Sorry to keep changing my story but heres the update:

After attempting to follow another guide elsewhere, I ended up with an  unbootable kernel so I just finished a fresh install of Ubuntu 9.10  Netbook Remix, an update to the 2.6.33 kernel and am attempting to  install b43 through the Hardware Drivers wizard

[EDIT] - After installing the b43 driver from Harware Drivers, I still cannot detect any APs, however it does show up in Network Tools as wlan1

[EDIT 2] - If I reboot my netbook, it is able to connect to an AP but for only about 20 seconds before it says it has disconnected

---

### Post by chenxiaolong on 2010-04-09
I'm not sure if this has to do with the problem, but the b43 website ([http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)) specifically says that a certain firmware is required for the 14e4:4315 wireless card.

---

### Post by drumin90 on 2010-04-10
Still no luck as of now

---

### Post by chenxiaolong on 2010-04-10
I just installed Ubuntu 10.04 beta 2. I'll test b43 on the default kernel and the 2.6.33 kernel.

EDIT: b43 works awesome-ly on Lucid's default kernel (2.6.32-19-generic [based on 2.6.32.9]) with the lp firmware: [http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp](http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp).

---

### Post by drumin90 on 2010-04-10
do they have a netbook remix for lucid yet?

---

### Post by chenxiaolong on 2010-04-10
Not yet.

---

### Post by drumin90 on 2010-04-10
would the netbook remix for kubuntu 10.04 be different than ubuntu 10.04 as far as b43 goes?

---

### Post by chenxiaolong on 2010-04-10
I've always had trouble with KDE's version of network-manager, so if I use KDE, I just install network-manager-gnome and set "nm-applet" to start on login.

---

### Post by drumin90 on 2010-04-10
So more or less, I should just wait until Ubuntu 10.04 NR is released? lol

---

### Post by chenxiaolong on 2010-04-10
Yeah.

---

### Post by erpc on 2010-04-10
i have worked b43 module on 10.04 without DMA error. I use latest default kernel (2.6.32-19), install STA driver before install b43-fwcutter from synaptic. after load system use sudo rmmode wl && sudo modprobe b43
aircrack working
monitor mode working
i'm happy=)

---

### Post by chenxiaolong on 2010-04-11
Welcome to Ubuntu Forums...and...AWESOME!!!

Happy you got it working.

---

### Post by drumin90 on 2010-04-11
I think I found the 10.04 netbook release.  [http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-beta2-netbook-i386.iso](http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-beta2-netbook-i386.iso)

---

### Post by chenxiaolong on 2010-04-11
Nice. I assumed there wasn't one yet because it wasn't listed on Distrowatch.

---

### Post by drumin90 on 2010-04-11
Yeah it wasn't listed on Ubuntu's page either.  I browsed the folder containing all the releases and found it

---

### Post by drumin90 on 2010-04-11
> **erpc said:**
> i have worked b43 module on 10.04 without DMA error. I use latest default kernel (2.6.32-19), install STA driver before install b43-fwcutter from synaptic. after load system use sudo rmmode wl && sudo modprobe b43
aircrack working
monitor mode working
i'm happy=)

Unfortunately, this did not work for me.

Installing the b43 driver from Harware Drivers DID work however on 10.04

[EDIT] - Nevermind.  After a few reboots, it stopped working again

Ok I checked dmesg and I have hundreds of lines that say "b43-phy0 ERROR: Fatal DMA error: 0x00000000 0x00000000 0x00000000 0x00000000 0x00000000 0x00000000"

---

### Post by arcull on 2010-04-12
Hi there. I'm having the same issue.```
lspci -nn |grep Broadcom
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
``` Trying with B43 driver I get the same errors in dmesg. I currently have Lucid installed with kernel ```
uname -a
Linux Laptop 2.6.32-20-generic #29-Ubuntu SMP Fri Apr 9 20:35:00 UTC 2010 x86_64 GNU/Linux

``` I didn't have any luck yet. I tried to install linux-backports-modules-wireless-2.6.32.20-generic via synaptic which should provide compat-wireless linux modules, but still no luck. Did anyone of you made some progress?

---

### Post by leorolla on 2010-04-12
From the first post I suppose that a possible solution is to install the files from
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

---

### Post by arcull on 2010-04-12
> From the first post I suppose that a possible solution is to install the  files from
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/")

I tried the 2.6.33 kernel as suggested, but no luck in my case, my router gets detected and also connection shows as established, but can't browse the web with it. There are still errors ```
  232.904203] wlan0: associated
[  232.906314] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  236.178826] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  236.178838] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[  236.178843] b43-phy0 ERROR: CONFIG_B43_FORCE_PIO must be set in your kernel configuration.
[  239.541323] No probe response from AP 00:40:10:20:00:03 after 500ms, disconnecting.
```

---

### Post by JackyBoyII on 2010-04-12
I followed this tutorial on my Dell mini 10v running backtrack, and after some fiddling and help from my dad (who nows linux alot better than I do!) I eventually got to the end.

iwconfig needs detects the card, but when I enable it, or start networking anything to do with the wirless is very laggy and sometimes ifconfig just doesn't report back at all.
on boot I had all the b43 errors, so I did the modprobe -r b43, modprobe b43 but still very laggy. I checked dmesg and it had all those errors still and also said there was an error with the firmware and said a website to go back and download it again.

I didn't have my netbook with me to copy exactly what it says, but this is the gist of it. I do have it nearby if any other info is needed.

Thanks for your help

---

### Post by drumin90 on 2010-04-12
> **erpc said:**
> i have worked b43 module on 10.04 without DMA error. I use latest default kernel (2.6.32-19), install STA driver before install b43-fwcutter from synaptic. after load system use sudo rmmode wl && sudo modprobe b43
aircrack working
monitor mode working
i'm happy=)

> **arcull said:**
> I tried the 2.6.33 kernel as suggested, but no luck in my case, my router gets detected and also connection shows as established, but can't browse the web with it. There are still errors ```
  232.904203] wlan0: associated
[  232.906314] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  236.178826] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  236.178838] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[  236.178843] b43-phy0 ERROR: CONFIG_B43_FORCE_PIO must be set in your kernel configuration.
[  239.541323] No probe response from AP 00:40:10:20:00:03 after 500ms, disconnecting.
```

Same problem for me.  I can detect APs and can even connect to them, but I do not actually have internet access

---

### Post by chenxiaolong on 2010-04-12
Does the internet work if you manually specify the DNS server to, for example:

OpenDNS: 208.67.222.222, 208.67.220.220
Google: 8.8.8.8, 8.8.4.4

by Editing your wireless connection in the NetworkManager preferences?

OR you can also run:

```
echo "nameserver 208.67.222.222" | sudo tee -a /etc/resolv.conf
echo "nameserver 208.67.220.220" | sudo tee -a /etc/resolv.conf
```

```
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
```

for OpenDNS's DNS servers and Google's Public DNS servers, respectively.

---

### Post by arcull on 2010-04-13
chenxiaolong, I'll give it a try, but I don't think it is gonna work. I have the feeling this DMA mode is really a big problem, so I wonder how do I switch to PIO as suggested by dmesg. I saw your suggestion ```
echo "options b43 pio=1" | sudo tee /etc/modprobe.d/b43.conf
```, but afterwards I'm not able to modprobe b43 module, I don't remember the exact error it says, but it is something like "PIO not found". Does this command really force PIO in kernel configuration, or should I compile my own kernel with this switch?

---

### Post by drumin90 on 2010-04-13
[FONT=monospace]At this point I don't care if I  have monitor mode or injection.  I just want internet access but the STA  driver doesn't even work.  Any ideas?[/FONT]

---

### Post by JackyBoyII on 2010-04-13
Hey, I posted before, but I explained very badly what was going on.

So I have reinstalled BT4 to hopefully do it all more efficiently,  Before when I installed it, in dmesg it said that it was missing a couple of firmware files. So does that mean I will have to run the Reconfigure fwcutter command and download the firmware before I do the update kernal?

And then that was my next problem, First it says to download the 3 files, unfortunately the links on the front page are down, so do i have to find another source for all 3 files? or should I just get the latest files I can off the same site?

Then one last thing, after typing in the command to install the new kernel it says &quot;just boot into the new kernel with GRUB&quot;. Would someone be able to give me a little guide, or a place where to look on how to do this?

 I would greatly appreciate all help, thank you

---

### Post by drumin90 on 2010-04-13
I can help with the last part.  As your computer is booting, it should show a menu of the kernels you can boot into.  If it doesn't, after you boot, run ```
uname -r
``` and see if it booted into the latest kernel anyways

---

### Post by arcull on 2010-04-13
I have partially good news :) I know the thread is focused on b43 driver, but after a few days of trying I got sick of this and decided to give wl driver a try and managed to make it work. I know I wont have monitor mode with it, but it is still better than nothing. So what I did is. First installed all updates available for Lucid, so my kernel is now ```
Linux Laptop 2.6.32-20-generic #30-Ubuntu SMP Mon Apr 12 15:20:57 UTC 2010 x86_64 GNU/Li
```, next I did remove these packages via synaptic:
linux-backports-modules-wireless-lucid-generic
linux-backports-modules-wireless-2.6.32-20-generic
b43-fwcutter

Afterwards I installed:
bcmwl-kernel-source
broadcom-sta-common
broadcom-sta-source
bcmwl-modaliases
Then I rebooted laptop and my wifi is currently working. Hope this helps someone.

---

### Post by JackyBoyII on 2010-04-13
> **drumin90 said:**
> I can help with the last part.  As your computer is booting, it should show a menu of the kernels you can boot into.  If it doesn't, after you boot, run ```
uname -r
``` and see if it booted into the latest kernel anyways

no, the new kernel just isn't in the list at all when I reboot, just the normal ones

---

### Post by leorolla on 2010-04-13
> **drumin90 said:**
> [FONT=monospace]At this point I don't care if I  have monitor mode or injection.  I just want internet access but the STA  driver doesn't even work.  Any ideas?[/FONT]

You should try the bcmwl-kernel-source package:

Get wired connection
Update
Upgrade
Remove packages like linux-backports-modules*
Install bcmwl-kernel-source
sudo rmmod b43
sudo modprobe wl

If it fails, open a new topic with more information and askinf for help.

If all you care about is having internet, b43 is not the best choice to spend your attempts.

---

### Post by chenxiaolong on 2010-04-13
Wow! A lot of people replied while I was still at school :D.

**arcull (14 Hours Ago 01:26 AM):** The command does, in fact, force PIO mode, but only kernel 2.6.32 with compat-wireless or kernel 2.6.33 support it.

compat-wireless: [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)
Ubuntu Kernels: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

--------------------------------

**drumin90 (3 Hours Ago 11:59 AM):** Awwww...oh well. Here's what you have to do to get the b43 driver working:

```
sudo rmmod b43 ssb wl
sudo apt-get purge linux-backports-modules-[karmic/lucid] b43-fwcutter bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
```

Then, check the files in /etc/modprobe.d/ and make sure that they don't contain:

```
blacklist wl
```

and then reboot.

--------------------------------

**JackyBoyII (3 Hours Ago 12:12 PM):** The instructions for the firmware files are at: [http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp](http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp), but since BackTrack 4 is based on Ubuntu 8.10 Intrepid, it has kernel 2.6.30, which is not supported by the new b43, required to make this wireless card work :(.

(Dang, long run-on sentence.

--------------------------------

**JackyBoyII (1 Hour Ago 01:34 PM):** Try running:

```
sudo update-grub
```

--------------------------------

I hope I covered everyone's replies. If not, tell me :D.

---

### Post by rlelliott on 2010-04-14
backtrack 4 final with fully operational b43 open source drivers (monitor mode capability)?

install bt4 to hd

use supported usb wireless, or wired connection for inet access.

open synaptic and add all ubuntu repos and remove backtrack repos.

edit sources.lst and change "intrepid" to lucid.

apt-get update.

select 2.6.32-19-generic, generic headers and the bcmwl-kernel-source packages for download ONLY.

install aptoncd

create aptoncd from download only packages.

burn cd for later installs ( goto synaptic add cd repo... after initial bt4 install)

search for and remove regdb and crda as they will be superseded by the wireless-crda package depend by the new kernel 

install packages previously downloaded EXCEPT bcml-kernel-source.

Reboot into new kernel

install bcmwl-kernel-source.

reboot.

now that we have a working dkms wl module loaded.. we can rmmod the wl driver and modprobe b43 ( the firmware comes preloaded on bt4 ;)

Now..

We now have a working b43 enabled 14e4:4315 (Broadcom bcm4312 rev 01) wireless adapter in backtrack 4 AND a way to refresh the system without an internet connection if we so choose.

*********ALWAYS********** Allow the wl dkms driver to load at boot and then rmmod wl, modprobe b43. You will receive DMA errors is this rule is not followed with the above procedure.

********REMEMBER******** after following the above steps remove all ubuntu repos and ONLY add the backtrack repos back. you will break your install if you update using ANY other repos than backtrack... run apt-get update; apt-get upgrade after removing all repos but backtracks.....and dont go messing with upgrading to KDE4 from the installed KDE3.5... leave it alone and live with your new stable kde3.5 backtrack 4 linux install.

Have fun.... :)

regards,
killin1a4

---

### Post by chenxiaolong on 2010-04-14
Nice.

---

### Post by JackyBoyII on 2010-04-17
> **rlelliott said:**
> backtrack 4 final with fully operational b43 open source drivers (monitor mode capability)?


Yes! It works! using this guide I have now got backtrack 4 working with injection

So I will write up my experience to hopefully help other people that are in the same position. 
I have a dell mini 10v.

to install the kernel I used this guide: [http://www.jwgoerlich.us/blogengine/2009/12/default.aspx](http://www.jwgoerlich.us/blogengine/2009/12/default.aspx)
 But obvikously just follow it for the kernel bit.

then for the cmwl-kernel-sources bit, this didn't work so i down;loaded bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb  (if you google it, you should be able to get a download for it pretty easily. But when I did "dpgk -i bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb" IT came up with an error.  So i then had to use this guide [http://ubuntuforums.org/showthread.php?t=1355905](http://ubuntuforums.org/showthread.php?t=1355905) to get it to work properly to install.

I know have to modprobe -r wl and modprobe b43 at every start, but I will write a script to do it.

Kismet works, aireplay works, so I am guessing the rest will work too!

Thanks greatly for everyones help

---

### Post by chenxiaolong on 2010-04-17
Seems like Lucid is the magic here :D. To make the commands automatically run, add this to "/etc/rc.local"

```
modprobe -r wl
sleep 3               #Wait 3 Seconds
modprobe b43
```

---

### Post by DarkAngel88 on 2010-04-17
> **chenxiaolong said:**
> Seems like Lucid is the magic here :D. To make the commands automatically run, add this to "/etc/rc.local"

```
modprobe -r wl
sleep 3               #Wait 3 Seconds
modprobe b43
```

Funny tho, I've been using those commands in my rc.local file until recently (yesterday actually) has lucid was crashing just after the login screen when booting.  Removing the commands and booting normally did it and now, I'm using latest lucid with latest kernel and compat-wireless.  Injection works and I don't have issues at all, except the one where sometimes, it won't boot past the grub window (just restart the computer and eventually, it'll work)

---

### Post by dalga999 on 2010-04-17
Can you post a guide on the first page for working injection/monitor mode and no dma errors in ubuntu? I tried this on pio mode but no success. Also, which version of ubuntu and kernel should I use?
 
Thanks

---

### Post by chenxiaolong on 2010-04-17
DarkAngel88: The newest Lucid kernel screwed me in the same way :D.

dalga999: PIO mode has never worked. The b43 driver originally worked on the Ubuntu 10.04 Lucid Beta 2 kernel, but doesn't work after updates. 

Off topic: These waves of working and not working make me think of y=cos(x)+1/2. I guess I've been doing too much pre-calc homework.

---

### Post by rlelliott on 2010-04-20
Installed the latest daily kubuntu last night... i must say that it is running GREAT!! Now for the reason we are here....

Installed Kubuntu lucid lynx daily

Connected via wired eth0

Installed all updates

Installed bcmwl-kernel-source

removed network-manager, knetworkmanager and installed wicd (seems to work better)

changed interface to wlan0 for wicd

added "ifconfig eth1 up" to rc.local (just to be on the safe side, for b43 use later)

created a script to load b43 after boot

```

#!/bin/sh
sudo rmmod wl
sudo sleep 4
sudo modprobe b43
sudo sleep 4
sudo ifconfig wlan0 up

```

reboot

copy or cut firmware from broadcoms sta drivers

run  script

YAY!! working b43 open source drivers :)

Regards,
RL Elliott

---

### Post by chenxiaolong on 2010-04-20
rlelliott: Nice :D! Hopefully it will continue to work in the final Ubuntu 10.04 release.

---

### Post by tempoAccount on 2010-04-21
I have a Dell Mini 9 and after I updated kernel in Karmic, my fully working b43 stopped working. I then put in Lucid beta 2 instead. This didn't work either. Not with the 2.6.32-19 or the 2.6.32-21 which was installed in an update. I then tried 2.6.33 as suggested here but without any luck. 

2.6.34-rc5-lucid fixed all my problems.

I used the guide here to upgrade kernel:

[http://www.ramoonus.nl/2010/02/25/](http://www.ramoonus.nl/2010/02/25/)

But of course used the 2.6.34-rc5-lucid from:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/)

---

### Post by chenxiaolong on 2010-04-21
tempoAccount: Welcome to Ubuntu Forums :D! And cool! I didn't know the development version of kernel 2.6.34 is out already.

---

### Post by wolfgang61 on 2010-04-23
For me the final solution was:

1. install 2.6.34:
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/linux-headers-2.6.34-020634rc5-generic_2.6.34-020634rc5_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/linux-headers-2.6.34-020634rc5_2.6.34-020634rc5_all.deb
dpkg -i *.deb

```

2. create /etc/modprobe.d/b43.conf with this content:

```
options b43 pio=1 qos=0
```

this works reliably since a few hours.
I also tried options nohwcrypt=1 hwtkip=0 btcoex=0 but they
were not needed after all.

---

### Post by chenxiaolong on 2010-04-23
Cool! So PIO mode is working under kernel 2.6.34?

Sorry, I haven't had time to test b43 myself. I've had many school projects and also, the Ubuntu 10.04 beta 2 wouldn't boot. BUT FEAR NOT :D, Ubuntu 10.04 RC is up and running and ready for testing :D.

EDIT: Confirmed working :D!

---

### Post by piratesmack on 2010-04-24
Thanks, wolfgang; I'll try that with the latest compat-wireless and 2.6.33.2.

---

### Post by chenxiaolong on 2010-04-24
I'm not sure if the newest compat-wireless still compiles under kernel 2.6.32 :).

---

### Post by piratesmack on 2010-04-24
> **chenxiaolong said:**
> I'm not sure if the newest compat-wireless still compiles under kernel 2.6.32 :).

I'm using 2.6.33.2, and it compiled fine.
Also, b43 is finally working! :D

Just in case something breaks in the future, I used compat-wireless-2010-04-24.

The driver-select script now supports b43, so you don't have to build all the other drivers.

Just do
```

scripts/driver-select b43
make
sudo make install
sudo echo "options b43 pio=1 qos=0" > /etc/modprobe.d/b43.conf

```

---

### Post by chenxiaolong on 2010-04-24
Awesome :D! Is this on Lucid? It would be awesome to get it working with kernel 2.6.33.2 on Lucid as kernel 2.6.34 is a little too "crashy" right now :D.

---

### Post by piratesmack on 2010-04-24
> **chenxiaolong said:**
> Awesome :D! Is this on Lucid? It would be awesome to get it working with kernel 2.6.33.2 on Lucid as kernel 2.6.34 is a little too "crashy" right now :D.

Nah, I'm using Slackware-Current.
I haven't tried it on any other distros, but I'm sure it would work.

Here's the kernel config if you need it
[http://slackware.mirrors.tds.net/pub/slackware/slackware-current/source/k/config-generic-smp-2.6.33.2-smp](http://slackware.mirrors.tds.net/pub/slackware/slackware-current/source/k/config-generic-smp-2.6.33.2-smp)

Note: If you do use that kernel config, make sure support for your filesystem is built into the kernel ([*] not [M]). Otherwise, you'll need an initrd to boot your system. Slackware's generic kernel has all filesystems built as modules.

---

### Post by chenxiaolong on 2010-04-25
Thanks for the config! I'm running 64 bit Ubuntu, so I'll modify the config file as necessary.

---

### Post by chenxiaolong on 2010-04-25
Unfortunately, the b43 driver included with kernel 2.6.34-RC5 is very slow. The maximum speed I can transfer a file to another computer is 15.6 kpbs and it will disconnect after about 20 seconds, requiring a module reload to get it working again. Download speed is good. I'll test kernel 2.6.34-RC5 with compat-wireless and also kernel 2.6.33.2 with and without compat-wireless.

---

### Post by piratesmack on 2010-04-25
Yeah, I noticed it's a bit slower than wl.
It's fast enough for just surfing the web though.

It seems to work a lot better with wicd than wl did. And I was having problems connecting after rebooting my computer (I had to shutdown my computer and turn it back on to reconnect), but not with b43.

---

### Post by chenxiaolong on 2010-04-25
I've never tried b43 with Wicd, but I don't even want to think about the experience I had with wl and Wicd...ugh...:D. Anyway, with kernel 2.6.34-RC5, I have periodic disconnects when uploading. It never happens when I download. Hmm...

---

### Post by slobeech on 2010-04-26
hello all
completely new here - for now juat one question: i have somehow (played around with different distros and livecds and win7) managed to "brake" the wifi. 
i can still "find" and "see" - broadcom bcm4312 - but can't make it work. i formated whole disk. fresh ubuntu instalation 09.10 - nothing.
i have tried probably at least 5 livecds ubuntu, pclinuxos, crunchbang, elive, mandriva,... but it doesn't work anywhere.  ...
oh yes - the question: if i "see" the wifi card - is it still possible that it is broken (hardware failure")? .. or must i just "play" around with it some more (maybe one of distribution installed wrong firmware??)

thanks!

---

### Post by chenxiaolong on 2010-04-26
This isn't a software problem. Hopefully reinstalling Ubuntu didn't cause you to waste too much of your time :D. All you have to do is:

1) Physically take the wireless card out from your laptop.

2) Touch all the pins on the wireless card to drain the electricity from it, thereby resetting the card's RAM (tells the card what state it's in).

---

### Post by piratesmack on 2010-04-26
Turning my laptop off and taking the battery out for a couple seconds always works for me when that happens. I've never actually had to remove the wireless card.

---

### Post by chenxiaolong on 2010-04-26
That doesn't work for me :(. I guess it's different on every laptop.

---

### Post by slobeech on 2010-04-27
it seemed strange to be software yes...
thank you both!! will try as soon as i get home. (alhtough physicaly taking card out - would probably void warranty - will have to check)

thanks again!!

---

### Post by chenxiaolong on 2010-04-27
Mine is under my RAM/Hard drive cover, so it doesn't void my warranty (not that I would ever need it :D). I'm pretty sure all Dell laptops are like that.

---

### Post by KMcC on 2010-04-28
Chenxaiolong,

You've done a fantastic job with this forum! Can you summarize the steps those of us running Karmic with wl need to do to move to b43 when we get our lucid upgrade in the next few days?

My computer is HP mini 110; I have the version with Bluetooth, so I'm particularly interested in finally getting both kinds of wireless to work together!

---

### Post by piratesmack on 2010-04-28
Just compiled 2.6.33.3

b43 is working without compat-wireless, but still needs these options
```

options b43 pio=1 qos=0

```

---

### Post by chenxiaolong on 2010-04-28
KMcC: I'll put together a guide tomorrow after Lucid is out. I highly recommend that you do a fresh install of Lucid, instead of upgrading Karmic. The last time I upgraded Ubuntu (9.04 --> 9.10), a lot of my hardware stopped working (like sound and graphics).

piratesmack: Thanks for the info, but PIO mode under kernel 2.6.33.3 only connects to one of my routers. I don't know why :(. I'll test again tomorrow, when Lucid is out.

EDIT: Kernel 2.6.33.3 -- "pio=1 qos=0" (PIO on, QOS off) AND "pio=0 qos=1" (DMA mode, QOS off) both work fine.

EDIT2: Connects to both of my routers perfectly.

---

### Post by piratesmack on 2010-04-28
> **chenxiaolong said:**
> 
"pio=0 qos=1" (DMA mode, QOS off) both work fine.


Hmm, that's working for me, but only because it falls back to PIO mode when DMA fails :(

---

### Post by chenxiaolong on 2010-04-28
Oh...I guess I didn't notice that. I just checked dmesg : 

> [ 5226.381322] b43-phy2 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 5226.381328] b43-phy2 ERROR: This device does not support DMA on your system. Please use PIO instead.
[ 5226.381333] b43-phy2: Controller RESET (DMA error) ...
[ 5226.742851] b43-phy2: Loading firmware version 478.104 (2008-07-01 00:50:23)
[ 5240.531256] b43-phy2: Controller restarted

---

### Post by sduvick on 2010-04-30
hey guys, i've been watching this thread for a long time, and previously the fixes put forth were working fine. I updated to Lynx lts a few days ago, compiled compat wireless and it worked for a day, then about half an hour into using my laptop, it dma'd on me. traditional FATAL DMA 0x0000000 .... I have tried "pio=1 qos=0" and "pio=0 qos=1" and neither have stopped the DMA. I did reset the card before and after the dmas occured.
any ideas?
ps. you guys do a great job of helping the regular users around here!

EDIT: I retried pio and qos and it gave me "unknown symbol in module" which pointed to pio. why can't it understand PIO now? it worked in the RC i had a few days ago?

EDIT 2: now i recompiled compat wireless and it's giving me MAC suspend failed.

---

### Post by chenxiaolong on 2010-04-30
First post updated. Please tell me if I made any errors. I am really tired right now :(.

---

### Post by NIN101 on 2010-05-01
> EDIT 2: now i recompiled compat wireless and it's giving me MAC suspend failed.

Same here. 

As piratesmack wrotes, this is a solution: 
> options b43 pio=1 qos=0

rmmod b43
echo "options b43 pio=1 qos=0" > /etc/modprobe.d/b43.conf
modprobe b43

---

### Post by mikeioannina on 2010-05-01
Yes! it works
After a clean install of lucid I had to disassemble the whole netbook to take the card off to be able to boot. Then I did the steps in the first post and also installed b43-fwcutter and the card works fine with no errors! also monitor mode works but I haven't tested injection

---

### Post by bond-o on 2010-05-01
Followed the instructions and can see my b43 with 2.6.33-02063303-generic.  However, WPA or wpa_supplicant seems to not be functioning properly for my hidden network.  I have not tried a known good network with open authentication.

I have working scripts from Hardy, Intrepid, and Jaunty that will not work with Lucid.  It seems as if a continuous loop occurs until it "crashes" the card.  The loop starts at "sudo wpa_supplicant -Dwext -iwlan0 -c/home/"name"/Scripts/wpa_supplicant_home.conf -dd".


I also have working WICD "tweeked" configurations from Hardy and Intrepid returns "Bad Password".  When viewing /var/lib/wicd/wlan0, the PSK continues to change to hex versus "passphrase".  If I enter the hex within the WICD GUI, I still receive a "BAD Password" error and now the hex is changed to the passphrase format.  And yes, I have manually edited to force both hex and passphrase with the same "Bad Password" error.   

In addition, I have a Cisco AIR-CB21AG-A-K9 PC Card that produces the same results as above.

---

### Post by TironN on 2010-05-02
Well I've got it running perfectly under 2.6.34-rc5-lucid! Finally with pio=1 and qos=0 all is good!

I did try under 2.6.33 but dmesg returned:
```
b43: unknown parameter: 'pio'
```

Not sure if anyone's seen this because I would prefer to be running it on a stable release but what do you think?

---

### Post by chenxiaolong on 2010-05-02
bond-o: I noticed that you didn't list Karmic in the working distros. I could never get wpa_supplicant to work under Karmic. When you connect with wpa_supplicant, what does "dmesg" say? Does it says something like "Connecting to ap 00:##:##:##:##:## timed out"?

As for WiCD, the last time I used WiCD, it didn't require the SSID of a hidden network to connect, which is a problem, since the WPA hex key is generated from the SSID and the passphrase. I have no idea why it's converting the PSK back to a passphrase, as the router only accepts a PSK hex key while connecting :confused::confused:.

Do you use WPA[2] with TKIP authentication on your network? If you do, could you try to modprobe b43 with "pio=1 qos=0 nohwcrypt" or you could try changing your router settings to WPA[2] with AES authentication. I use this and it works fine, with NetworkManager. I can test wpa_supplicant, if you want.

One more thing (sorry!), I'm using kernel 2.6.34-RC6. B43 seems to connect more reliably on that kernel.

TironN: B43 seems to connect more reliably on the 2.6.34 kernel. If you really want to use kernel 2.6.33, you can install compat-wireless to get it working, but seeing how quickly the RC's are released, 2.6.34 stable should be out soon :D.

By the way, kernel 2.6.34-RC6 is out now :D.

---

### Post by bond-o on 2010-05-02
chenxiaolong: I never installed Karmic and I was only on Jaunty for a short period of time due to issue between Virtual Box and VMware.  I utilize my laptop for work and try to make it as stable as possible.  I was moving to Lucid thinking that the LTS would have been more solid with networking.

Anyway, I ended up rebuilding due to a kernel issue that I could not correct and was receiving a crash during reboot.

So, I am currently running 2.6.32-21-generic-pae and have followed some your previous posts along with some others.  I am experiencing the b43 loading, but receive the "b43-phy0 ERROR: CONFIG_B43_FORCE_PIO must be set in your kernel configuration." error.  I have firmware version 410.2160 (2007-05-26 15:32:10) loaded.  I added the b43.conf file as well as manually loading the driver with "pio and qos", but it returned "unknown pio", or something equivalent.  So, I am guessing that this is a kernel issue.

As to WICD, I have made this work with my Cisco PC Card with the ath5k drivers.  For some odd reason, WICD has changed the way the psk="$_PSK" was being handled.  It was converting the passphrase into hex, but then injecting the hex with the " "'s to make it a passphrase.  Thus, kicking back a bad password.  In the versions I mentioned in my previous post, this worked without issue.

For more information regarding WICD and Hidden WPA Network, see [http://wicd.net/punbb/viewtopic.php?id=566](http://wicd.net/punbb/viewtopic.php?id=566).

---

### Post by chenxiaolong on 2010-05-02
bond-o: Kernel 2.6.32 does not work well at all with b43. B43 requires the CONFIG_B43_FORCE_PIO option to be set in the kernel configuration to enforce PIO mode, which the 2.6.32 b43 does not support. Only kernel _>_2.6.33 or compat-wireless support PIO, which doesn't compile under 2.6.32.

---

### Post by WoodsieLord on 2010-05-03
Hello there,

I'm in need of advice. I own a netbook with a broadom 4315 and I'm having trouble to get it working for Aircrack.

I do have a minimum experience with aircrack since I have another notebook with an Atheros NIC which allows me to crack my own WEP key.

So!, I got ubuntu 10.04 installed recently and after some struggle I got the card working for a few seconds. Long story short: Yes, I've been reading this post and a lot more... and yes, I've tried disabling the network-manager service and double checked the airmon-ng check kill command which confirms that (apparently) nothing is bothering.

In Detail: This is what I've done so far.
- I installed the b43 drivers. I've been able to see nearby access points (including mine, of course). Device was eth1 and airodump didn't work neither did Kismet.
- I installed the b43-fwcutter tool and ran it.
- then I blacklisted the wl and lib80211 modules from blacklist.conf
- I am disabling network-manager service and killing the wpa_supplicant process. Airmon-ng says there's nothing bothering.
- after modprobing b43, I get the card recognized as wlan0.
- I am able to set the card to monitor mode using 'iwconfig wlan0 mode monitor'.
- For a very few seconds I'm able to:
1. Run kismet and see access points.
2. Run airodump-ng to see access points and or capture IVs for any specific ones.

This only works for a few (1 - 3) seconds. Afterwards, the numbers freeze, and that's all. No error messages. Whats even worse:

a. If I quit (be it Kismet or Airodump-ng) and restart it, I can't see any network (no packets can be captured either).
b. If I restart the interface (ifconfig wlan0 down//up) I can -once again- capture a few packets Or view available access points.
c. In combination, if I leave an airodump capture running and then I restart the interface (using ifconfig) the captured packets increment.

I hope I'm providing enough information to earn a helping hand. I also think I've been reading and searching enough... if I'm wrong, please let me know.

What I'm running:
Hardware: HP Mini 311, Atom N270 (32bit x86), 1GB RAM, ION chipset (nvidia integrated GPU).
Software: Ubuntu 10.04 i386, downloaded last week. Normal version (Not the Netbook remix).
Aircrack-ng installed from Synaptics manager, the only version available. Same with Kismet, installed from Synaptics.

Thanks in avance for any tip or directions,
WoodsieLord.

---

### Post by chenxiaolong on 2010-05-03
WoodsieLord: First of all, the included Aircrack-ng will not work with the Broadcom 4315 wireless card. I have no idea why. You need to compile the svn (latest development) version of Aircrack-ng:

```
sudo apt-get remove aircrack-ng
sudo apt-get install build-essential subversion libssl-dev
mkdir aircrack_source
cd aircrack-source
svn co http://trac.aircrack-ng.org/svn/trunk/ aircrack-ng
cd aircrack-ng
make unstable=true
sudo make install
```

For Kismet, are you sure you have "source=b43,wlan0,wifi" set in "/etc/kismet/kismet.conf"?

When I run Aircrack-ng, this is what I do:

1) Disconnect from network, while leaving Network-Manager running.
2) sudo ifconfig wlan0 down
3) sudo iwconfig wlan0 mode monitor
4) sudo ifconfig wlan0 up (My laptop locks up for a few seconds after this while Network-Manager redetects the wireless card)
5) sudo kismet OR sudo airodump-ng wlan0

and then everything works and nothing locks up.

If you have any questions, feel free to make another post or PM me :D.

Good luck!

---

### Post by TironN on 2010-05-04
Well I think now I have it working I'll stay with rc5 until the stable 2.6.34 is released.

---

### Post by mzaba on 2010-05-05
Hi.
I'm trying to use aircrack-ng in my laptop and I'm having problems. I don't even get to set my wireless interface on monitor mode. I'm using Ubuntu 10.04 Lucid Lynx and a Broadcom BCM4312 [14e4:4315]

I started trying 4 weeks ago with 9.10 and different kernels, but nothing worked.
I have been reading many forums and tried a lot of things.

I installed Ubuntu 10.04 and activated b43 driver and Broadcom controller STA from the "Hardware Controllers" application under UBUNTU desktop. After this, wireless card works correctly, I can connect to a free server near my home without nay type of key (Hot Spot).

This is what I know, I have to change my identifier from eth2 to wlan0 and then set monitor mode.
I have tried like this (original kernel UBUNTU10.04   2.6.32.21 ):

sudo su
apt-get install git-core
apt-get install aircrack-ng

git clone [http://git.bu3sch.de/git/b43-tools.git](http://git.bu3sch.de/git/b43-tools.git)
cd b43-tools/fwcutter
make
cd ../../

wget [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
tar xjf broadcom-wl-4.178.10.4.tar.bz2

cd broadcom-wl-4.178.10.4/linux
sudo ../../b43-tools/fwcutter/b43-fwcutter -w ../../../../lib/firmware wl_apsta.o

iwconfig

The result is the same as before:
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:189  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

Can someone help me, are these lines here correct?

Thanks in advance!!!

---

### Post by chenxiaolong on 2010-05-05
When you activated monitor mode, your wireless card needs to be running with the b43 driver:

sudo rmmod wl
sudo modprobe b43

Also, to activate monitor mode, you need to deactivate the card first:

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up #<--Your computer might freeze for a few seconds here

To change back to monitor mode:
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up

Please post back or PM me if you have any problems.

Good Luck!:D

---

### Post by mzaba on 2010-05-05
sorry

---

### Post by mzaba on 2010-05-05
i

---

### Post by chenxiaolong on 2010-05-05
Could you please delete the two extra posts?

Thank you.

---

### Post by mzaba on 2010-05-05
It's great!
It seems, now it works. Monitor mode is activated.
I haven't read anything before about this advice (now it's logical, remove other module). These two lines where the solution:

sudo rmmod wl
sudo modprobe b43

Rest is like in many places in the web. I'll try everything better later.
I'll write the results.

---

### Post by chenxiaolong on 2010-05-05
Awesome:D!! It seems like it's working for everyone now!

---

### Post by mzaba on 2010-05-07
I think it is not working for everyone!!!
Things are better, and everything thanks to you but I haven't got real success! I'm sure I will

My problem is that I can only make injection in channel 11 and very slowly. These are my steps and some screens. Code:

sudo rmmod wl
sudo modprobe b43
sudo airmon-ng start wlan0

I use airmon-ng for monitor mode because I can't run aireplay with wlan0 . "No answer" is written instead of "Injection is working" . With airmon appears something similar to this:

Code:
There are some processes in trouble, if aireplay or airodump stop in
 a few seconds you will want to kill some of them:
..... list of process....
wlan0          phy0(monitor mode enabled)

I do it with mon0:

sudo aireplay-ng -9 mon0

Here injection starts but only on channel 11 with the only 2 wireless I have near my laptop. Results are good : 100%. With wlan0 0%. Really I have more in other channels. Then I attack with packages:

sudo aireplay-ng -3 1 -a 00:11:E3:D4:0C:74 mon0
sudo airodump-ng -c 11 --bssid 00:11:E3:D4:0C:74 -w /media/D/MyDocs/file mon0 (another terminal)
sudo aircrack-ng -n64 /media/D/MyDocs/file-01.cap (another terminal)

18 IVs for Aircrack in 5min. Failed and next try in 5000 IVs, but never gets to 5000

Thanks in advance! You're very good.

---

### Post by chenxiaolong on 2010-05-07
Whenever I use any aircrack-ng program, before running it, I set the channel of the wireless card:

[CODE]sudo iwconfig wlan0 channel 6[/CODE

---

### Post by zubodybop on 2010-05-09
I'm a complete Linux newbie, and I can't figure out how to get this wireless card to work. I've done so many instructions, and I still can't figure it out. I did everything listed under the most recent update on the first page, and still no networks show up. I'm running Ubuntu 10.04, and this annoying lack of wireless is the only reason I'm not making the switch. I can't figure this out.

The wireless card I'm using is the one with topic is about, and I finally realized that the Broadcom of the same name that I was following a tutorial for was a different version (14e4:4312), which isn't my version, so my previous attempts to get it to work failed. Now that I've found this thread, it's been helpful and I've done the steps present in the first post, but to no avail. Wireless Networks just don't show up, with no error messages or anything popping up. Running Ubuntu 10.04 using the kernel you specified in the first post.

I also followed what mzaba did, but when I got to the command sudo rmmod wl, I get the message ERROR: Module wl does not exist in /proc/modules

---

### Post by mzaba on 2010-05-09
Hi. I had my first success with aircrack. I got the key of my wireless network, but I needed about 100 min. And I had to stop my second try in a friend's house after 4 hours.... 
I have a lot to learn. I need to learn how to use better Aireplay and Airodump-ng.
Data column increases very slowly. 
Thanks to Ubuntu Forums!

---

### Post by chenxiaolong on 2010-05-10
zubodybop: Could you post the output of "dmesg | grep b43" so I can see what errors b43 is producing?

mzaba: Yeah...Aircrack-ng injection with this card is very slow...but the awesome Linux developers will fix that :D.

---

### Post by zubodybop on 2010-05-11
[    7.400849] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.400866] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    7.816894] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    8.196819] Registered led device: b43-phy0::tx
[    8.196833] Registered led device: b43-phy0::rx
[    8.196849] Registered led device: b43-phy0::radio
[   11.360249] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   11.644304] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[   11.820466] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[   12.016356] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   18.593311] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[   18.619455] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.619477] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64

Thanks for the help, dude. Much appreciated. =D

---

### Post by julester23 on 2010-05-11
I'm also experiencing the disconnect problem. I am running a Lenovo S10 on 2.6.33-02063303-generic with mac80211 patched wireless-compat from 2010-04-26 and the 478 firmware. Running airodump-ng lasts about a half second (pulls in APs), then fails to get any more data after that time. In fact, the wireless card is worthless until i reload the module with 'rmmod b43; modprobe b43;' If I am associated with an AP, and i am using airodump on a mon0 interface created by airmon-ng, pings fail within a second of starting the dump. I've tried many variations with kernel versions, and wireless-compat versions (newest ones fail to compile). Nothing has worked so far.

[ 8943.550917] b43-phy8: Broadcom 4312 WLAN found (core revision 15)
[ 8943.618652] phy8: Selected rate control algorithm 'minstrel'
[ 8943.625649] Registered led device: b43-phy8::tx
[ 8943.625728] Registered led device: b43-phy8::rx
[ 8943.625802] Registered led device: b43-phy8::radio
[ 8943.626052] Broadcom 43xx driver loaded [ Features: PMNLS, Firmware-ID: FW13 ]
[ 8943.701441] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[ 8943.709274] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[ 8943.722258] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[ 8943.921313] b43-phy8: Loading firmware version 478.104 (2008-07-01 00:50:23)

---

### Post by chenxiaolong on 2010-05-11
zubodybop: Sorry for not being able to give you an answer yet :(.

Can you post the outputs of:

```
lsmod | grep wl
lsmod | grep b43
lsmod | grep ssb
lsmod | grep ndiswrapper
sudo iwlist scan
```

If "sudo iwlist scan" doesn't give you any networks, then you probably need to reset your card (take-out-the-card-from-computer process :D).

julester23: First of all, welcome to Ubuntu Forums! 

Kernel 2.6.34 does not have the any disconnect problems that I know of. Kernel 2.6.34-RC7 came out yesterday, which is last release candidate, so the stable version of 2.6.34 should be out soon.

---

### Post by mzaba on 2010-05-12
Hi
I have another usb wireless card with a rtl8187 chipset and I've heard it's better than BCM4312, I'm trying it. At first I thought it was better injecting and receiving packets, but now I think is not faster. I'm thinking that I will need to patch the driver in UBUNTU 10.04. What do you think?

---

### Post by chenxiaolong on 2010-05-12
mzaba: Here's the guide to your wireless card in Ubuntu: [http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0) :D

---

### Post by mzaba on 2010-05-12
Thank you!!
I also have found some threads inside Ubuntu Forums. I'll see how it works

---

### Post by chenxiaolong on 2010-05-12
You're welcome!

Let me know how it goes :D.

---

### Post by zubodybop on 2010-05-12
alex@alex-laptop:~$ lsmod | grep wl
alex@alex-laptop:~$ lsmod | grep b43
alex@alex-laptop:~$ lsmod | grep ssb
ssb                    40330  1 b44
alex@alex-laptop:~$ lsmod | grep ndiswrapper
alex@alex-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

This is puzzling. It doesn't look like it picked up any networks.

---

### Post by chenxiaolong on 2010-05-12
The module (driver) doesn't seem to be loading (as indicated by "lsmod | grep b43." Try loading the module (sudo modprobe b43) and running "sudo iwlist scan" again.

---

### Post by zubodybop on 2010-05-13
Hey, man. Thanks for the help. I got it to work. =) Really appreciate it. The wlist scan told me everything I needed to get the wireless working. I entered the SSID of the network into my network connections, and bam, it worked. Much appreciated.

---

### Post by chenxiaolong on 2010-05-13
Nice :D! So it didn't work because the driver wasn't loaded. You can make the b43 driver load automatically by adding "b43" to the file "/etc/modules"

---

### Post by mzaba on 2010-05-13
Hi Chenxiaolong: I have followed the tuto you told me and now aircrack-ng works much better. I decode wep keys in 10-20 min! More or less like the video tutorials you can find everywhere. With some networks I have problems connecting with UBUNTU but in windows 7 everything goes fine.
The usb wireless card is not exactly the same as the tuto but there was no problem with r8187 driver.
It is a RTL8187L chipset, 500mw and 14dbi antenna for 60€

---

### Post by chenxiaolong on 2010-05-13
I'm not sure what causes it to not connect, but I'm pretty sure it will be fixed with later versions of the driver.

(I'm sorry that I don't have a better answer :()

---

### Post by jpl888 on 2010-05-14
Hi,

I'm not sure what this tutorial is for now? 

My bcm4312 works out of the box with the stock kernel and b43 where it would only work with the proprietary wl before. 

No crashes yet but I've only had it enabled 5 mins :)

---

### Post by chenxiaolong on 2010-05-14
Hopefully it won't crash then :D. Most of the other people had to use kernel 2.6.33 with b43 (PIO mode on).

---

### Post by carlonzo on 2010-05-15
Hi!
I installed 2.6.33 kernel on 10.04 with PIO on and QoS off...but every 2 minuts it crash down and i have to reinstall the module!! mmm why? 
I think that i will install wl module.. :/
 
im sorry for my english.. :D

---

### Post by jpl888 on 2010-05-15
Well I've been using it for the best part of a day left it on over night and no errors, or crashes to speak of. 

To the previous poster maybe you should just try the stock kernel and enable b43 in Jockey. It is working well for me albeit I am 64 bit.

---

### Post by chenxiaolong on 2010-05-15
carlonzo: Welcome to Ubuntu Forums! Like jpl888, you can try booting the stock Ubuntu kernel. If that doesn't work, you can try kernel 2.6.34-RC7 from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/).

---

### Post by carlonzo on 2010-05-15
thank you boy...!!! I'll try it...
see u!

---

### Post by chenxiaolong on 2010-05-15
You're welcome! Hopefully it will work.

---

### Post by NIN101 on 2010-05-16
The DMA bug is pissing me off :-). If you search the [mailing list of the developers](http://lists.infradead.org/pipermail/b43-dev/), you will see that they know about it. But still no fix. As they say, it is a strange bug.  PIO is enough to connect to one/your Access Point and surf the web. But you can't play with aircrack when using b43 in pio mode. After some time with aircrack, airodump etc., my card stops to work. So I have to reload b43.  I hope it will work ASAP with DMA. I am using Lucid and kernel. 2.6.34 rc7.

---

### Post by chenxiaolong on 2010-05-16
The only way to test the state of the DMA mode of b43 is to compile compat-wireless or wireless-testing (takes forever). I'll do some testing soon. I accidentally screwed up my Ubuntu installation from compiling Compiz 0.9 and Xorg 1.8 to /usr.

---

### Post by chenxiaolong on 2010-05-16
Yes!!! Kernel 2.6.34 is out. I'm going to test it when Ubuntu packages it.

---

### Post by TironN on 2010-05-19
> **chenxiaolong said:**
> Yes!!! Kernel 2.6.34 is out. I'm going to test it when Ubuntu packages it.

I have got a self compiled 2.6.34 stable running under Arch Linux and b43 is 100% stable!

I did have to manually install the firmware but it is definitely working!

EDIT:

A couple of hours later and it's still working. Just letting you know.

---

### Post by tormod on 2010-05-20
> **chenxiaolong said:**
> Yes!!! Kernel 2.6.34 is out. I'm going to test it when Ubuntu packages it.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

---

### Post by chenxiaolong on 2010-05-20
TironN: Nice! Is it working in DMA or PIO mode?

---

### Post by TironN on 2010-05-21
> **chenxiaolong said:**
> TironN: Nice! Is it working in DMA or PIO mode?

I haven't tried DMA yet but I will sometime this weekend!

---

### Post by chenxiaolong on 2010-05-21
Cool! Let us know how it goes! :D

---

### Post by mober on 2010-05-23
I've tried with 2.6.34 kernel + compat-wireless-2010-05-22 + broadcom-wl-4.178.10.4 firmware

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)
[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-22.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-22.tar.bz2)
[http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.b](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.b)

I get this error:
```
[ 2558.500577] b43-phy1: Loading firmware version 478.104 (2008-07-01 00:50:23)
[ 2564.032390] b43-phy1 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 2564.032397] b43-phy1 ERROR: This device does not support DMA on your system. Please use PIO instead.
[ 2564.032400] b43-phy1: Controller RESET (DMA error) ...
[ 2564.260258] b43-phy1: Loading firmware version 478.104 (2008-07-01 00:50:23)
[ 2569.781343] b43-phy1: Controller restarted
```

Then broadcom 4312 works ok and stable, but I think it's in PIO mode.
There is the output of modinfo b43 | grep parm:
```
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
```

I think the DMA error is not fixed at new 2.6.34 kernel.
At [http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.34/ChangeLog-2.6.34-wireless](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.34/ChangeLog-2.6.34-wireless) you can see the new features of wireless drivers at 2.6.34-stable kernel and you can find this improvement:```
commit 9e3bd9190800e8209b4a3e1d724c35f0738dcad2
Author: Linus Torvalds <torvalds@linux-foundation.org>
Date:   Fri Feb 26 10:34:27 2010 -0800

    b43: fall back gracefully to PIO mode after fatal DMA errors
    
    This makes the b43 driver just automatically fall back to PIO mode when
    DMA doesn't work.
    
    The driver already told the user to do it, so rather than have the user
    reload the module with a new flag, just make the driver do it
    automatically. We keep the message as an indication that something is
    wrong, but now just automatically fall back to the hopefully working PIO
    case.
    
    (Some post-2.6.33 merge fixups by Larry Finger <Larry.Finger@lwfinger.net>
    and yours truly... -- JWL)
    
    Signed-off-by: Linus Torvalds <torvalds@linux-foundation.org>
    Signed-off-by: John W. Linville <linville@tuxdriver.com>
```

The question is...
**Is actually possible get bcm4312 [14e4:4315] work under Ubuntu with b43 driver in DMA mode anyway?**

---

### Post by chenxiaolong on 2010-05-23
mober: Welcome to Ubuntu Forums!

There currently is not a way to get b43 working in DMA mode with the 14e4:4315. A few months ago, someone (Sorry, I didn't bookmark the link) said that DMA was supposed to be fixed for 2.6.34, but instead, only PIO was stabilized. I'm not sure when DMA mode is going to be fixed now.

---

### Post by piratesmack on 2010-05-23
chenxiaolong, you might want to edit your post to recommend installing 2.6.33.4 or 2.6.34

2.6.33.3 had some nasty I/O-related bugs

---

### Post by chenxiaolong on 2010-05-23
Sure thing :D.

---

### Post by MarioHaddad on 2010-05-26
Hey ! 10.04 x64 with the kernel you stated in the first post did not work for me... not even standard internet use. STA would not install, ( tried it after trying the commands in the first post ) when using the Hardware Drivers thingy, when i try to install something, after it downloads the driver it says it cannot install. i rolled back to my working Karmic thats why im not accurate with what happens... so im gonna try again in a few days, but before i do i want to know that i got it right :

1) install 10.04
2) install the newer kernel
3) JUST PUNCH IN THE COMMANDS IN THE FIRST POST?

or should i install fwcutter then compat wireless THEN try those commands ? 

thank you :guitar:

---

### Post by chenxiaolong on 2010-05-26
Sorry for the slow response. I was at school :(.

These are the steps:

Install the build-essential and git-core packages:

```
sudo apt-get install build-essential git-core
```

Download and install the b43 firmware. I prefer to use the firmware instructions (quoted here) on the b43 website, rather than Ubuntu's b43-fwcutter.

```
mkdir b43-stuff
cd b43-stuff
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2
tar xjf b43-fwcutter-013.tar.bz2
cd b43-fwcutter-013
make
cd ..
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

Then run the commands on the first post:

```
sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf
```

And that should be it :D.

The Broadcom STA driver will only work under kernel 2.6.32.* because the kernel headers directory structure changed in kernel 2.6.33 and up (meaning that you will have to change the source code to make it work).

---

### Post by MarioHaddad on 2010-05-27
thats pretty quick for me !! :P... thank you ! gonna try it now..

and one other thing, is there a Linux dist that would run 14e4:4315 in DMA with monitor mode ?

---

### Post by chenxiaolong on 2010-05-27
All Linux distros would be same. It's the kernel that provides the new drivers. A new kernel is release about every two months. Hopefully kernel 2.6.35 will support DMA mode with this card.

---

### Post by TironN on 2010-05-27
> **chenxiaolong said:**
> All Linux distros would be same. It's the kernel that provides the new drivers. A new kernel is release about every two months. Hopefully kernel 2.6.35 will support DMA mode with this card.
We can always hope! Someone is going to have to fix this soon!

---

### Post by MarioHaddad on 2010-05-27
aaah I see.. or you could just wait for me to finish my studies in computer science :P 

btw 10.04 is working perfectly for me now :D :popcorn:

EDIT: Except Bluetooth :P but doesn't really matter to me for now..

---

### Post by chenxiaolong on 2010-05-30
Kernel 2.6.35 RC1 is out! I'll test b43 in DMA mode sometime after my school finals are over. 

MarioHaddad: You can PM me about the bluetooth and I'll try to help you fix it :D.

---

### Post by underplay on 2010-05-31
2.6.34-020634-generic locks up for me as well, the lockup time is random, anywhere from 0 seconds to 20 minutes.

Doesnt matter if im just using wlan0 or airmon-ng to start mon0, both lockup. Seems there are still some I/O issues, im using a Compaq Mini

Im not sure if its related but im having trouble doing fake authentication on one of my specific routers(WRT54GS v4) 

Please let us know if you ever get DMA mode working.

---

### Post by orengolan on 2010-05-31
I have 10.4, 2.6.32-22-generic.
I get the following dependency error when trying to follow the instructions on the first post.

sudo dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb 
```
Selecting previously deselected package linux-headers-2.6.34-020634-generic.
(Reading database ... 98189 files and directories currently installed.)
Unpacking linux-headers-2.6.34-020634-generic (from linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb) ...
dpkg: dependency problems prevent configuration of linux-headers-2.6.34-020634-generic:
 linux-headers-2.6.34-020634-generic depends on linux-headers-2.6.34-020634; however:
  Package linux-headers-2.6.34-020634 is not installed.
dpkg: error processing linux-headers-2.6.34-020634-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.34-020634-generic

```

---

### Post by chenxiaolong on 2010-05-31
You need to download all three files to a new directory and then run:

```
sudo dpkg -i linux*2.6.34*.deb
```

You can also install the **linux-image*.deb** package first, then **linux-headers*.deb**, and then **linux-headers*-generic.deb**.

Hopefully this is a quick enough response :D (I've never responded within 10 minutes before :D).

---

### Post by orengolan on 2010-05-31
works, but after boot i don't see the wireless networks (using wicd).

I also purged and installed b43-fwcutter but it didn't help.

here is some info that can help in troubleshooting:
lshw -C network
```
*-network UNCLAIMED
```

yuka@yuka-laptop:~$ iwconfig 
```
lo        no wireless extensions.
eth0      no wireless extensions.
```


thank you so much for the quick reply!

---

### Post by chenxiaolong on 2010-06-01
It seems like the b43 module isn't loading.

You can load it with:

```
sudo modprobe b43
```

and you can make it load automatically on boot by adding "b43" (on a separate line) to /etc/modules.

Hope this helps.

---

### Post by rlelliott on 2010-06-01
Just as an announcement, I have been working with a group of people on a new security distro based on Kubuntu 10.04 LTS Lucid Lynx. This distro has fully working and stable out of the box (2.6.32) b43 drivers for the 14e4:4315 (Broadcom bcm4312 rev 01) wireless device. Check [http://secmic.org](http://secmic.org) the site should be live soon. Thanks to Chenxiaolong, many people now understand how to properly load this module and the steps that need to be taken beforehand.

Regards,
rlelliott

---

### Post by chenxiaolong on 2010-06-01
rlelliott: I already have a partition for SECmic to be installed on :D.

I have two questions for you:

1) How did you get b43 working on kernel 2.6.32 (or was that a typo)?

2) Will SECmic have a 64 bit edition?

Anyway, good luck with your distro :D.

---

### Post by rlelliott on 2010-06-01
1)

SECmic comes with the wl dkms driver loaded at boot. After login a script has been created along with a desktop icon. Loading the b43 driver is a click and pass entry process.

This method has been tested and proved for the last 3 months. We chose to stay with kubuntu's shipped kernel so as to keep updates streamlined from the already wonderfull ubuntu/kubuntu repo.

2)

Because of the nature of most of the not so popular, but extremely useful security apps, a 64bit edition is not currently planned. 


Furthermore, I have been running the final version of SECmic3 for about 2 weeks now, and I must say, IT RUNS GREAT! The first two versions of SECmic were based on Karmic Kola hence the name and were internal releases. SECmic3 will be the first public release. It was completely rebuilt using Kubuntu 10.04 LTS Lucid Lynx and is fully update compatible using the standard ubuntu/kubuntu repo. 10+ menus under the main SECmic menu, and over 200 security oriented applications. The site is up, but for now is at a very minimal stage. It should be live with iso+md5 check sum on 06/04/2010! I am very pleased to have taken part in this project, and I must say that credit for the path of knowledge needed to make the b43 portion work is due to the massive amount of research you have done. Thank you.

Regards,
Rlelliott

---

### Post by chenxiaolong on 2010-06-01
Looks like an awesome security distro -- with current packages! :D :D. I'm looking forward to using it. 

Once SECmic3 is released on your website, I'll try and see if I can compile the applications under [K]ubuntu x64.

By the way, your distro is going to released on the last day of my high school freshman year. What an awesome start to summer!

[Off topic-ness ends here :P]

---

### Post by rlelliott on 2010-06-04
The torrent file has been uploaded to [http://secmic.org](http://secmic.org). If some of you guys want to download it, and test your cards, please do. Ow yea and Seeeeeeeeeeeedddd.

---

### Post by orengolan on 2010-06-04
thanks chenxiaolong. you are awesome.

---

### Post by chenxiaolong on 2010-06-04
rlelliott: Downloading it right now :D! I'm getting ~140 KiB/s. I'll definitely seed, but Road Runner caps my upload speed at ~60 KiB/s.

---

### Post by rlelliott on 2010-06-04
Awesome! We will be doing a small marketing push on google, facebook, and myspace to see if we can get a community started. It would be great to see people try to figure out how to get some of the apps that are tricky to compile going on SECmic. Thank you for your support.

Regards,
Rlelliott

---

### Post by MarioHaddad on 2010-06-05
> **rlelliott said:**
> Awesome! We will be doing a small marketing push on google, facebook, and myspace to see if we can get a community started. It would be great to see people try to figure out how to get some of the apps that are tricky to compile going on SECmic. Thank you for your support.

Regards,
Rlelliott


Facebook is the fastest.. searched for the page today guess you havent made it yet :D tracker is offline for me :( still at 0.0% :(

---

### Post by chenxiaolong on 2010-06-05
I'm mirroring SECmic on my website, although uploading will take a LONG time (~49 KiB/s right now).

---

### Post by rlelliott on 2010-06-05
Thanks to Chenxiaolong, The server is now seeding the torrent, and it is being tracked here. I will be startig a new thread about this and no longer post here.

[http://linuxtracker.org/index.php?page=torrent-details&id=7721a0e2ba58002fcf9ac544c7acad101ae7dae4](http://linuxtracker.org/index.php?page=torrent-details&id=7721a0e2ba58002fcf9ac544c7acad101ae7dae4)

---

### Post by sixstringartist on 2010-06-06
So could someone recap the status of the MAC suspend failure message? I know it was mentioned, but I didnt see a solution.

Also, Im getting this in dmesg on one particular AP.

> wlan0: deauthenticated from XX:XX:XX:XX:XX:XX (Reason: 7)

Could someone tell me where I can reference what reason 7 is actually referring to? Is this in the kernel, or is it being generated by the b43 driver? Any documentation on that would be greatly appreciated.

---

### Post by chenxiaolong on 2010-06-06
I'm pretty sure that "Reason: 7" is caused by either the kernel or the wireless stack (software interface) as the error occurs with other non-Broadcom cards also. 

As far as I know, both of those errors (at least for me) occur when QOS (quality of service) is on. QOS is usually used for streaming media, VOIP, ethernet protocols, and multiplayer games. Torrenting--seeding, uploading, and copying files over the network tend to lag a little [A LOT :(].

Hopefully b43 will be fixed so that these errors don't happen anymore.

---

### Post by carlonzo on 2010-06-08
[OT]

secMIC is fantastic! good job boy!!!

[/OT

---

### Post by rlelliott on 2010-06-08
Almost 3 months of non stop work (karmic kola) took place to bring it all together. It was then completely rebuilt using Kubuntu 10.04 LTS Lucid Lynx. Thank you for your support.

---

### Post by MarioHaddad on 2010-06-08
still at 0% and 0 connected peers/seeds :( ( all torrent ports and properly forwarded on my router and i can download other things from torrents but not secmic :\ )

---

### Post by frka on 2010-06-10
Hi =)

I have install the 2.6.34 kernel and my wireless card is now working for ~30 sec.

When i run *rmmod b43* and then *modprobe b43 pio=1 qos=0 *the card connect to the WLAN for further 30 sec.
In this time-frame i can ping every website and open google or other sites, than the connection break and i have to unload the b43 mod and load it again. thats sucks :P

Here my dmesg:
```

[  105.336973] b43-phy1: Broadcom 4312 WLAN found (core revision 15)
[  105.411028] phy1: Selected rate control algorithm 'minstrel'
[  105.425916] Registered led device: b43-phy1::tx
[  105.425995] Registered led device: b43-phy1::rx
[  105.426067] Registered led device: b43-phy1::radio
[  105.426290] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[  105.664345] b43-phy1: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  111.249773] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  112.214743] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy1
[  118.821027] wlan0: deauthenticating from 00:04:0e:4d:aa:80 by local choice (reason=3)
[  118.821649] wlan0: authenticate with 00:04:0e:4d:aa:80 (try 1)
[  118.825262] wlan0: authenticated
[  118.825378] wlan0: associate with 00:04:0e:4d:aa:80 (try 1)
[  118.828639] wlan0: RX AssocResp from 00:04:0e:4d:aa:80 (capab=0x411 status=0 aid=2)
[  118.828662] wlan0: associated
[  118.833110] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  129.361067] wlan0: no IPv6 routers present
[  150.324149] No probe response from AP 00:04:0e:4d:aa:80 after 500ms, disconnecting.
[  150.368231] cfg80211: All devices are disconnected, going to restore regulatory settings
[  150.368257] cfg80211: Restoring regulatory settings
[  150.368277] cfg80211: Calling CRDA to update world regulatory domain
[  150.379379] cfg80211: World regulatory domain updated:
[  150.379394]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  150.379411]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  150.379424]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  150.379438]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  150.379451]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  150.379464]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  151.765109] wlan0: authenticate with 00:04:0e:4d:aa:80 (try 1)
[  151.964171] wlan0: authenticate with 00:04:0e:4d:aa:80 (try 2)
[  152.164205] wlan0: authenticate with 00:04:0e:4d:aa:80 (try 3)
[  152.364178] wlan0: authentication with 00:04:0e:4d:aa:80 timed out
[  214.811687] r8169 0000:04:00.0: eth0: link up
[  214.813085] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  225.312130] eth0: no IPv6 routers present


```and my syslog
```
Jun 10 22:25:40 netbook avahi-daemon[761]: Registering new address record for fe80::924c:e5ff:fe98:5b51 on wlan0.*.
Jun 10 22:25:42 netbook dhclient: DHCPREQUEST of 10.0.8.12 on wlan0 to 255.255.255.255 port 67
Jun 10 22:25:42 netbook dhclient: DHCPACK of 10.0.8.12 from 10.0.8.1
Jun 10 22:25:42 netbook dhclient: bound to 10.0.8.12 -- renewal in 386863 seconds.
Jun 10 22:25:42 netbook NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Jun 10 22:25:42 netbook NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 10 22:25:42 netbook NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jun 10 22:25:42 netbook NetworkManager: <info>    address 10.0.8.12
Jun 10 22:25:42 netbook NetworkManager: <info>    prefix 21 (255.255.248.0)
Jun 10 22:25:42 netbook NetworkManager: <info>    gateway 10.0.8.1
Jun 10 22:25:42 netbook NetworkManager: <info>    nameserver '10.0.8.1'
Jun 10 22:25:42 netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 10 22:25:42 netbook NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 10 22:25:42 netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jun 10 22:25:42 netbook avahi-daemon[761]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.8.12.
Jun 10 22:25:42 netbook avahi-daemon[761]: New relevant interface wlan0.IPv4 for mDNS.
Jun 10 22:25:42 netbook avahi-daemon[761]: Registering new address record for 10.0.8.12 on wlan0.IPv4.
Jun 10 22:25:43 netbook NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jun 10 22:25:43 netbook NetworkManager: <info>  Policy set 'Auto Tux' (wlan0) as default for routing and DNS.
Jun 10 22:25:43 netbook NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jun 10 22:25:43 netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jun 10 22:25:43 netbook ntpdate[1610]: adjust time server 91.189.94.4 offset -0.018145 sec
Jun 10 22:25:49 netbook kernel: [  129.361067] wlan0: no IPv6 routers present
Jun 10 22:26:10 netbook kernel: [  150.324149] No probe response from AP 00:04:0e:4d:aa:80 after 500ms, disconnecting.
Jun 10 22:26:10 netbook wpa_supplicant[1219]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jun 10 22:26:10 netbook NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jun 10 22:26:10 netbook kernel: [  150.368231] cfg80211: All devices are disconnected, going to restore regulatory settings

Jun 10 22:26:10 netbook kernel: [  150.368257] cfg80211: Restoring regulatory settings
Jun 10 22:26:10 netbook kernel: [  150.368277] cfg80211: Calling CRDA to update world regulatory domain
Jun 10 22:26:10 netbook kernel: [  150.379379] cfg80211: World regulatory domain updated:
Jun 10 22:26:10 netbook kernel: [  150.379394]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 10 22:26:10 netbook kernel: [  150.379411]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 10 22:26:10 netbook kernel: [  150.379424]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 10 22:26:10 netbook kernel: [  150.379438]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 10 22:26:10 netbook kernel: [  150.379451]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 10 22:26:10 netbook kernel: [  150.379464]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 10 22:26:10 netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun 10 22:26:11 netbook wpa_supplicant[1219]: Trying to associate with 00:04:0e:4d:aa:80 (SSID='Tux' freq=2462 MHz)
Jun 10 22:26:11 netbook NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun 10 22:26:11 netbook kernel: [  151.765109] wlan0: authenticate with 00:04:0e:4d:aa:80 (try 1)
Jun 10 22:26:12 netbook kernel: [  151.964171] wlan0: authenticate with 00:04:0e:4d:aa:80 (try 2)
Jun 10 22:26:12 netbook kernel: [  152.164205] wlan0: authenticate with 00:04:0e:4d:aa:80 (try 3)
Jun 10 22:26:12 netbook kernel: [  152.364178] wlan0: authentication with 00:04:0e:4d:aa:80 timed out
Jun 10 22:26:14 netbook NetworkManager: <debug> [1276201574.003011] periodic_update(): Roamed from BSSID 00:04:0E:4D:AA:80 (Tux) to (none) ((none))
Jun 10 22:26:21 netbook wpa_supplicant[1219]: Authentication with 00:04:0e:4d:aa:80 timed out.
Jun 10 22:26:21 netbook NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jun 10 22:26:21 netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun 10 22:26:26 netbook NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Jun 10 22:26:26 netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Jun 10 22:26:26 netbook NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1570
Jun 10 22:26:26 netbook NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jun 10 22:26:26 netbook avahi-daemon[761]: Withdrawing address record for 10.0.8.12 on wlan0.
Jun 10 22:26:26 netbook avahi-daemon[761]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.8.12.
Jun 10 22:26:26 netbook avahi-daemon[761]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 10 22:26:26 netbook NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Tux'
Jun 10 22:26:26 netbook NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun 10 22:26:26 netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 10 22:26:26 netbook NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun 10 22:26:26 netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 10 22:26:26 netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 10 22:26:26 netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 10 22:26:26 netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 10 22:26:26 netbook NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun 10 22:26:26 netbook NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Tux' has security, and secrets exist.  No new secrets needed.
Jun 10 22:26:26 netbook NetworkManager: <info>  Config: added 'ssid' value 'Tux'
Jun 10 22:26:26 netbook NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun 10 22:26:26 netbook NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun 10 22:26:26 netbook NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun 10 22:26:26 netbook NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 10 22:26:26 netbook NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 10 22:26:26 netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 10 22:26:26 netbook NetworkManager: <info>  Config: set interface ap_scan to 1
Jun 10 22:26:28 netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning

```any idea?

---

### Post by chenxiaolong on 2010-06-10
You could try loading b43 with:

```
sudo modprobe b43 pio=1 qos=1
```

For me, that same problem happens when QOS is on. What processor are you running? The Intel Core Duo and the Intel Atom processors are known to have problems with b43 and the 14e4:4315.

---

### Post by frka on 2010-06-10
> **chenxiaolong said:**
> You could try loading b43 with:

```
sudo modprobe b43 pio=1 qos=1
```For me, that same problem happens when QOS is on. What processor are you running? The Intel Core Duo and the Intel Atom processors are known to have problems with b43 and the 14e4:4315.

It seems that it works now =)

Btw: It is an Dell Inspiron Mini 10 with an Intel Atom. 
Dell delivers this Netbook with an Ubuntu 8.x and there is no problem to run WiFi

Thank you for your help! \\:D/

---

### Post by chenxiaolong on 2010-06-10
You're welcome :D.

So:

QOS on --> Intel Core Duo, Intel Atom

QOS off --> Intel Core Solo, Intel Core 2 Duo, Intel Core i3/i5/i7, and AMD

---

### Post by hellion_fi on 2010-06-18
Thanks for the tutorial, it's been helping me to get this far - wireless connection up and running with b43/2.6.34-kernel/Ubuntu 10.04/Lenovo s10 -system. My concern for now is connection speed and its stability.

I have been getting connection speeds (as seen from the nm/Connection information - don't know if there is a way that is more commonly used in this context - I'm still quite new at this... :-?) of 1Mb/s - 11Mb/s (or thereabouts), but with more emphasis on the 1Mb/s than the double digits... When I log in after reboot, the indicated speed can be even 54Mb/s, but drops almost instantly to 1Mb/s when data is being transferred. If I try to restart networking, the entire system hangs and only the power button in the computer is responding to anything. I'm able to force the connection speed to a fixed (indicated) speed using iwconfig, but if I set it to full 54Mb/s, the connection stays up, but no data (e.g. web pages) seem to get transferred. With slower speeds (11Mb/s-24Mb/s) everything seems to be ok, but still the responses from websites etc. seem to be uncharacteristically sluggish.

From reading from this thread and [other sources]("http://en.wikipedia.org/wiki/PIO_Mode"), I understood that the PIO mode is the only option at least so far, and the limits to data transfer rates with PIO mode are limited to something less than the full 54Mb/s. Therefore without the DMA mode working the 54Mb/s is not even theoretically possible, correct?

If the iwconfig-force is a working solution/workaround to this, is there a way to make this to happen automatically when connecting to a wlan / during bootup / login?

---

### Post by chenxiaolong on 2010-06-18
hellion_fi: Welcome to Ubuntu Forum! I'm glad you joined us in our mission to a working 14e4:4315 with b43 :D!

Everything you said in your post is 100% correct. PIO mode does make the card extremely sluggish. QoS, which must be turned off to connect to certain routers, also contributes to the "sluggishness" of the card. With QoS off, streaming media, torrents, etc. are extremely slow.

I'm not sure what you mean by iwconfig-force, but if you need anything to run at boot, just add the command line to the file "/etc/rc.local"

---

### Post by hellion_fi on 2010-06-18
chenxiaolong: With the iwconfig-force I meant 
```
sudo iwconfig wlan0 rate 24M
```
with the rate set to desired figure at the end there. I added the above line to my /etc/rc.local, and at least after rebooting just now, the nm/Connection information shows the speed being 24Mb/s, which it almost never has been after reboot (as said, it could be 54Mb/s, 11Mb/s, or even 2Mb/s or 1Mb/s). This would point to the fact that the rc.local -script works ok - well at least it sets the rate to be fixed and it seems to be stable, but as you said, very slow to respond to nearly any web traffic request. Since Lenovo s10 is an Intel Atom processor system, I use QoS =1 -option, but everything is slow, nevertheless.

Well, until someone manages to produce a solution with working _and stable_ DMA-support... :icon_frown:

Thanks.

---

### Post by chenxiaolong on 2010-06-18
Hopefully b43 will be fixed in the upcoming kernels. There doesn't seem to be much works done on it though...:(.

---

### Post by wolfen3 on 2010-06-20
> **chenxiaolong said:**
> Sorry for the slow response. I was at school :(.

These are the steps:

Install the build-essential and git-core packages:

```
sudo apt-get install build-essential git-core
```

Download and install the b43 firmware. I prefer to use the firmware instructions (quoted here) on the b43 website, rather than Ubuntu's b43-fwcutter.

```
mkdir b43-stuff
cd b43-stuff
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2
tar xjf b43-fwcutter-013.tar.bz2
cd b43-fwcutter-013
make
cd ..
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

Then run the commands on the first post:

```
sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf
```

And that should be it :D.

The Broadcom STA driver will only work under kernel 2.6.32.* because the kernel headers directory structure changed in kernel 2.6.33 and up (meaning that you will have to change the source code to make it work).

I habe done everything and i get this error after typing sudo modprobe b43

FATAL: Error inserting b43 (/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)


I tried to do it on live-usb ubuntu and ubuntu installed on hd

ubuntu 10.04
uname -r 2.6.32-21-generic

---

### Post by chenxiaolong on 2010-06-20
For b43 to work, you need to install kernel 2.6.33 or kernel 2.6.34. It will not work in kernel 2.6.32. Please see the first post of this thread ([http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)) for information on how to install the newer kernels.

---

### Post by bulletproof_dav on 2010-06-21
I Have a Dell Mini 9, with atom processor

```
lspci -nn | grep Broadcom
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

I followed chenxiaolong's steps

```
sudo apt-get install b43-fwcutter
```

then i installed kernel
```
uname -r
``` 
2.6.34-020634-generic

i restarted then ```
sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf
```

i restarted again and its working perfect.

the problems start occurring when i put the card in monitor mode.
sometimes it works and some other times it doesnt 

```
dmesg
```
b43-phy4 ERROR: MAC suspend failed
b43-phy4 ERROR: MAC suspend failed

---

### Post by lubo777 on 2010-06-23
thanks for sharing this HOWTO .. it took me few days to find it ... 

I have linked your HOWTO in a few other Linux distros forums, hope this will save some time for other b43 users to find it :)
:popcorn:

---

### Post by chenxiaolong on 2010-06-23
lubo777: Thank you for doing that :D. Hopefully more people can use b43 with this card now!

---

### Post by wheelern on 2010-07-02
Is there anyway you can maybe start a new thread that has all of the updates on it? I did everything on your first post, but it's not working. It almost seem like my wireless card is turned off, but it won't turn on when I touch the heat-sensor "on button." I feel like my answer might be in this thread somewhere, but I doubt I'll find it. Anyway you can help?

Thanks

---

### Post by chenxiaolong on 2010-07-02
I'm almost 100% sure that the reason it's not working is because you don't have the b43 firmware installed :D. Here's how you can install it:

You can install the deb package attached to this post (I packaged the files that are installed from the commands below) or you can run these commands:

```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2
tar xjf b43-fwcutter-013.tar.bz2
cd b43-fwcutter-013
make
cd ..
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

And a restart should get your wireless working :D.

EDIT: [Forgot to attach deb file]

---

### Post by holodeck on 2010-07-07
My monitor mode isn't working. I did everything as described on the first page, but it still isn't working, when i start monitor mode in aircrack-ng it works for maybe 30 secondsa and then stops. airodump cannot detect any APs it just freezes :(

Any thoughts ?

here's the output

magog@magog-laptop:~$ sudo modprobe b43
magog@magog-laptop:~$ dmesg | grep b43
[  111.375631] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  111.375655] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[  111.475444] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  111.585251] Registered led device: b43-phy0::tx
[  111.585294] Registered led device: b43-phy0::rx
[  111.585337] Registered led device: b43-phy0::radio
[  111.641266] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[  111.699020] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[  111.703647] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[  111.852294] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  737.916386] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[  769.053703] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  769.053726] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[  769.134998] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  769.205603] Registered led device: b43-phy0::tx
[  769.205653] Registered led device: b43-phy0::rx
[  769.205693] Registered led device: b43-phy0::radio
[  769.257266] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[  769.260612] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[  769.264963] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[  769.412282] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
magog@magog-laptop:~$ 

Kerlnel version is 2.6.34-020634-generic
I have Dell studio 1535 withwlan minicard Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

---

### Post by nastelroy on 2010-07-08
Hi i'm new here,

first time i use b43, this driver support with my ubuntu, although it manually configured (coz NetworkManager can't detect my BCM4312)..
[INDENT]vostro@vostro-laptop:~$ uname -r
[/INDENT][INDENT]2.6.32-21-generic

[/INDENT]And I can use it for monitoring mode(kismet and aircrack-ng)
After one night stay collecting data in monitoring mode, b43 cannot drive my wireless again,,

the kernel says:

[INDENT]ul  8 14:53:53 vostro-laptop kernel: [   90.280458] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
Jul  8 14:53:58 vostro-laptop kernel: [   95.801423] b43-phy0: Controller restarted
Jul  8 14:53:58 vostro-laptop kernel: [   95.801523] b43-phy0: Controller RESET (DMA error) ...
Jul  8 14:53:58 vostro-laptop kernel: [   96.032588] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
Jul  8 14:54:04 vostro-laptop kernel: [  101.553240] b43-phy0: Controller restarted
Jul  8 14:54:04 vostro-laptop kernel: [  101.553335] b43-phy0: Controller RESET (DMA error) ...
Jul  8 14:54:04 vostro-laptop kernel: [  101.784267] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)


[/INDENT]may kismet or aircrack can make b43 like that?

---

### Post by nastelroy on 2010-07-09
> **holodeck said:**
> My monitor mode isn't working. I did everything as described on the first page, but it still isn't working, when i start monitor mode in aircrack-ng it works for maybe 30 secondsa and then stops. airodump cannot detect any APs it just freezes :(

Any thoughts ?

here's the output

magog@magog-laptop:~$ sudo modprobe b43
magog@magog-laptop:~$ dmesg | grep b43
[  111.375631] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  111.375655] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[  111.475444] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  111.585251] Registered led device: b43-phy0::tx
[  111.585294] Registered led device: b43-phy0::rx
[  111.585337] Registered led device: b43-phy0::radio
[  111.641266] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[  111.699020] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[  111.703647] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[  111.852294] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  737.916386] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[  769.053703] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  769.053726] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[  769.134998] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  769.205603] Registered led device: b43-phy0::tx
[  769.205653] Registered led device: b43-phy0::rx
[  769.205693] Registered led device: b43-phy0::radio
[  769.257266] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[  769.260612] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[  769.264963] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[  769.412282] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
magog@magog-laptop:~$ 

Kerlnel version is 2.6.34-020634-generic
I have Dell studio 1535 withwlan minicard Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)


I have same problem with you...

vostro@vostro-laptop:/var/log/kismet$ uname -r
2.6.34-020634-generic


dmesg:
segfault at 2 ip b75cb50b sp bfe9e8ac error 4 in libc-2.11.1.so[b758b000+153000]

vostro@vostro-laptop:/var/log/kismet$ lspci -vv | grep Bro
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)




Dell vostro 1320

---

### Post by nastelroy on 2010-07-09
> **nastelroy said:**
> Hi i'm new here,

first time i use b43, this driver support with my ubuntu, although it manually configured (coz NetworkManager can't detect my BCM4312)..[INDENT]vostro@vostro-laptop:~$ uname -r
[/INDENT][INDENT]2.6.32-21-generic

[/INDENT]And I can use it for monitoring mode(kismet and aircrack-ng)
After one night stay collecting data in monitoring mode, b43 cannot drive my wireless again,,

the kernel says:
[INDENT]ul  8 14:53:53 vostro-laptop kernel: [   90.280458] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
Jul  8 14:53:58 vostro-laptop kernel: [   95.801423] b43-phy0: Controller restarted
Jul  8 14:53:58 vostro-laptop kernel: [   95.801523] b43-phy0: Controller RESET (DMA error) ...
Jul  8 14:53:58 vostro-laptop kernel: [   96.032588] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
Jul  8 14:54:04 vostro-laptop kernel: [  101.553240] b43-phy0: Controller restarted
Jul  8 14:54:04 vostro-laptop kernel: [  101.553335] b43-phy0: Controller RESET (DMA error) ...
Jul  8 14:54:04 vostro-laptop kernel: [  101.784267] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)


[/INDENT]may kismet or aircrack can make b43 like that?

It was solved my self by upgrade to kernel 2.6.34-020634-generic
kismet worked...but after capture 2-4 minutes, kismet became freeze

any idea? please

---

### Post by dnguy010 on 2010-07-13
> **nastelroy said:**
> It was solved my self by upgrade to kernel 2.6.34-020634-generic
kismet worked...but after capture 2-4 minutes, kismet became freeze

any idea? please

I also got the same problem, kismet, airocrack, wireshark ... stop working after 30 sec. I wonder if there is anyway we can fix this driver?

---

### Post by eric512 on 2010-07-13
> **dnguy010 said:**
> I also got the same problem, kismet, airocrack, wireshark ... stop working after 30 sec. I wonder if there is anyway we can fix this driver?

Yes - me too. Stops working between 30s and 2mins, but sometimes it will run AIRODUMP-NG for 20 mins. When I start AIREPLAY-NG, it hangs.

Mine is a WUSB100 v1. 

Stops on the following:

backtrack 2.6.28.1    -   rt2800usb
backtrack 2.6.30.9    -   rt2870sta
ubuntu 2.6.32-21-generic    -   rt2870sta (staging)

Tried ralink's latest rt2870sta - doesn't work at all.

---

### Post by ghinix on 2010-07-25
Thanks so much for helping get my Ubuntu 10.04 Netbook wireless working!!!
However how do we get monitor mode back on?
thanks in advance

---

### Post by ghinix on 2010-07-25
Ok going for another attempt to get the Broadcom bcm4312 rev 01 working again (using this process by “chenxiaolong” seemed to work)...

…hopefully this time my dvd drive won’t be so loud and noisy. Any ideas what could be causing the laptop dvd drive noise?

Thanks so much!

---

### Post by NIN101 on 2010-08-02
2.6.35 is out. Does it work with DMA now? Some tests?

---

### Post by chenxiaolong on 2010-08-02
I'll test that later on today. I'm using kernel 2.6.35-12-generic from the xorg-edgers PPA.

---

### Post by chenxiaolong on 2010-08-02
Unfortunately, the card still only works in DMA mode in kernel 2.6.35.

EDIT: Correction: Only works in PIO mode.

---

### Post by piratesmack on 2010-08-02
You mean PIO?

Damn

---

### Post by chenxiaolong on 2010-08-02
Oh OOPS :D. Yeah, I mean PIO.

---

### Post by NIN101 on 2010-08-02
So it will be fixxed:
-never
-in the distant future

I just can't believe anymore that there will be a patch soon :-(.

---

### Post by piratesmack on 2010-08-02
Oh well, at least we got a new configurator in 2.6.35
'make nconfig'

EDIT:
Also, does the 14e4:4315 really support packet injection?
Couldn't get it working on mine.

---

### Post by chenxiaolong on 2010-08-02
NIN101: I don't think it's going to be fixed any time soon. The b43 website lists the 14e4:4315 card as being supported. I don't think anyone is working on the driver or if there is, that person doesn't have this card.

piratesmack: Packet injection crashes my computer. I bet the 4315 card supports it, but the b43 driver doesn't yet.

---

### Post by theboss9999 on 2010-08-05
Hi, i followed the tutorial on the first page but applied the newest driver, OS - Ubuntu 10.04, kernel ..sth 34, wifi card Broadcom bcm4312 rev1. After restart i could see wifi card after running iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

But there are no WIFI networks on the list, i have the driver installed but i still can't use my wireless. ANY suggestions appreciated!

Activating monitor mode i get :airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
946    NetworkManager
954    avahi-daemon
957    avahi-daemon
1249    wpa_supplicant
2993    dhclient


Interface    Chipset        Driver

wlan0        Broadcom    b43 - [phy0]SIOCSIFFLAGS: Unknown error 132

                (monitor mode enabled on mon0)

---

### Post by chenxiaolong on 2010-08-05
Can you post the output of "dmesg" and check to see if "sudo iwlist scan" returns any networks?

---

### Post by kelvin.illa on 2010-08-10
Thanks, man. The kernel upgrade works -- plus the commands.

I persuaded my sister to have me replace Windows 7 on her Dell Inspiron 11.6" with Ubuntu Netbook Edition 10.04. When the wireless stopped working (b43), I was bound to look bad if not for this post.

Thanks, again.

---

### Post by chenxiaolong on 2010-08-10
You're welcome! I'm glad it worked for you!

---

### Post by kelvin.illa on 2010-08-10
> **chenxiaolong said:**
> You're welcome! I'm glad it worked for you!

Sorry to burst your bubble. I really wanted it to but it didn't work.

It turns out, the problem with the b43 driver was its very poor ability of catching wi-fi signal. When I was working on a fix for the problem, I was very close to the wireless router because I had to connect the netbook via ethernet. Then, whenever I think it gets fixed, I move to another room just several meters away; that's when the netbook loses wi-fi. I even reverted to current kernel (2.6.32-24) on Ubuntu, and it still works while I'm near the wireless router -- about only a few meters. I know it's not the wireless router's fault because other notebooks work fine with it.

There's another suggested driver on the "Hardware Drivers" list -- Broadcom STA -- but it doesn't work at all, not even poorly.

I wish, because I have absolutely no idea, there's an alternative to this b43 because the connection it creates is of very poor quality. The signal strength drops exponentially with distance.

But hey, don't feel discredited for just this one as, from what I've read here, you have already helped many others. Keep up the good work! Cheers!

---

### Post by chenxiaolong on 2010-08-10
You didn't burst my bubble :D. I sort of expected b43 to not work completely anyway.

Here's a thread about enabling and troubleshooting the Broadcom STA driver: [http://ubuntuforums.org/showthread.php?t=1347483](http://ubuntuforums.org/showthread.php?t=1347483). Just as a side note: the Broadcom STA driver only works with the stock 2.6.32.x kernels.

---

### Post by kelvin.illa on 2010-08-11
> **chenxiaolong said:**
> You didn't burst my bubble :D. I sort of expected b43 to not work completely anyway.

Here's a thread about enabling and troubleshooting the Broadcom STA driver: [http://ubuntuforums.org/showthread.php?t=1347483](http://ubuntuforums.org/showthread.php?t=1347483). Just as a side note: the Broadcom STA driver only works with the stock 2.6.32.x kernels.

Oh my god, man! Oh -- my -- god! STA works!

> **chenxiaolong said:**
> Here: I'll give you the complete steps to make the Broadcom STA driver work.

1. sudo rmmod b43 ssb wl

2. sudo apt-get --purge remove linux-backports-modules-karmic b43-fwcutter bcmwl-kernel-source

3. Open all the files in /etc/modprobe.d/ and make sure that all of these lines AREN'T there:
   blacklist ssb
   blacklist b43
   blacklist wl

4. Open /etc/modules and make sure that these aren't there:
   b43
   ssb
   wl

5. Open /etc/modprobe.d/aliases.conf (if it exists) and make sure "alias wlan0 b43" isn't there.

6. Now remove or rename the b43 folder and the b43-legacy folder (if they exist) in /lib/firmware.

7. Reboot your computer.

8. Install the Broadcom STA driver using Jockey or install the package "bcmwl-kernel-source"

9. Reboot your computer.

Thank you so much! The only thing about STA is that it messes with 'NetworkManager' a little. The icon shows that it's not connected to a wireless network yet clicking on "Connection Information" shows that you are in fact connected. But that's very little compared to b43.

I remember trying out STA when I first installed Ubuntu on the netbook but got turned off by it because of that aesthetic issue. After b43, I never got to having a functional installation of STA. From what I understood from the above tutorial (from you of course), it removes all the previous wireless driver configurations and clutter, bringing it back to the status of a fresh OS install. Brilliant!

Thanks, Xaio.

---

### Post by chenxiaolong on 2010-08-11
You're welcome! Hopefully, it will stay working this time :D.

---

### Post by piratesmack on 2010-08-12
Well, 2.6.35.1 is out
Anybody tried it yet?

I'll probably compile it later tonight.

---

### Post by BobKingsley on 2010-08-12
Hi,

very nice forum and good work here. Ive been reading a lot and now its my time to ask something too XD :D  

I also have the BCM4312 card14e4:4315  rev.1 on a Compaq Mini Netbook.

Well I wanted to know if, once I installed the b43 drivers as described nicely above, the wireless device is shown as wl0 or eth1 ? 

When I installed Ubuntu 10.04 , well when I booted up the live USB, it gave me the two options, and I think I chose the first option bcm43xx or something, and now the device is shown under iwconfig:

```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:178  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```  the STA option is still available when I go to "Hardware Drivers"

As far as Ive read in the STA threat, STA will only give me the eth1 option right?:(

by the way I have kernel 2.6.32-21-generic 

the driver is shown as :  wl     i think

How can I find out which driver I installed?


Greets,

Bob

---

### Post by chenxiaolong on 2010-08-12
BobKingsley: You're correct. B43 names the wireless card 'wlan0' and the Broadcom STA driver names the wireless card 'eth1'

The Broadcom STA driver is 'wl', which is much easier to type when using commands :D.

You can also check which driver you're using by running:

```
[COLOR="SeaGreen"]goudouyaosi[/COLOR]@[COLOR="DarkOrchid"]cxl-d6657k1[/COLOR]:[COLOR="Blue"]~[/COLOR]$ [COLOR="Red"]lshw -C Network[/COLOR]
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:f5:76:51
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.108 firmware=sb v2.17 latency=0 multicast=yes
       resources: irq:30 memory:f8500000-f850ffff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:73:21:c0:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=**b43** driverversion=2.6.34-020634-generic firmware=N/A ip=10.0.0.28 multicast=yes wireless=IEEE 802.11bg

```

---

### Post by BobKingsley on 2010-08-12
Hi, thanks chenxiaolong. Yes seems like im running the wl0 driver hmmm not sure if its the STA driver , dont think so because its still in the Hardware Drivers thingy.  Anyway I want to change it to B43 so the interface shows up as wl0

(Do I have to uninstall the driver first before trying to install B43? If so how do I do that?) :) Umm nevermind Im reading the first post right now the partof the compat drivers ..installing and disabeling the current driver ill give it a try... if something goes wrong ill post it here...

Oh and by the way. 1. do I need the "patch" packet? i think I read about it somewhere in this threat...  and 
2. almost at the end it says

 "Remove the package "[COLOR=SeaGreen]bcmwl-kernel-source[/COLOR]."  It's the easiest way to ensure that the b43 driver isn't blacklisted. "

Do I need to remove it completely with the "purge" command or just remove the packet itself without dependencies and config?

Here is what the command showed:

```
ubuntu@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:38:20:bd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.100 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:feafc000-feafffff

```

HMMM something went wrong through the "make install" ?
```

INSTALL /home/ubuntu/Desktop/compat/compat-wireless-2010-08-11/net/mac80211/mac80211.ko
  INSTALL /home/ubuntu/Desktop/compat/compat-wireless-2010-08-11/net/wireless/cfg80211.ko
  INSTALL /home/ubuntu/Desktop/compat/compat-wireless-2010-08-11/net/wireless/lib80211.ko
  INSTALL /home/ubuntu/Desktop/compat/compat-wireless-2010-08-11/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/ubuntu/Desktop/compat/compat-wireless-2010-08-11/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/ubuntu/Desktop/compat/compat-wireless-2010-08-11/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.32-21-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
Updating Ubuntu's initramfs for 2.6.31-wl under /boot/ ...
Cannot find /lib/modules/2.6.31-wl
Will now run update-grub to ensure grub will find the new initramfs ...
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
make: *** [install-modules] Error 1
```

should I continue or will it cause trouble? (It didnt disconnect me from wireless yet,,,)

---

### Post by chenxiaolong on 2010-08-12
BobKingsley: Whoa! You're reading way too far down :D.

Here are the exact steps you need to do:

1) Remove the Broadcom STA driver and the b43-fwcutter package, if it's installed.

```
sudo apt-get remove b43-fwcutter bcmwl-kernel-source
```

2) Then install the latest b43 firmware.

```
cd ~
mkdir b43-files
cd b43-files
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2
tar xjf b43-fwcutter-013.tar.bz2
cd b43-fwcutter-013
make
cd ..
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

3) Download the 2.6.33.4 or the 2.6.34 kernel from:

[2.6.33.4]
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.4-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.4-lucid/)

[2.6.34]
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

You need to install:

linux-headers-*-<amd64/i386>.deb
linux-headers-*-all.deb
linux-image-*-<amd64/i386>.deb

4) Set b43 to run in PIO mode and turn off QOS.

```
sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf
```

5) Reboot!

Upload speeds and file sharing (through network) will be noticeably slower than the Broadcom STA driver.

---

### Post by BobKingsley on 2010-08-12
Hi, thanks Ill try it .

Just one question you said: 

```
... export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```


what does FIRMWARE_INSTALL_DIR mean? Does it mean the directory I unpack the firmware? 
the: b43-fwcutter-013 directory?

Or do I type it in like that?

---

### Post by chenxiaolong on 2010-08-12
You can just copy and paste the commands.

This line:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
```

sets the variable FIRMWARE_INSTALL_DIR to /lib/firmware, so if FIRMWARE_INSTALL_DIR is mentioned in any other command, it will be interpreted as /lib/firmware.

---

### Post by BobKingsley on 2010-08-12
Hi everything went OK until the last line which returned an error. :( Here is the output:

```
ubuntu@ubuntu:~$ cd b43-files
ubuntu@ubuntu:~/b43-files$ tar xjf b43-fwcutter-013.tar.bz2
ubuntu@ubuntu:~/b43-files$ cd b43-fwcutter-013/
ubuntu@ubuntu:~/b43-files/b43-fwcutter-013$ make
     DEPEND   dep/md5.d
     DEPEND   dep/fwcutter.d
     CC       obj/fwcutter.o
fwcutter.c: In function &#8216;to_be16&#8217;:
fwcutter.c:76: warning: dereferencing type-punned pointer will break strict-aliasing rules
fwcutter.c: In function &#8216;to_be32&#8217;:
fwcutter.c:102: warning: dereferencing type-punned pointer will break strict-aliasing rules
     CC       obj/md5.o
     CC       b43-fwcutter
ubuntu@ubuntu:~/b43-files/b43-fwcutter-013$ cd..
cd..: command not found
ubuntu@ubuntu:~/b43-files/b43-fwcutter-013$ cd
ubuntu@ubuntu:~$ export FIRMWARE_INSTALL_DIR="/lib/firmware"
ubuntu@ubuntu:~$ tar xjf broadcom-wl-4.178.10.4.tar.bz2
ubuntu@ubuntu:~$ cd broadcom-wl-4.178.10.4/linux
ubuntu@ubuntu:~/broadcom-wl-4.178.10.4/linux$ sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
sudo: ../../b43-fwcutter-013/b43-fwcutter: command not found

```


btw.. removing the bcmwl-kernel-source put an error at the end: does it have to do with that?

```
 ubuntu@ubuntu:~$ sudo apt-get remove b43-fwcutter bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package b43-fwcutter is not installed, so not removed
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 269 not upgraded.
2 not fully installed or removed.
After this operation, 2,589kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131067 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing bcmwl-kernel-source (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by chenxiaolong on 2010-08-12
When you run these commands, make sure you stay in the b43-fwcutter-013 folder. Don't run the commands highlighted in red. A copy and paste of the list of commands from my previous post should work.

```
...
[COLOR="Red"]ubuntu@ubuntu:~/b43-files/b43-fwcutter-013$ cd..
cd..: command not found
ubuntu@ubuntu:~/b43-files/b43-fwcutter-013$ cd[/COLOR]
ubuntu@ubuntu:~$ export FIRMWARE_INSTALL_DIR="/lib/firmware"
ubuntu@ubuntu:~$ tar xjf broadcom-wl-4.178.10.4.tar.bz2
ubuntu@ubuntu:~$ cd broadcom-wl-4.178.10.4/linux
ubuntu@ubuntu:~/broadcom-wl-4.178.10.4/linux$ sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
sudo: ../../b43-fwcutter-013/b43-fwcutter: command not found
```

About the other error:

Are you running the liveCD? If you are, then there isn't a way to get b43 working correctly. If Ubuntu is installed, run "ls -l /" and make sure that the vmlinuz file isn't highlighted in red.

---

### Post by BobKingsley on 2010-08-12
Ok Ill try it and report here . :)


Ehhm  its a Live USB with persistent 2 GB "caspr" Memory

I did the command to check if its red .... 

```
lrwxrwxrwx   1 root root    30 2010-04-29 12:26 vmlinuz -> boot/vmlinuz-2.6.32-21-generic

```IT IS ...  :(


is that a problem?



I did the firmware installation steps until the end  and it said extracting. no errors.
```
ubuntu@ubuntu:~/b43-files/broadcom-wl-4.178.10.4/linux$ sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
This file is recognised as:
  ID         :  FW15
  filename   :  wl_apsta.o
  version    :  478.104
  MD5        :  bb8537e3204a1ea5903fe3e66b5e2763
Extracting b43/ucode5.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/ucode13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/ucode14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/ucode16.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/n0initvals16.fw
Extracting b43/lp0initvals16.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/lp0bsinitvals16.fw
ubuntu@ubuntu:~/b43-files/broadcom-wl-4.178.10.4/linux$ 
```and now I install the kernel? then set the b43 to run in PIO mode and turn off the QOS thingy?

I tried installing the kernel things first installed the headers  was all ok and then installed the image at the end gave me an error:

```
ubuntu@ubuntu:~/Desktop/b43files$ sudo dpkg -i linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
Selecting previously deselected package linux-image-2.6.34-020634-generic.
(Reading database ... 149870 files and directories currently installed.)
Unpacking linux-image-2.6.34-020634-generic (from linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb) ...
Done.
dpkg: dependency problems prevent configuration of linux-image-2.6.34-020634-generic:
 linux-image-2.6.34-020634-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-2.6.34-020634-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.34-020634-generic
ubuntu@ubuntu:~/Desktop/b43files$ 

```any ideas?

Do i have to activate it or something? or do something it will load it on next boot?  

about the error do i have to worry about it or can i ignore it?   i mean the other error when u asked me if i had a a liveCD

--------

Update:  I did the process and installed the kernel with the error, then I did the last commands you told me.  
```

sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf
```

and then some error came up something with modprobe  HMM (i know im an idiot haha should have saved the output) :(   but anyway ..

I rebooted and then it was a bit slow and the network manager in the corner showed disconnected  on wireless.  But driver seems to be b43 now but doesnt show any networks there. I did the iwconfig and showed essid: any not set or something. (Im on Windows now thats why i cant post the output but I will as soon as I get back home.

btw the uname -r  said still kernel 2.6.32   and not 2.6.34 as (tried) to install before the reboot.

Now iwconfig however shows wlan0 instead of eth1


Will get back to this when im back home on monday and see if I (or we :) ) can get this to work.

Greets and nice weekend to all,

Bob

---

### Post by chenxiaolong on 2010-08-12
When you installed the kernel, it said the package "initramfs-tools" is missing:

```
ubuntu@ubuntu:~/Desktop/b43files$ sudo dpkg -i linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
Selecting previously deselected package linux-image-2.6.34-020634-generic.
(Reading database ... 149870 files and directories currently installed.)
Unpacking linux-image-2.6.34-020634-generic (from linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb) ...
Done.
dpkg: dependency problems prevent configuration of linux-image-2.6.34-020634-generic:
 linux-image-2.6.34-020634-generic depends on **[COLOR="Red"]initramfs-tools[/COLOR]** (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-2.6.34-020634-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.34-020634-generic
ubuntu@ubuntu:~/Desktop/b43files$
```

so, you have to install that package with apt-get:

```
sudo apt-get install initramfs-tools
```

Then, kernel 2.6.34 should show up in your boot menu.

All the other commands seemed to have worked. 

One more thing: Instead of removing the Broadcom STA driver (which didn't work), you can open the file /etc/modprobe.d/blacklist-bcm43.conf:

```
sudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```

and change it to:

> # Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
#blacklist b43
#blacklist b43legacy
#blacklist ssb
#blacklist bcm43xx
blacklist wl

That will stop the Broadcom STA driver from being loaded. Any line that starts with "#" is skipped.

Hopefully that'll work. I've never used a live USB before, so I'm not too familiar with how certain things work :(.

---

### Post by Mike_tn on 2010-08-16
This was my final fix. I was so thrilled, thanks so much to chenxiaolong!

 [COLOR=#ff0000][COLOR=Black]I started with Wubi install of Ubuntu 10.04 on a Windows Dell Inspiron 1564 laptop. 
Dell Wireless 1397 WLAN Mini-Card (BCM4312)

Previously experimented with Wget, the b43 cutter, and lots of other web surfing & reading 
but that was not enough.I needed the b43 firmware to get the b43 firmware! grrr

So I used the firmware zip file you shared instead 
because I only had a Windows wireless connection. Woo Hoo! 
Even happy when it only worked for 1 minute at first.

installed the i386 of v2.6.34 ("all deb" had to install first due to dependencies)
fixed up the PIO and QOS as told.

Genius! off and running finally.  You made my week...month even.

One issue. Maybe this was mentioned but I didn't read all of the 50+ pages of forum here. Once online it wanted to add about 250 installs including an older version of the kernel than the one you told me about. I allowed only security updates, no recommended ones, and unchecked half a dozen kernel updates which were only updating to v 2.6.32XX. I hope the updater doesn't keep trying that one. Can I tell it to look at my installs better? Do you think many of the recommended ~200 install updates I didn't allow are worthy ones? Anyway, that install decision may blast a newbie as soon as he gets your fix going so I thought it was important.
:D
[/COLOR] [/COLOR]

---

### Post by chenxiaolong on 2010-08-16
Mike_tn: First of all, welcome to Ubuntu Forums! I'm happy you got your wireless working. 

You can safely install all the upgrades, including the older kernel. It will not remove the newer kernel 2.6.34 and won't affect it in any way. The updated older kernel (if that makes sense) will be below the 2.6.34 kernel on the boot menu. 

So, upgrade away :D!

---

### Post by Mike_tn on 2010-08-16
**chenxiaolong**: It was nice to get a quick reply.  And I appreciate your time!  Perhaps you have time because it's summer? You know a lot for a young man.
This Linux OS is the fastest bootup in the land! Makes Windows 7 load time a bit silly.   Also I read about PIO and QOS, and since I don't stream through the web it should be fine.  I don't notice any intolerable slowness.  Also read that PIO has uses. Teaches patience maybe too :) 
My one last thought was on doing downloads. It was suggested to use a download manager to get the Ubuntu ISO, which I did, and put it in the folder with Wubi for install with Windows.  If such a large and important download is done through the b43 driver with QOS turned off, could there be issues?I only read references to streaming voice, video etc. taking a negative hit without QOS. But bit/rate seemed close conceptually to what download managers watch in order to get smooth flow of the package so nothing is corrupted. What goes on with clear streaming information signals is probably not identical to the flow of uncorrupted packages but I'm not sure. Any thoughts on the ability of doing large uncorrupted downloads with b43?

---

### Post by chenxiaolong on 2010-08-16
Mike_tn: It is my summer break right now, although it's about to be over :(.

I'm pretty sure QOS just throttles certain internet applications to make more important ones go faster. Most streaming applications require most of your bandwidth, which is where QOS is useful. I've never experienced any slowdowns due to QOS being off (disregarding the PIO speed decrease). I can generally get a 1.2 mbytes/s consistent download speed without any b43 problems--close to what I get with the Broadcom STA driver. I've also had no file corruptions in my downloads (or if there were, my download manager fixed them :D).

I can see what you're saying, but I've never had any problems.

---

### Post by kelvin.illa on 2010-08-17
This is just a follow-up to chenxiaolong's tutotrial and some more.

> Originally Posted by chenxiaolong  
Here: I'll give you the complete steps to make the Broadcom STA driver work.

1. sudo rmmod b43 ssb wl

[INDENT][/INDENT]2.* sudo apt-get --purge remove b43-fwcutter bcmwl-kernel-source

> 3. Open all the files in /etc/modprobe.d/ and make sure that all of these lines AREN'T there:
blacklist ssb
blacklist b43
blacklist wl

4. Open /etc/modules and make sure that these aren't there:
b43
ssb
wl

5. Open /etc/modprobe.d/aliases.conf (if it exists) and make sure "alias wlan0 b43" isn't there.

6. Now remove or rename the b43 folder and the b43-legacy folder (if they exist) in /lib/firmware.

7. Reboot your computer.

8. Install the Broadcom STA driver using Jockey or install the package "bcmwl-kernel-source"

9. Reboot your computer.

*it was originally "sudo apt-get --purge remove linux-backports-modules-karmic b43-fwcutter bcmwl-kernel-source" back when in Karmic. This won't work in Lucid so omit "linux-backports-modules-karmic", otherwise purging won't proceed.

So you resulted to using Broadcom STA instead of b43 because b43 is crap but you find out that STA messes up nm-applet. If you don't know what I'm talking about about STA messing up nm-applet, then you're good; if you do, then continue. Here's the fix from [lauchpad]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/574270"):

> yodaliu wrote on 2010-08-11:	 #17
I added NetworkManager daily trunk builds PPA to my system and upgrade.
The connection satus is correct now.

[https://launchpad.net/~network-manager/+archive/trunk]("https://launchpad.net/~network-manager/+archive/trunk")

Your wi-fi should work perfectly now.

---

### Post by BobKingsley on 2010-08-17
Hi,

I did the apt/get for the tools and it tells me:

```
ubuntu@ubuntu:~$ sudo apt-get install initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
initramfs-tools is already the newest version.
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 269 not upgraded.
3 not fully installed or removed.
(Reading database ... 153319 files and directories currently installed.)
Removing bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing bcmwl-kernel-source (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```will try that and then reboot and see if it works,  should I try installing the other image package again, that gave the initramfs-tools error?

tried installing the tools package it said newest version is already installed   hmm but problems removing bcmwl-kernel-source

by the way, whats strange is that at bootup its all white the layout and the network manager has a different icon, and its stuck loading and then after a minute or so it loads up but goes back to the black layout..  could it be related to the kernel update?

it also says in the network manager on top: "Wireless: wireless disabled"

How can I enable it? :S

I did the "changes" to blacklist-cm43.config   but the file was empty,  is that good or bad? xd :D   I added the things you told me  now lets see if it works.. Ill reboot...

... nothing changed still the same  wireless disabled and kernel still shows uname -r : 2.6.32-21

lshw  shows:
```

*-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: c4:17:fe:38:20:bd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.32-21-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg 
```ifconfig doesnt list wlan0   :(


HMM dmesg showed the following:
```

[   54.454784] Compat-wireless backport release: compat-wireless-2010-08-03-4-g7746bc0
[   54.454795] Backport based on linux-next.git next-20100811
[   54.604744] Linux video capture interface: v2.00
[   54.792110] uvcvideo: Found UVC 1.00 device HP Webcam-50 (10f1:1a13)
[   54.826512] input: HP Webcam-50 as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input7
[   54.826680] usbcore: registered new interface driver uvcvideo
[   54.826690] USB Video Class driver (v0.1.0)
[   54.934790] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   54.934821] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[   55.004184] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[   55.004213] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243
......
[   55.393490] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.700306] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
.....
[   55.854017] phy0: Selected rate control algorithm 'minstrel'
[   55.856283] Registered led device: b43-phy0::tx
[   55.856344] Registered led device: b43-phy0::rx
[   55.856402] Registered led device: b43-phy0::radio
[   55.856580] Broadcom 43xx driver loaded [ Features: PMNLS, Firmware-ID: FW13 
.....
[  177.816361] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[  177.816386] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[  177.816406] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  177.821166] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  188.068120] eth0: no IPv6 routers present
[  299.816364] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[  299.816383] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[  299.816396] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
.....
[  537.989151] ------------[ cut here ]------------
[  537.989181] WARNING: at /build/buildd/linux-2.6.32/net/sched/sch_generic.c:261 dev_watchdog+0x1fe/0x210()
[  537.989194] Hardware name: Compaq Mini CQ10-100
[  537.989204] NETDEV WATCHDOG: eth0 (atl1c): transmit queue 0 timed out
[  537.989213] Modules linked in: binfmt_misc ppdev lp parport dm_crypt snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm arc4 snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi joydev b43 snd_seq_midi_event mac80211 snd_seq cfg80211 snd_timer snd_seq_device led_class compat_firmware_class snd ssb uvcvideo pcmcia psmouse soundcore videodev compat serio_raw v4l1_compat snd_page_alloc pcmcia_core atl1c squashfs aufs nls_iso8859_1 nls_cp437 vfat fat dm_raid45 xor fbcon tileblit font bitblit softcursor vga16fb vgastate i915 drm_kms_helper drm i2c_algo_bit intel_agp video ahci output agpgart usb_storage
[  537.989421] Pid: 0, comm: swapper Not tainted 2.6.32-21-generic #32-Ubuntu
.....
[ 5418.000384] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 5418.000398] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 5418.000409] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```Havent I went to the website, but it explains the steps zou explained to me with fwcutter doesnt it? i have already done this with fwcutter and the firmwarebefore or?  HMMM

since its saying "correct firmware for the driver" and "b43/ucode15.fw"  maybe its the broadcom diver 4.15.... and not 4.178... 

also, it seemed to have loaded the Bcm 43xx driver    hmm

any ideas?

---

### Post by JanusDC on 2010-08-28
> **kelvin.illa said:**
> So you resulted to using Broadcom STA instead of b43 because b43 is crap but you find out that STA messes up nm-applet. If you don't know what I'm talking about about STA messing up nm-applet, then you're good; if you do, then continue. Here's the fix from [lauchpad]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/574270"):
> yodaliu wrote on 2010-08-11:	 #17
I added NetworkManager daily trunk builds PPA to my system and upgrade.
The connection satus is correct now.

[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)
Your wi-fi should work perfectly now.

You are my hero =D>

---

### Post by dened on 2010-08-30
Hello,

I want to share my experience with you. I don't have Ubuntu, still using Slackware 13.1 But, sometimes ago I bought Dell Vostro V13 laptop with bcm4312 14e4:4315 inside. Only one thing didn't work - aircrack. Everytime after 10-300 sec. airodump-ng was being frozen. Only reloading of module helped me. I tried many kernels and 3 distros, but without any effect.
Day ago I loaded my kernel with: acpi=off noapic vga=normal options and it worked! Also works now on 2.6.33.4 Slackware kernel.
I use b43 module.

---

### Post by kelvin.illa on 2010-09-06
> **kelvin.illa said:**
> This is just a follow-up to chenxiaolong's tutotrial and some more.



[INDENT][/INDENT]2.* sudo apt-get --purge remove b43-fwcutter bcmwl-kernel-source



*it was originally "sudo apt-get --purge remove linux-backports-modules-karmic b43-fwcutter bcmwl-kernel-source" back when in Karmic. This won't work in Lucid so omit "linux-backports-modules-karmic", otherwise purging won't proceed.

So you resulted to using Broadcom STA instead of b43 because b43 is crap but you find out that STA messes up nm-applet. If you don't know what I'm talking about about STA messing up nm-applet, then you're good; if you do, then continue. Here's the fix from [lauchpad]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/574270"):



Your wi-fi should work perfectly now.

> **JanusDC said:**
> You are my hero =D>

I appreciate that.

I merely put two different pages together in case someone else stumbles upon this problem -- it took me a hell lot of googling though. I hope this post has made your googling efforts less burdensome.

---

### Post by buster_oz on 2010-09-08
> **kelvin.illa said:**
> This is just a follow-up to chenxiaolong's tutotrial and some more.


2.* sudo apt-get --purge remove b43-fwcutter bcmwl-kernel-source



*it was originally "sudo apt-get --purge remove linux-backports-modules-karmic b43-fwcutter bcmwl-kernel-source" back when in Karmic. This won't work in Lucid so omit "linux-backports-modules-karmic", otherwise purging won't proceed.

So you resulted to using Broadcom STA instead of b43 because b43 is crap but you find out that STA messes up nm-applet. If you don't know what I'm talking about about STA messing up nm-applet, then you're good; if you do, then continue. Here's the fix from [lauchpad]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/574270"):



Your wi-fi should work perfectly now.


sir kelvin
im new in linux Ubuntu 10.04 LTS..
at first in my Hardware Drivers, only Broadcom STA and the graphics driver is display.. when i type iwconfig it gave a result:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:216  Noise level:165
          Rx invalid nwid:0  invalid crypt:90  invalid misc:0

pan0      no wireless extensions

and as i followed your instructions , rebooted and when i open back Hardware drivers, it displays the B43 driver which i Activated and give a result in iwconfig ... 

wlan0 with the correct SSID of my router. which is what i wanted to have.

the thing is it keeps on disconnecting and after some time it wont be able to connect to the router and when it does it doesnt have an internet connection. so i Activated the Broadcom STA driver and it automatically disabled the B43 driver and after reboot, open my Hardware driver and it no longer have the B43 driver on the list.

question is, if i may,  how can i make B43 driver back on the list of Hardware drivers and use it with stability so that my card will be able to be in monitor mode.??

thank you sir in advance..
im from philippines also.. ):P

---

### Post by max! on 2010-09-09
Hello,
So I'm new to this forum and kind of new to ubuntu. This question is partly about the b43 drivers and partly about aircrack.
I  followed all of your steps to install the b43 drivers and everything  worked perfectly! I was having some weird issues with connecting and  disconnecting and then i upgraded the kernel and everything seems to be  working great.
However, when I follow any of the steps to start aircrack, I seem to have issues. Here's more or less what happens:

```

root@max-laptop:/aircrack_source/aircrack-ng# ifconfig wlan0 down
root@max-laptop:/aircrack_source/aircrack-ng# iwconfig wlan0 mode monitor
root@max-laptop:/aircrack_source/aircrack-ng# ifconfig wlan0 up
root@max-laptop:/aircrack_source/aircrack-ng# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Monitor  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
root@max-laptop:/aircrack_source/aircrack-ng# airmon-ng start wlan0


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
5703    avahi-daemon
5704    avahi-daemon
6890    NetworkManager
6894    wpa_supplicant


Interface    Chipset        Driver

wlan0        Broadcom    b43 - [phy12]
                (monitor mode enabled on mon0)

root@max-laptop:/aircrack_source/aircrack-ng# airmon-ng check kill


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
5703    avahi-daemon
5704    avahi-daemon
6890    NetworkManager
6894    wpa_supplicant
Killing all those processes...
root@max-laptop:/aircrack_source/aircrack-ng# aireplay-ng --test mon0
23:08:57  Trying broadcast probe requests...
23:08:57  Injection is working!
23:08:59  Found 4 APs

23:08:59  Trying directed probe requests...
23:08:59  <bssid> - channel: 11 - <essid>
23:09:02  Ping (min/avg/max): 2.007ms/58.786ms/80.522ms Power: -70.06
23:09:02  18/30:  60%

23:09:02  <bssid> - channel: 11 - <essid>
23:09:08   0/30:   0%

23:09:08  <bssid> - channel: 11 - <essid>
23:09:14   0/30:   0%

23:09:14  <bssid> - channel: 11 - <essid>
23:09:20   0/30:   0%


```It  seems to be working fine for 10 or so seconds and then quickly  fails--you can see that by how it gets the first 17/17 and then  basically goes 0/120.  Also, my connection goes down and I have to reset  the b43 drivers......... 
So more or less this happens every time i  use any of the aircrack tools. Any thoughts as to what might be going  on? I followed the instructions for acquiring the correct version of the  aircrack tools but no change. This was working fine on my system just a  few days ago and i honestly cannot figure out what might have  changed.........
Thanks!

EDIT:
--Nevermind, I just used the SECmic distribution instead. It works great right out of the box/flash drive.
Thanks!

---

### Post by rlelliott on 2010-09-14
Glad to see it worked for you! SECmic3.1 will be available in the coming days @ [http://secmic.org]("http://secmic.org") based on Kubuntu 10.04.1 / KDE 4.5.1

b43 / wl hybrid compatibility is included with module launchers located on the desktop for your choosing after login.

---

### Post by iamgeniusrnti on 2010-09-15
> **chenxiaolong said:**
> [COLOR=Green]2010-05-23: B43 works out of the box with the 14e4:4315 card in Ubuntu 10.04 LTS with PIO mode on and QOS off (on kernel 2.6.33.4 or 2.6.34).[/COLOR]

So, basically, this is how to get it working:

Download the 2.6.33.4 or the 2.6.34 kernel from: 

[2.6.33.4]
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.4-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33.4-lucid/")

[2.6.34]
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/")

You need to install:

linux-headers-*-<amd64/i386>.deb
linux-headers-*-all.deb
linux-image-*-<amd64/i386>.deb

and then run:

```
sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf
```and reboot and that's it :D.


I hope this worked for you. It worked for me. 

By the way, I'm turning 14 on September 26, so wish me a happy birthday :)

Firstly Happy Birthday... secondly, I ran these steps on my Acer one D250 which the Gods of Ubuntu said worked out of box and I still have no wireless:S  

I feel like a fat kid who just found out there's no such thing as a cupcake.  Now my wife is mad at me because I just blew an hour of my time and I'm still slaved to a stupid CAT5.

lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

The wired Lan works perfectly, but it doesn't even offer me a chance to do wireless LAN-why?  Ubuntu says it's right there!

I'm so frustrated... what am I doing wrong?

---

### Post by rlelliott on 2010-09-15
> **iamgeniusrnti said:**
> Firstly Happy Birthday... secondly, I ran these steps on my Acer one D250 which the Gods of Ubuntu said worked out of box and I still have no wireless:S  

I feel like a fat kid who just found out there's no such thing as a cupcake.  Now my wife is mad at me because I just blew an hour of my time and I'm still slaved to a stupid CAT5.

lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

The wired Lan works perfectly, but it doesn't even offer me a chance to do wireless LAN-why?  Ubuntu says it's right there!

I'm so frustrated... what am I doing wrong?

The method used in SECmic3.1 is to install the wl dkms module, let it load at boot, cut the firmware for the b43 module, Then load b43 after the wl module has loaded, also we could not get the knetwork-manager to work with it, so we opted to uninstall it and go with wicd. If you are only interested in connectivity and don't need monitor mode, the wl module should suffice. My findings suggest that the b43 module offers a better connection.

---

### Post by iamgeniusrnti on 2010-09-15
> **rlelliott said:**
> The method used in SECmic3.1 is to install the wl dkms module, let it load at boot, cut the firmware for the b43 module, Then load b43 after the wl module has loaded, also we could not get the knetwork-manager to work with it, so we opted to uninstall it and go with wicd. If you are only interested in connectivity and don't need monitor mode, the wl module should suffice. My findings suggest that the b43 module offers a better connection.

I don't understand... I don't know what I'm supposed to do.  I tried activating the broadcom driver and it says it's activated but not in use.  I would desperately like to use it right?  Why won't it work?  What am I doing wrong?  Wicd says there are no wireless networks...

Here is uname -r 2.6.32-24-generic

Here is ls -l /
drwxr-xr-x   3 root root  4096 2010-09-15 22:24 boot
drwxr-xr-x   2 root root  4096 2010-09-15 19:21 cdrom
drwxr-xr-x  18 root root  3720 2010-09-15 22:23 dev
drwxr-xr-x 172 root root 12288 2010-09-15 22:23 etc
drwxr-xr-x   4 root root  4096 2010-09-15 19:22 home
lrwxrwxrwx   1 root root    33 2010-09-15 20:49 initrd.img -> boot/initrd.img-2.6.32-24-generic
drwxr-xr-x  24 root root 12288 2010-09-15 20:43 lib
drwx------   2 root root 16384 2010-09-15 19:03 lost+found
drwxr-xr-x   2 root root  4096 2010-05-14 13:27 media
drwxr-xr-x   2 root root  4096 2010-04-23 06:11 mnt
drwxr-xr-x   2 root root  4096 2010-04-29 08:17 opt
dr-xr-xr-x 187 root root     0 2010-09-15 18:04 proc
drwx------  12 root root  4096 2010-09-15 22:10 root
drwxr-xr-x   2 root root 12288 2010-09-15 20:57 sbin
drwxr-xr-x   2 root root  4096 2009-12-05 16:55 selinux
drwxr-xr-x   3 root root  4096 2010-04-29 16:54 srv
drwxr-xr-x  12 root root     0 2010-09-15 18:04 sys
drwxrwxrwt  14 root root  4096 2010-09-15 22:25 tmp
drwxr-xr-x  12 root root  4096 2010-04-29 16:50 usr
drwxr-xr-x  15 root root  4096 2010-04-29 08:26 var
lrwxrwxrwx   1 root root    30 2010-09-15 20:49 vmlinuz -> boot/vmlinuz-2.6.32-24-generic

lspci:
samantha@samantha-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

---

### Post by rlelliott on 2010-09-15
I installed the wl dkms with

```
sudo apt-get install bcmwl-kernel-source
```

I then installed the firmware with 

```
sudo apt-get install b43-fwcutter
```

After reboot, load the b43 module with

```
sudo modprobe b43
```

open wicd goto preferences and change the wireless interface from "eth1" to "wlan0"

eth1 is the interface the wl module uses

wlan0 is the interface the b43 module uses

also more info about the wl dkms can be found @ [http://packages.ubuntu.com/lucid/bcmwl-kernel-source]("http://packages.ubuntu.com/lucid/bcmwl-kernel-source")

more info about the b43 module can be found @ [http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43")

You must allow the wl dkms module to load first if you want the b43 module to load without errors. Hope this helps you. If not you could download secmic-3.1-desktop-i386 @ [http://secmic.org]("http://secmic.org") tomorrow and have it working out of the box!

---

### Post by iamgeniusrnti on 2010-09-15
THANK YOU!  Finally got it up and running!  

That cleared up a lot.  BTW the bmc kernel thing wouldn't install under [v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/").  I wound up using 2.6.33.4 instead.  So I assume after every reboot I have to use the modprobe command?  Can I add it to the rc.local like this:
 
modprobe -r b43 sleep 3 modprobe b43

---

### Post by rlelliott on 2010-09-15
> **iamgeniusrnti said:**
> THANK YOU!  Finally got it up and running!  

That cleared up a lot.  BTW the bmc kernel thing wouldn't install under [v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/").  I wound up using 2.6.33.4 instead.  So I assume after every reboot I have to use the modprobe command?  Can I add it to the rc.local like this:
 
modprobe -r b43 sleep 3 modprobe b43

The method i posted is for the kernel that come with 10.04.
If you are using this method of loading b43 with that kernel you must modprobe it each time after login.

Im not sure about the 2.6.33.4 kernel.

I made a script called "load-b43.sh" to do the work. Then created a desktop launcher enabled execute and open in term.

**load-b43.sh**

```

#!/bin/sh
sudo ifconfig eth1 up
sudo sleep 2
sudo rmmod wl
sudo sleep 4
sudo modprobe b43
sudo sleep 4

```

**load-wl.sh**

```
#!/bin/sh
rmmod lib80211_crypt_tkip
rmmod wl
rmmod lib80211
sleep 4
modprobe wl

```


*EDIT*:

secmic-3.1-desktop-i386 will be released today @ noon. Are you ready to pentest with the most up-to-date security distro on the planet?

Thanks go out to Brian for his continued support, ideas and rigorous testing, also Chenxiaolong for his efforts in packaging SECmic's tools and unknowingly helping us figure out how to get b43 working under the shipped kernel. With out these people especially Brian, none of what we have created would be possible. Secure your connected world... ;D

---

### Post by iamgeniusrnti on 2010-09-16
> **rlelliott said:**
> The method i posted is for the kernel that come with 10.04.
If you are using this method of loading b43 with that kernel you must modprobe it each time after login.
 
Im not sure about the 2.6.33.4 kernel.
 
I made a script called "load-b43.sh" to do the work. Then created a desktop launcher enabled execute and open in term.
 
**load-b43.sh**
 
```

#!/bin/sh
sudo ifconfig eth1 up
sudo sleep 2
sudo rmmod wl
sudo sleep 4
sudo modprobe b43
sudo sleep 4

```
 
**load-wl.sh**
 
```
#!/bin/sh
rmmod lib80211_crypt_tkip
rmmod wl
rmmod lib80211
sleep 4
modprobe wl

```
 
 
*EDIT*:
 
secmic-3.1-desktop-i386 will be released today @ noon. Are you ready to pentest with the most up-to-date security distro on the planet?
 
Thanks go out to Brian for his continued support, ideas and rigorous testing, also Chenxiaolong for his efforts in packaging SECmic's tools and unknowingly helping us figure out how to get b43 working under the shipped kernel. With out these people especially Brian, none of what we have created would be possible. Secure your connected world... ;D
 
This weekend I will toss it on a thumb drive and check it out.  But this is for my wife's netbook...
 
With my current set up all I need to do is sudo modprobe b43 and lights right up.  What I need to do is figure out how to get it to automatically modprobe late without having to manually run that command.

---

### Post by iamgeniusrnti on 2010-09-17
OK got it.  All I did was build a simple script:

#!/bin/sh
sudo modprobe b43

Then saved it in /etc/init.d/

Then ran this command:

sudo update-rc.d .network-launcher.sh defaults

Problem solved:)

---

### Post by rlelliott on 2010-09-27
Happy bday Chen :P.

---

### Post by chenxiaolong on 2010-09-27
Thanks, rlelliott :D!

---

### Post by lethalfang on 2010-10-10
I just installed Ubuntu 10.04.1 on my HP laptop, and run into this dreaded 14e4:4315 problem. Yep, no wireless connection. 

I've searched around the web and came across this thread. I was reading the first post which has a set of instruction, the first of which is to download and install:
linux-headers-2.6.33-02063304-generic_2.6.33-02063304_amd64.deb

But I don't seem to have all the dependencies to install this. How do I install all the dependencies first?

By the way, which I try to get the b43 driver to work or STA?

Thanks in advance.

---

### Post by piratesmack on 2010-10-10
Downloaded Ubuntu 10.10 this morning, ran it live, copied the b43 firmware from my Slackware install, and... No more DMA errors? :)

```

$ dmesg | grep b43
[    7.317587] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.317657] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   35.939961] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   36.345269] Registered led device: b43-phy0::tx
[   36.345340] Registered led device: b43-phy0::rx
[   36.345409] Registered led device: b43-phy0::radio
[   36.738831] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   36.738845] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   36.738856] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  116.985287] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)

```

Connects to my router almost instantly, too. 
Broadcom STA didn't do that.

Has anybody else given it a try?

edit:
nevermind, after a while a DMA error appeared
```

[ 1344.212852] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1344.212881] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[ 1344.212897] b43-phy0: Controller RESET (DMA error) ...
[ 1344.444296] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[ 1349.969288] b43-phy0: Controller restarted

```

At least you don't need to create the b43.conf thing anymore.

---

### Post by lethalfang on 2010-10-14
I did the fix on 10.10, which has finally allowed the wireless card to work, but the performance is nevertheless quite weak. 
Every so often, the connection would drop. File transfer via SSH guarantees that connection will be killed. Every time the connection is killed, I must restart network-manager to re-connect. 

This really is a miserable piece of hardware made by Broadcom! :icon_frown:

---

### Post by element23 on 2010-10-16
I'm running 10.10 on a Gateway 7330gz with Broadcom BCM4306/3 network card. Connection keeps dropping and often will not connect at all. The B43 drivers worked fine on 9.10, but I guess that went out the window. Is there any chance at all that some sort of update will occur to fix the problem everyone here is having?:confused:

---

### Post by monochromec on 2010-10-19
Finally got it working on a brand-new install of 10.10 after just too many hours of trial and error :-). For the greater parish, here's the info: standard Dell Vostro 1320 (core duo T6600 with BCM 4312 rev 01, with our beloved PCI ID 14e4:4315, Phoenix BIOS rev A08 - latest from the Dell website). 

Initially I tried the STA driver mentioned in earlier posts as well as the standard approach suggested with the original FW from broadcom (4.150.10.5) for the B43 module, both solutions did not work on this baby. After checking the syslog, I noticed strange DMA errors ocurring with B43 driver as already pointed out earlier in this thread. Almost on the edge of getting the development environment ready for a custom kernel-compile, I did more research only to find out that the existing version of the driver falls back into PIO mode if DMA errors keep ocurring (something that's missing from the logs BTW!). 

The solution for this particular type of h/w was actually going for a different version of the firmware as outlined in [wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43"). The version you're looking for is 4.178.10.4. Once you've followed the instructions and installed the low-power firmware with fw-cutter, the interface works after a suitable reboot.

This eliminates the need for going for any ndiswrapper business... (if this is possible at all for this wireless card?)

---

### Post by cucu007 on 2010-11-12
> **rlelliott said:**
> On a Lenovo G550 R6U, after putting notebook in hibernation, when it came back up, dmesg shows that the the card is having dma errors. I powered down the machine. After sitting for about 20 seconds, powered on the machine. I rmmod wl, then modprobe b43. No DMA errors. I have not tried to load b43 without first loading the wl driver. Has anyone tested this?


My advise to you is switch the minipci adapter for another one. I can help you switch it if you want, drop me a PM if interested. I am running this machine flawlessly now using an intel miniPCI

---

### Post by saipu on 2010-11-27
Has anybody try this out?
[http://wiki.frugalware.org/index.php/B43_with_open_source_firmware](http://wiki.frugalware.org/index.php/B43_with_open_source_firmware)

---

### Post by saipu on 2010-11-27
> **saipu said:**
> Has anybody try this out?
[http://wiki.frugalware.org/index.php/B43_with_open_source_firmware](http://wiki.frugalware.org/index.php/B43_with_open_source_firmware)

Latest OpenFWWF:
[http://www.cs.umd.edu/projects/maranello/](http://www.cs.umd.edu/projects/maranello/)

---

### Post by monochromec on 2010-12-01
The success was a short one as the device switched over to working on an on-and-off basis only more and more frequently. I finally managed to track it down to a bug in the intersection of the 2.6.35-23 kernel that comes out of the box with 10.10, the module dell_laptop in charge of the hardware wifi switch (aka the wfkillswitch) and the driver I installed as described in my earlier post.

After numerous cul-de-sacs I went down including downgrading to 2.6.3x and 2.6.2x kernels, different broadcom drivers including an ndiswrapper alternative, here's a solution that finally worked for me: a complete re-install of 9.10, automatic upgrade to 10.04 LTS and then a manual upgrade to 10.10 (as this was not LTS at the time of installation yet - see [www.ubuntu.com/desktop/get-ubuntu/upgrade]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade") for details). When installing 9.10, I chose the STA driver via the Administration->Additional Driver menu option, confirming that it worked OK with the kill switch on the kernel that came with 9.10 (2.6.31-22). Keeping the kernel to 2.6.35-22 across the upgrade to 10.10 worked for me and I haven't encountered any of the mentioned problems in this LOOOONG thread so far. I hope that finally the kernels guys will eliminate this bug in a future release - or maybe this open source firmware will do the trick?

---

### Post by zdenal on 2010-12-02
This Broadcom card is supported by wl driver on Lucid Mavarick and above. 

But it has problems due improper modules load.

Try these steps:

[http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii](http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii)

to get working wireless for the Broadcom Cards with wl driver. b43 is obsolete for many hardware now...

---

### Post by rild on 2010-12-04
> **zdenal said:**
> This Broadcom card is supported by wl driver on Lucid Mavarick and above. 

But it has problems due improper modules load.

Try these steps:

[http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii](http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii)

to get working wireless for the Broadcom Cards with wl driver. b43 is obsolete for many hardware now...
I've tried, but it doesn't work for me. The solution that works for me is to use b43 driver install instructions from [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers")  and to force b43 module to use PIO mode instead of DMA. It is described [here]("http://blog.foxxtrot.net/2010/05/broadcom-b43-drivers-on-ubuntu.html").

---

### Post by elect on 2010-12-07
> **chenxiaolong said:**
> [COLOR="Green"]2010-05-23: B43 works out of the box with the 14e4:4315 card in Ubuntu 10.04 LTS with PIO mode on and QOS off (on kernel 2.6.33.4 or 2.6.34).[/COLOR]



And what about compact-wireless and blacklisting wl/bcm43xx, etc..?

---

### Post by rild on 2010-12-13
> **elect said:**
> And what about compact-wireless and blacklisting wl/bcm43xx, etc..?
I've made a lot of attempts. Before to made this one I've tried to clean the mess from the previous failures. After that I've just followed the instructions from the two links provided in my post above and ... everything works fine in 10.10

---

### Post by teklife on 2010-12-16
hello everybody. new to linux and loving it. terminal tells me i have this wireless card: 

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

i would like to use aircrack, and although the instructions on the first page seem detailed enough, i'm wondering how much has changed since it was written, as my kernel is the latest (2.6.35-24). 

my biggest concern is messing up my wireless card by not blacklisting wl, as mentioned in the beginning of this thread. is this still necessary to do?  and if so, how do i do it? i've googled for it, but i haven't yet found instructions on how to blacklist wl.

since there have been changes to the kernel/drivers, are the original instructions still relevant, or is there an updated version?

sorry if this has been asked before, but 83 pages is a lot to read. i simply don't have the time.

cheers

---

### Post by elect on 2010-12-16
> **rild said:**
> I've made a lot of attempts. Before to made this one I've tried to clean the mess from the previous failures. After that I've just followed the instructions from the two links provided in my post above and ... everything works fine in 10.10

Yeah, me too, thats the problem..

It works also for me, but sometimes it just loses the signal, and i can spend all the time I want looking at it for reconnecting, but it cannot will reconnect anymore, the only way is rebooting..

---

### Post by rlelliott on 2010-12-17
I used to own a notebook with this card. My success was found by installing bcmwl with synaptic, allowing wl dkms to load at boot, then modprobe b43. This method worked well.

---

### Post by teklife on 2010-12-17
> **rlelliott said:**
> I used to own a notebook with this card. My success was found by installing bcmwl with synaptic, allowing wl dkms to load at boot, then modprobe b43. This method worked well.

hi rlelliot, is this a response to my  question? i'm sorry, it's not clear to me if it is or not.

i don't understand what it means to allow wl dkms to load at boot, then modprobe b43. will it be obvious to see wl dkms load at boot, and is modprobe b43 a terminal command? sry if  this is an utterly stupid question. i'm  just learning. thanks;)

---

### Post by rlelliott on 2010-12-17
I installed the wl dkms with

```
sudo apt-get install bcmwl-kernel-source
```

I then installed the firmware with 

```
sudo apt-get install b43-fwcutter
```

After reboot, load the b43 module with

```
sudo modprobe b43
```

eth1 is the interface the wl module uses

wlan0 is the interface the b43 module uses

also more info about the wl dkms can be found @ [http://packages.ubuntu.com/lucid/bcmwl-kernel-source]("http://packages.ubuntu.com/lucid/bcmwl-kernel-source")

more info about the b43 module can be found @ [http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43")

You must allow the wl dkms module to load first if you want the b43 module to load without errors. Hope this helps you. If not you could download Secmic 4.04 or 4.10 @ [http://secmic.org]("http://secmic.org") as it includes b43 preloaded.

---

### Post by teklife on 2010-12-17
thanks for the detailed instructions mate, i would have never guessed to do that on my own. 

now, once i complete these steps, i may proceed with the instructions from page 1? 

i'm still wondering if somewhere within the 83 pages of this thread, and over the years, if an updated version of those instructions has been posted.

cheers!

---

### Post by rlelliott on 2010-12-17
If you read through the pages of this Topic, you should gain a good working knowledge of how wireless card modules are built and loaded and a good base of how most modules work in Linux. 

To answer your question, if you follow my instructions you will not need to use the ones posted on the main page. The steps listed there are more advanced and allow you to load b43 standalone without first loading wl.

Also you may want to create a script that loads b43, unloads b43, loads wl, and unloads wl. Although this method is not the preferred method (Chen's method is preferred, on first page) it works, and is easy to perform quickly.

---

### Post by ivotkl on 2011-01-24
Comands entered:
ifconfig
iwconfig
sudo lshw -C network



Output shows:
root@ivan-lnv:/home/ivan# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

root@ivan-lnv:/home/ivan# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Encryption key:eek:ff
          Power Management:eek:ff
          
root@ivan-lnv:/home/ivan# sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f4500000-f4503fff
  *-network DISABLED
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:c8:ba:d7
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.102 duplex=half firmware=sb v3.04 latency=0 link=yes  multicast=yes port=twisted pair
       resources: irq:17 memory:f4600000-f460ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:82:2b:9c:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg





Do I need to use broadcom-wl-4.150.10.5.tar.bz2,  broadcom-wl-4.80.53.0.tar.bz2, both or none (meaning a different one)?  How do I do that?

Oh and BTW, I have no Eth0 after upgrading the system, not even booting  up with the previous kernel, but I do have wirless and wired connection  with XP.
I'm running Ubuntu Studio with Windows XP dual boot. Lenovo G550 with 4GB RAM. Model name is 2958J6Y.

Thank you so much for the help.
Greets.

PS: I also posted it [here](http://ubuntuforums.org/showthread.php?p=10391310#post10391310) because I didn't know which topic suits my situation best. I guess the other one, but anyways... Hope you can help me. =)

---

### Post by hilariusmind on 2011-02-12
Folks

I'm past desperation now. I've tried to follow the first few and the last many tips of how to use this broadcom chipset. I just can't make it work on my Kubuntu Maverick AMD64 system.

I've removed, purged and rinstalled bcmwl-kernel-source, b43-fwcutter, and firmware-b43-lpphy-installer packages in many different orders and combinations. After blacklisting nothing and everything and all combinations of b43, wl and ssb and many reboots later I still can't use the wireless card on my notebook (HP pavillion dv2 - 14e4:4315 broadcom chipset).

The weirdest thing is that once I got it working on Kubuntu 9.10 (I remember to have only blacklisted the b43 module), it still worked on through all 10.04 upgrade and updates until 10.10. After upgrading from 10.04 to 10.10 wireless kept working. Then, after one 10.10 update I could not get the wireless interface to work anymore. Every time I power on my notebook the wireless led stays orange (it is supposed to be blue until you press the switch to kill wireless and turn it orange). I'm loosing what is left of my hair here...

In order to make sure it was not some leftover trash from earlier attempts or upgrades, I've even booted live images of: Kubuntu 10.10 AMD64 and regular 32-bit and Fedora 14 AMD64 and regular 32-bit. After trying to install and remove packages nothing worked: the same orange led.

Everyday I perform an "aptitude update && aptitude full-upgrade" eagerly hoping that some bug was fixed and I could use my notebook again on wireless.

Does anyone have a new idea (or an old one that I could try)?

Thanks in advance.

---

### Post by hilariusmind on 2011-02-12
> **hilariusmind said:**
> The weirdest thing is that once I got it working on Kubuntu 9.10 (I remember to have only blacklisted the b43 module), it still worked on through all 10.04 upgrade and updates until 10.10. After upgrading from 10.04 to 10.10 wireless kept working. Then, after one 10.10 update I could not get the wireless interface to work anymore. Every time I power on my notebook the wireless led stays orange (it is supposed to be blue until you press the switch to kill wireless and turn it orange).

Just to answer my own question in case anybody else was facing the same problem: something in the update had just blocked the card. All you have to do is unblock it.

So, you have to install the drivers (in my case b43-fwcutter, firmware-b43-lpphy-installer):

```
sudo aptitude install b43-fwcutter firmware-b43-lpphy-instaler
```

And then you have to run:

```
sudo rfkill unblock all
```

That's it.

I've found that solution on this [other thread]("http://ubuntuforums.org/showthread.php?p=10453237#post10453237")

---

### Post by chissy on 2011-05-03
Thanks man :)
Worked for me in Ubuntu 10.10, does anyone know if this issue is solved in 11.04?

---

### Post by Pingue_Pinguino on 2011-05-06
FYI, this How-To is still working on 11.04. I'm using it my Dell Vostro 1320  that come from factory with this hardware on.

Just to be more precise, the card is working in PIO mode with QOS disabled.
I've tried to load the b43 module without any parameters but, after a couple of minute, i've got DMA error.

---

### Post by piratesmack on 2011-06-10
So I just noticed that on the b43 page it says the DMA errors were fixed in kernel 3.0
[http://linuxwireless.org/en/users/Drivers/b43#Known_issues](http://linuxwireless.org/en/users/Drivers/b43#Known_issues)

Anybody tried it yet?

---

### Post by piratesmack on 2011-06-15
Just an update, the b43 driver is trouble-free for me with kernel 3.0-rc3.

edit:
okay, not 100% trouble-free.

I lost my connection a few times. Can't reconnect until I unload/reload b43. Seems to only happen after I've used suspend to RAM at least once.

Testing this as a workaround:
cat /etc/pm/sleep.d/75-b43.sh
```

#!/bin/sh
case $1 in
suspend|hibernate)
  /sbin/modprobe -r b43
;;
resume|thaw)
  /sbin/modprobe b43
;;
esac

```

---

### Post by dened on 2011-09-01
I checked on kernel 3.0.4, and I don't have DMA errors right now. Also I don't have freezes in airodump-ng. HW: Dell Vostro V13, SW: Slackware 13.37, my own kernel 3.0.4

---

### Post by aggelos91 on 2011-11-07
i have ubuntu 11.10 on a dell inspiron 1525 with broadcom wireless card.. i have install the b43 and the aircracker and all its good.. but ... when i give airodump-ng mon0 after 30 seconds stops and if i give again airodump-ng i can't see nothing... why? (sorry for my bad english)

---

