---
title: "How can I change to the generic Kernel?"
date: 2013-04-03
forum: Ubuntu Studio
---

### Post by cjhill1836 on 2013-04-03
After installing Ubuntu Studio 12.10, my computer is somewhat unstable. It will freeze randomly, without giving any type of error. I'm hoping the culprit is the low latency kernel, since I previously had Ubuntu 12.04 running with no issues. I do not need the specialized kernel since I am using the distro for processing photographs.

How can I change to the generic Kernel?

Thanks in advance for any help!

---

### Post by slickymaster on 2013-04-03
You can start here: [UbuntuStudio/RealTimeKernel]("http://UbuntuStudio/RealTimeKernel")

---

### Post by ibjsb4 on 2013-04-03
You could use [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") to install different kernels.

[ATTACH=CONFIG]240915[/ATTACH]

---

### Post by tgalati4 on 2013-04-03
[https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

---

### Post by cjhill1836 on 2013-04-04
Thanks For the help everyone, I was able to switch to the generic kernel with Synaptic Package Manager. Seems stable so far, and I learned a little about the kernels in the process.

Cheers!

---

### Post by ibjsb4 on 2013-04-04
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by zequence on 2013-04-04
> **cjhill1836 said:**
> Thanks For the help everyone, I was able to switch to the generic kernel with Synaptic Package Manager. Seems stable so far, and I learned a little about the kernels in the process.

Cheers!

I'd just like to point out that there really is practically no difference between linux-generic and linux-lowlatency. So, it is extremely unlikely that you will encounter stability issues with only one of the two.

However, if you are not doing low latency audio work, you might not have any need of linux-lowlatency. linux-lowlatency may require more battery power. Also, it has a bit slower throughput (about 10% decrease in throughput). But, the latter is mostly a problem for big servers.

---

### Post by shaone on 2014-03-10
I recently installed the lowlatency kernal (for audio production purposes) and my laptop is noticeably sluggish since then (lenovo B570 i5 with ubuntu 13.10).

How do I switch back to generic using either apt-get or synaptics?
Or even create a boot option to load into either generic or lowlatency, if such a thing is possible?

After reading through suggested links I see a lot of info about kernels themselves but not much instruction about how to manage/change them, not that I understand anyways.

Any help (simple step guide ideally) would be much appreciated!

Thanks
Sean

---

### Post by jejeman on 2014-03-10
Boot option is already set up in GRUB.
Just choose what you want.

---

### Post by brianmc on 2014-03-13
> **shaone said:**
> I recently installed the lowlatency kernal (for audio production purposes) and my laptop is noticeably sluggish since then (lenovo B570 i5 with ubuntu 13.10).

How do I switch back to generic using either apt-get or synaptics?

To simply install the current generic kernel:[INDENT][FONT=courier new]**$***** sudo apt-get update && sudo apt-get install linux-generic***[/FONT]
[/INDENT]
> **shaone said:**
>  Or even create a boot option to load into either generic or lowlatency, if such a thing is possible?

After reading through suggested links I see a lot of info about kernels themselves but not much instruction about how to manage/change them, not that I understand anyways.

If all you have on the system is Ubuntu, by default you'll not get the option to select a specific kernel image on boot. You should be able to hold down 'Shift' to get the menu during bootup, or you can edit [FONT=courier new]*/etc/default/grub*[/FONT] and force its display.

I'd use nano to edit that:[INDENT][FONT=courier new]**$***** sudo nano /etc/default/grub***[/FONT]
[/INDENT]
If you place a '[FONT=courier new]*#*[/FONT]' before the two [FONT=courier new]*GRUB_HIDDEN_TIMEOUT*[/FONT] lines, then the menu will be displayed every time you boot the system. Alternate kernels may-well be rolled up in a sub-menu; but, your changes won't be visible until you regenerate the boot components of Grub:[INDENT][FONT=courier new]**$***** sudo update-grub***[/FONT]
[/INDENT]

If you've never seen the list of available kernels at boot, I'd not be surprised if you've several old ones left. Simplest way to get rid of old/unused images is with **[FONT=fixedsys]*Synaptic*[/FONT]**. Select packages by *Status: Installed*, and start typing the kernel image number(s) in to find the removable old ones (eg: '*3.11.0-*').

If this solves your issues, please follow the instructions to [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

