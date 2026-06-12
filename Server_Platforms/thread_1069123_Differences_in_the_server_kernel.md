---
title: "Differences in the server kernel"
date: 2009-02-13
forum: Server Platforms
---

### Post by chmac on 2009-02-13
Hola,

I'm considering switching to the server kernel so as to get PAE support on my Lenovo X301 laptop (with 128Gb solid state drive). I've read the a [two]("http://www.serverwatch.com/tutorials/article.php/3715071") ["]page]("http://http://www.serverwatch.com/sreviews/article.php/3716396) comparison of the two kernels, and the [Ubuntu server kernel info]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel"). I'm still not fully clear on the differences between the server and the regular kernel.

Can anyone else shed any light on this?

I use my laptop as a general purpose desktop (web browsing, skype, flash, office, etc) plus some development work (I host a few VMs, Zend Studio). From the two comparisons it sounds like the server kernel is better for VMs ([second article under Leaky IPC Namespaces]("http://http://www.serverwatch.com/sreviews/article.php/3716396/virtu")) but the desktop kernel has a higher interrupt per second level ([first article under Ticks and HZ]("http://www.serverwatch.com/tutorials/article.php/3715071/v")). Sounds to me like one advantage, one disadvantage.

Is there anything else I should be aware of before switching my laptop to use the server kernel?

---

### Post by cmnorton on 2009-02-15
I like this post, because it has asked a lot of other questions. As to using your desktop as a workstation -- I cannot in good faith say my maxed out Lenovo Thinkpad T61p is really a server as opposed to a low or medium-end work station. However, it does the job well enough. I base my opinion based on empirical evidence; that is just make sure you have enough hardware resources, especially for VM. 

My take on the kernel differences are more for when you take that Ubuntu server and make it a full blown production system, and even, then when that production system is exposed to the internet or a very large corporate intranet. A higher frequency of interrupts for desktop might logically point to helping X-based applications get serviced quickly.

---

### Post by chmac on 2009-02-15
I wonder if the lower tick rate will actually reduce power consumption on my laptop. My only concerns with speedy response are that audio and video play smoothly.

I plan to try the server kernel before upgrading to 2Gb of RAM. If it goes well, I'll hopefully upgrade my memory in a week or so. I'll try to post my experiences back here.

---

