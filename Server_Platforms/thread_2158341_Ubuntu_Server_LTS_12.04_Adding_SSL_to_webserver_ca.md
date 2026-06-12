---
title: "Ubuntu Server LTS 12.04 Adding SSL to webserver causes hang on boot?"
date: 2013-06-28
forum: Server Platforms
---

### Post by elbeano on 2013-06-28
Added SSL to a webserver only to find that when the prompt comes up to enter the password, no time is offered to actually type it in. Apparently additional processes take over with the new default concurrent bootup. The system later hangs. I CAN boot using the recovery mode + resume normal bootup, as this gives me the time to enter the passphrase. Editing the startup in /etc/init.d/rc by changing concurrency to "none" didn't help.

---

### Post by DJ_Max on 2013-06-29
Either set your HTTP server to use your passphrase, or remove the passphrase from the certificate.

---

### Post by CharlesA on 2013-06-29
> **DJ_Max said:**
> Either set your HTTP server to use your passphrase, or remove the passphrase from the certificate.

This. Make sure the passphrase-less key is set to only be readable by root.

---

