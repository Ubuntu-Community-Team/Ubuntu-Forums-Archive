---
title: "Make VirtualBox run FAST!! Possible?"
date: 2015-08-19
forum: Virtualisation
---

### Post by 777funk on 2015-08-19
I tried Win 7 in VirtualBox and it was almost unusable slow. Certainly not something I'd want to use for any length of time. I wasn't too worried since Xubuntu is my main OS...

Until Now. 

My wife needs to use Stamps.com and it isn't supported. So I need to use Windows. I figured I'd like to use VirtualBox but is there a way to make it run faster?

---

### Post by Bucky Ball on 2015-08-19
*Thread moved to **Virtualisation**.*

More RAM generally does it. How much do you currently have in the box?

---

### Post by 777funk on 2015-08-19
Thanks and thanks for the move. Sorry about that! Didn't know about the VM section. 

I have 8GB in the physical machine. I think I left it at 2GB when I setup the VM.

---

### Post by Bucky Ball on 2015-08-19
I don't know about Win7, but probably a gobbler. Set it at 3 or 4Gb and see what gives. I have Win7 and 4Gb, not as a VM, just a regular install.

PS: Where does stamps.com stall? As it's web based I'm trying to figure what is preventing it. Do you have a problem with Flash or something? Does it throw an error? :-k

I just had a fiddle and got as far as creating an account, which isn't far, but I am not in the US anyhow. :)

---

### Post by TheFu on 2015-08-21
Standard performance tuning for VMs: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)  Outside GPU stuff, 90% of native is possible with little effort. For heavy GPU things, I don't think you can use virtualbox - need VGA passthru which requires specific hardware, firmware, and GPU devices.

---

