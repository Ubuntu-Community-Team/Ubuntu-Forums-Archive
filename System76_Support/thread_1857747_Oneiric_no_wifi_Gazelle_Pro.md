---
title: "Oneiric no wifi Gazelle Pro"
date: 2011-10-10
forum: System76 Support
---

### Post by Bufke on 2011-10-10
Just updated to Oneiric beta 2 and now I have no wifi :( Anything I can do besides wait for release and hope an update fixes it?

---

### Post by Bufke on 2011-10-10
Ah as typical I figured it out right after posting. To fix edit /etc/modprobe.d/iwlwifi.conf and comment out the 

options iwlagn 11n_disable50=1 11n_disable=1

Now it works! I don't see any bug reports for this specific issue though there do appear to be some related to intel wifi cards. I'm sure the System76 folk can do better testing than I.

---

### Post by isantop on 2011-10-13
Is your wireless network N-only?

---

### Post by Bufke on 2011-10-13
While it supports N, it's set to mixed mode.

---

