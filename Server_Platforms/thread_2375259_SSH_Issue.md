---
title: "SSH Issue"
date: 2017-10-23
forum: Server Platforms
---

### Post by biotic2 on 2017-10-23
Hey,

So I am running a headless ubuntu server. The server has 2 accounts thus far. When I ssh into it, and use account1, I have access to all the ssh shortcuts (tab to finish filename, etc) and it displays "account1@servername:~$". That is fine. But when I use account 2, I cannot use the shortcuts and it only displays "$" without a username of the server name.

Any help would be greatly appreciated

Thanks

---

### Post by The Cog on 2017-10-23
Check what working directory and shell the second user is configured for. I think you may find they are not configured for /bin/bash, or their configured home directory is missing. You should be able to see this info in /etc/passwd.

---

