---
title: "Have to go to Grub to boot"
date: 2013-03-01
forum: Ubuntu Development Version
---

### Post by cbennett926 on 2013-03-01
Ok, so I have an nVidia card and I have some issues (go figure). I had quite some difficulties getting my driver to work and now it does amazing and I love it, however whenever I first power up and boot my laptop I have to hold shift to go to grub and select ubuntu from there, or else I get a black screen with a white line in the top left and that's it. There are no erros, no beeps, and no messages when it does that, I then manually restart and go to Grub and select "Ubuntu" and it boots up and runs just fine. 

Does anyone know what might be happening?

I did have an older image on there from when I first installed ( a few hours ago, but I didn't do updates while installation) and I removed them and updated the grub doing

```


sudo update-grub2

```

And I still don't understand the issues. here is the output of listing my kernel(s):

```


cody@Cody-ThinkPad-W520:~$ dpkg --list | grep linux-image
ii  linux-image-3.7.0-7-generic               3.7.0-7.15                                                                  amd64        Linux kernel image for version 3.7.0 on 64 bit x86 SMP
ii  linux-image-extra-3.7.0-7-generic         3.7.0-7.15                                                                  amd64        Linux kernel image for version 3.7.0 on 64 bit x86 SMP
ii  linux-image-generic                       3.7.0.7.11                                                                  amd64        Generic Linux kernel image


```

Do those three not "work together" to provide my actual 3.7.0-7-generic kernel?

---

### Post by cbennett926 on 2013-03-01
Bump

---

### Post by oldfred on 2013-03-01
If you have kernel 3.7, you must be Raring. Moved to Raring Forum.

---

### Post by rrnbtter on 2013-03-01
Greetings,
My best guess is that you have purged a kernel image but the purge did not remove the images from /boot, hence when you update grub the updater is still putting the purged image in the default boot position, and since the image has been theoretically purged the system can't boot.
Solution: Open nautilus as super user and manually delete the images that were left behind. Then sudo apt-get update-grub.
After that you should be fine. 
Also you should do a sudo apt-get autoclean.
Hope this is helpful

---

### Post by pqwoerituytrueiwoq on 2013-03-01
> **oldfred said:**
> If you have kernel 3.7, you must be Raring. Moved to Raring Forum.

could be xorg edgers ppa on 12.10

---

### Post by grahammechanical on 2013-03-01
Either way sometimes ```
sudo update-grub
``` is not sufficient. Sometimes we also need ```
sudo grub-install /dev/sda
``` The first command updates the configuration files in /boot/grub. The second command re-installs Grub into the MBR of sda. Sometimes that is necessary for some changes to be picked up. By the way, update-grub2 and update-grub do the same thing. They just run a script that in turn runs a Grub utility. So, no confusion there, please.

Regards.

---

### Post by rrnbtter on 2013-03-01
Greetings,

> **grahammechanical said:**
> Either way sometimes ```
sudo update-grub
``` is not sufficient. Sometimes we also need ```
sudo grub-install /dev/sda
``` The first command updates the configuration files in /boot/grub. The second command re-installs Grub into the MBR of sda. Sometimes that is necessary for some changes to be picked up. By the way, update-grub2 and update-grub do the same thing. They just run a script that in turn runs a Grub utility. So, no confusion there, please.

Regards.

Now there's some handy info!

Personally I would like to see a "ls /boot" and compare that with "sudo dpkg -i linux*.deb".  Just to know what grub is doing.  He could also open grub.cfg and see what kernel is in the default position.  

I didn''t mention in my previous post that I'm having the same results here on two Raring systems, with files not being purged and picked up by grub. I have been manually deleting whats left over and it does fine. Could be a bug.

---

### Post by cbennett926 on 2013-03-03
> **oldfred said:**
> If you have kernel 3.7, you must be Raring. Moved to Raring Forum.



Nope sorry I definitely don't have Raring... I updated from Edgers.




However, I did find out that I had a lot of older Kernels and just had to update my grub and change the default grub to 0 from 

```


/etc/default/grub


```

And it booted to the right kernel. But I reallly bricked and fubar'd my drivers and innevetably had to reinstall Ubuntu all together. I found out how big of a pain it is to install nVidia drivers on 12.10, so as a work around I installed 12.04 and installed all of my drivers from there, upgraded to 12.10 via 

```


sudo apt-get ugrade -d 


```

And now I have Kernel 3.7-* and my up-to-date nVidia drivers so all is well and Steam is happy!

---

### Post by zika on 2013-03-03
> **cbennett926 said:**
> Nope sorry I definitely don't have Raring... I updated from Edgers.




However, I did find out that I had a lot of older Kernels and just had to update my grub and change the default grub to 0 from 

```


/etc/default/grub


```

And it booted to the right kernel. But I reallly bricked and fubar'd my drivers and innevetably had to reinstall Ubuntu all together. I found out how big of a pain it is to install nVidia drivers on 12.10, so as a work around I installed 12.04 and installed all of my drivers from there, upgraded to 12.10 via 

```


sudo apt-get ugrade -d 


```

And now I have Kernel 3.7-* and my up-to-date nVidia drivers so all is well and Steam is happy!Reinstall was of course not necessary... I suspect that Your problem is that initramfs updates were done only on Your active kernel at the time You've upgraded Your system... Also at the time You've installed NV drivers previous time... It is somewhat blessing and somewhat a curse that process of updating initramfs for kernel (when it is needed) are done only for a single kernel, depending on process, either active one or latest one... Bearing that in mind problems could be avoided...

---

### Post by cbennett926 on 2013-03-03
Well I had also had a bad iso on my DVD that I used (it was a torrent from alternative downloads and missed a couple files) so it was a bad install all together, but in the process I learned how to make a bootable USB so I'd say it was worth it. But yeah, I had no idea how confusing the whole thing was, but you're right it was an initramfs issue. It's all good now though.

---

### Post by Cavsfan on 2013-03-03
I did a fresh install from today's iso and here is my output from dpkg --list | grep linux-image:
```
cavsfan@cavsfan-MS-7529:~$ dpkg --list | grep linux-image

ii  linux-image-3.8.0-9-generic               3.8.0-9.18                                                          amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-9-generic         3.8.0-9.18                                                          amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic                       3.8.0.9.23                                                          amd64        Generic Linux kernel image
```

I added the x-org edgers ppa and have nvidia driver 310.32 installed. I swear that if it weren't for the custom grub method in my signature I would be pulling my hair out big time.
Especially since I have Precise, Quantal, Raring, Lucid and windows 7 loaded on this box. Re-installing is always a challenge.

---

