---
title: "bug:? Black Screen of death amd/ati chipset"
date: 2016-04-06
forum: Ubuntu Development Version
---

### Post by broadcast23 on 2016-04-06
I have an amd A8-3820 processor.  When I boot the 16.04 beta 2 loads to black screen (kernel unknown).  When I load 4.4.0-12 still doesn't load.  But when I load 4.4.0-10 works fine. I am using the integrated graphics on the processor.  I was reading somewhere that flgx driver isn't working, (I am using generic driver at this time).  So my guess is that the generic driver isn't working either.  On another hard disk I have an install of 14.04.4 and I want to be able to upgrade when 16.04 is released. Can anybody help in this situation.

---

### Post by crcarson on 2016-04-07
Also have a black screen (after PW entered) on 16.04 but it does load the desktop after 90 seconds delay.

---

### Post by grahammechanical on 2016-04-07
> **fglrx**

The  fglrx driver is now deprecated in 16.04, and we recommend its open  source alternatives (radeon and amdgpu). AMD put a lot of work into the  drivers, and we backported kernel code from Linux 4.5 to provide a  better experience. When  upgrading to Ubuntu 16.04 from a previous release, both the fglrx  driver and the xorg.conf will be removed, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware). 


More information is available here [https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/) 



[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Xenial is now at kernel 4.4.0-17 on my machine. If that other machine has an AMD video adapter my advice would be to stick with 14.04 until you see how things go between now and the end of summer. Or, put in a test install of 16.04 before you risk upgrading a production machine.

Regards.

---

### Post by QIII on 2016-04-07
This will be rough through the end of summer most likely.

AMD is doing exactly what the open source community has been asking for - concentrating on a a truly good, feature-rich open source driver.  They have been working hand-in-hand with Canonical in order to accomplish this.  Ubuntu will be the first distribution to benefit.

But there are a few ripples making this difficult:  a new version of X server and AMD's need to also move forward on the emerging Vulkan technology.

AMD hasn't the time to update fglrx if they are going to meet their ambitious timelines for both the Radeon and AMDGPU drivers and Canonical doesn't have the resources to maintain a working solution. 

This is difficult, no doubt.  But AMD is actually to be commended for its all-out effort to support the open source community.

---

### Post by broadcast23 on 2016-04-07
I loaded 4.4.0-10 on my machine and did apt-get dist-upgrade kernel was updated to 4.4.0-17, but no go.  How can you get the propitiatory drivers installed if you can't load the live beta disk in the first place (mind boggles). Anyways AMD has their work cut out for them

---

### Post by QIII on 2016-04-07
You cannot install the fglrx driver in 16.04.  It does not work.

Unless you have a Volcanic Islands chipset or the time and desire to get AMDGPU working (experimentally) with some of the selected Sea Islands chips, you can't use AMDGPU.

Most users of 16.04 will be left with the radeon driver as the only option for the time being.

---

### Post by biji on 2016-04-16
Yeah, I've also tried 16.04 beta, and it is pitch black after login. VGA: discrete and r7 m265
While I dual boot Fedora 24 alpha, and it load correctly

---

