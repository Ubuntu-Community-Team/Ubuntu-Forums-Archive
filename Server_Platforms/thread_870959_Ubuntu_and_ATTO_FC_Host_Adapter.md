---
title: "Ubuntu and ATTO FC Host Adapter"
date: 2008-07-26
forum: Server Platforms
---

### Post by SYmek on 2008-07-26
Hi there!
I'd like to overtake possible problems with challenge I'm facing. We use Atto Celerity FC-42ES fibre channel controller, which is neither supported by Debian disto nor Debian is supported by manufacturer. There are only drivers for RH and Suse provided. 

Does any one here have any experiences with installing ATTO fibre channel products on Debian distros (possible Ubuntu Server > 7.10)?

Is there any sense trying it? I will need to nuke our current server to find it out, so any tips greatly appreciated! If I will have to look for another FC controller I need to know it as soon as possible. QLogic is good option as I heard. 

Thanks!
Simon.

---

### Post by SYmek on 2008-07-28
Just did it. Compile and install went just fine. 

cheers,
sy.

---

### Post by XStylus on 2008-08-13
> **SYmek said:**
> Just did it. Compile and install went just fine. 

cheers,
sy.


Here at work I'm giving heavy consideration to switching a CentOS system to an Ubuntu system and it's got a pair of ATTO cards, one of them being an FC-42 like yours. By chance would you be willing to list the steps you went to in getting it all set up? I'm more familiar with Ubuntu than I am with CentOS, but there seems to be better device vendor support for CentOS.

---

