---
title: "Running application server, or serving files though app-get"
date: 2012-09-14
forum: Server Platforms
---

### Post by tombruton87 on 2012-09-14
We are setting up a server for an office, we need to be able to control what applications are installed on systems, however at the same time want to give our employees the most flexibility. All of our machines are running Ubunutu and are all full desktop's not thin clients.

The reason I am against have a local apt-get repo is the constant work of keeping programs and packages up to date.

What would you guys recommend. Any more detail wanted fire away!

---

### Post by sandyd on 2012-09-16
That is easy.
To install software on Linux, you need root/sudo permissions.

Simply create an non-administrator account for the user to use. They will not be able to install applications, as only root/sudoed users can.

---

### Post by markbl on 2012-09-16
Why not set up apt-mirror on your server? It will keep itself updated automatically so there is no work there. User PC's will just apt-get update from that server and present each user the occasional "updates available" prompt so little work there either?

Advantage is that all your packages are downloaded once only on your internet link, not once per user machine, and only when you schedule the cron job, i.e. overnight.

---

