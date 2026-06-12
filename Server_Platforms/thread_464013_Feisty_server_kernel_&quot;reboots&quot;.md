---
title: "Feisty server kernel &quot;reboots&quot;"
date: 2007-06-04
forum: Server Platforms
---

### Post by Robvdl on 2007-06-04
Hi all, I have been having a bit of problems with the Feisty server kernel, well, I believe it's the kernel anyway, here is what's happening:

[list=1]
[*]Installed Feisty server edition on my trusty spare K6-2-500 machine. This by default comes with the 2.6.20-15-server kernel as I recall. Installation went smoothly as expected, but as soon as I go to boot into my newly installed server, it instantly "reboots" the machine within seconds. I cannot get in at all, without it rebooting on me every time, even safe mode does not get me in.

[*]I installed the Feisty alternative CD instead and opted for a "command line only" install. Once again, installation went smoothly, and this time I could get into my system no problem. This is using the 2.6.20-15-generic kernel. I also tried the 2.6.20-16-generic, 2.6.20-15-lowlatency and 2.6.20-16-lowlatency kernels, all of these kernels work no problem. So I tried installing the server kernel again using "sudo apt-get install linux-server". Once again, I cannot get into the server kernel, the machine instantly reboots on me! It reboots using both the 2.6.20-15-server and 2.6.20-16-server, so none of the server kernels work for me basically.

[*]I installed Feisty alternative CD on another machine this time. This is an unusual machine, a Compaq Deskpro, socket 370 (Intel 810 board), with a VIA Samuel 2 700MHz CPU. Once again, all kernels works (generic, and lowlatency), except for the server kernels.
[/list]
What is going wrong? Why can't I use the server kernels? I never had this problem with Edgy. Is there a possibility the server kernel expects a certain CPU? Like at least a P4 or something?

Has anyone else been having this problem?

---

### Post by Chayak on 2007-06-04
If the current server kernel is giving you problems then just use the generic one.  To be honest you won't see much if any difference in performance on a home server and you can always switch later.

---

