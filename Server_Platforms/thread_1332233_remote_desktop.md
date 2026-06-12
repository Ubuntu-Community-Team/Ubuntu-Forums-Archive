---
title: "remote desktop"
date: 2009-11-20
forum: Server Platforms
---

### Post by Hungry_Wolf on 2009-11-20
Hi guys!

I setup a ubuntu server with gnome. I've enable remote desktop but as we know, to fully connected to a the remote server, we need to click "OK" on a pop-up windows that grant access to allow user to share the desktop. My problem now is, after I setup every thing for remote desktop, I forget to grant access to myself, so when at home, I still can't connected to the server. So I'm wondering whats the command line that I need to enter to grant access to myself so that I can remote access there?

Regards,
ChenHaw

---

### Post by scorp123 on 2009-11-20
The command is "vino-preferences" and you can trigger it via SSH. e.g.
```
ssh -X youruser@remote-server "/usr/bin/vino-preferences"
```

---

