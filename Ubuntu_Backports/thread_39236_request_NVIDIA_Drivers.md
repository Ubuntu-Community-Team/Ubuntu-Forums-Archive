---
title: "request: NVIDIA Drivers"
date: 2005-06-03
forum: Ubuntu Backports
---

### Post by thechitowncubs on 2005-06-03
Are the new drivers going to be backported or are they going to be in the official repos?

---

### Post by jdong on 2005-06-04
Is there some really good reason to backport it?


Being a kernel module in main and all, I don't like building it unless absolutely necessary :)

---

### Post by Technoviking on 2005-06-04
[QUOTE=jdong]Is there some really good reason to backport it?


Being a kernel module in main and all, I don't like building it unless absolutely necessary :)[/QUOTE]
There are supposed to be some good speed increases, but I not sure if it is worth a backport. I will look it next week and see of the advantages or work mucking with the kernel.

Mike

---

### Post by jdong on 2005-06-04
well, I'm running a custom kernel, so I'll see about these "speed increases". Also, maybe power management improved? (hey, you can always be optimistic!)



As far as a backport... only when Breezy gets the new Nvidia.

---

### Post by thechitowncubs on 2005-06-04
Thanks for the replies... it would be nice, but not necessary.

---

### Post by tommi on 2005-06-05
i will also wait for a backport (laptop,gf2go, probs with 7174). Lets see, how long we will wait :)

---

### Post by sinbad782 on 2005-06-06
There's a few nice new features in these drivers, such as support for GPU overclocking etc. via Coolbits - see:

[http://www.phoronix.com/scan.php?page=article&item=185&num=1](http://www.phoronix.com/scan.php?page=article&item=185&num=1)

But again, it's probably not worth backporting these if there are going to be major problems elsewhere.

---

### Post by sinbad782 on 2005-06-06
Oops - wrong link. Here's the right one:

[http://www.phoronix.com/scan.php?page=article&item=197&num=1](http://www.phoronix.com/scan.php?page=article&item=197&num=1)

---

### Post by codejunkie on 2005-06-06
you could manually install the driver from nvidia im using it right now its working great i gained about 60fps :)  and it fixed some screen painting issues with my card.
i just changed "nvidia" to "vesa"  "nv" also works in the xorg.conf file restarted x with ctrl+alt+backspace removed nvidia-glx, linux-restricted-modules, and nvidia-settings installed the build-essential and kernel-headers package for my kernel, ctrl+alt+F1 then sudo su telinit 3 and killall gdm ran the installer when it finished changed /etc/X11/xorg.conf back to "nvidia" and it worked.
this might help somebody but don't blame me if something goes wrong cause what works for one might not work for the other.

---

### Post by MaX on 2005-06-07
[QUOTE=sinbad782]Oops - wrong link. Here's the right one:

[http://www.phoronix.com/scan.php?page=article&item=197&num=1](http://www.phoronix.com/scan.php?page=article&item=197&num=1)[/QUOTE]
 not to be picky or anything, but use the edit post feature

---

### Post by Cwiiis on 2005-06-07
[QUOTE=jdong]Is there some really good reason to backport it?


Being a kernel module in main and all, I don't like building it unless absolutely necessary :)[/QUOTE]
 I'd like to request Ubuntu packages of the 6629 drivers - The 7xxx series causes an X hang for many people (see [http://www.nvnews.net/vbulletin/showthread.php?t=31858](http://www.nvnews.net/vbulletin/showthread.php?t=31858)) and using the existing 6629 packages (from morgue) forces you to use an old kernel. Especially as nvidia no longer support 'legacy' (Geforce 2 Ultra and below) cards after version 7174, it'd be very helpful to have a maintained set of 6629 drivers, for people that suffer from this problem and still want render acceleration.

As a side note, for people that think render acceleration is unnecessary, Battle for Wesnoth is almost unplayably slow on my Athlon 1.2ghz machine (Geforce 2 Ultra) without it. Not to mention it stopping me from possibly using the nice Composite features in the future...

---

### Post by Gnobody on 2005-06-08
Please backport this, I cannot manually install this in my chrooted enviroment.   There are a ton of bug fixes and perfomance tweaks as well as OpenGL 2.0 support.

---

### Post by jdong on 2005-06-08
It's not in Breezy yet :(

I'll see what I can do :)

---

### Post by jdong on 2005-06-08
[quote=#ubuntu-devel]fabbione JohnDong: please do not backport the kernel or l-r-m[/quote]

Sorry :(. Kernel modules are a pain to backport and maintain.

---

