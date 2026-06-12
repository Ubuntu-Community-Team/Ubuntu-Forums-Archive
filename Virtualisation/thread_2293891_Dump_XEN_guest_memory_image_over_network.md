---
title: "Dump XEN guest memory image over network"
date: 2015-09-08
forum: Virtualisation
---

### Post by sklpr on 2015-09-08
Hello all, 

I am new into memory forensics thing and I am trying to dump a memory image from a *XEN* guest (Ubuntu 12.04 x64 - domU) in order to analyze it on *dom0* (Ubuntu server 12.04 x64) with ***volatility*** . For this purpose I am using *LiME* ( Linux Memory Extractor ). .

Thing is I have to log into *XEN guest *(domU) via gvncviewer and type some commands on terminal and then with netcat on the host (dom0) acquire the memory dump over a TCP port . 

Is there any possible way to do that **over network without logging** in the guest (domU) ?

Any ideas-documentation are welcome , thanks in advance

---

