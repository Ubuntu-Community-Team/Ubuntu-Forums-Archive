---
title: "vmware workstation 6 sound - feisty"
date: 2008-03-25
forum: Virtualisation
---

### Post by jewishj on 2008-03-25
I am running an XP x64 guest in VMWare Workstation 6 on Feisty and after fighting with sound for a while (getting device /dev/dsp doesnt exist messages) and trying alot of the methods described on these forums I was able to get sound working sometimes using vmware-dsp as described at [http://communities.vmware.com/thread/47101](http://communities.vmware.com/thread/47101).

This would either hit or miss for me - that is when I would power on the guest I would either get the /dev/dsp error again and have no sound, or it would work perfectly (with perfect sound in the guest and host at the same time).  

I found that the sound will work only if I'm playing video/music when I load the VM.  This leads me to believe that the sound will only work in the guest when it is active in the host.

I am looking for any suggestions on how to make the sound work in the guest regardless of whether it is active in the host.

Thanks in advance for any help

---

