---
title: "Control nvidia GPU fan speeds"
date: 2012-03-05
forum: Server Platforms
---

### Post by Picchioni on 2012-03-05
Hi All,
I'm hoping maybe someone might be in a similar situation and can provide some insight.

I'm utilizing 4 evga GTX580 Superclocked cards in a 100% headless Ubuntu Server 11.10 x64 environment for use with CUDA  From what I've been reading it essentially takes an act of god to be able to tweak the fan speed settings within linux when X is installed, and appears to be next to impossible if you're in a 100% headless environment.
 
Does anyone have an idea on how to manually tweak the fan speeds in a way that doesn't involve X?

I took a look at this, which is written for RedHat Based Distros:
[http://sites.google.com/site/akohlmey/random-hacks/nvidia-gpu-coolness](http://sites.google.com/site/akohlmey/random-hacks/nvidia-gpu-coolness)

I'm wondering if this can be applied to a Debian/Ubuntu Style environment?

---

### Post by Cheesemill on 2012-03-06
The only way that I have managed this is to connect my GPU to a Windows machine and flash it's BIOS with custom settings.

Like you I have found it impossible to control the fans using software under Ubuntu.

---

### Post by Picchioni on 2012-03-06
> **Cheesemill said:**
> The only way that I have managed this is to connect my GPU to a Windows machine and flash it's BIOS with custom settings.

Like you I have found it impossible to control the fans using software under Ubuntu.

How did you go about flashing the bios with custom settings?

---

### Post by jawilljr on 2012-03-06
[Manual Fan Control for nVIDIA Settings](http://en.gentoo-wiki.com/wiki/Nvidia#Manual_Fan_Control_for_nVIDIA_Settings)

Hope this helps...

Jerry

---

### Post by haqking on 2012-03-06
I think this is exactly what you are after

[https://sites.google.com/site/akohlmey/random-hacks/nvidia-gpu-coolness](https://sites.google.com/site/akohlmey/random-hacks/nvidia-gpu-coolness)

---

### Post by d4m1r on 2012-03-06
It definitely is possible, I can manually and dynamically change my GTX260's fan speed via command line. Google "ubuntu nvclock" :)

---

### Post by Cheesemill on 2012-03-07
> **d4m1r said:**
> It definitely is possible, I can manually and dynamically change my GTX260's fan speed via command line. Google "ubuntu nvclock" :)

Possible with a GTX260, but nvclock doesn't support 4xx or 5xx series GPU's.

---

### Post by Grenage on 2012-03-07
Failing that, the low-tech solution is a variable resistor 'switch'.

---

### Post by average650 on 2012-03-07
I am having a similar problem, but I have 2 headless cards (gtx580s) and 1 card connected to dual monitors(8400gs). 

I've used the page that haqking linked too and it seems very close to what I need, but when I try to install and run the code provided, I get an error that says gpu0 is already connected to an x server. I looked briefly through the code but I don't know enough to figure out how to edit to to ignore that gpu and only affect the others. 

Could anyone provide some advice or assistance here?

---

