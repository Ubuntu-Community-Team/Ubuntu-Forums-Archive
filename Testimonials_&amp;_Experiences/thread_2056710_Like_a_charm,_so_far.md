---
title: "Like a charm, so far"
date: 2012-09-12
forum: Testimonials &amp; Experiences
---

### Post by geronl on 2012-09-12
Several days ago my HDD failed on my Toshiba Satellite L305, badly. I had no recovery disk. There was a recovery partition on it, but...well what is the point really?

Anyway, new "clean" HDD and no budget for Windows so I download Linux Ubuntu 12.04 onto a USB flashdrive, I run it off the drive and am online with wifi within seconds.

Awesome.

It didn't fill my screen but someone helped me out, Linux users are very helpful, and its working beautifully. I do miss a few things. 

There is an online game my nephew likes "Hero Up" that hates Linux apparently. And there is one forum I love that doesn't seem to want to load for me at all. Oh well.

---

### Post by mastablasta on 2012-09-12
you can dual boot and i am not sure oyu need to pay for new windows if you only replace the hard disk. you could just use the code you have. they might need to be activated by MS manually. or not.

---

### Post by black veils on 2012-09-14
you can install the ubuntu operating system from the flash drive onto the harddrive, this will give you more options. you can properly install software which you probably need, like java and flash, and codecs for playing mp3 files or dvds.

after install, and booting into new system:

in the **software sources** application, you can enable the 'canonical parters' repository.

then in the **software center** search for:

*openjdk *for the java 6 runtime

*flash* for the adobe flash flugin


for codecs:

open the **terminal** application

paste this into the window```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```press the **enter** key and let it process. you may need to respond to one or 2 things, just press **enter** to do so.

---

### Post by BrianBlaze on 2012-09-14
I love bootable USB's! My only beef is I have not found a way to save my configurations when I change something on the USB... how sad :'(

---

### Post by black veils on 2012-09-14
> **BrianBlaze said:**
> I love bootable USB's! My only beef is I have not found a way to save my configurations when I change something on the USB... how sad :'(

it makes things slow, but you can use a lighter desktop, like lxde, or xfce.

anyway, you can save configurations, remake the bootable usb with disk creator or unetbootin (the latter can be done using linux or windows). choose the amount of space for storage, it might be slower when larger.

---

### Post by stalkingwolf on 2012-09-14
did you install restricted extras?  might change being able to view the forum.
the game might run on play on linux or crossover.

---

### Post by tehcavil on 2012-09-15
> **stalkingwolf said:**
> did you install restricted extras?  might change being able to view the forum.
the game might run on play on linux or crossover.

naw, i checked out the game he was talking about and as soon as you load the page, a little popup comes up and says "this game only works on a windows or mac computer" or someting along those lines.

---

### Post by geronl on 2012-09-16
> **BrianBlaze said:**
> I love bootable USB's! My only beef is I have not found a way to save my configurations when I change something on the USB... how sad :'(

That reminds me. I tested Ubuntu 12.04 on a flash drive first and loved it. I was online within seconds. Then I installed it and the installed Ubuntu already remembered my WEP key! Its a small thing but I thought it was cool.

---

