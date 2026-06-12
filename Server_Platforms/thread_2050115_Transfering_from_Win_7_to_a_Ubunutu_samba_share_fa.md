---
title: "Transfering from Win 7 to a Ubunutu samba share fails unless server is restarted"
date: 2012-08-30
forum: Server Platforms
---

### Post by z0mbi3 on 2012-08-30
This is a weird one. When I try to transfer files from Windows 7 to a Samba share on my Ubuntu server the transfer will hang on discovering files, eventually failing altogether. All that can be seen in the folder is a 0kb file where the file should have gone.

If I restart the samba daemon then it still doesn't work. If I restart the whole server then it works for a time but eventually goes back to the above behaviour.

This always used to work fine up until around a week ago. All I can think is that an update must have knackered something but I'm unsure what. I've certainly made no config changes to samba.

Any help would be greatly appreciated.

---

