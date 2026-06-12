---
title: "Xubuntu 14.04.1 Super slow on new laptop"
date: 2015-01-13
forum: Ubuntu, Linux and OS Chat
---

### Post by robert148 on 2015-01-13
Okay so I'm fairly new to xubuntu and I have a newer laptop fresh install of xubuntu and it is just so sluggish, the internet takes forever to load but yet if I click my wifi and refresh it; it does load faster. but even the desktop seems so slow like I feel like everything should be click/load. I've tried a bunch of tweaks and nothing seems to work, I don't really know all the commands yet so I've been playing/learning off google and forums.


Laptop
AMD A6-6310 APU with AMD Radeon R4 Graphics
4GB RAM

---

### Post by kerry_s on 2015-01-13
i think it's just ubuntu 14 in genearal, the enviroment don't matter. i was messing around with debian and everything just felt faster, i tried all the de otions installing seperatly using the net installer, i found the xfce4 setup to be the fastest, everything was just click & bam. right now i'm on elementary os freya, it's beta built on ubuntu 14.04, even here i can feel some of the sluggishness, eos is pretty barebones install to, eos luna built on ubuntu 12 lts is very fast.

i'm thinking about doing a custom debian xfce4 later today, just because ubuntu feels so slow & i want as fast as possible with out any bloat(apps i don't use). i been distro hopping for about a week now trying different things.

---

### Post by QIII on 2015-01-13
As there does not seem to be a request for assistance here, moved from General Help to Ubuntu, Linux and OS Chat.

---

### Post by robert148 on 2015-01-13
Well my buddy has the same laptop as me running same xubuntu and hes just seems so much faster and I'm not sure why I lose wifi but it doesnt actually lose wifi its just like the net goes super sluggish but as soon as i reclick my wifi it speeds up again for like 2 minutes then back to sluggish

---

### Post by kerry_s on 2015-01-13
> **robert148 said:**
> Well my buddy has the same laptop as me running same xubuntu and hes just seems so much faster and I'm not sure why I lose wifi but it doesnt actually lose wifi its just like the net goes super sluggish but as soon as i reclick my wifi it speeds up again for like 2 minutes then back to sluggish

did you turn ipv6 to ignore? what kind of wifi? realtec has disconnection problems on some models.

---

### Post by robert148 on 2015-01-14
Well I seemed to fixed it by updating from 14.04 to 14.10 an unregular update or whatever you would call it seems waaaay faster now. And I turned Ipv6 off to be safe and I do have a realtek netcard, but its weird like my WiFi wasn't disconnecting it was like it would lag super bad but if I refreshed my network it would be fine, I even pinged google 100 times and came back with 0% packet loss and only 45ms no spikes even it was so weird. Thank you all so much, great to see people that are actually willing to help!

---

### Post by mörgæs on 2015-01-14
Good, please spread the word. Some people stick to 14.04 only because of the long term support and never give 14.10 a chance.

---

### Post by kerry_s on 2015-01-14
yeah, i no the symptoms, i have a usb wifi thats realtec, i'm using a different usb wifi instead. i just basically gone old school on my setup, turned off anti-aliasing of the font, tweak the swap, preload,, host file fix,...

good enough to use now.

---

### Post by mastablasta on 2015-01-14
14.04 to 14.10 is not unregular update it's an upgrade to a new version with shorter support time. 

you could porbably just upgrade the kernel in 14.04 and would get same result onyl support for it would be longer.

even if the laptops look the same are same model and all they do not neceassarily have same components. however, if they do and really are the same all you would need to do is check your friends setup and kernel. in linux drivers are part of kernel (except for some that can't be inlcuded in kernel due to legal reasons and some other things). so newer kernel (core of the OS) means newer drivers as well.

---

