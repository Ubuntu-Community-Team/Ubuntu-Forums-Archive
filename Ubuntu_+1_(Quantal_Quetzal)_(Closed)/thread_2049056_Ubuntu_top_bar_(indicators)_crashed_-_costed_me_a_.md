---
title: "Ubuntu top bar (indicators) crashed - costed me a meeting"
date: 2012-08-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-27
That was a tricky one: The top bar crashed but I got no warning / apport whatsoever, it just stalls, you get no visual indication.

The weird thing is that it continues to show on top of the screen, normally. I was looking at the clock every now and then: "8:15, I still got 45 minutes to get a cab". Well, it was 10:00. I left-clicked / right clicked the clock, no menu, nothing. 

I managed to reproduce it: When I leave Open Office Calc running it crashes after about 15 minutes. For some reason I cant understand, it makes the top bar stall with no crash message on logs.

And to avoid Calc from crashing, I had to disable spell-checking / auto-correction on Calc Menu / Tools / Options. 

I'm not drunk: I also find it hard to understand how these things are related. But they are :\

Regards,
Effenberg

---

### Post by jbicha on 2012-08-27
I think it's been discussed previously. Yes LibreOffice is currently [broken]("http://pad.lv/1041354") in Quantal.

---

### Post by effenberg0x0 on 2012-08-27
> **jbicha said:**
> I think it's been discussed previously. Yes LibreOffice is currently [broken]("http://pad.lv/1041354") in Quantal.

Hi, yep, it has always been to some degree anyway. But I had never seen it crash the indicators, and in a way that indicators just sit there stalled. It's really weird.

Regards,
Effenberg

---

