---
title: "Opteron Quad Socket Turbo Core"
date: 2013-02-14
forum: Server Platforms
---

### Post by the1kingbob on 2013-02-14
Hello,

I was hoping to find out a little information on the turbo function of opteron and how well it plays with ubuntu server 12.04. I am currently running four 16-core opteron 6376 chips. The speeds this chip operates at are 2.3, 2.6, and 3.2GHz for stock, full load turbo, and half load turbo. I have been able to get the system to boost to 2.6GHz, verified using turbostat and bios set to max performance. I have not been able to get it to boost to 3.2GHz though. I have been testing using an mpirun. I have been using the -np to specify threads and --npersocket to specify threads per socket. I have tried all bios options under power settings, I believe they were max performance, OS control, system control, and on demand(I believe). 

Max performance and system control options yield 2.6GHz, maxP all the time where as system control is on demand. OS control yields me only 2.35 sometimes, not sure what is up with that. 

I thank you for any input.

---

