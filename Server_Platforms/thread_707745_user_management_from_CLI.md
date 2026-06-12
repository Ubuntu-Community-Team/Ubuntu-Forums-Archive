---
title: "user management from CLI"
date: 2008-02-25
forum: Server Platforms
---

### Post by alohre on 2008-02-25
Hello, are there any good tools to manage users from the cli, preferably ncurses based, something alike the gui tools, but usable for a headless server. I have googled a lot, and have not found a single good tool for this. I'm looking for something alike the user management in yast in suse. I know I can use useradd and the likes, but I'd like to have a bit more userfriendly tool with support for user expiration. Just hoping someone has a good answer, unless I have to start whipping up the perl myself :)

---

### Post by jhetrick62 on 2008-02-25
Take a look at the man page for adduser.  It's somewhat interactive and offer a ton of settings possibilities, although useradd offers an expiration option.

addgroup, deluser, and several others that are more interactive than their normal  counterparts like useradd, userdel, ect.

Jeff

---

