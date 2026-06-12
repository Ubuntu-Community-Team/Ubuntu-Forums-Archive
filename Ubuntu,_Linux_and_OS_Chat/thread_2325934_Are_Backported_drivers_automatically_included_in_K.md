---
title: "Are Backported drivers automatically included in Kernel updates?"
date: 2016-05-26
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2016-05-26
My kids and wife are all using HP Stream Laptops, and the laptops all come with the realtek rtl8723be wireless device.

So, for the last year and a half, every time there's a Kernel update they have to recompile and reinstall the wireless driver (which I've automated with a single command). I keep waiting for this driver to make it into the Kernel and [I just read]("https://github.com/lwfinger/rtlwifi_new") that the driver might make it into Kernel 4.7:

> 
This code will build on any kernel 3.0 and newer as long as the distro has not modified any of the kernel APIs. It includes the following drivers:
  
rtl8192ce, rtl8192se, rtl8192de, rtl8188ee, rtl8192ee, rtl8723ae, rtl8723be, and rtl8821ae.

  
Added March 16, 2016: All branches of this repo now support the ant_sel module option for rtl8723be. In addition, patches to implement this feature have been submitted to the linux-wireless repo. If accepted, they should appear in kernel 4.7; however, they will be packported to kernels 4.0 and newer when they reach mainline.




So, the question for ya'll is this: Will the driver be magically backported with a Kernel update? -- Do I need to upgrade their Kernel to 4.7? -- or is there another method? I know, for instance, that when 16.04.1 is released, it will be released with an updated hardware enablement stack. The updated hardware stack, however, is **_not_** backported to a 16.04 installation without [intervention by the user]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").
[h=2][/h]

---

