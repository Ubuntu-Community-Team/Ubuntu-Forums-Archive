---
title: "Desperate with Elementary OS Freya &amp; Intel/Nvidia hybrid laptop"
date: 2015-05-08
forum: Ubuntu/Debian BASED
---

### Post by Nikos_T on 2015-05-08
Hello.
I would appreciate any help because I am quite stuck here trying to get Elementary OS Freya to work on my laptop (lenovo z710 i7-4710 mq) with hybrid intel/nvidia graphics card.
I have lost my whole day yesterday coming across many blank screens instead of login etc etc. The trouble is that after all this, I don't think I did actually set anything.
The situation now is that I can login to x environment but everything seems quite buggy, moving slowly etc etc.
On top of everything my touchpad stopped working and I have to use an external mouse!
This output also does not seem very promising :~$ lspci | grep VGA & sudo lshw -C video[1] 4683
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d1000000-d13fffff memory:c0000000-cfffffff ioport:5000(size=64)
[1]+  Done                    lspci | grep --color=auto VGA

I guess that it would be useful to tell you the steps I followed after installing Elementary Freya (the last time I ran over all this procedure to get it work):
apt-get update/upgrade/dist-upgrade

and then i install [FONT=Consolas]libegl1-mesa libgbm1 libgl1-mesa-dri libva1 , rebooted and installed mesa-utils and xserver-xorg-video-intel
after all this I followed [this]("https://elementaryforums.com/index.php?threads/howto-install-latest-nvidia-driver-on-linux-without-getting-black-screen.7/#post-12") guide to update with the latest drivers (nvidia-346) for my nvidia geforce 840M ([/FONT]http://www.geforce.com/drivers/results/83686).
[COLOR=#747C87][FONT=Consolas][/FONT][/COLOR][FONT=Consolas]As the install of nvidia-346 was successful, i rebooted my computer. After the boot logo I went to black screen.
[/FONT][COLOR=#747C87][FONT=Consolas][/FONT][/COLOR][FONT=Consolas]Then Ctrl+Alt+F1 to login to console and apt-get install bumblebee bumblebee-nvidia
As I did this I rebooted and I could finally login with graphical interface.
However everything seemed a little buggy.
I tried modifying the /etc/bumblebee.conf changing "nvidia-current" to "nvidia-346" and adding the choice for nvidia driver in order to get it to use this drivers. No big difference...
There is also no /etc/X11/xorg.conf file
Now almost everything seems buggy,** my touchpad does not work at all and my drivers set up is all a waste of time**.
I am really desperate for some help here.
Thank you very much.
Nikos
[/FONT][COLOR=#747C87][FONT=Consolas]
[/FONT][/COLOR]

---

