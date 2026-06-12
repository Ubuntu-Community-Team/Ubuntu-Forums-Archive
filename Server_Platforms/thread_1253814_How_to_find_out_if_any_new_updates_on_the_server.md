---
title: "How to find out if any new updates on the server?"
date: 2009-08-30
forum: Server Platforms
---

### Post by chong67 on 2009-08-30
How do I find out what is new to update on the 9.04 server?

It doesnt have nice prompt like on the desktop to tell us what to get.

Thanks!

---

### Post by Bachstelze on 2009-08-30
```
sudo apt§get update && sudo apt-get dist-upgrade
```

---

### Post by nerr on 2009-08-30
If you run screen with the system information displayed at the bottom of the screen, it will occasionally make an icon appear that says "#!" to let you know that there are updates available. (# is replaced with however man updates are available).  Since I run screen constantly over SSH anyway, that's my method for discovering if updates are available.

---

