---
title: "Can I use virtualbox on a netbook?"
date: 2011-07-16
forum: Virtualisation
---

### Post by dioxholster on 2011-07-16
I want to run windows, so I thought of using virtualbox because I can't do a dual boot after I already have had Ubuntu installed. So will windows run without slowing down the computer? And how does it work, i never really tried it before? Is it a better option than wine?

---

### Post by snowpine on 2011-07-16
Sure you can do dual boot even though you installed Ubuntu first; there are tutorials all over these forums and also on the official help pages at ubuntu.com. :)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

To answer your question, YES you can run VirtuaBox on your netbook. Performance will not be as good as a dual boot, because the system resources are divided between the "host" (Ubuntu) and the "guest" (Windows). But if your netbook has a powerful processor and plenty of RAM, and your needs are modest (no multimedia/games/etc.) then you may be satisfied with the VirtualBox solution. :)

---

### Post by dioxholster on 2011-07-16
I'll see if i can do the dual boot thing, even though it sounds complicated.

---

### Post by snowpine on 2011-07-16
> **dioxholster said:**
> I'll see if i can do the dual boot thing, even though it sounds complicated.

Unfortunately when Microsoft desgined the Windows installer, they did not take into consideration that customers might want to dual-boot with other operating systems. I agree this adds an extra level of complexity, but just carefully follow the instructions step-by-step and you should be fine.

If you had installed Windows first and then Ubuntu, it would not be complicated at all, as the Ubuntu installer is "smart" enough to detect Windows and automatically give you the dual-boot option. :)

---

### Post by fjgaude on 2011-07-16
I've been running a Dell netbook with Ubuntu for two or more years with VMware Player running a Windows XP VM. No 3D graphics of course, but the speed of it all is acceptable. After all a netbook usually is not that fast to begin with, eh?

---

### Post by CharlesA on 2011-07-17
Running a VM on top of a running OS on a netbook is possible, but it might be a bit slugging depending on how powerful the CPU is and how much memory you have.

I'd probably dual boot in that case.

---

### Post by Lars Noodén on 2011-07-17
> **snowpine said:**
> Unfortunately when Microsoft desgined the Windows installer, they did not take into consideration that customers might want to dual-boot with other operating systems. 
Just a point of information: Unfortunately they appear to have been aware of this for a long time and the problems are probably intentional.  [BeOS](http://www.birdhouse.org/beos/byte/30-bootloader/) ran into the problem long ago.  Right now, nothing can be done about the lack of cooperation, so the only work around is to either install Windows first on the HD and then install Ubuntu, or else use Windows in Qemu or VirtualBox.  

However, if there are just one or two applications that are the reason, then it might be easier and much better performance with [WINE](https://help.ubuntu.com/community/Wine#Installing%20Windows%20Applications%20With%20Wine).

---

### Post by snowpine on 2011-07-17
> **Lars Noodén said:**
> Right now, nothing can be done about the lack of cooperation, so the only work around is to either install Windows first on the HD and then install Ubuntu, or else use Windows in Qemu or VirtualBox.  

That's simply not true. It is possible to install Windows after Ubuntu. See the how-to I linked to in post #2. :)

---

### Post by Lars Noodén on 2011-07-17
> **snowpine said:**
> That's simply not true. It is possible to install Windows after Ubuntu. See the how-to I linked to in post #2. :)

Yes, and the How-To's section on installing Ubuntu after Windows seems much simpler than the other way around which appears to involve replacing the MBR. ;)

---

### Post by snowpine on 2011-07-17
> **Lars Noodén said:**
> Yes, and the How-To's section on installing Ubuntu after Windows seems much simpler than the other way around which appears to involve replacing the MBR. ;)

That's exactly what I said in post #4. ;)

---

### Post by Lars Noodén on 2011-07-17
> **snowpine said:**
> That's exactly what I said in post #4. ;)

Which reinforces the point made in the link posted in #7 about BeOS.  :)

Regardless, if possible, it is better to stick with WINE for both performance and maintenance reasons.

---

### Post by dioxholster on 2011-07-20
I gave the virtualbox a go, but its not working, the installation doesnt come up telling me I need a 32bit display thing and has a black screen. There isnt a 32bit option in the settings menu. If I can't figure this one out I will try to dual boot.

---

### Post by CharlesA on 2011-07-20
> **dioxholster said:**
> I gave the virtualbox a go, but its not working, the installation doesnt come up telling me I need a 32bit display thing and has a black screen. There isnt a 32bit option in the settings menu. If I can't figure this one out I will try to dual boot.
Bump up the amount of video memory allotted to the guest.

---

### Post by dioxholster on 2011-07-20
> **CharlesA said:**
> Bump up the amount of video memory allotted to the guest.


i tried that to like 50mb but still nothing. 

edit: nevermind i gave it 96mb it seems to be working.

---

### Post by Jake.Debord on 2011-07-21
> **snowpine said:**
> Unfortunately when Microsoft desgined the Windows installer, they did not take into consideration that customers might want to dual-boot with other operating systems. I agree this adds an extra level of complexity, but just carefully follow the instructions step-by-step and you should be fine.

If you had installed Windows first and then Ubuntu, it would not be complicated at all, as the Ubuntu installer is "smart" enough to detect Windows and automatically give you the dual-boot option. :)

"It's not a bug, It's a feature!"

:P[IMG]http://www.oraclealchemist.com/wp-content/uploads/2008/07/bug-feature.jpg[/IMG]

---

