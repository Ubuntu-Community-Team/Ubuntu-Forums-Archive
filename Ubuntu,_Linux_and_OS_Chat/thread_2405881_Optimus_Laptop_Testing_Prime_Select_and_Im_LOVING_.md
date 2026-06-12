---
title: "Optimus Laptop Testing Prime Select and Im LOVING IT!"
date: 2018-11-12
forum: Ubuntu, Linux and OS Chat
---

### Post by edneyhelene on 2018-11-12
Hello how are you guys doing?

Ive been using My laptop with GTX 850m and Optimus Technology for some time, always came back to windows because of the tearing problem...then came bumblebee as a temporary solution, in fact it was much better for me, no more tearing, but still some minor problems while running 3d got me  and disappointed me..I used to run Arch Based distros because it was really a pain in the ass to fix the problems with it on deb based distros but it changed!

I have read that ubuntu devs where requiring people to test  this new optimus solution implemented, actually it ' s freaking good! Im testing with Lutris, Wine, Steam Proton and i only have good things to say..

The only problem i had? tearing ( Yeah this is an old problem with optimus drivers).

So what do i think?

I think its amazing, a huge step forward actually, got more stability using 3D and  to fix tearing what i did was :

```
sudo gedit /etc/modprobe.d/nvidia-drm-nomodeset.conf
options nvidia-drm modeset=1
sudo update-initramfs -u
```

And also i installed the Nvidia 410 drivers using the ppa drivers  instead of the suggested ones ( the suggested ones are still on 390, its too old, would like to see an update faster about it, its impossible to use dxvk with 390 ones)

So my impressions are these, would help if you could include these steps on the driver installer script, actually i would love to work at canonical, im actively applying  and dont require visa to EU as far as im Italian hahah..

Thats it, thanks and keep the good work!

---

### Post by mastablasta on 2018-11-14
> **edneyhelene said:**
> 
So my impressions are these, would help if you could include these steps on the driver installer script, actually i would love to work at canonical, im actively applying  and dont require visa to EU as far as im Italian hahah..


thanks for the tips.

you should know that this forum is mostly made from users. developers visit it very rarely. not sure if people from Canonical visit it at all.

perhaps the tips /solution could be added to some online documentation. though, now that you posted it here search engines will find it when people search for it.

---

### Post by edneyhelene on 2018-11-14
Yeup, where does devs are located? i would love to tell em that its really a great thing!

---

### Post by slickymaster on 2018-11-14
Not a support request.

Thread moved to **Ubuntu, Linux and OS Chat**

---

