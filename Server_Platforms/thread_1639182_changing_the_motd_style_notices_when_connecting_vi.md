---
title: "changing the motd style notices when connecting via ssh"
date: 2010-12-06
forum: Server Platforms
---

### Post by sean.ferguson on 2010-12-06
Hi, 

I'm running Ubuntu Server 10.10 and noticed that every time I log into the server via ssh it gives details that i don't necessarily want it to show.
```

[B]Linux zeus 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/[/B]
Last login: Mon Dec  6 19:01:53 2010 from 192.168.2.3
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
```The section in bold i know to be found in /etc/motd but when i edit and save the file the changes are not saved. Does anyone know what file this is stored in and how i can change this. Thanks :)

---

### Post by windependence on 2010-12-06
There are scripts that generate the motd in **/etc/update-motd.d/.**
 
Remove what you don't want from the directory or add your own.
 
-Tim

---

### Post by sean.ferguson on 2010-12-06
Oh I see, thanks for your help.

I much more used to BSD based systems on server platforms :)

---

### Post by dwhitney67 on 2011-03-28
> **windependence said:**
> There are scripts that generate the motd in **/etc/update-motd.d/.**
 
Remove what you don't want from the directory or add your own.
 
-Tim

Removal of unwanted files is an option; however I would recommend that one merely change the permissions on the file(s) so that they are no longer executable.
```

sudo chmod -x <file>

```

---

