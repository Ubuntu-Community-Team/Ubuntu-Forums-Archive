---
title: "Ubuntu and the AMD APU"
date: 2011-07-05
forum: The Cafe
---

### Post by AnnAni1234 on 2011-07-05
Hi everyone

I have been windows free for about 3 years and am loving it the reason for this post is I wanted to know two things

What does the release of the new APU platform mean for Linux in general?
     How will it impact functionality because my professor who only uses Linux says that the gpu is what is going to carry the APU and that Linux lacks the support for the gpu acceleration so it will be slow only using the CPU

I am probably going to get a lot of heat for this but in regards to gnome 3 why was the shell interface looked down upon from what i have seen in fedora it looks beautiful but I am only talking about the visual interface

and sorry if this in the wrong thread i am kind of new to this whole discussion i usually post tech questions

---

### Post by mcduck on 2011-07-06
Based on the Phoronix article & benchmarks, the new AMD processors and their built-in GPUs work just fine with Linux. Phoronix ran the benchmarks using Ubuntu 11.04.

The GPU isn't supported by open-source drivers, though, so you'll need to use AMD's proprietary driver with them.

[http://www.phoronix.com/scan.php?page=article&item=amd_llano_linux&num=1]("http://www.phoronix.com/scan.php?page=article&item=amd_llano_linux&num=1")

---

### Post by 3rdalbum on 2011-07-06
Isn't the APU just a GPU and a CPU on the one die? I fail to see how that would be so drastically different to having the GPU on a different physical part of the motherboard to the CPU.

Linux supports the GPU using proprietary drivers. In the future (probably soon...) it will support the GPU using open-source drivers, just like how it supports all the previous GPUs.

---

### Post by handy on 2011-07-06
AMD have given a great deal of help to the development of the open-source AMD driver stack, I expect that they will continue to do so.

---

### Post by mcduck on 2011-07-06
> **3rdalbum said:**
> Isn't the APU just a GPU and a CPU on the one die? I fail to see how that would be so drastically different to having the GPU on a different physical part of the motherboard to the CPU.

Linux supports the GPU using proprietary drivers. In the future (probably soon...) it will support the GPU using open-source drivers, just like how it supports all the previous GPUs.

CPU + whatever additional processors one might want to add to it. Like a GPU or some other specific-purpose accelerator.

The main difference would be smaller size, lower power consumption, and at least potentially better performance resulting from removing extra hardware, buses and wiring from between the CPU and GPU. And of course lower price as compared to producing two separate chips.

I'd see those AMD CPU's mainly as suitable for building very small-size computers with reasonable graphics capabilities and more CPU power than, for example, Atom-based system would have. Like a compact home theater computer that could also handle normal computing tasks and even play some games.

...and of course the laptop models should give reasonable graphics power for cheaper laptops, without having to go for more expensive separate GPU.

---

### Post by handy on 2011-07-06
iMac's & the like would also be suitable I think.

---

### Post by AnnAni1234 on 2011-07-14
People are missing my question 

I am asking if Ubuntu will be able to use the gpu acceleration because it cant do it as of yet the system would only rely on the cpu making it very slow?

that is what i am asking

---

### Post by mcduck on 2011-07-14
> **AnnAni1234 said:**
> People are missing my question 

I am asking if Ubuntu will be able to use the gpu acceleration because it cant do it as of yet the system would only rely on the cpu making it very slow?

that is what i am asking

Actually I answered that question already, even with a link to benchmark data about the performance. :D

The answer is yes, AMD's proprietary drivers do support the GPU part of Llano-family APUs.

---

### Post by ssam on 2011-07-14
once the opensource openCL implementation (clover) is ready then lots of opensource will able to take advantage of the GPU part to do work (not just graphics acceleration.)

if you are interested you can follow the blog of one of the developers [http://steckdenis.wordpress.com/](http://steckdenis.wordpress.com/)

---

