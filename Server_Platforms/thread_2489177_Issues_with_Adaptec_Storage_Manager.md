---
title: "Issues with Adaptec Storage Manager"
date: 2023-07-21
forum: Server Platforms
---

### Post by grausamkeeit on 2023-07-21
Hello everybody. There was a very unpleasant problem, I put ASM on the server, the manager starts and works, but I can't connect to it from another PC. Maybe someone faced this?? Looked around the internet, none of the solutions helped.
The rules for ASM ports in ufw are set, so the problem is definitely not in them.


Adaptec 6805 controller, here is the software for it: [https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-6805/](https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-6805/)


I will provide all the information you need if you tell me where to start

---

### Post by MAFoElffen on 2023-07-22
Your link posted is broke for me, but a quick Google search found what you were trying to point to...

I went here: [https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-6805/](https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-6805/)

...and found that the software they have for download, only goes up to Ubutu 16.04 LTS. What "supported release" of Ubuntu are you running?

---

### Post by grausamkeeit on 2023-07-23
Damn, I didn't notice this. Is there any way to make it work on Ubuntu 22.04?

And sorry for broken link, fixed it

---

### Post by grausamkeeit on 2023-07-24
I installed Ubuntu 16.04 but the problem still persists. Although I run the agent, and everything is fine with it, it works, but the server is also not visible in ASM

---

### Post by QIII on 2023-07-24
Installing a release that is no longer supported (unless you pay for Extended Security Maintenance, ESM) was not a good idea. You have opened a can of security worms and should not expose the system to the web.

If it is likely proprietary, the chances of making it work for anything after 16.04 are likely nil.  It looks like all the other Linux choices only apply to very old, unsupported versions, too.  If the OEM does not have a version that supports a more recent release, there's not much to be done.

You may be forced to find another hardware solution.

---

### Post by MAFoElffen on 2023-07-24
I would have stayed running 22.04. 

It is still configurable from the Controller BIOS ARC Setup Utility by pressing the keys <Cntrl><A> when the BIOS prompts for that during the POST... But that is local.

I believe ARCCONF will work locally, but the only remote version for that is for VMware ESXi. But the CLI version, he could run it connected via shh.

I looked at the .deb and it is definitely a binary built for 16.04. Which there were lots of UI changes between then and not-- Python versions, GTK changes, etc. But the again, that card came out circa Ubuntu 10.04... So about 12-13 years ago.

Curious which Automatic Storage Manager (ASM) you are running.

---

