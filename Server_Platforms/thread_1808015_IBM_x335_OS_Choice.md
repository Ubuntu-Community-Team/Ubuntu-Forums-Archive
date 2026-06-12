---
title: "IBM x335 OS Choice"
date: 2011-07-19
forum: Server Platforms
---

### Post by sudoCrushMS on 2011-07-19
I recently acquired an IBM x335, and wanted to install Ubuntu 11.04 Server on it. The only problem is, I would like to have a 64-bit OS for memory support (I'm guessing 32-bit maxes at 4GB RAM like desktop OS's, correct me if I'm wrong...). However, the 64-bit release appears to be AMD architecture, and my server is Intel (2 - Xeon 2.6GHz). Anyone done this/know which release to use?

---

### Post by jerrrys on 2011-07-20
the [xeon 2.6]("http://ark.intel.com/products/27271/Intel-Xeon-Processor-2_60-GHz-512K-Cache-400-MHz-FSB") processor is a 32bit processor and not capable of running 64bit.  which seems strange to me, seeing how the x335 is suppose to be 64bit machine (i run a x235).

anyhow, if you use the 32bit server install.  the server kernel can see more that 4G of ram...

EDIT:  the x335 is a 32bit maching.  i was thinking of the x236.  anyhow you got a 32bit machine...

---

