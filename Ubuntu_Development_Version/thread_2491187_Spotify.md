---
title: "Spotify"
date: 2023-09-28
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2023-09-28
Has anybody been able to install Spotify on Ubuntu 23.10
.  I tried and had multiple dependency issues.
Henry

---

### Post by #&amp;thj^% on 2023-09-28
A few ways as  you did not post what you tried: [https://www.spotify.com/uk/download/linux/](https://www.spotify.com/uk/download/linux/)
Flatpak version is also an option.
Mine:
```
apt policy spotify-client
spotify-client:
  Installed: 1:1.2.18.999.g9b38fc27
  Candidate: 1:1.2.18.999.g9b38fc27
  Version table:
 *** 1:1.2.18.999.g9b38fc27 500
        500 http://repository.spotify.com stable/non-free amd64 Packages
        100 /var/lib/dpkg/status
     1:1.2.13.661.ga588f749 500

```

---

### Post by Frogs Hair on 2023-09-28
I usually install spotify and my mail client via snap to avoid dependencies problems with .debs due to upgrades or new releases. I use the snap on Ubuntu Budgie 23.10. Flatpak should work also.

---

### Post by Hewjr100 on 2023-09-29
Not a big fan of snaps yet, but I will go with Flatpak for now.  Thanks for your suggestions.

Henry

---

