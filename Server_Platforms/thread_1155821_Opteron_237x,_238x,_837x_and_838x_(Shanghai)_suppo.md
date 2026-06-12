---
title: "Opteron 237x, 238x, 837x and 838x (Shanghai) support of DVFS"
date: 2009-05-11
forum: Server Platforms
---

### Post by cboneti on 2009-05-11
Hi, 

I am very interested by the processor's ability to change frequency per core, independently. I considering buying a quad-core Shanghai Opteron, but I fear that the ability of changing frequencies per core is only available in the Barcelona processors. Do you guys know if the Shanghai really can do DVFS per core? 

I know that a lot of news in the web say it may do a bunch of things, but how the processor works on the real system may be quite different. I would like to know if any of you, out there has access to one of these processors and could try to see if you can change the frequencies of the cores independently.

You can check it running cpufreq-info, or looking in /sys/devices/system/:
cat cpuX/cpufreq/affected_cpus
cat cpuX/cpufreq/related_cpus
cat cpuX/cpufreq/scaling_available_frequencies

Just check if they can affected and related cpus are only the ones you are looking into. (or send me the output for cpu0 and cpu1).

I would appreciate your help. Thank you,

Carlos

---

