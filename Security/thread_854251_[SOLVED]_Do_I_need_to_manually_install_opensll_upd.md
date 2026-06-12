---
title: "[SOLVED] Do I need to manually install opensll updates?"
date: 2008-07-09
forum: Security
---

### Post by psyncho on 2008-07-09
I use Synaptic. It currently provides openssl 0.9.8g while the latest is 0.9.8h. Do I need to manually monitor and update security stuff like this?
Is this not a security hole?  Are all Ubuntu systems affected?

---

### Post by HalPomeranz on 2008-07-09
In general the update manager will prompt you to install updates when they are necessary/available.  Sometimes the version of a package like OpenSSL will lag the Open Source version by a release or two, but it's usually nothing to worry about.  Either the package maintainers are working on packaging the update, or the changes in the new release aren't critical enough to warrant an immediate update.

In this specific case, I believe the security hole in 0.9.8g doesn't impact the Ubuntu package because the standard Ubuntu package is not compiled with the TLS server name extensions.

---

### Post by psyncho on 2008-07-09
Thanks! I assumed as much but needed a little validation.

---

