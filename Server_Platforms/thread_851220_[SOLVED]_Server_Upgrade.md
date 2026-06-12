---
title: "[SOLVED] Server Upgrade"
date: 2008-07-06
forum: Server Platforms
---

### Post by maustin2 on 2008-07-06
After attempting to upgrade to 8.04.1, system became somewhat unstable. I have come up with a plan and I hope it is possible.

My plan is to install 8.04.1 to my second hard drive. Copy the files from the primary hard drive that I wish to save, to the new install. Then transfer the new install back to my primary hard drive.

If anyone has done this and was successful, please let me know. If not possible, please suggest an alternative to accomplish the same.

Thanks for any assist.:confused:

---

### Post by cariboo on 2008-07-06
Use:

```
sudo aptitude safe-upgrade
```

This way you won't get any surprises

Jim

---

