---
title: "Expanding SC Storage"
date: 2011-02-01
forum: Ubuntu Cloud and Juju
---

### Post by flabr03 on 2011-02-01
Whats the best way to expand storage for walrus buckets? I could use local storage but I'd prefer SAN storage.  Does Open Eucalyptus support SAN storage? 

Would I just move all the files in /var/lib/eucalyptus/whatever to the SAN disk or is there a supported way to do it?

---

### Post by kim0 on 2011-02-04
Why don't you simply mount your SAN on the directory  /var/lib/eucalyptus/

---

