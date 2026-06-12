---
title: "low latency kernel only works for super user"
date: 2011-05-17
forum: Ubuntu Studio
---

### Post by ssj71 on 2011-05-17
I am not actually running Ubuntu Studio but I thought maybe someone here could help me best. I installed the -lowlatecy kernel for Natty out of Bogani's ppa (not the pae version) to get lower latency than I could muster from the -generic. 

It really improves the number of xruns but only if I start JACK control using sudo which susequently requires all my other programs to be started in terminals using sudo. Without JACK being started by super user it tells me it cannot allocate memory or threads.

I've tried to read from the wiki but the partial install guide is pretty old, so I'm reluctant to run commands that I don't really understand. If you can offer any advice thanks.

---

### Post by jejeman on 2011-05-17
Follow this instructions for Real time support
[https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support)

---

### Post by ssj71 on 2011-05-18
I needed to add my username to the audio group. Should have tried that before. I maybe didn't even need the lowlatency kernel (I'll test it soon). Thanks a lot!

---

