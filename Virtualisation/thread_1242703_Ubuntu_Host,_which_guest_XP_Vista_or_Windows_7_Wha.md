---
title: "Ubuntu Host, which guest? XP Vista or Windows 7? What's fastest?"
date: 2009-08-17
forum: Virtualisation
---

### Post by edwardtilbury on 2009-08-17
I have a Toshiba Laptop

Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
3 Gigs of ram...
My OS is Ubuntu 64bit 9.04


What should I run as a guest windows OS?
I need speed... Excel , Visual Basic office stuff, light photoshop

I assume XP 32-bit is the fastest.. but maybe I'm wrong...
Would I benefit from running a 64bit version of Vista or Windows 7?

What has your experience been between the 3 OS's..?

Thanks!

---

### Post by SoftwareExplorer on 2009-08-17
I usually use XP because it isn't just plain ugly without transparency. Shallow reasoning, I know, but what applications run on 7 or Vista that don't on XP?

---

### Post by Scunizi on 2009-08-17
You won't be able to run 64bit anything in the guest unless the host is also 64 bit.  Win 7 is preferable over vista and maybe close to xp at this point.. try Virtualbox direct from their site.. easy install and easy setup..

---

### Post by SoftwareExplorer on 2009-08-17
You also might have to turn on 'virtualization features' in your bois for 64 bit.

---

### Post by edwardtilbury on 2009-08-18
My pc is 64 bit so I'll probably try windows 7 64 bit on my virtualbox when the final release comes out.

---

### Post by SoftwareExplorer on 2009-08-18
> **edwardtilbury said:**
> My pc is 64 bit so I'll probably try windows 7 64 bit on my virtualbox when the final release comes out.
The RTM(Release to manufacture), the last freely downloadable version is already out. They next version you will have to buy.

---

### Post by pdtpatrick on 2009-08-20
What Virtualization software are you using? Virtual Box? KVM or Xen? I use KVM with virt-manager, works great. XP and Vista runs just as good. Though as expected, vista takes a lot of memory and spikes the cpu here and there but that's foreseen. I like XP for now but i usually only put things in VM for testing purpose so you are more prone to find OSes like vista and Windows 7 and such as i'd like to see how they work :)

---

