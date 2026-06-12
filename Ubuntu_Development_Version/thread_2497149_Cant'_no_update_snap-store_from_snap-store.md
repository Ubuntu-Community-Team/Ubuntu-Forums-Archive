---
title: "Cant' no update snap-store from snap-store"
date: 2024-04-25
forum: Ubuntu Development Version
---

### Post by hectorsales on 2024-04-25
Hi, Cant' no update snap-store from snap-store. the error: "Unknown Snapd Exception: Cannot refresh "snap-store..."(attached screenshot).

---

### Post by corradoventu on 2024-04-25
The message is clear: you can't update snap-store because it's open. snap-store must be closed to be updated.
```
sudo killall snap-store
sudo snap refresh snap-store

```

---

### Post by hectorsales on 2024-04-26
> **corradoventu said:**
> The message is clear: you can't update snap-store because it's open. snap-store must be closed to be updated.
```
sudo killall snap-store
sudo snap refresh snap-store

```

 Thanks for you tip. I resolve the issue.

---

