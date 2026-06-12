---
title: "Older NVIDIA graphics"
date: 2024-11-05
forum: Ubuntu Development Version
---

### Post by chrismine on 2024-11-05
I have old machines with NVIDIA graphics cards it seems Ubuntu does not support it anymore.

I have worked around that by using an old AMD Radeon card but it has now died.

I can install Linux Mint which still works with NVIDIA - for now - but how long until it's also not supported?

I use this older hardware for playing/learning/testing but without support for older NVIDIA cards I'm stuck ....

Any ideas how to get it to work again?

Plucky shows 20 Year splash screen in correct resolution but thenn stops on black screen with cursor.

---

### Post by corradoventu on 2024-11-05
Plucky development is just starting, how's it going with 24.04 Noble?

---

### Post by grahammechanical on 2024-11-05
Actually it is Nvidia that stops supporting its video cards after a certain time. It is then that Ubuntu stops providing the Nvidia proprietary video driver. The latest Nvidia drivers will not work with older Nvidia cards. Older Nvidia drivers may not work with the latest Linux kernels.

Your machines can still use the open source video driver called Nouveau for Nvidia cards. Remove the proprietary video driver and a reboot should see Ubuntu load using Nouveau.

Regards

---

### Post by chrismine on 2024-11-05
Nvidia will probably still work with 24.04 Noble.
It started happening on the end of 24.10 Oriole. I want to use the machine to run Ubuntu development versions. Seems to be end of the road ...

---

### Post by chrismine on 2024-11-05
Even on a live boot grasphics does not work. I also "think" nouveau does not work anymore with older NVIDIA cards.

---

### Post by Frogs Hair on 2024-11-10
If you were using a 390 driver it is not likely supported on many Linux distributions . If like me have or had Fermi card the open source may not work either.. I had a 730GT and the fan screamed with open source driver so I had to upgrade. My 8400GS is obsolete also. I discovered the reason for their low price when purchased.

---

### Post by chrismine on 2024-11-12
Playing with Linux Lite - running on Ubuntu Noble sources..

---

### Post by chrismine on 2024-11-12
> **corradoventu said:**
> Plucky development is just starting, how's it going with 24.04 Noble?

Playing with Linux Lite - running from Ubuntu Noble sources - how long until even this distro does not support the older Nvidia cards....

---

### Post by deadflowr on 2024-11-12
> **chrismine said:**
> Playing with Linux Lite - running from Ubuntu Noble sources - how long until even this distro does not support the older Nvidia cards....

It'l support the card as long as the distro exists.
Though, the caveat would be that you would need to make sure you use the General Availability (GA) kernel stack and not the Hardware Enablement (HWE) Kernel Stack.

The GA Kernel Stack is the original stack currently used by 24.04, with the 6.8 kernel. It'll remain the 6.8 series until the distro end of life.

The HWE stack will be upgraded a few times until it uses the same kernel stack that 26.04 will use at it's launch.

So there is a chance that the driver won't be compatible with a newer HWE kernel stacks.
But it will remain compatible with the older GA stack.
If that make sense.

As far as the nvidia drivers go, if installed from the Ubuntu Sources and not somewhere else,
those too will be supported for the same time as the GA kernel stack.

So support should run until 2029 or 2034 with Ubuntu Pro.


HWE ref: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

