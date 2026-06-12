---
title: "Upgrade to 10.04 under Hyper-V screen now scrolls really slow"
date: 2010-05-06
forum: Server Platforms
---

### Post by prevoj on 2010-05-06
I have a virtual machine that was running Ubuntu Server 9.10 under Hyper-V on Windows Server 2008 R2 and the performace was acceptable. I run it in text mode with no X windows. I use it for LAMP. I upgraded to 10.04 and now the console is almost unusable it is sooo slow. It starts booting and text is painting fast and then something happens to the video. The screen goes to green, draws a few vertical lines, then clears back to a black screen but you can tell it is in a new video mode and the rest of the boot process and logging in and using the system is horrible because scrolling and redrawing of the screen crawls. Never had this problem in 9.10.
 
I'm sure that it is a "flipping from a text to a graphic text mode" issue at some point during the boot process. I've tried playing with kernel options (vga and nomodeset) but neither helps. When it gets about half way through the boot, something is making it change and then I'm screwed.
 
Any ideas would be greatly appreciated. I enabled ssh and I can ssh in with no problem. Performance is great so it is definitely the console now being in a "graphics mode" kind of issue. I can ssh but sometimes you still have to use the console and it's terrible!

---

### Post by cariboo on 2010-05-06
Run top from the prompt to see what is using all your resources.

---

### Post by prevoj on 2010-05-06
> **cariboo907 said:**
> Run top from the prompt to see what is using all your resources.
 
I already checked that and the system is completely idle. I sure it's due to the video changing from text to a non-text mode and then Hyper-V is really slow supporting the virtualized video. Like I said, if I ssh in, everything is fine.
 
So I guess my question is, what would switch me away from vga text mode half way through the boot to a vga graphics mode even though I have used the vga=normal nomodeset kernel options and I'm not running X.

---

### Post by Cosma on 2010-05-06
the same happens when running 10.04 server in kvm. the screen updates very slow (maybe because of plymouth?).

---

### Post by Cosma on 2010-05-11
i just installed 10.04 server on vmware esx4.0 and noticed the same problem

---

### Post by aesux on 2010-07-29
A clean install of a VM under Windows Server 2008 R2 using 10.4 server edition 64 bits, make the same video effect.

No one has detected where is the problem?

Thanks

---

### Post by babarehner on 2010-11-10
Try disabling the frame buffer- [http://www.babarehner.com/ewrench1011/VirtualMachines/hyperv-ubuntu/UbuntuLAMP4.0.pdf](http://www.babarehner.com/ewrench1011/VirtualMachines/hyperv-ubuntu/UbuntuLAMP4.0.pdf)

Cheers

---

### Post by JimLiu on 2010-12-20
I have this problem for 10.04 on Hyper-V as well. But it seems to be fixed in 10.10. FYI.

---

