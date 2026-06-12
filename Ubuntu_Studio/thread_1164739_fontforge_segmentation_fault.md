---
title: "fontforge segmentation fault"
date: 2009-05-19
forum: Ubuntu Studio
---

### Post by Smbrandes on 2009-05-19
Greetings,

 Another baffling day. Running fontforge all day and it worked well. Went to dinner came back and resumed work and the thing crashed with a segmentation fault. This occurred every time I tried to import a bmp image, which  I had been doing all afternoon. The only difference in the system I can see is that a file operations icon was present before dinner though it was not doing anything. After dinner no such icon and no more success. also upon reboot still the same segmentation fault. NO other information provided in the terminal either. This all started after it randomly crashed and I used the recover process which did nothing much but take me back to a prior saved state. 

Once again another bizarre thing. And no further ideas how to proceed.

Jaunty 64 bit studio

---

### Post by Smbrandes on 2009-05-20
A minor but irritatingly unobvious thing transpired to cause the faulting. Essentially the imported bmp must be 2 color or else failure occurs.

---

### Post by Stochastic on 2009-05-20
> **Smbrandes said:**
> A minor but irritatingly unobvious thing transpired to cause the faulting. Essentially the imported bmp must be 2 color or else failure occurs.

Sounds like you've found a bonafide bug that you should report to the developers here: [https://bugs.launchpad.net/ubuntu/+source/fontforge](https://bugs.launchpad.net/ubuntu/+source/fontforge) (preferably with an apport bug trace).  These forums really aren't the place to report bugs as hardly any developers are around these parts.

Here's a little more info on filing bug reports: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

