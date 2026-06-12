---
title: "Major security hole found in Linux kernel"
date: 2011-04-01
forum: The Cafe
---

### Post by mmix on 2011-04-01
confirmed?

[http://it.toolbox.com/blogs/locutus/major-security-hole-found-in-linux-kernel-45303](http://it.toolbox.com/blogs/locutus/major-security-hole-found-in-linux-kernel-45303)

> 
It didn't take me long to narrow down the problem being a floating pointer in the dma drivers section of the kernel. I had a look further and saw that in the dma channel registers for the intel chipset (the chipset the motherboard uses in this netbook) in the union called intel_mid_dma_cfg_lo there is an element called reser2 with a default value of 6.

 

In the code of this dma driver reser2 never goes higher than 5 yet the driver for the graphics card was trying to access 6 when the scan rate combined with the netbooks native screen resolution and a fully saturated color, such as white or blue was displayed.

 

So I had a look into what happens when reser2 is called as 6 and found the floating pointer. As this is a floating pointer it can be directed to any part of the computers memory and access the functions there. This means that I could very easily use this pointer to access ring 0 mode of the kernel and have root access to any part of the computer.

This is a major security hole as it is very easy to exploit. I checked and it is in all the 2.6 series of the kernel. It is not in the 2.4 series as they use the older dma method. I have sent a patch to kernel.org and I hope they don't ignore me as they did with my ATI rage patch. This is too important and has the potential to botnet every current Linux distribution installed today.


---

### Post by 3rdalbum on 2011-04-02
Would require malicious code to be running already, so no it's not likely to "botnet every current Linux distribution".

---

