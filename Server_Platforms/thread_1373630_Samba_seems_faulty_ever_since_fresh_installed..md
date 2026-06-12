---
title: "Samba seems faulty ever since fresh installed."
date: 2010-01-05
forum: Server Platforms
---

### Post by Grey08 on 2010-01-05
Hi

the samba seems not working ever since i fresh install from system. When i want to share a folder, error message appears :

Samba's testparm returned error 1: Loaded smb config files from --parameter-name=usershare allow guests
lp_load: refreshing parameters from --parameter-name=usershare allow guests
params.c:OpenConfFile() - Unable to open configuration file "--parameter-name=usershare allow guests":
	No such file or directory
Error loading services..

Why is that? is that i havent install its other installation? i installed it from "apt-get install". But when i go to other Windows XP, i can see this [ubuntu box] at the [network place]

Best regards
Grey08

---

### Post by Muttley99 on 2010-01-06
can you post your smb.conf file?

save your smb.conf as something else and restart samba;

[HTML]sudo /etx/init.d/samba restart[/HTML]

are the smb.conf permissions correct and is it installed in the correct place?

[HTML]/etc/samba.smb.conf[/HTML]

so from XP you can see the share? but you can't see the share from a linux client? did you try findsmb from the client?

---

