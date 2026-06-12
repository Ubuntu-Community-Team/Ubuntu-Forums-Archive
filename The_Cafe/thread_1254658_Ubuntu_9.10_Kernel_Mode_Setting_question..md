---
title: "Ubuntu 9.10 Kernel Mode Setting question."
date: 2009-08-31
forum: The Cafe
---

### Post by wildman4god on 2009-08-31
I was reading up on kernel mode setting, it seems pretty cool, but my question is if it only works with "some intel graphics cards" what does that mean for the 80-90% of computers that don't have intel cards? does that mean we get text boot, or will it fall back to usplash?

---

### Post by bl33d on 2009-08-31
> **wildman4god said:**
> I was reading up on kernel mode setting, it seems pretty cool, but my question is if it only works with "some intel graphics cards" what does that mean for the 80-90% of computers that don't have intel cards? does that mean we get text boot, or will it fall back to usplash?

a lot of pcs have intel :P

---

### Post by Tibuda on 2009-08-31
> **wildman4god said:**
> I was reading up on kernel mode setting, it seems pretty cool, but my question is if it only works with "some intel graphics cards" what does that mean for the 80-90% of computers that don't have intel cards? does that mean we get text boot, or will it fall back to usplash?

usplash is going to be replaced by xsplash

---

### Post by gletob on 2009-08-31
> **bl33d said:**
> a lot of pcs have intel :P

"Intel Graphics Card"

not processors like intel/AMD/VIA

But GPUs like NVIDIA/ATI/Intel

And why would that be an excuse to exclude others?

---

### Post by wildman4god on 2009-08-31
> **bl33d said:**
> a lot of pcs have intel :P

really, most of the pcs I see in stores and the internet advertise nvidia and ati, I think I saw an intel based laptop once or twice on dell's website, at least in america. and of all the pcs I have owned I never had an intel card. But it still doesn't answer my question, my computers have either nvidia or ati, what happens to the boot on mine, I have heard that it may have problems starting up if KMS is not supported.

---

### Post by bl33d on 2009-08-31
> **gletob said:**
> "Intel Graphics Card"

not processors like intel/AMD/VIA

But GPUs like NVIDIA/ATI/Intel

i know what he meant

---

### Post by bl33d on 2009-08-31
> **wildman4god said:**
> really, most of the pcs I see in stores and the internet advertise nvidia and ati, I think I saw an intel based laptop once or twice on dell's website, at least in america. and of all the pcs I have owned I never had an intel card. But it still doesn't answer my question, my computers have either nvidia or ati, what happens to the boot on mine, I have heard that it may have problems starting up if KMS is not supported.

but most pcs come with integrated graphics. and most of them are intel

---

### Post by wildman4god on 2009-08-31
not mine, all my pcs and laptops have integrated grapchis and they are either ati or nvidia.

---

### Post by bl33d on 2009-08-31
> **wildman4god said:**
> not mine, all my pcs and laptops have integrated grapchis and they are either ati or nvidia.

intel is the biggest integrated graphics producer. my netbook is intel :P

---

### Post by wildman4god on 2009-08-31
> **bl33d said:**
> intel is the biggest integrated graphics producer. my netbook is intel :P

ofcourse netbooks, but I am talking about desktops and laptops, I don't own a netbook yet.

---

### Post by bl33d on 2009-08-31
> **wildman4god said:**
> ofcourse netbooks, but I am talking about desktops and laptops, I don't own a netbook yet.

they are the largest producer of integrated chips for desktops/laptops/netbooks. everything :P

---

### Post by wildman4god on 2009-08-31
> **bl33d said:**
> they are the largest producer of integrated chips for desktops/laptops/netbooks. everything :P

okay but my problem remains, I don't have intel graphics what happens when I try and boot the next version of ubuntu and my nvidia integrated graphics don't support it?

---

### Post by gletob on 2009-08-31
> **bl33d said:**
> they are the largest producer of integrated chips for desktops/laptops/netbooks. everything :P

Still doesn't make it right to switch to something that'll leave ATI/NVIDIA users in the cold.  And largest producer doesn't mean that there aren't a TON of PCs that use some other brand of graphics.  Your previous statements are true but your logic is seriously wrong.

BTW:If you keep sticking your :P out, it's bound to get cut off.

---

### Post by bl33d on 2009-08-31
> **gletob said:**
> Still doesn't make it right to switch to something that'll leave ATI/NVIDIA users in the cold.  And largest producer doesn't mean that there aren't a TON of PCs that use some other brand of graphics.  Your previous statements are true but your logic is seriously wrong.

its not logic. its a true statement. fedora 12 alpha has kms for nvidia.ati and intel.

---

### Post by bl33d on 2009-08-31
> **wildman4god said:**
> okay but my problem remains, I don't have intel graphics what happens when I try and boot the next version of ubuntu and my nvidia integrated graphics don't support it?

it just falls back 2 the old way.

---

### Post by wildman4god on 2009-08-31
> **bl33d said:**
> it just falls back 2 the old way.

you mean usplash or xsplash or what ever it's called, okay that works, I hope they get more complete support by the next LTS

---

### Post by bl33d on 2009-08-31
> **wildman4god said:**
> you mean usplash or xsplash or what ever it's called, okay that works, I hope they get more complete support by the next LTS

oh u are asking about the splash screen. as far as i know xsplash doesnt need kms to run. kms just makes stuff smoother

---

### Post by wildman4god on 2009-08-31
> **bl33d said:**
> oh u are asking about the splash screen. as far as i know xsplash doesnt need kms to run. kms just makes stuff smoother


Okay, I was wondering because if unsupported cards made the boot process go back to text base boot it would suck and scare the heck out of new potential ubuntu users.

---

### Post by bl33d on 2009-08-31
> **wildman4god said:**
> Okay, I was wondering because if unsupported cards made the boot process go back to text base boot it would suck and scare the heck out of new potential ubuntu users.

if i understand ok. xsplash needs xorg to work. usplash doesnt

---

### Post by wildman4god on 2009-08-31
> **bl33d said:**
> if i understand ok. xsplash needs xorg to work. usplash doesnt

so in other words, if your computer can run desktop ubuntu (which uses xorg) it can also run xsplash, okay cool, but 10 second boot provided by KMS would still be nice to have on all cards, I can see ati drivers coming in the spring release and hopefully nvidia by next fall, however I am wondering if nvidia will support KMS at all because I was on their forums and people were wondering about KMS support and a nvidia official said that they wouldn't support it because it would require too much work and something about... 

"Kernel modesetting was specifically designed to be incompatible with the NVIDIA driver.

There are no plans to use DRI, TTM, or Gallium3D since the driver already has its own code for what those components provide."

you can check the site [here]("http://www.nvnews.net/vbulletin/showthread.php?t=113645")

---

### Post by bl33d on 2009-08-31
> **wildman4god said:**
> so in other words, if your computer can run desktop ubuntu (which uses xorg) it can also run xsplash, okay cool, but 10 second boot provided by KMS would still be nice to have on all cards, I can see ati drivers coming in the spring release and hopefully nvidia by next fall, however I am wondering if nvidia will support KMS at all because I was on their forums and people were wondering about KMS support and a nvidia official said that they wouldn't support it because it would require too much work and something about... 

"Kernel modesetting was specifically designed to be incompatible with the NVIDIA driver.

There are no plans to use DRI, TTM, or Gallium3D since the driver already has its own code for what those components provide."

you can check the site [here]("http://www.nvnews.net/vbulletin/showthread.php?t=113645")

fedora 12 has kms through noveau. i dont know if they can make it switch from nouveau to the nvidia prop driver.

---

### Post by Frak on 2009-08-31
> **bl33d said:**
> i know what he meant

> **bl33d said:**
> but most pcs come with integrated graphics. and most of them are intel

I get about 5 computers in my shop every day. In an entire week, maybe 4 of them have Intel integrated graphics, and 3 of those 4 use add-in graphics. Even laptops rarely have Intel Graphics, with the exception of netbooks.

> **wildman4god said:**
> so in other words, if your computer can run desktop ubuntu (which uses xorg) it can also run xsplash, okay cool, but 10 second boot provided by KMS would still be nice to have on all cards, I can see ati drivers coming in the spring release and hopefully nvidia by next fall, however I am wondering if nvidia will support KMS at all because I was on their forums and people were wondering about KMS support and a nvidia official said that they wouldn't support it because it would require too much work and something about...

Both ATi and Nvidia prop. drivers will fail to run XSplash. Since the drivers are proprietary, they are limited to the userspace they run in. Everything in userspace is started long after the splash.

---

### Post by bl33d on 2009-08-31
> **Frak said:**
> I get about 5 computers in my shop every day. In an entire week, maybe 4 of them have Intel integrated graphics, and 3 of those 4 use add-in graphics. Even laptops rarely have Intel Graphics, with the exception of netbooks.



Both ATi and Nvidia prop. drivers will fail to run XSplash. Since the drivers are proprietary, they are limited to the userspace they run in. Everything in userspace is started long after the splash.

o ok i didnt know that. but cant they make nouveau switch to the prop driver after the boot?

---

### Post by Frak on 2009-08-31
> **bl33d said:**
> o ok i didnt know that. but cant they make nouveau switch to the prop driver after the boot?
I don't see why not. It would just load the Nouveau driver, rmmod it when the userspace loads, then modprobe and depmod the Nvidia driver.

Seems like a lot to do for a simple animation, though.

---

### Post by bl33d on 2009-08-31
> **Frak said:**
> I don't see why not. It would just load the Nouveau driver, rmmod it when the userspace loads, then modprobe and depmod the Nvidia driver.

Seems like a lot to do for a simple animation, though.

it does look good in fedora 12 though :D

---

### Post by joey-elijah on 2009-08-31
> **Frak said:**
> I don't see why not. It would just load the Nouveau driver, rmmod it when the userspace loads, then modprobe and depmod the Nvidia driver.

Seems like a lot to do for a simple animation, though.

YOWCH! That's pretty hefty, like you say, for a simple boot screen.

I've always used Nvidia by choice, though my netbook has some lame intel integrated semi-muscle in it, but i'd hate to feel as though the "ubuntu desktop experience" was limited to a specific combination of "hardware".

---

### Post by wildman4god on 2009-08-31
> **Frak said:**
> I get about 5 computers in my shop every day. In an entire week, maybe 4 of them have Intel integrated graphics, and 3 of those 4 use add-in graphics. Even laptops rarely have Intel Graphics, with the exception of netbooks.



Both ATi and Nvidia prop. drivers will fail to run XSplash. Since the drivers are proprietary, they are limited to the userspace they run in. Everything in userspace is started long after the splash.

okay then back to my original question, if my nvidia graphics card is not supported by kms then what will my boot look like, will it be usplash or text, and if it's just text then that's poor planning and work by the developers. they shouldn't include a technolgy thats limited to a certain manufacturer.

---

### Post by cdekter on 2009-08-31
Your question has already been answered - if your graphics card does not support KMS, it will automatically fall back to using usplash. In other words, it will function exactly as it does in 9.04. 

This would not be the first time that the kernel developers made the decision on everyone's behalf to break compatibility with proprietary software. They do so love their little games...

---

