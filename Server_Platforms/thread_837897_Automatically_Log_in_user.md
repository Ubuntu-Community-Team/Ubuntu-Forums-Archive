---
title: "Automatically Log in user"
date: 2008-06-23
forum: Server Platforms
---

### Post by magicplayr2000 on 2008-06-23
Hi, what's a good way to automatically log in a user when my server has to restart?  I just lost power for a second, just long enough to make me realize how much of a pain it is to hook a monitor and keyboard back up in order to log a user in.

If it's not a good idea to do this, which is understandable, will everything work properly without a user logged in?  I've got a cron job tied to an account, will that job still run without the user logged in?

---

### Post by cariboo on 2008-06-23
You don't have to login, if you are using ssh you log in when you connect from an other computer.

Jim

---

