---
title: "Pan P8 ?"
date: 2010-10-16
forum: System76 Support
---

### Post by zaphod777 on 2010-10-16
Have you guys checked out the Sager NP5135 for your next model?
[http://www.sagernotebook.com/index.php?page=product_info&model_name=NP5135](http://www.sagernotebook.com/index.php?page=product_info&model_name=NP5135)

It looks like what everyone has been wanting. It has USB 3.0 plus it has a nVidia NVIDIA® GeForce™ GT 425M GPU with 1GB of RAM.

The only downside I think is since it has the optimus technology for so you can switch from the integrated video card or the nVidia card and I don't think Ubuntu or Linux in general can really handle switching like that without restarting X.

---

### Post by 3Miro on 2010-10-18
> **zaphod777 said:**
> 
The only downside I think is since it has the optimus technology for so you can switch from the integrated video card or the nVidia card and I don't think Ubuntu or Linux in general can really handle switching like that without restarting X.

The new Linux kernel has that option, I don't know how well it works yet, I think it is still experimental. If the Kernel has it, the X-server will have it soon (if it is not already there).

---

### Post by zaphod777 on 2010-10-25
> **3Miro said:**
> The new Linux kernel has that option, I don't know how well it works yet, I think it is still experimental. If the Kernel has it, the X-server will have it soon (if it is not already there).

do you have any links for that? Everything I have found so far is that it is that we won't see it anytime soon.

---

### Post by 3Miro on 2010-10-26
This is what I have form 2.6.34 Gentoo kernel (now there is 2.6.36). It says the kernel can switch the drivers, however, the X server cannot, you have to logout/login to do this.

---

### Post by 3Miro on 2010-10-26
I am definitely waiting for a new System76 model, every day I am getting more an more sick of my current garbage laptop. However, I am afraid of the ATI in the current Pangolin and Serval is a bit out of my price range (it also apparently requires proprietary drivers for the wifi).

---

### Post by zaphod777 on 2010-11-19
> **3Miro said:**
> This is what I have form 2.6.34 Gentoo kernel (now there is 2.6.36). It says the kernel can switch the drivers, however, the X server cannot, you have to logout/login to do this.

I guess Wayland will take care of this but I don't think we will see Wayland until 11.10 at least.

---

