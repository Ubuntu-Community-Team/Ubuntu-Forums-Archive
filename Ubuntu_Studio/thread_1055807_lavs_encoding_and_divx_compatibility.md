---
title: "lavs encoding and divx compatibility"
date: 2009-01-31
forum: Ubuntu Studio
---

### Post by sbrbot on 2009-01-31
According to specification my standalone DVD + DivX player Samsung DVD-V6500 does support:

Supported CODEC formats:   DivX3, DivX4, DivX5 (GMC 1WP)
Supported file formats:    *.avi, *.mpeg
Supported audio formats:   AC3, MP3, WMA
Supported caption formats: * .SMI, * .SRT, * .SUB

But it does not reproduce DivX created with mencoder when video codec is lavc (mencoder -ovc lavc). With xvid encoding everything is fine. According to mencoder documentation lavc encoding actually produce DivX coded movies.

:KS What is the problem with compatibility of this lavc?

:KS What this "GMC 1WP" in specification for DivX5 stands for?

:KS Why xvid encoding is many times slower than lavc encoding?

:KS What is lavc comparing to ffmpeg?

---

