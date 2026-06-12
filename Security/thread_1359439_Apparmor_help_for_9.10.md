---
title: "Apparmor help for 9.10"
date: 2009-12-19
forum: Security
---

### Post by HoboGarden on 2009-12-19
So I recently installed 9.10.  I installed the apparmor profiles from the repository.  I noticed two unconfined processes, avahi-daemon.  How can I reset the process so I can start enforcing the profile?

---

### Post by rookcifer on 2009-12-19
> **HoboGarden said:**
> So I recently installed 9.10.  I installed the apparmor profiles from the repository.  I noticed two unconfined processes, avahi-daemon.  How can I reset the process so I can start enforcing the profile?

First make sure the profile is in enforcing mode:

```
sudo aa-enforce avahi-daemon
```

Then restart avahi-daemon:

```
sudo restart avahi-daemon
```

---

### Post by HoboGarden on 2009-12-19
Thanks

---

