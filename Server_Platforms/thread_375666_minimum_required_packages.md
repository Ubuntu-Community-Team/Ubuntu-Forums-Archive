---
title: "minimum required packages"
date: 2007-03-04
forum: Server Platforms
---

### Post by homli on 2007-03-04
I'm new to Ubuntu... especially on servers.  Coming from RHEL, I appreciate Debian/Ubuntu's "security by default" mindset.  With that in mind, I was surprised by a few of the packages included in the minimal server install.  Not based on security threats with the packages, but on the idea that if it isn't necessary, it doesn't belong on a production server.  Some obvious ones... laptop-detect, libiw28, pcmciautils, ppp, pppconfig, pppoeconf, wireless-tools, and wpasupplicant.

So, my question is... What packages, if any, are you removing from your servers before deploying?

---

### Post by homli on 2007-03-04
> **homli said:**
> Some obvious ones... laptop-detect, libiw28, pcmciautils, ppp, pppconfig, pppoeconf, wireless-tools, and wpasupplicant.

Nevermind... I see there are dependencies from tasksel-data, ubuntu-minimal, and ubuntu-standard.  Looks like the minimal install really is a minimal install, at least without breaking dependencies.

---

