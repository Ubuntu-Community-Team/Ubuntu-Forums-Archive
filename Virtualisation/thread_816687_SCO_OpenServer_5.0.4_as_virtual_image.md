---
title: "SCO OpenServer 5.0.4 as virtual image"
date: 2008-06-02
forum: Virtualisation
---

### Post by SergeiFranco on 2008-06-02
I am not accustom to the whole notion of virtual PC as there was not need... But now I come across a problem, we have an old custom software that only works under SCO OpenServer 5.0.4. 
Right now it is run on some old hardware that we are leasing for mega $$$ as our server gave up (server... right... pentium pro, my cellphone is more powerful ;)), and it is impossible to find the hardware that that software will run on.
So, is it possilbe to "dd" the whole harddisk on to a now disk and virtually run that on some modern PC, preferably under Ubuntu?
Or do I have to install the whole thing "virtually"?
Could you please advise on how to do it for an average noob (in virtualization)?
BTW we own all the licences for the software and OS (we paid mega $$$ long time ago) so everything is legal (well, if you can "own" a licence that is ;)).

Thank you very much, your help is highly appreciated.

---

### Post by gary vollink on 2008-06-03
The idea that you cannot get the disk to boot on newer hardware is because SCO required kernel relinks to support new hardware.

Depending on the nature of your software, and the configuration of your old SCO box, you may not be any better off trying to virtualize it.  I don't think SCO is offically supported in any of the VM packages that I have seen.  VMWare, as one example - you will have no network (maybe you don't need it).

If you attempt this, you will need to install it from original media.  Once you have this media, you MAY be able to copy the old application from the disk into the new install.

---

### Post by SergeiFranco on 2008-08-03
I have made a dd copy of the harddisk, now I am trying to boot it under VMWARE Server (under Windows), I also follow this guide [http://www.rcmb.ca/sco-restore.htm](http://www.rcmb.ca/sco-restore.htm) (part on how to relink the blc driver).
My problem right now is that it fails with "Out of low (below 1Mb) memory" error on linking process.
Is there anything I can do to pass that process?

---

