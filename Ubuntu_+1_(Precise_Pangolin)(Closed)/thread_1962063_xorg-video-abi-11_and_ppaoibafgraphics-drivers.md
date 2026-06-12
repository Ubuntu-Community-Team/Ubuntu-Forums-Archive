---
title: "xorg-video-abi-11 and ppa:oibaf/graphics-drivers"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-04-20
While using ppa oibaf/graphics-drivers in order to enable upgrade of xserver-xorg-video-radeon I get: Depends: xorg-video-abi-11... Where to get that virtual package...?

---

### Post by dino99 on 2012-04-20
its due of x 1.12 from edgers i suppose, let it activated, then:

ppa-purge ppa:xorg-edgers/ppa

---

### Post by zika on 2012-04-20
> **dino99 said:**
> its due of x 1.12 from edgers i suppose, let it activated, then:

ppa-purge ppa:xorg-edgers/ppaI am not sure that I understood all but: yes, I have xorg-edgers turned on... ;)

---

### Post by dino99 on 2012-04-20
> **zika said:**
> I am not sure that I understood all but: yes, I have xorg-edgers turned on... ;)

purging the ppa will get back abi 11 as requested. (as edgers have abi 12)

---

### Post by zika on 2012-04-20
> **dino99 said:**
> purging the ppa will get back abi 11 as requested. (as edgers have abi 12)Now I get it... Thank You...

Update&#8321;: xorg-edgers and oibaf/graphics-drivers can not live together... I guess that is what dino99 wanted to tell me... ;)

---

### Post by dino99 on 2012-04-20
> **zika said:**
> Now I get it... Thank You...

Update&#8321;: xorg-edgers and oibaf/graphics-drivers can not live together... I guess that is what dino99 wanted to tell me... ;)

you're right, and after installing oibaf ppa package, then you can install back edgers if you want/like the bleeding scary troubles :)

---

### Post by zika on 2012-04-20
> **dino99 said:**
> you're right, and after installing oibaf ppa package, then you can install back edgers if you want/like the bleeding scary troubles :)No, I can not. I tried, of course... Then I would need to uninstall radeon which started all of this... ;)
Round-Robin...

---

### Post by dino99 on 2012-04-20
> **zika said:**
> No, I can not. I tried, of course... Then I would need to uninstall radeon which started all of this... ;)
Round-Robin...

Patience, QQ will start in a few weeks, then enjoy again the breakages ):P

---

### Post by zika on 2012-04-20
> **dino99 said:**
> patience, qq will start in a few weeks, then enjoy again the breakages ):p
Yes!

---

### Post by Harry33 on 2012-04-20
Virtual packages
xorg-video-abi-11 and xorg-input-abi-16 (with xserver 1.11) and
xorg-video-abi-12 and xorg-input-abi-16 (with xserver 1.12)
are not really real packages.

They really are virtual ones, and xserver-xorg-core provides those,
in order to make sure you have correct input and video drivers installed.
You see, drivers depend on those virtual packages.
Drivers for xserver 1.11 depend on video-abi-11 or input-abi-16.
Drivers for xserver 1.12 depend on video-abi-12 or input-abi-16.

Hope this helps.

---

### Post by zika on 2012-04-20
> **Harry33 said:**
> Virtual packages
xorg-video-abi-11 and xorg-input-abi-16 (with xserver 1.11) and
xorg-video-abi-12 and xorg-input-abi-16 (with xserver 1.12)
are not really real packages.

They really are virtual ones, and xserver-xorg-core provides those,
in order to make sure you have correct input and video drivers installed.
You see, drivers depend on those virtual packages.
Drivers for xserver 1.11 depend on video-abi-11 or input-abi-16.
Drivers for xserver 1.12 depend on video-abi-12 or input-abi-16.

Hope this helps.
As I said:
> **zika said:**
> While using ppa oibaf/graphics-drivers in order to  enable upgrade of xserver-xorg-video-radeon I get: Depends:  xorg-video-abi-11... Where to get that **virtual** package...?
But, nevertheless, Your post helped me think more and (now) I kind of see all the bits and pieces... I'm trying to mix apples and oranges... ;)

Update&#8321;: I must admit that with oibaf ppa driver Unity 3D for the first time after a while works stable at my place. I did not test it recently but... Quite on time for great finale... Which I will not witness (I'll be on a trip to the sea... ;))

---

