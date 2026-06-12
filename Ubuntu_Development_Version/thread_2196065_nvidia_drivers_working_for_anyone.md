---
title: "nvidia drivers working for anyone?"
date: 2013-12-27
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-12-27
i installed kubuntu onto a spare HDD and was messing with config and had a GPU lockup (card is OCed, may not be entirely the drivers fault) trying to get audio, realized i forgot the nvidia driver installed it and rebooted and i am getting issues with nadia-persisted
anyone having any luck with nvidia drivers on trusty?

---

### Post by cariboo on 2013-12-27
I'm running the Nvidia driver here, it runs mostly OK, except for some tearing when looking at graphics heavy forum pages.

---

### Post by fooman on 2013-12-27
they work fine here with kernels up to 3.12  ...not working with the 3.13 kernels.  my card is a gtx480 with driver version 331.20-0ubuntu7

i do not have nvidia-persistenced installed presently.

---

### Post by pqwoerituytrueiwoq on 2013-12-28
i installed nvidia-331-updates and all the things it pulled with it on kubuntu

---

### Post by Elfy on 2013-12-28
I had some issues with the same thing (Xubuntu) - just hung while booting - ended up back with nouveau, was 331 proprietary though.

---

### Post by P-I H on 2013-12-28
I have a Geforce GTX 660 and it is working fine with the nvidia-331-updates driver (331.20) installed with System Settings/Software&Updates/Additional AdditionalDrivers.
However I am a little bit worried over the update to kernel 3.13.
I cannot use the correct resolution with the Nouveau driver, so that is no alternative on this system.

---

### Post by VinDSL on 2013-12-28
The edgers 304.117 legacy drivers are working beautifully here, on a 3.12x mainline kernel.

Hasn't been patched yet, for Linux 3.13-rcx, as 'fooman' said... :(

---

### Post by spupazza on 2013-12-28
> **VinDSL said:**
> The edgers 304.117 legacy drivers are working beautifully here, on a 3.12x mainline kernel.

Hasn't been patched yet, for Linux 3.13-rcx, as 'fooman' said... :(
Can I ask you, what will happen when Trusty will swicth to 3.13.x series?
I mean will you have to reinstall the nvidia drivers by yourself or the update process will take care of everything? (I mean update the drivers along with the kernel and compile those against it, smothless with you having just to reboot)

---

### Post by pqwoerituytrueiwoq on 2013-12-28
ok, i figured out what happened and got it to boot and run
1st issue i had was removing the driver, i was unable to remove [FONT=courier new]nvida-prime[/FONT] as [FONT=courier new]dpkg-architecture[/FONT] (from [FONT=courier new]dpkg-dev[/FONT]) is a missing dependency, modified a line in the uninstall script and remove it
installed the missing dependency
anyway i had nvida gone and could not boot
the system was trying to use unity which is not present on the KDE install
when installing [FONT=courier new]nvidia-313-updates[/FONT] it creates/replaces [FONT=courier new]/etc/lgihtdm/lightdm.conf[/FONT] file with a unity config, removing this file allows the system to use kde again

so to install the nvida driver on kubuntu

```
sudo apt-get install dpkg-dev nvidia-331-updates
sudo rm /etc/lightdm/lightdm.conf
sudo reboot
```
if it does not boot right
ctrl+alt+f1 into a console and run the rm command above then run [FONT=courier new]sudo service lightdm start[/FONT]

---

### Post by VinDSL on 2013-12-28
> **spupazza said:**
> Can I ask you, what will happen when Trusty will swicth to 3.13.x series?
Somebody will patch it sooner_or_later.  Seems like it takes longer n' longer these days.

Took (like) a month or two for 'them' to patch the legacy drivers, during the 3.12x cycle.

I do web searches, every day;  watch this forum, launchpad, check various PPAs, and so forth and so on.

Sometimes, I get tired of waiting and patch it myself (if I can find a diff file that works).  LoL!

Eventually, you will be able to install it from the official PPA.

---

### Post by VinDSL on 2013-12-28
> **pqwoerituytrueiwoq said:**
> ok, i figured out what happened [...]
Good job, detective!

I need to get down n' dirty with my DM.  I haven't had a mouse pointer at my login screen for several weeks.

Oh, the joy(s) of +1 testing...  ;)

---

### Post by pqwoerituytrueiwoq on 2013-12-28
made a bug report for the missing dependency
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1264734](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1264734)
no idea where to report the more critical issue with the lightdm config file

---

### Post by VinDSL on 2013-12-28
Thanks for [**[COLOR="#FF0000"]spurring me to action[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=2195166&p=12885245&viewfull=1#post12885245")... ;)

---

### Post by ventrical on 2013-12-30
> **cariboo907 said:**
> I'm running the Nvidia driver here, it runs mostly OK, except for some tearing when looking at graphics heavy forum pages.


 it is working ok here also . I think there is a new feature  where Open GL has some default settings which we used to have to set manually, ie; Sync to Vblank.

---

### Post by paul_in_london on 2014-01-02
> **VinDSL said:**
> The edgers 304.117 legacy drivers are working beautifully here, on a 3.12x mainline kernel.

Hasn't been patched yet, for Linux 3.13-rcx, as 'fooman' said... :(

Happy New Year all. :)

The legacy nvidia driver has now been patched to work with the 3.13 kernel. Change log available here:

[http://www.ubuntuupdates.org/package/xorg-edgers/saucy/main/base/nvidia-graphics-drivers-304](http://www.ubuntuupdates.org/package/xorg-edgers/saucy/main/base/nvidia-graphics-drivers-304)

Working ok here:

```
paul@trusty-64:~$ apt-cache policy nvidia-304
nvidia-304:
  Installed: 304.117-0ubuntu1~xedgers~saucy3
  Candidate: 304.117-0ubuntu1~xedgers~saucy3
  Version table:
 *** 304.117-0ubuntu1~xedgers~saucy3 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status
     304.116-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/restricted amd64 Packages
paul@trusty-64:~$
```

```
paul@trusty-64:~$ uname -a
Linux trusty-64 3.13.0-rc6-custom #1 SMP Mon Dec 30 00:50:10 GMT 2013 x86_64 x86_64 x86_64 GNU/Linux
paul@trusty-64:~$
```

---

### Post by sgage on 2014-01-02
331.20 drivers work fine here with a GeForce 8500 GT. Just out of curiosity, why are people using the legacy drivers?

---

### Post by paul_in_london on 2014-01-02
> **sgage said:**
> 331.20 drivers work fine here with a GeForce 8500 GT. Just out of curiosity, why are people using the legacy drivers?

Unfortunately my Quadro FX 1400 card in this box is only supported by the legacy driver. When I get a Haswell replacement mobo for my broken box (which has a newer GeForce card) I may be able to use that instead of the Quadro card.

---

### Post by Cavsfan on 2014-01-03
Running 331.20 on my Geforce 9800 GT here. I remember installing nvidia-settings and nvidia-331-updates I believe.

How the rest got on here is a mystery to me. 

[ATTACH=CONFIG]249161[/ATTACH]

[ATTACH=CONFIG]249166[/ATTACH]

Smooth as silk. :)

---

### Post by PJs Ronin on 2014-01-03
Here be 331.20 on nVidia GTX650.
```
wayne@trusty:~$ sudo apt-cache policy nvidia-331:
  Installed: 331.20-0ubuntu7
  Candidate: 331.20-0ubuntu7
  Version table:
 *** 331.20-0ubuntu7 0
        500 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty/restricted amd64 Packages
        100 /var/lib/dpkg/status
```

```
wayne@trusty:~$ uname -aLinux trusty 3.12.0-7-generic #15-Ubuntu SMP Sun Dec 8 23:39:27 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
wayne@trusty:~$ 

```
Until about 5 days ago I had no problems, but now I notice that just b4 dash activates on bootup (doesn't happen after logout/login) the entire screen gives a 'checkerboard' flash.   Doesn't seem to effect anything.

---

