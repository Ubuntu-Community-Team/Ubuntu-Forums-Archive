---
title: "A close call (usermod -G)"
date: 2012-10-21
forum: The Cafe
---

### Post by Wim Sturkenboom on 2012-10-21
Nearly borked my system this morning trying to help a user here.

I ran *_usermod -G www-data wim_* to add the only adminstrative user to the www-data group. This wiped all additional groups that the user was a member of (including sudo) :( Luckily I checked, and because sudo remembered the password and I did not close the terminal yet, I could correct the situation.

Close, very very close.

The correct command is, by the way, *_usermod -aG www-data wim_*

---

### Post by steeldriver on 2012-10-21
yes I've started to use/recommend using gpasswd (which adds the _user _to the _group_) instead for that exact reason

```
gpasswd --add wim www-data
```

---

### Post by Wim Sturkenboom on 2012-10-21
Thanks, I will try to remember that command ;)

It would, by the way, not have happend if there would have been an obvious way in system settings -> user accounts to simply add / remove users to /from groups. There might be a way but I simply did not see it.

Will make another thread about that.

---

### Post by cariboo on 2012-10-21
You could also install gnome-system-tools, then run users-admin to get the old Users & Groups interface back.

---

### Post by Lars Noodén on 2012-10-21
www-data usually shouldn't contain any regular users.  It is reserved by the http server for privilege separation so that parts of it can run unprivileged.

---

### Post by Wim Sturkenboom on 2012-10-22
gnome-system-tools is now installed; currently researching how to integrate it in gnome-control-center (if at all possible).

And I know it was not the optimal solution to make a user a member of www-data; the final solution for the problem was therefore also different.

---

