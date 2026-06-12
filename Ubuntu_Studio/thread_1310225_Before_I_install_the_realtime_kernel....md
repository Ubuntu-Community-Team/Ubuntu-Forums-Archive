---
title: "Before I install the realtime kernel..."
date: 2009-11-01
forum: Ubuntu Studio
---

### Post by lavadisco on 2009-11-01
I'm running Jaunty and want to install the realtime kernel for audio production. I have a few questions first:

- I have read that my NVidia video driver will not work with the realtime kernel? If so, how do I prepare to deal with this prior to the new kernel installation?

- Is the current Jaunty RT kernel stable? I have read that some have had trouble with it.

- Once installed, will I see options for realtime and non-realtime kernels in GRUB? 

Thanks!

---

### Post by gareththegeek on 2009-11-02
> I have read that my NVidia video driver will not work with the realtime kernel? If so, how do I prepare to deal with this prior to the new kernel installation?
I could never get the nvidia driver to work with the real time kernel in Jaunty and had to revert to Hardy. To prepare for realtime kernel I would recommend simply uninstalling nvidia driver.

> Once installed, will I see options for realtime and non-realtime kernels in GRUB? 
Yes the realtime kernel is listed separately in grub with the letters rt after the version number, so you can go back to the original kernel.

---

### Post by junglejuice on 2009-11-02
i'm also quite curious to know about how the rt kernel fairs in 9.10. i  use an nvidia card on 9.04 currently,  but could never get the realtime kernel to work on 9.04. so i have simply been using the generic kernel which has not been a great solution cause i cannot get realtime midi playback in rosegarden. if any body using an nvidia card successfully with the 9.10 rt kernel has had some success/problems with it please let us know :)

---

### Post by AutoStatic on 2009-11-02
> **lavadisco said:**
> I'm running Jaunty and want to install the realtime kernel for audio production. I have a few questions first:

- I have read that my NVidia video driver will not work with the realtime kernel? If so, how do I prepare to deal with this prior to the new kernel installation?Use the open source *nv* driver instead of the restricted *nvidia* driver. You won't have any 3D effects but I assume you don't really need those in an audio production environment.

> **lavadisco said:**
> - Is the current Jaunty RT kernel stable? I have read that some have had trouble with it.I use Jaunty at the moment but not with the stock RT kernel because I think it's no good. I use almost the same RT kernel as Karmic, you can get it here: [https://launchpad.net/~dnjl/+archive/kernel](https://launchpad.net/~dnjl/+archive/kernel)

> **lavadisco said:**
> - Once installed, will I see options for realtime and non-realtime kernels in GRUB?That depends if your /boot/grub/menu.lst is stock or not. If it's stock then the RT kernel entry will be added automatically as the default entry. If you modified your menu.lst yourself you will be prompted during the install what you'd like to do with your menu.lst, it's pretty much self-explanatory.

---

### Post by lavadisco on 2009-11-02
Is it possible to have my machine use the nv driver with the RT kernel, and the restricted nvidia driver with the non-RT kernel? Or am I limited to only one driver? Oh, and if I uninstall the restricted driver will my machine default back to the nv driver? Or will I have to install it?

AutoStatic - Regarding the RT kernel you linked to; once I've installed the deb and the dnjl-kernel-repository, is there a further step I have to take to install the RT kernel?

---

### Post by AutoStatic on 2009-11-02
> **lavadisco said:**
> Is it possible to have my machine use the nv driver with the RT kernel, and the restricted nvidia driver with the non-RT kernel? Or am I limited to only one driver?No you're not, it takes some configuration though because you have to tell Ubuntu to use the *nv* driver for the RT kernel and the *nvidia* driver for the standard kernel. No idea how to set that up, maybe someone else could shed a light on this.

> **lavadisco said:**
> AutoStatic - Regarding the RT kernel you linked to; once I've installed the deb and the dnjl-kernel-repository, is there a further step I have to take to install the RT kernel?You can open up Synaptic, click Reload and start searching for *linux-rt*. The 2.6.31-9 RT kernel will show up then and you can install it. After the installation succeeded make sure to untick the dnjl kernel repo (and eventually any other dnjl repo's that got added) in Settings - Repositories - Third Party Software and click Reload again. Then reboot and the new kernel should show up in your Grub menu.

---

### Post by trulan on 2009-11-02
> **lavadisco said:**
> Is it possible to have my machine use the nv driver with the RT kernel, and the restricted nvidia driver with the non-RT kernel? Or am I limited to only one driver?
Here's how we did it before they fixed the NVidia drivers to work with Karmic's RT kernel:
[http://ubuntuforums.org/showthread.php?t=1287967](http://ubuntuforums.org/showthread.php?t=1287967)
Now that's using Grub2 so I don't know how much of it will apply to Jaunty...
Basically, the driver is selected by a line in /etc/X11/xorg.conf, and it's a little script that replaces xorg.conf on bootup, based on which option you select.

However, the NVidia drivers are patched and working quite well in Karmic 9.10 so there's not too much need for the driver chooser script anymore.
> **lavadisco said:**
> Oh, and if I uninstall the restricted driver will my machine default back to the nv driver? Or will I have to install it?
It'll default back - or, if you don't want to uninstall the nvidia driver, you can manually change it: ```
gksudo gedit /etc/X11/xorg.conf
```Find the line that says 'driver=nvidia' and change nvidia to nv or vesa.

The script in the link above does this automatically, based on what you choose at the grub menu.

---

### Post by lavadisco on 2009-11-03
I installed the realtime kernel. When it was finishing up it asked me if I wanted to keep the current menu.lst or use the "package maintainer's version". It was not immediately clear to me which one to pick. I chose to keep the current version, thinking that the realtime option would be added. However, upon restart it was not. Now that I've messed this up, how can I add the entry to menu.lst now?

---

### Post by GraysonPeddie on 2009-11-03
Try to [FONT="Courier New"]update-grub[/FONT] and see what happens.

Note that I'm using version 2 of Grub in Karmic Koala.

---

### Post by AutoStatic on 2009-11-03
> **lavadisco said:**
> I installed the realtime kernel. When it was finishing up it asked me if I wanted to keep the current menu.lst or use the "package maintainer's version". It was not immediately clear to me which one to pick. I chose to keep the current version, thinking that the realtime option would be added. However, upon restart it was not. Now that I've messed this up, how can I add the entry to menu.lst now?You could do it manually:
- make a copy first of your current menu.lst: **sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.orig**
- open your menu.lst: **sudo gedit /boot/grub/menu.lst**
- copy and paste the stanza for your current kernel which should look like:
```
title    Ubuntu 9.04, kernel 2.6.28-16-generic
uuid    lotsofdigitsandcharacters
kernel    /boot/vmlinuz-2.6.28-16-generic lotsofdigitsandcharacters ro quiet splash
initrd /boot/initrd.img-2.6.28-16-generic
quiet
```
and change the references to the 2.6.28-16 kernel to *2.6.31-9-rt*
- reboot and you should be able to select the 2.6.31-9-rt kernel

---

### Post by Vigh on 2009-11-03
is it the same for ati drivers in the latest rt-kernel, no matter how many times i install the drivers, my graphics dont appear to be working properly

---

### Post by lavadisco on 2009-11-04
Got it all working tonight. 3ms latency, woohoo! The Linux pro audio dream is finally a reality. That was the absolute last thing I needed Linux to do for me to make up for what I lost when I wiped Windows completely a few months ago. Too awesome.

Thanks everybody for all the help!

---

### Post by AutoStatic on 2009-11-04
Nice! =D>
Enjoy the experience!

---

### Post by lavadisco on 2009-11-25
Sorry to reanimate this thread but...

Just got a new laptop and put a fresh install of 64-bit Karmic on it and want to install the realtime kernel. Anything I should know before installing it? Did the weird installation of the RT kernel on Jaunty, previously, and I'm assuming Karmic is easier. Just to be sure, this is all I have to do, right?:

```
 sudo apt-get install linux-rt linux-headers-rt
```

Thanks!

---

### Post by trulan on 2009-11-26
You should be good to go.  The only thing that might get missed is updating Grub.  Since Karmic uses Grub2 you don't edit menu.lst (it's not there), things are done automatically.  If it doesn't run update-grub when you install the kernel, you'll have to do it manually.
```
sudo update-grub
```

---

### Post by bluesscream on 2009-11-26
jaunty's -rt urged me learning how to compile kernels myself :biggrin:
but with karmics 2.6.31-9-rt amd64 you will not run into such problems. Backports are not available still now and the latest nvidia drivers may be not fixed - so I've overheard an irc chat. If you run into this, there exists a little driver-select-script until it's fixed ;) 
Congratulations to your new laptop! May I ask for brand and properties?

---

### Post by trulan on 2009-11-26
> **bluesscream said:**
> ...the latest nvidia drivers may be not fixed - so I've overheard an irc chat.
NVidia drivers are working on my desktop.  Once in a while X will fail to start, and it needs an alt-printscreen-R-E-I-S-U-B reboot, then it works.  I'd say mine boots better than 90% of the time.  Jaunty booted about 33% of the time on the same machine. ;)

---

### Post by lavadisco on 2009-11-29
> **bluesscream said:**
> 
Congratulations to your new laptop! May I ask for brand and properties?

This:

[http://www.sagernotebook.com/product_customed.php?pid=177856](http://www.sagernotebook.com/product_customed.php?pid=177856)

Got 2.53GHz proc 1066MHz bus, 4GB RAM, 500 GB/7200 RPM HDD.

---

