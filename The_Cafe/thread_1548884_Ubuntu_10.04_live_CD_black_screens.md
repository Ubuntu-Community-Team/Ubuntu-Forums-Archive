---
title: "Ubuntu 10.04 live CD black screens"
date: 2010-08-09
forum: The Cafe
---

### Post by candtalan on 2010-08-09
On several occasions I have used a 10.04 Live CD and it ends with display of a black screen. This seems to be related to modeset and careful use of nomodeset or a string including this, seems to fix it and the CD boots as expected.

I was displaying at a local computer fair yesterday, and by chance had the opportunity to demonstrate Ubuntu to someone who had never heard of Ubuntu, was holding a slow laptop, and was now quite interested in trying it.
Black screen.

I then used 8.04.4 Live CD which worked well I am glad to say.

This problem with 10.04 is bad for Ubuntu's reputation. I distribute live CDs regularly and I know it does not take much for a long time Windows user to find reasons to believe anti GNU/Linux FUD.

I installed 10.04 on an elderly Toshiba Satellite recently and - black screen. In this case a simple nomodeset entry was not sufficient, I needed to also state i915 in a short string. I am just about experienced enough to handle such things, but what about the damage it must be doing to wider efforts to cure Bug#1?

I heard opinion yesterday that i915 was 'deliberately' blacklisted in 10.04. Is this true? (I gather this is a video driver or chip?)

I earnestly hope that problems affecting live CDs can be quickly sorted. 

My use of Live CDs for demonstrations on a regular basis highlights to me the importance of a getting a good Live CD experience for  Windows users who are getting interested in Ubuntu. 

For existing (Ubuntu) GNU/Linux users, a problematic Live CD experience is simply an inconvenience :-(  
but to others, the Live CD is the formal ambassador of a wonderful alternative (which might not work?)

---

