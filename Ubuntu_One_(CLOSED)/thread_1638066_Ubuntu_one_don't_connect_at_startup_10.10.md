---
title: "Ubuntu one don't connect at startup 10.10"
date: 2010-12-05
forum: Ubuntu One (CLOSED)
---

### Post by Me Mechant on 2010-12-05
Hi everyone,

I'm very pleased with ubuntu one, there is still work to do but this is a great product! Good job to the team! Keep up the good work!

Yesterday i upgrade from 10.04 to 10.10 everything is fine except the fact that ubuntu one don't connect at startup, i have to do it manually. When i do it manually ubuntu one connect perfectly and synchronize my files as usual.

I use ubuntu one on my netbook and on my desktop and the problem is the same for both computer!   

Thanks !

(edit: Yes, ubuntu one is in my startup applications)

---

### Post by duanedesign on 2010-12-07
There are a couple bugs right now being addressede about startup of Ubuntu one on boot. This first one has a fix released in the proposed repository. You might try enabling Proposed Updates in your Software Sources and updating Ubuntu One and see if it helps.

Launchpad bug 651237 in ubuntuone-client (Ubuntu Maverick) ubuntuone-launch fails to start syncdaemon if dbus call times out [Undecided,Fix committed] [https://launchpad.net/bugs/651237](https://launchpad.net/bugs/651237)

Launchpad bug 635636 in ubuntuone-client [maverick] ubuntuone-launch fails to connect syncdaemon if get_metadata times out [Medium,Confirmed] [https://launchpad.net/bugs/635636](https://launchpad.net/bugs/635636)

thank you,
duanedesign

---

