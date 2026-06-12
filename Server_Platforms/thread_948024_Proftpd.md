---
title: "Proftpd"
date: 2008-10-14
forum: Server Platforms
---

### Post by unsoc on 2008-10-14
I haven't used my home server for awhile now and I've forgot my login for the FTP. How can I make a new user account in SSH letting me see all the server files so I can grab some things I need off it?

---

### Post by lykwydchykyn on 2008-10-15
Usually, proftpd uses system accounts for authentication.  If you can ssh in, you should be able to ftp in.  Of course, if you can ssh in, why not just sftp?

---

### Post by unsoc on 2008-10-17
I'm not to familure with ssh commands to be honest. I'm just starting out with playing with the server at my home so I can use it for some things at work.

After throwing some names and passes at it I was able to get back into it.

---

### Post by lykwydchykyn on 2008-10-17
sftp commands are the same as ftp, it just runs over ssh and requires no extra installation apart from openssh-server.

If you need a graphical client, you can use konqueror or nautilus, or winscp on windows.

---

### Post by unsoc on 2008-10-19
Thanks for the information, I've removed proftpd now.

---

