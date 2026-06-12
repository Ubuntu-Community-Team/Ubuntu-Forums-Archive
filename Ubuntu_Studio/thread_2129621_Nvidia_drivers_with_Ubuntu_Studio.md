---
title: "Nvidia drivers with Ubuntu Studio"
date: 2013-03-26
forum: Ubuntu Studio
---

### Post by Gramler on 2013-03-26
Has anyone had any luck with getting "nvidia-current" and "nvidia-current-updates" working with Ubuntu-Studio.
I keep running into:
"Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-25-lowlatency/updates/dkms/
"

and subsequently
"ERROR (dkms apport): kernel package linux-headers-3.8.3-030803-generic is not supported
Error! Bad return status for module build on kernel: 3.8.3-030803-generic (x86_64)
"nvidia-current

I know this is really an issue with the underlying low-latency kernel, but I am having no luck with ferreting out if it is possbile with the low latency kernel at all. There are some description for getting it to work with the latest stock kernels here:
[http://ubuntuforums.org/showthread.php?t=2106616](http://ubuntuforums.org/showthread.php?t=2106616)
But it is not clear to me if this is applicable to low-latency scenario

I need to run Ubuntu Studio  with a dual monitor set-up and a Nvidia card, but I also need to run Virtual Box for some  device configuration utilities (and running Vbox really requires the Native Nvidia drivers for video acceleration)

Tx
Max

---

### Post by tartalo on 2013-03-26
If you are using Ubuntu Studio because of the low latency Kernel, using the proprietary Nvidia driver is counterproductive.

If not, switch to the regular kernel.

---

### Post by jejeman on 2013-03-26
I'm useing properity driver.
```
$ dkms status 
nvidia-current, 304.60, 3.2.0-33-lowlatency, x86_64: installed
nvidia-current, 304.60, 3.2.0-35-lowlatency, x86_64: installed
nvidia-current, 304.60, 3.2.0-36-lowlatency, x86_64: installed
nvidia-current, 304.60, 3.2.0-37-lowlatency, x86_64: installed
nvidia-current, 304.60, 3.2.0-38-lowlatency, x86_64: installed
nvidia-current, 304.60, 3.2.0-39-lowlatency, x86_64: installed
vboxhost, 4.1.22, 3.2.0-33-lowlatency, x86_64: installed
vboxhost, 4.1.22, 3.2.0-35-lowlatency, x86_64: installed
vboxhost, 4.1.22, 3.2.0-36-lowlatency, x86_64: installed
vboxhost, 4.1.22, 3.2.0-37-lowlatency, x86_64: installed
vboxhost, 4.1.22, 3.2.0-38-lowlatency, x86_64: installed
vboxhost, 4.1.22, 3.2.0-39-lowlatency, x86_64: installed
```Oh, I need to purge some kernels...:)
>  using the proprietary Nvidia driver is counterproductive.I didn't know that. Hm, I didn't notice any drawbacks.

---

### Post by NNJRob on 2013-03-28
I'm currently on my AMD netbook,, But, my desktop runs 12.04 studio, with the 3.2xx low-latency kernel & Nvidia 3.04 drivers..that were selected at install, first update (no jockey use required by me,later), and it's working well

---

### Post by eddier on 2013-03-28
If you have a dig around with Google,there are issues with Nvidia drivers and the 3.8 Kernel.
Some people have claimed success using nvidia 313 drivers.

This is what stopped me in my tracks with studio 13 beta. I also tried updating Mint 14 with the 3.8 kernel-no go with Nvidia,ended up with 800x600 resolution and nvidia settings claiming no drivers were installed!

I had no problem with my Laptop.

I'm a bit surprised there isnt more noise about this in the community.

eddie

P.s. Kernel 3.9 is on the brink of realease.

---

### Post by zequence on 2013-04-04
linux-lowlatency is more or less exactly the same as linux-generic, which means, anything that will work on linux-generic, will work on linux-lowlatency.

The tiny difference in between them is that linux-lowlatency is configured for preempt, while linux-generic is configured for voluntary preempt.

---

### Post by zequence on 2013-04-04
> **Gramler said:**
> Has anyone had any luck with getting "nvidia-current" and "nvidia-current-updates" working with Ubuntu-Studio.
I know this is really an issue with the underlying low-latency kernel, but I am having no luck with ferreting out if it is possbile with the low latency kernel at all. There are some description for getting it to work with the latest stock kernels here:
[http://ubuntuforums.org/showthread.php?t=2106616](http://ubuntuforums.org/showthread.php?t=2106616)


It is not a problem concerning linux-lowlatency, as linux-lowlatency supports everything that linux-generic does. They are more or less the same kernel.

This is however not linux-lowlatency: 
> "ERROR (dkms apport): kernel package linux-headers-3.8.3-030803-generic is not supported
Error! Bad return status for module build on kernel: 3.8.3-030803-generic (x86_64)
"nvidia-current

---

### Post by Gramler on 2013-04-04
Kernels:
I am on 3.5 for low latency and 3.6 for generic.
Also have 3.8 for debugging some unrelated (usb) issue
Maybe 3.2 is the "magic"? Not sure.

Nouveau driver:
I have tried the Nouveau driver again.... this time it worked fine with VBox. Not sure why it was giving trouble the first time.
So I am using this for the interim, swapping back to Nvidia on 3.6 if I need the 3D or CUDA (painful, but don't need to do this often)
BTW the Nouveau driver is giving hassle on suspends.. but I digress.

I will take a look at this again in a week or so. I suspect it has something to do with 3.8 being installed.
From the message "Bad return status for module build on kernel: 3.8.3-030803-generic (x86_64)" it seems to be using 3.8 resource when installing Nvidia on 3.5 low-latency.  For sure I know Nvidia is not working with 3.8 on my system.

I will start with removing 3.8 Kernel and see. 

Why is using NVidia with Studio Counter productive? (Would like to see some rationale for this... certainly it has been a pain. But I thought it is just something to my config. Are there wider/general issues with this?


M.

---

### Post by zequence on 2013-04-04
Try booting into the kernel you want to install the driver to. Then just install it.

---

### Post by hellslinger on 2013-06-19
I had some trouble with this too, on a couple of different machines. IIRC, on the first machine, I had to purge at least the nvidia package, and maybe the linux kernels that weren't the most recent lowlatency version. 

Here's what just worked on my system: upgrade to nvidia-experimental-310. I'm currently running 3.8.0-24 with it. I have not tried any games yet, but it is working with KDE Desktop Effects just fine. I'll come back to this thread and leave a message if I have any problems.

---

### Post by Gramler on 2013-06-20
Hi

Just a quick update on this...

After an update to Raring (13.04) it seems that this problem has gone away.

Rgrds

Max

---

### Post by pepsifx357 on 2013-08-03
Just in case anyone was still using 12.04 and looking to get Nvidia working with an RT kernel.  I had to build my RT kernel from scratch, which means no automatic updates.  I used kernel 3.4.47 with the corrisponding x.x.47 RT patch.  I purged Nvidia and used the Experimental Nvidia 310 package for my 560 ti.  I can play games and all kinds of stuff now!  Haven't had any problems.

---

