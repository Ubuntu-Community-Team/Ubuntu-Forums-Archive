---
title: "ssh auto-login only works when im logged in"
date: 2011-06-01
forum: Security
---

### Post by m-momr on 2011-06-01
Ok, so i have setup auto ssh login for my server.
And it works, but only when i have a active connection.

if i use "ssh server.com" it asks for my password.
If i then open a new terminal and issue "ssh server.com" it logs right in.

I really don*t understand whats wrong.

I have tried setting up 2 virtual machines on my local computer and with the same setup it works fine.

Any ideas?

SOLVED:
my home folder was encrypted, so when no users were logged in the home folder was unmounted ;)

---

### Post by FuturePilot on 2011-06-01
See here for a workaround. [http://ubuntuforums.org/showpost.php?p=8452729&postcount=7]("http://ubuntuforums.org/showpost.php?p=8452729&postcount=7")

---

### Post by m-momr on 2011-06-02
> **FuturePilot said:**
> See here for a workaround. [http://ubuntuforums.org/showpost.php?p=8452729&postcount=7]("http://ubuntuforums.org/showpost.php?p=8452729&postcount=7")

Thanks :)

---

