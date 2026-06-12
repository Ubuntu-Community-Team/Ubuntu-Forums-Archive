---
title: "[SOLVED] Disable Programs on logon"
date: 2008-06-11
forum: Server Platforms
---

### Post by Benismyhorse on 2008-06-11
Hi, I was wondering if there was a way to make programs disabled (like terminal) as I am trying Ubuntu in a school zone and was hoping if I could stop students from getting into some programs.

Thanks

---

### Post by cdenley on 2008-06-11
```

sudo chgrp admin /usr/bin/gnome-terminal
sudo chmod 750 /usr/bin/gnome-terminal

```

---

### Post by HermanAB on 2008-06-11
Yes, there is a way to control things with fine granularity and the good news is that Ubuntu is configured to do just that by default.

Carefully read the sudoers man page, then make a special group for the children and restrict them to specific programs in sudoers.

Cheers,

Herman

---

