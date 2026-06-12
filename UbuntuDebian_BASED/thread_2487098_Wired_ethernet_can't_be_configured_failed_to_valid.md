---
title: "Wired ethernet can't be configured: failed to validate module [mii] BTF: -22"
date: 2023-05-23
forum: Ubuntu/Debian BASED
---

### Post by dealy663 on 2023-05-23
Hi

I'm running Pop_OS 22.04 kernel: 6.2.6-76060206, on a Lenovo Thinkpad X390 Yoga. This system was working fine, and then last week the wired ethernet stopped working. I had been allowing the suggested system updates to occur as the notifications arrived. Today I finally sat down to troubleshoot this problem and it seems like there is a module called mii.ko (which exists on my system) but that it is somehow breaking every usb ethernet adapter I've tried 2 realteks and an AX88.... 

I'm unable to configure any of these, I've tried different usb ports, and the adapters seem to be fine on my other computer. One thing that does appear slightly suspicious is that while my kernel is up to 6.2.6-76060206, all of my linux-modules-extra-<kernel version>-generic options are still in the 5.15.xx range and I can't do the good ole [COLOR=#b22222]sudo apt install --reinstall linux-modules-extra-$(uname -r)[/COLOR] trick because apparently there are no newer 6.26.xx extras.

Any ideas of how to untangle this mess and get my USB ethernet adapters working again? Any idea what could have caused this to happen in the first place?

Thanks, Derek
[COLOR=#FFFFFF][FONT=&amp]
[/FONT][/COLOR]

---

### Post by chili555 on 2023-05-24
Isn't this issue now solved? [https://www.reddit.com/r/pop_os/comments/13pu8ym/miiko_problems_do_i_need_to_revert_my_kernel/](https://www.reddit.com/r/pop_os/comments/13pu8ym/miiko_problems_do_i_need_to_revert_my_kernel/)

---

### Post by coffeecat on 2023-05-24
Pop_OS. *Thread moved to **Ubuntu/Debian BASED** sub-forum.*

---

