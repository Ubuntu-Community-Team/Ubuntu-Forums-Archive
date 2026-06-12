---
title: "bash screen resolution"
date: 2011-02-08
forum: Server Platforms
---

### Post by ibompotsaris on 2011-02-08
Hello all, I am just coming from a clean install of Lucid Server x64 on a desktop configuration. No problems really but for one.

With no GUI installed -something I wish to remain as is- I am having difficulties browsing through bash due to low resolution. 

So the question is: "how can I go to a higher screen resolution?"

Is installing GPU drivers due to solve the problem?

---

### Post by CharlesA on 2011-02-08
I just SSH in and maximize that window. Haven't found a way to increase the resolution, unfortunately.

---

### Post by ibompotsaris on 2011-02-08
&#921; know there is a way though and just for the merit of learning how I think I must insist a bit. Thanks though for the answer.

---

### Post by cipherboy_loc on 2011-02-08
While I don't have an nVidia graphics card (the default ATI in my Dell), and the resolution automatically gets adjusted during boot, something that I have found to be of some help is to change the resolution of the GRUB boot loader. If you set that to a resolution closer to that of your monitor, if might stick during the boot process.

Also, I think there is a way to pass a resolution to the kernel on boot...

Cipherboy

---

### Post by ibompotsaris on 2011-02-08
> **cipherboy_loc said:**
> While I don't have an nVidia graphics card (the default ATI in my Dell), and the resolution automatically gets adjusted during boot, something that I have found to be of some help is to change the resolution of the GRUB boot loader. If you set that to a resolution closer to that of your monitor, if might stick during the boot process.

Also, I think there is a way to pass a resolution to the kernel on boot...

Cipherboy


Starting to sound better... This last thing about the kernel rings a bell. Thanks...
Any chance for a brief "how to"?

---

### Post by cipherboy_loc on 2011-02-08
[http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php)

For the list of kernel options. More or less (you will have to look up the numbers), but you have to edit the GRUB_CMDLINE_LINUX_DEFAULT to include the specified VGA mode. I think you can also change the GRUB_CMDLINE_LINUX line to specify the correct VGA mode also.


Cipherboy

---

### Post by towheedm on 2011-02-08
> **cipherboy_loc said:**
> [http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php)

For the list of kernel options. More or less (you will have to look up the numbers), but you have to edit the GRUB_CMDLINE_LINUX_DEFAULT to include the specified VGA mode. I think you can also change the GRUB_CMDLINE_LINUX line to specify the correct VGA mode also.


Cipherboy

This method has been deprecated long ago.  To pass grub's resolution on to the kernel use the GRUB_GFXPAYLOAD_LINUX command.

---

### Post by matt_symes on 2011-02-08
Hi

I believe this is what you are looking for.

[http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html)

Don't forget to sudo update-grub

Kind regards

---

### Post by ibompotsaris on 2011-02-09
> **matt_symes said:**
> Hi

I believe this is what you are looking for.

[http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html)

Don't forget to sudo update-grub

Kind regards

Worked like a charm plus gave me an insight with some of the inner workings of GRUB! I really, really want to thank you all guys for your replies but of course BEST regards to matt_symes!

---

