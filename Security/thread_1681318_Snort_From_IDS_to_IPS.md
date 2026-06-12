---
title: "Snort: From IDS to IPS"
date: 2011-02-04
forum: Security
---

### Post by Geared on 2011-02-04
Hi all,

I am currently running snort as an IDS on the same machine that acts as our gateway. I installed it using [FONT=Courier New]sudo apt-get install snort.[/FONT]

However, I'd like to make it run as an IPS. Is it possible to convert that currently running snort instance from running as an IDS to an IPS without having to download the snort tar balls and install it? I do not want the tar balls because during updates and upgrades, I'd like the whole OS and installed apps (such as snort) to be upgraded.

Thanks

---

### Post by cariboo on 2011-02-05
You are probably better off using the tarballs, as the way Ubuntu is setup, once a version is released, you only get security updates to packages, not newer versions.

---

