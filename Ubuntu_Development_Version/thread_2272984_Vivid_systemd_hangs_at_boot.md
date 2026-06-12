---
title: "Vivid systemd hangs at boot"
date: 2015-04-09
forum: Ubuntu Development Version
---

### Post by drfox on 2015-04-09
I would like to know how to troubleshoot this problem. I am running Xubuntu on a T420. I upgraded to Vivid some months ago. For the past month, it will not boot without interrupting grub and selecting upstart. If I do a normal automatic boot I get an splash screen with an icon and 3 blinking dots.
If I select recovery, it will boot to the menu which gives me several options, including "resume normal boot". When I select that, it goes to terminal and hangs with a flashing cursor.
Thanks for any help

---

### Post by dino99 on 2015-04-09
since a week or so, i've seen many xubuntu/kubuntu users complaining about login issue; it seems that all their bugs are not fixed yet ;)
if you boot without 'quiet splash' you will see the boot details processes and where it hangs (maybe it fail somewhere)

---

### Post by grahammechanical on 2015-04-10
I experienced loading problems when a long term Ubuntu vivid switched from Upstart to SystemD. It seems that fresh installs from the latest daily images do not have these problems. In my case systemd was reporting the failure to load kernel modules. In my opinion you have these options.

1) look through the logs to identify the problems and try to find a way to fix it.
2) re-install with the latest ISO image but do not format the / partition or any partition used by the installation.
3) do a complete fresh install with the latest daily ISO image.

I could not be bothered with trying to fix things. So, I choose option 2 in my list. And it worked. Loading times are much faster. Very little needed to be re-installed. I do suspect that this particular system is not loading as fast as it should be doing. I may yet put a fresh install into this partition before moving on to the next development release.

Regards.

---

### Post by VMC on 2015-04-12
> **9d9 said:**
> since a week or so, i've seen many xubuntu/kubuntu users complaining about login issue; it seems that all their bugs are not fixed yet ;)
if you boot without 'quiet splash' you will see the boot details processes and where it hangs (maybe it fail somewhere)

I can leave 'splash', but need to remove 'quiet' for mine to work. I notice with 'quiet' that it hangs with /dev/sdc error. I'm unsure if removing 'quiet' slows down systemd enough to pass or not. I still see the /dev/sdc error , but it passes by it and continues to boot. Obviously, log files will help. :) , but at the monent I'm enjoying using nouveau without nvidia *proprietary install.*

---

