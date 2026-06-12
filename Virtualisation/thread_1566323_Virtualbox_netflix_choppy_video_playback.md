---
title: "Virtualbox netflix choppy video playback"
date: 2010-09-02
forum: Virtualisation
---

### Post by cinger on 2010-09-02
Trying to watch netflix instant using virtualbox, xp sp3 but video playback is choppy.  

I am running lucid 10.04 on a  fresh install with gnome 2.30.0, kernel 2.6.32-24-generic,  2.0 GiB RAM, Intel(R) Celeron(R) CPU 2.40 GHz, 49.8 GiB available  space.  Running Oracle VM VirtualBox 3.2.6 r63112.  Set up virtual xp  sp3 using youtube tutorial posted on youtube here [http://www.youtube.com/watch?v=ZuyPJFhVTxQ](http://www.youtube.com/watch?v=ZuyPJFhVTxQ)  .  Virtual machine set up with 984 MB base memory, 32 MB video memory,  3d vid acc enabled, 2d vid acc disabled, with guest additions installed.  I set the virtual machine up on a 10 GiB partition, the actual size right now is 1.88 GiB.  This machine used to have Xp as the primary os and at that time netflix instant worked  well. I tried adjusting screen resolution to  1024x768 from 1152x864 as mentioned previously but no avail.  Max for  this system is 2048x2048.

Any ideas on whether or not this system could support non-choppy video  playback?  Suggestions appreciated, let me know if I can provide any  other specs.

---

### Post by lbrty on 2010-09-06
> **cinger said:**
> Trying to watch netflix instant using virtualbox, xp sp3 but video playback is choppy.  

I am running lucid 10.04 on a  fresh install with gnome 2.30.0, kernel 2.6.32-24-generic,  2.0 GiB RAM, Intel(R) Celeron(R) CPU 2.40 GHz, 49.8 GiB available  space.  Running Oracle VM VirtualBox 3.2.6 r63112.  Set up virtual xp  sp3 using youtube tutorial posted on youtube here [http://www.youtube.com/watch?v=ZuyPJFhVTxQ](http://www.youtube.com/watch?v=ZuyPJFhVTxQ)  .  Virtual machine set up with 984 MB base memory, 32 MB video memory,  3d vid acc enabled, 2d vid acc disabled, with guest additions installed.  I set the virtual machine up on a 10 GiB partition, the actual size right now is 1.88 GiB.  This machine used to have Xp as the primary os and at that time netflix instant worked  well. I tried adjusting screen resolution to  1024x768 from 1152x864 as mentioned previously but no avail.  Max for  this system is 2048x2048.

Any ideas on whether or not this system could support non-choppy video  playback?  Suggestions appreciated, let me know if I can provide any  other specs.

Try using VMWare Player (it's free). Leave all the settings defaulted when installing Win XP and give it a try.

[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

---

### Post by cinger on 2010-09-07
thanks for the suggestion, vmware player worked much better than virtualbox for this application, also liked the interface of vmware a little more.  the refresh rate with vmware is able to keep up with the slower scenes and you only start noticing the 'choppyness' during action sequences.  default was for 512mb ram, which seemed to work as well as when i ramped it to 1024.  recommended storage was 40g which seems like way more than i plan to use on xp, but i may mess around and see if smaller partitions will decrease performance.  not perfect playback yet, but definitely an improvement.  -thanks again.

---

### Post by lbrty on 2010-09-08
> **cinger said:**
> thanks for the suggestion, vmware player worked much better than virtualbox for this application, also liked the interface of vmware a little more.  the refresh rate with vmware is able to keep up with the slower scenes and you only start noticing the 'choppyness' during action sequences.  default was for 512mb ram, which seemed to work as well as when i ramped it to 1024.  recommended storage was 40g which seems like way more than i plan to use on xp, but i may mess around and see if smaller partitions will decrease performance.  not perfect playback yet, but definitely an improvement.  -thanks again.

Great! :) The virtual machine is not 40 GB yet. That number represents the max size the virtual machine can grow too. Have you installed VMware Tools? If you have not, I would suggest you install it if your going to keep using VMware Player. It will shrink the partition of the virtual machine when it starts expanding. Lastly, once I installed Win XP, activated it, and ran the updates, I shutdown the virtual machine and copied the virtual machine folder (under your home directory). By doing this you can copy the backup that you made in case the current virtual machine of Win XP has issues.

---

### Post by cinger on 2010-09-08
Yeah, I installed the vmware tools.  Thanks for the vm backup tip as well, was curious.  Also, I thought that might be the case about vm disk size, thanks for confirmation.  I am hoping that one day when I buy a newer, faster pc that this option of running netflix via xp vm will allow better playback.
:KS

---

### Post by LightningCrash on 2010-09-08
> **cinger said:**
> Yeah, I installed the vmware tools.  Thanks for the vm backup tip as well, was curious.  Also, I thought that might be the case about vm disk size, thanks for confirmation.  I am hoping that one day when I buy a newer, faster pc that this option of running netflix via xp vm will allow better playback.
:KS
I couldn't get it working well enough to play back on a Core 2 Duo E6750. I ended up using a Wii.

Since the VM is sending the framebuffer through the RAM, you're pretty well tanked there. Your only option is to drop the resolution on the host **and** guest... I saw a lot of improvements doing that.

---

### Post by cinger on 2010-09-08
So the main factor is RAM?  Wonder how much it would take.  My pc is maxed out at 2gb but I'm looking at some system76 pcs with 4 - 8gb.  Thanks for reminding me about trying to adjust the resolution, I'll give it a try.

---

### Post by lbrty on 2010-09-09
I have 512 MB of RAM with my current virtual machine and I do not have this issue. I was thinking it may be the CPU since the Celeron line is on the lower end, however according to LightningCrash s/he is having the same issues with an Intel Core 2 Duo (I also have an Intel Core 2 Duo with a different model). Is your video choppy on hulu.com or any other video websites? I know you stated in the original posting that you watched a video from youtube.com. Was it choppy there (I am assuming not since you probably would have mentioned it)? Maybe it is your GPU (graphics processing unit) or the L2 cache on the CPU. I would try the resolution as LightningCrash suggested to see if that helps. Anyone else have any ideas?

---

### Post by cinger on 2010-09-09
I adjusted resolution from 1152x864 to 1024x768.  I think my xrandr output was saying 1024x768 had better refresh rate at 85.0 (xrandr, lspci output follows).  Vmware is set to mirror host resolution and after this adjustment video playback is much improved; it seemed to keep up with some old anime action scenes, but couldn't quite cut it with fast live-action scenes (shaky cam, etc.).  It's an old machine, not top-of-the-line for sure.  It keeps up with youtube/hulu videos well.  I used to run xp on the machine as the primary and only os and it could play streaming movies on netflix without problem.
(Thanks again for all the assistance.)
xrandr (before changing to 1024x768
```
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2048 x 2048
VGA1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1024x768       75.0 +   85.0     75.1  
   1280x1024      60.0  
   1152x864       75.0* 
   800x600        85.1     75.0  
   640x480        85.0     75.0     60.0  
   720x400        70.1 
```lspci
```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

```

Edit: So maybe it has to do with the integrated graphics.  The youtube tutorial author Infernal6 noted that he wasn't sure how well this would run with integrated graphics, but that he had good results with a dedicated card.

---

