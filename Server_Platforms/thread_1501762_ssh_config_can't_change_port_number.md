---
title: "ssh_config can't change port number"
date: 2010-06-04
forum: Server Platforms
---

### Post by mrmooge88 on 2010-06-04
I've got 10.04 on a headless server on a home network.
I've edited /etc/ssh/ssh_config and changed line 39 from:

#   Port 22

to:

Port 30000

I then
user@server$: sudo /etc/init.d/ssh reload

from the host
user@desktop$: ssh servername -p 30000
ssh: connect to host servername port 30000: Connection refused

What am I doing wrong?
I've also tried completely restarting the computer.
Thanks for the assistance.

---

### Post by Bachstelze on 2010-06-04
The file you want to edit is [font=monospace]ssh**d**_config[/font]. ;) [font=monospace]ssh_config[/font] is the config file for the SSH *client*, not the server.

---

### Post by mrmooge88 on 2010-06-04
Whoops! Thanks. It looks like I need to pay a little more attention.

---

