---
title: "ufw application profiles, outgoing ports &amp; syntax in general"
date: 2013-10-28
forum: Security
---

### Post by flickerfly on 2013-10-28
I'd like to use ufw application profile a bit more heavily. I'm looking for deeper documentation on the syntax for the profiles. Does such exists?

More specifically, I'd like to be able to specify outgoing ports required using application profiles. Consider a heavily locked down machine where all outgoing traffic is denied by default in the same way that all incoming traffic typically is. I'd like to then have an apt profile that permits me to perform apt-get updates, and if possible, limit that to specific destinations.

Is that possible? Where can I read more about application profile definition syntax?

---

