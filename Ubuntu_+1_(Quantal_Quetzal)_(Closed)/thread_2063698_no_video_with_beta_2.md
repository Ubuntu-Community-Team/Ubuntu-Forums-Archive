---
title: "no video with beta 2"
date: 2012-09-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by geovino on 2012-09-27
just ran 12.10 beta 2 live and no video. just a garbled screen. :(

I have an Nvidia Geforce 8400 GS video card. 

How to get the video to work? Had no problem with 12.04

---

### Post by arpanaut on 2012-09-27
Try nomodset as a boot option

When you first see the purple screen immediately hit any key then  hit enter, then hit F6, select nomadset as a kernel parameter.
That should get you going.

---

### Post by geovino on 2012-09-27
> **arpanaut said:**
> Try nomodset as a boot option

When you first see the purple screen immediately hit any key then  hit enter, then hit F6, select nomadset as a kernel parameter.
That should get you going.
thanks, once that's done and I want to install on the hdd, will the video setting stay that way?

---

### Post by mc4man on 2012-09-27
You really only need to remove splash from the boot options. nomodeset will work but provides a crap live session if you were to go there instead of directly to live installer
(either way you'll be fine once installed

There may be a fix at hand thru a kernel patch, won't know till an image shows up that includes it..
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1043518](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1043518)

---

### Post by philinux on 2012-09-27
> **mc4man said:**
> You really only need to remove splash from the boot options. nomodeset will work but provides a crap live session if you were to go there instead of directly to live installer
(either way you'll be fine once installed

There may be a fix at hand thru a kernel patch, won't know till an image shows up that includes it..
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1043518](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1043518)

+1 nomodeset is awful.

---

### Post by mc4man on 2012-09-27
> **philinux said:**
> +1 nomodeset is awful.
In the past nomodeset would boot to unity-2d which worked pretty good. Now it gives you unity/compiz with indirect rendering thru llvmpipe which at least in a live session isn't going to impress that many users
(perf may be hardware sensitive

---

### Post by philinux on 2012-09-27
> **mc4man said:**
> In the past nomodeset would boot to unity-2d which worked pretty good. Now it gives you unity/compiz with indirect rendering thru llvmpipe which at least in a live session isn't going to impress that many users
(perf may be hardware sensitive

Indeed on nvidia 8600gt it's like a pig running through treacle. ;)

---

### Post by geovino on 2012-09-27
> **philinux said:**
> Indeed on nvidia 8600gt it's like a pig running through treacle. ;)

I see what you mean. setting it to nomodeset didn't look too good. 

I'll wait until the final comes out. Do you think the video will work without making the video adjustments on the final version?

---

