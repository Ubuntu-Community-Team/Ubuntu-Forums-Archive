---
title: "Heat Issues on Serval serp3"
date: 2009-06-03
forum: System76 Support
---

### Post by DomIncollingo on 2009-06-03
I'm running Jaunty on a serval serp3 that has a 2.4 GHz processor and 4 GB of memory.  The laptop is about 18 months old.  I normally place the laptop on a small stand (so air can circulate under the laptop), and the laptop runs fine. It feels a little warm (and the fan occasionally revs up) when I run CPU-intensive software development tools (JBoss application server, 2 instances of Eclipse, Oracle client), but it has never shut down due to heat.

Last week I placed the laptop directly on the desk (no laptop stand), and after about 20 minutes, the laptop overheated and shut itself off.  I could not restart the laptop until it cooled off (about 10 minutes or so).  I wasn't running anything CPU-intensive at the time, just Firefox, Thunderbird, and Open Office.  I'm trying to resolve this issue, and have two questions.

1) What is the normal (acceptable) temperature range for the CPU?  I installed the gnome sensors applet to monitor the heat, and when I run the laptop on a stand, the CPUs are typically in the 52 C to 55 C range, although they will go well above 60 C or even in the low 70s C when CPU-intensive applications are running.

2) How can I check to see if dust has accumulated in the fan area?  Which part do I remove?  Will I void the warranty if I remove parts to clean the fan?

Thanks very much.

Dom

---

### Post by thomasaaron on 2009-06-04
None of those CPU temps are enough to shut down the machine. They are normal for various workloads. Your graphics card may be getting too hot, though.

Try monitoring it via nvidia-settings.

I would recommend removing the larger bottom cover and using some canned air to blow it out -- especially the fan. It could have a family of dust bunnies living in it or something.

---

