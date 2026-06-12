---
title: "installs OK but won't boot"
date: 2011-12-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rtalcott on 2011-12-10
I have 2 ECS GF8100VM-M3 motherboards (AMD cpu) and both run 11.10 64 bit.  For the last few days I have been attempting to do a clean install of the 12.04 Daily Build.  The install completes but when the system reboots I end up seeing a listing of start-up operations which halts.  Right now I see

*Starting CPU interrupts balancing daemon

and a flashing cursor.  I can control-alt-delete and reboot into the grub menu.  If I select recovery mode I see: **Recovery menu (limited read-only menu)** and none of the selections get me to anything workable...any suggestions?

EDIT:  I am going to reinstall 11.10 to convince myself I don't have a hardware problem.

---

### Post by P-I H on 2011-12-10
I have a similar problem, when I boot the first time after installation. Also with Nvidia graphics.
To solve the problem I boot with Recovery mode. In the recovery menu I select the alternativ **root Drop to root shell promt**. At the prompt I type** exit** and then selects **resume Resume to normal boot**.
Now I get the login screen. After login I use **Additional drivers** to install the proprietary Nvidia driver and after this the system boots OK.

There is also this thread that describes a similar problem 
[http://ubuntuforums.org/showthread.php?t=1889658](http://ubuntuforums.org/showthread.php?t=1889658)

---

### Post by rtalcott on 2011-12-10
Thank YOU!  I will give that a try...probably in the next couple hours!

---

### Post by coffeecat on 2011-12-10
@rtalcott, I have an ECS GF8100VM-M5 motherboard which I was using to test Precise until about three weeks ago. I must admit I haven't updated it or even booted it up since then, but it was booting into Precise OK. However, I have an ATI Radeon 4350 PCIe card in it. Out of interest, are you using the onboard nvidia graphics or a PCIe card?

---

### Post by rtalcott on 2011-12-10
using the onboard....which is fine for what I do!

Just finished a reinstall of 11.10...this was my sanity check to assure myself that I did not have a hardware problem!

Now on to 12.04 again!

---

### Post by rtalcott on 2011-12-10
P-IH...Thank You!  I followed your instructions and ended up logging in to the cli...purged nvidia and reinstalled nvidia-current and all is well!

---

