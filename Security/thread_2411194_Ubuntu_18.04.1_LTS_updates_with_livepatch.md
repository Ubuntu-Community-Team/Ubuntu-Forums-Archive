---
title: "Ubuntu 18.04.1 LTS updates with livepatch"
date: 2019-01-26
forum: Security
---

### Post by cam17 on 2019-01-26
What is the difference performing updates using "livepatch" as opposed to the "software updater" 

I know you must log into livepatch to receive the updates which I am not doing. Is "software updater" less secure or have a security problem?

[ATTACH=CONFIG]282318[/ATTACH]

---

### Post by monkeybrain20122 on 2019-01-26
live patch applies security updates to kernels without requiring rebooting, so if you are in some kind of business that wants to minimise down time or preferably keep the system always on (say you run a server or do some intense computational experiments that need to run for days) that would be a nice feature. I think that is a paid service you have to sign up for though

---

### Post by PaulW2U on 2019-01-26
> **cam17 said:**
> What is the difference performing updates using "livepatch" as opposed to the "software updater"
Some kernel updates can be applied as patches and don't require a reboot. Due to various limitations, other updates will always require a reboot to take effect and will be offered as a normal update. The service is free for the personal use of up to three machines.

More info: [https://wiki.ubuntu.com/Kernel/Livepatch](https://wiki.ubuntu.com/Kernel/Livepatch) and [https://auth.livepatch.canonical.com/](https://auth.livepatch.canonical.com/)

---

### Post by cam17 on 2019-01-27
Thanks.  I am still wondering why? Is it forcing the application state to be uploaded to a Ubuntu site then re downloaded to the workstation?

---

