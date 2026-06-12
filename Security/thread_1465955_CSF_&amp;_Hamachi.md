---
title: "CSF &amp; Hamachi"
date: 2010-04-29
forum: Security
---

### Post by k2chris1983 on 2010-04-29
Hey Guys,

I'm having trouble getting CSF working with Hamachi and I was wondering if anyone has any idea? I know Hamachi uses ham0 but has to use eth0 to establish a connection to the VPN servers. When I turn on CSF, hamachi seems to die but I opened the ports in CSF (443,12975,32976,17771)... I keep getting login fail when start Hamachi up. 

I'm guessing this has to deal with CSF/iptables but no clue on how to setup those rules to work with Hamachi. Any clue? 

Thanks,

Chris

---

### Post by spynappels on 2010-04-30
You also need to open the port on your regular eth0 (or eth1) interface that Hamachi uses to talk to it's man in the middle server. I'm not sure which port that is now, as we changed from using Hamachi to using OpenVPN quite some time ago due to instability difficulties.

Opening the port should allow your Hamachi instance to talk to the central server and keep the connection open.

---

### Post by k2chris1983 on 2010-05-03
Yeah I have noticed that Hamachi is slowly dying in the Linux area. I have found a new one that offers better results and a lot more control. I'm now using NeoRouter to do all my Admin... 

Thanks for the help.

---

