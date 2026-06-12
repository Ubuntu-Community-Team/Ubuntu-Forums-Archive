---
title: "Maximum external monitor resolution of Serval Professional"
date: 2009-06-13
forum: System76 Support
---

### Post by yipdw on 2009-06-13
Hi all,  I'm looking for an authoritative answer re: the maximum screen resolution on the external DVI for the newest Serval Professional laptop (Serp5?)  I'm interested in purchasing one, but haven't yet been able to find an answer to this question.   

 In particular, I have access to a 2560x1600 LCD display that I want to use with the Serval Professional.  The issue with those is that one needs a video system with dual-link TMDS transmitters to supply the necessary bandwidth, and it's oddly difficult to find information on this for mobile video.  (NVIDIA's website, in particular, contains no solid information for their mobile GPUs -- only their desktop GPUs!)   

 As one of the ordering options for the Serval Professional is a 1920x1200 screen (which also requires dual-link TMDS), I expect that the GTX 260M and Quadro FX 2700M must be able to deliver this in some fashion.  But does the external connector work in the same way?  This may be a silly question, but I've been burned by this in the past. 

  NVIDIA states that the "maximum digital resolution" for the GTX 260M is 2048x1536; this contains the 1920x1200 image area but falls short of providing 2560x1600.  (Interestingly, an older part -- the GeForce 9400M GT -- is listed as being able to do 2560x1600.)  There is no such information available on NVIDIA's website for the Quadro FX 2700M.  So I don't think I'll get the answer from NVIDIA.   

 Any information would be greatly appreciated.   

 Thanks in advance,   

 - David

---

### Post by jimv on 2009-06-13
It looks like it *should* work, but I think the best way to find out would be to just give System76 a call.

You could also try one of these phone numbers for Nvidia (may or may not work):

408-486-2000

408-615-2500

---

### Post by yipdw on 2009-06-13
Hi Jim,

Thanks for the numbers; I'll give those a shot.

---

### Post by thomasaaron on 2009-06-15
> The issue with those is that one needs a video system with dual-link TMDS transmitters to supply the necessary bandwidth.

We don't have dual-link monitors to test with, however, the Serval only has one DVI output. My understanding is that it is not wired in such a way that it can be split with an adapter to accommodate a dual-link monitor.

---

### Post by yipdw on 2009-06-15
Hi Thomas,

> **thomasaaron said:**
> We don't have dual-link monitors to test with, however, the Serval only has one DVI output. My understanding is that it is not wired in such a way that it can be split with an adapter to accommodate a dual-link monitor.

Er, I think I might have misspoke.

The monitor I'm interested in using with the Serval only has one DVI input, so splitting the signal isn't required (to my knowledge).  It's more a matter of having the bandwidth to push a 2560x1600 image.  To give some model information: the LCDs I'm interested in using with the Serval are Apple's 30" Cinema HD display and the NEC MultiSync LCD3090WQXi.

I think there's a way to check (via X.org logs or some such) whether a video adapter will support such resolutions, but I can't remember how to do that (or if it's even possible) at the moment.  I'll check later today and will post if I find that out.

---

### Post by thomasaaron on 2009-06-15
OK, specs are here...
[http://www.nvidia.com/object/product_geforce_gtx_260m_us.html](http://www.nvidia.com/object/product_geforce_gtx_260m_us.html)

...and max resolution from dvi is...
2048x1536

---

### Post by yipdw on 2009-06-16
> **thomasaaron said:**
> OK, specs are here...
[http://www.nvidia.com/object/product_geforce_gtx_260m_us.html](http://www.nvidia.com/object/product_geforce_gtx_260m_us.html)

...and max resolution from dvi is...
2048x1536

Yeah, it looks like that is indeed the true upper limit of the GTX 260M.  Kind of funny that earlier models (i.e. the 9400M GT) support higher resolutions, but I guess that's just the way things go...

I'm still looking for specs on the Quadro FX 2700M -- NVIDIA's official literature ([http://www.nvidia.com/page/quadrofx_go.html](http://www.nvidia.com/page/quadrofx_go.html)) seems to say that display support depends on the OEM, but maybe there's a better answer than that available.  I'll give them a call.  

I'm also still poking around for a procedure to determine (via Xorg or whatnot) what a video system's maximum supported resolution is; if I can get that, then it'll be a lot easier to figure this out.

Thanks again.

---

### Post by thomasaaron on 2009-06-16
Quadro FX 2700M

Maximum resolution...
1920x1200 on LCD
2048*1536 on external monitor

---

### Post by yipdw on 2009-06-16
Hi Thomas,

> **thomasaaron said:**
> Quadro FX 2700M

Maximum resolution...
1920x1200 on LCD
2048*1536 on external monitor

Thanks for the info; can you tell me where you got those numbers?

---

### Post by thomasaaron on 2009-06-16
From the specs we receive from various upstream distributors.

---

### Post by yipdw on 2009-06-16
> **thomasaaron said:**
> From the specs we receive from various upstream distributors.

Cool, thanks.

Do you think 2560x1600 external output resolution is something that we'll be able to get on the next generation of Servals?  (Put another way: what feature request tracking mechanism should I be using?)

---

### Post by thomasaaron on 2009-06-16
I report all feature requests from the forums and email to my managers. So, consider it done.

---

### Post by yipdw on 2009-06-16
> **thomasaaron said:**
> I report all feature requests from the forums and email to my managers. So, consider it done.

 Excellent! :)  Feel free to drop me a line if you need any other details on what I'm looking for.

---

