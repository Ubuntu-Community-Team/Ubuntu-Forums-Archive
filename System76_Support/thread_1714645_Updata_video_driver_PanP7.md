---
title: "Updata video driver? PanP7"
date: 2011-03-25
forum: System76 Support
---

### Post by flucoe on 2011-03-25
Hi all,

After upgrading to Firefox 4, I went into the page [https://demos.mozilla.org/en-US/](https://demos.mozilla.org/en-US/) (no idea why...) and I got the message "Unfortunately, while your browser supports WebGL, your video drivers may  be too old. To view any of the demos tagged with WebGL, try updating  your drivers at [NVIDIA]("http://www.nvidia.com/Download/index.aspx"), [AMD]("http://support.amd.com/us/gpudownload/Pages/index.aspx"), and [Intel]("http://downloadcenter.intel.com/")."

I have a PanP7 with a Graphics ATI Mobility Radeon HD 4570 Graphics with 512MB GDDR2 Memory. I was wondering whether or not I should really update my drivers. I thought that the update manager would suggest me to update if it was required, but this has not been the case. Any suggestions? In case I should update, any suggestion on how to do it?

Thanks,

---

### Post by nevius on 2011-03-26
> **flucoe said:**
> Hi all,

After upgrading to Firefox 4, I went into the page [https://demos.mozilla.org/en-US/](https://demos.mozilla.org/en-US/) (no idea why...) and I got the message "Unfortunately, while your browser supports WebGL, your video drivers may  be too old. To view any of the demos tagged with WebGL, try updating  your drivers at [NVIDIA]("http://www.nvidia.com/Download/index.aspx"), [AMD]("http://support.amd.com/us/gpudownload/Pages/index.aspx"), and [Intel]("http://downloadcenter.intel.com/")."

I have a PanP7 with a Graphics ATI Mobility Radeon HD 4570 Graphics with 512MB GDDR2 Memory. I was wondering whether or not I should really update my drivers. I thought that the update manager would suggest me to update if it was required, but this has not been the case. Any suggestions? In case I should update, any suggestion on how to do it?

Thanks,

You probably need to install / enable the binary driver. See the following howto: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I will give you a fair warning. You should be careful to follow the steps exactly. If you screw something up, it can take a while to troubleshoot the problem(s) and fix them.

---

### Post by Flyers2391 on 2011-03-29
Is that warning about hardware acceleration?  If so, I think that is only supported with Windows at this time

---

### Post by isantop on 2011-03-29
Yep, I've confirmed that that message comes up if you don't have the proper drivers. Try going to System > Administration > Additional Drivers and see if the ATI drivers are listed there. If they are, click them and click "Activate".

---

### Post by flucoe on 2011-04-01
Hi,

I don't have any "additional drivers" option (by the way, I still use Ubuntu 10.04), just "hardware drivers". Anyway, the "ATI/AMD proprietary FGLRX graphics driver" is "activated and currently in use". No idea if this is the same isantop was asking me to do, but I didn't find the "additional drivers" option.

---

