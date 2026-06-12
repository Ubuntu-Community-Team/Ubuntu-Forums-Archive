---
title: "Intel to work on high-performance graphics... good for open source?"
date: 2006-08-16
forum: The Cafe
---

### Post by Donshyoku on 2006-08-16
There has been a lot of buzz lately about open Intel standards and drivers.  This is certainly good news, and I have seen the benefits of it with native X.org support for my 915GM.  It makes it a lot easier for me to install and go than to hunt down obscure Linux drivers for another product.

So I point here: [http://www.xbitlabs.com/news/video/display/20060816030933.html](http://www.xbitlabs.com/news/video/display/20060816030933.html)

Intel is said to be hiring engineers for high-performance, leading edge graphics.  It would be great to have a good, open, high-performance video card.  It would make XGL/AIGLX/Compiz and definately gaming a lot more viable on the Linux platform.  

Choices are great, open choices are even better.

---

### Post by IYY on 2006-08-16
This is indeed good news. Intel is very Linux-friendly when it comes to graphics drivers. 

Also, AMD said that they very well might open the ATI drivers now that it's their company.

The future is fairly bright.

---

### Post by Hotaru on 2006-08-16
AMD said that they don't intend to open their graphics drivers, as the performance of their proprietary ATi drivers is apparently as best as it can get... -_-

---

### Post by ember on 2006-08-16
The less good point about it is that they plan to hustle optimized routines into a BLOB which will be delivered with upcoming drivers. So it is likely that there will be no high performance open source driver, especially not for 3D.

(see: [http://marc.theaimsgroup.com/?l=linux-kernel&m=115536806403908&w=2]("http://marc.theaimsgroup.com/?l=linux-kernel&m=115536806403908&w=2")

---

### Post by prizrak on 2006-08-16
Only if Intel opens the 3D part up, which they won't.

---

### Post by nalmeth on 2006-08-16
> Only if Intel opens the 3D part up, which they won't.
What part isn't opened up? The i810 driver has 3D-support outofthebox. Are you saying I can find a more beefed up 3D driver for my intel card than the i810?

---

### Post by ember on 2006-08-16
As far as I know, all this is mainly about the i935 and i945, but in general you will always have 3D support, but no optimized routines if the current analysis is correct.

---

### Post by Donshyoku on 2006-08-16
> **ember said:**
> As far as I know, all this is mainly about the i935 and i945, but in general you will always have 3D support, but no optimized routines if the current analysis is correct.

This is referring not to the current or new Intel video products, but an upcoming card.  The current integrated solutions are not consider "high-performance." 

According to the articles I read, they are assembling a new team to work on a new card.  Whether or not it will be discrete is to question, but regardless, the gist I am getting is that this is not a currently existing or even testing product such as the current i9xx series of chipstets.

---

### Post by prizrak on 2006-08-17
> **nalmeth said:**
> What part isn't opened up? The i810 driver has 3D-support outofthebox. Are you saying I can find a more beefed up 3D driver for my intel card than the i810?

The i810 is about as high performance as a Toyota Prius. If we are talking about the high-performance graphics then the drivers have to be quite a bit more involved than what they are now for the low end market. From a post above about a binary blob that contains all the goodies it seems that Intel will not be opening up the high performance part only the "generic" stuff will be open. It's still better than nothing but not much different from the nVidia driver.

---

### Post by atrus123 on 2006-08-17
> **Hotaru said:**
> AMD said that they don't intend to open their graphics drivers, as the performance of their proprietary ATi drivers is apparently as best as it can get... -_-

ATI said that before the merger was approved.  AMD/ATI hasn't said anything yet.

---

### Post by Hotaru on 2006-08-17
> **atrus123 said:**
> ATI said that before the merger was approved.  AMD/ATI hasn't said anything yet.

I'm afraid you're wrong.
[http://www.osnews.com/comment.php?news_id=15472]("http://www.osnews.com/comment.php?news_id=15472")
The date of this statement is 12th of August 2006 - so AFTER the merge.

---

### Post by nalmeth on 2006-08-17
> The i810 is about as high performance as a Toyota Prius. If we are talking about the high-performance graphics then the drivers have to be quite a bit more involved than what they are now for the low end market. From a post above about a binary blob that contains all the goodies it seems that Intel will not be opening up the high performance part only the "generic" stuff will be open. It's still better than nothing but not much different from the nVidia driver.
I see..
I agree, i810 doesn't give stellar performance, but out of the box I can play games like Nexuiz, Unreal, and use AIGLX comfortably. 

I don't think the nv driver can perform adequately the same way.

Anyway, I thought that onboard graphics were subpar to begin with, is it really just the driver that is poor, and intel isn't giving me the bang for my buck? Can my card do better?

---

### Post by prizrak on 2006-08-17
> **nalmeth said:**
> I see..
I agree, i810 doesn't give stellar performance, but out of the box I can play games like Nexuiz, Unreal, and use AIGLX comfortably. 

I don't think the nv driver can perform adequately the same way.

Anyway, I thought that onboard graphics were subpar to begin with, is it really just the driver that is poor, and intel isn't giving me the bang for my buck? Can my card do better?

Unreal rocks but is fairly old :) AIGLX is pretty good on the Intels. In the case of an onboard video there are a few things making it slower. 
1) It has to be small so you don't have as many rendering conveyors (sorry I only heard the name in Russian might be diff in English). There is a smaller GPU (less transistors). Normally less memory.

2) Most of the time there is very little discreet memory available. For instance I have a GeForce Go 6200 (I think that's the one) with 128MB BUT I think only 32 or 64 of it is actual discreet video RAM and the rest is borrowed from system RAM as needed. Of course system RAM is slower.

Drivers make the difference when it comes to higher end hardware. Basically both ATI and nVidia use very creative programming to make the most out of the hardware. You could probably tune the Intel drivers to be better and faster but at the same time you won't be able to play Doom 3 or Half Life 2 anyway so there is little point. They are great for what they are meant to do and they do it very well actually.

The nv driver is actually a POS it doesn't really work right even in 2D. Of course it's damn dificult to reverse engineer nVidia hardware. The proprietary driver is pretty good unless you want Xorg 7.1 then you are screwed.

---

