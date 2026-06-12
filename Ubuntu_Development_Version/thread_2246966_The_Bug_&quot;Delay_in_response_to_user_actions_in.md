---
title: "The Bug &quot;Delay in response to user actions in Ubuntu 14.10 on cards AMD&quot;"
date: 2014-10-04
forum: Ubuntu Development Version
---

### Post by tamir2 on 2014-10-04
Constant periodic belated response of the system to the user. Evident even when you drive across the screen just with the mouse.
When you turn off the laptop weighs a welcome screen for a long time until the power goes off.
Perhaps the problem is in the open source driver for AMD graphics cards in the kernel 3.16
Who faced with a problem, please unsubscribe in the topic. Can support a bug-report on this subject - [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1377007](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1377007)

P.S. In Ubuntu 14.04 no such problem.
P.S.S. If you need information about my hardware, it is here - [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1377008](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1377008) (see description)

---

### Post by ventrical on 2014-10-04
> **tamir2 said:**
> Constant periodic belated response of the system to the user. Evident even when you drive across the screen just with the mouse.
When you turn off the laptop weighs a welcome screen for a long time until the power goes off.
Perhaps the problem is in the open source driver for AMD graphics cards in the kernel 3.16
Who faced with a problem, please unsubscribe in the topic. Can support a bug-report on this subject - [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1371651](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1371651)

P.S. In Ubuntu 14.04 no such problem.
P.S.S. If you need information about my hardware, it is here - [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1377008](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1377008) (see description)

That sounds like llvmpipe to me. Happens all the time with AMD. Intel as of recent also.

To check for llvmpipe go to top right cog wheel and select <About this Computer> and the graphics will tell you if it is llvmpipe.

---

### Post by tamir2 on 2014-10-04
**ventrical**,
 I'm sorry. I gave the wrong link to the bug-report, here's a link to my report -[ https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1377007]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1377007")
As for the graphics so:
Graphics: GLX Renderer: Gallium 0.4 on AMD ARUBA
  Card-1: Advanced Micro Devices [AMD/ATI] Radeon HD 7520G
           Card-2: Advanced Micro Devices [AMD/ATI] Radeon HD 7670M
Resolution: 1366x768@60.1hz

---

### Post by tamir2 on 2014-10-05
So what's the way out of the situation there? I hope correctly created bug report on launchpad. May need to add information in report or hang it on a completely different package?

---

### Post by ventrical on 2014-10-05
> **tamir2 said:**
> So what's the way out of the situation there? I hope correctly created bug report on launchpad. May need to add information in report or hang it on a completely different package?


The bug has been confirmed. Good work. The conventional wisdom says to wait it out until a bug-fix is ready. You may want to install gnome-session-flashback DE  and try running it in (metacity). That would be without compiz as compiz may also be a culprit here. That way you could still use your Utopic install without unity until bug-fix comes in. Sometimes they come like lightning, othertimes , slow.

---

### Post by tamir2 on 2014-10-06
Thank you for the warm response. I would hope that the developers will understand how to fix it in the near future. It seems to me that the problem is not very dependent on &#1089;ompiz. For the experiment, I installed Kubuntu (it does not depend on &#1089;ompiz), the problem remains as in Unity.

---

### Post by ventrical on 2014-10-08
> **tamir2 said:**
> **ventrical**,
 I'm sorry. I gave the wrong link to the bug-report, here's a link to my report -[ https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1377007]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1377007")
As for the graphics so:
Graphics: GLX Renderer: Gallium 0.4 on AMD ARUBA
  Card-1: Advanced Micro Devices [AMD/ATI] Radeon HD 7520G
           Card-2: Advanced Micro Devices [AMD/ATI] Radeon HD 7670M
Resolution: 1366x768@60.1hz



 Do you physically have 2 graphics adapter cards in your PC?

---

### Post by Smask on 2014-10-09
7520G = Integrated with the APU
7670M = Mobile

---

### Post by ventrical on 2014-10-09
Thnx .. that's what I thought.

---

### Post by tamir2 on 2014-10-11
Delays and brakes are gone :). 3.16.0-22- kernel everything is fine :). That's just I'm worried about the brightness of the screen, the level of non-retentive after a reboot, what could be wrong - can also make a bug-report?
P.S. 
One Integrated with the APU video card is another discrete

---

### Post by jerrylamos on 2014-10-11
Don't seem to have that problem with this AMD 6310:

DISTRIB_DESCRIPTION="Ubuntu Utopic Unicorn (development branch)"
Linux Acer5253 3.16.0-22-generic #29-Ubuntu SMP Thu Oct 9 16:26:18 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310]
model name	: AMD E-350 Processor
model name	: AMD E-350 Processor

Also running O.K. on another pc with an even older AMD ATI.

---

### Post by Smask on 2014-10-11
The 6310 has WLIW-4 or WLIW-5 shaders, which uses the R600 stack. Newer GPUs has GCN shaders, which uses the RadeonSI stack.

The main difference between the two stacks is that R600 based cards has hardware to handle 2D.
GCN based cards has dropped 2D hardware completely and uses 3D shaders to handle 2D, which explains the need for LLVM. Intel is a driving force behind LLVM.
You can use LLVM with R600 GPUs, but it isn't recommended.

---

