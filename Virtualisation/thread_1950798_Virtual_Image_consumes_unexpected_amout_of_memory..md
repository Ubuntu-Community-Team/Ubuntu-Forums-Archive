---
title: "Virtual Image consumes unexpected amout of memory."
date: 2012-04-01
forum: Virtualisation
---

### Post by nosmadar on 2012-04-01
I'm running Lucid (10.4) server and using KVM. My server is x64 with 12GB of memory. I created 2 VMs, both using Kubuntu 8.10.  I allocated 2GB ram to the first image and 1GB to the second VM. 
However the memory consumption in the server is about 2x that. almost 7GB and neither of the VMs is actually running. (Normal usage before the VMs was about 1.5 GB of memory.

So I have 2 questions.

1)Is there anyway to keep KVM from hanging on to all of that memory when the VMs are shut down.

2) Will they really always consume that much memory when running?  By comparison, I used virtual box on my little Acer laptop to create a VM with 1GB of memory and the laptop only *has* 1.6 GB physical memory and there is memory left over when that VM is running.

---

### Post by Cheesemill on 2012-04-01
How are you measuring your memory usage?
Maybe you are counting cached memory as well.

---

### Post by nosmadar on 2012-04-01
> **Cheesemill said:**
> How are you measuring your memory usage?
Maybe you are counting cached memory as well.

Gee, how did you know.  :-)

It turns out that indeed, 5.25 GB of the memory in use is cached memory, which I had not noticed until now. 
 
OK, so is there a remedy, such as a KVM setting I can apply to the KVM or to the images to prevent this from happening.  Or is this just how it works.  

I've pored over the KVM homepage, the QEMU web pages, the Virsh web pages and have found little or no discussion regarding how KVM manages memory. So any hints or explanations or places to go read explanations would be greatly appreciated.

---

### Post by nosmadar on 2012-04-01
I think I've got a handle on this now.  Found the following web site:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Which explained everything.

Sorry for the newb question.
Thanks,
N.

---

