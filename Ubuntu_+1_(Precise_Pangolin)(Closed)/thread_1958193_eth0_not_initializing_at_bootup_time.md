---
title: "eth0 not initializing at bootup time"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Hakunka-Matata on 2012-04-13
Wired Network not connected at bootup.  
Not initialized (turned on) either.  
#sudo ifup eth0, does not work.  
One way to fix it is with 
#dhclient eth0

that works, but I want to fix whatever I mucked up while trying to add "indicators" to the panel.  
Also the network "Indicator" which appears as an "up arrow next to a down arrow" is gone.  I don't know which "indicator-network" package to install from synaptic to get it back.

Thanks in advance.

Linux M5A78L-1204-64 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

