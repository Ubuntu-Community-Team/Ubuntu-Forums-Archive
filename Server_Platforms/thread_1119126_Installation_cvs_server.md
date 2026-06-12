---
title: "Installation cvs server"
date: 2009-04-07
forum: Server Platforms
---

### Post by Abdujaparov on 2009-04-07
Hi,
I installed a cvs server on ubuntu.The jail root is /repository and in this folder there is the folder /xubuntu. I initialized /repository/xubuntu with the init command. I create the user in this way:

```

cvsd-passwd /repository/xubuntu +angelo

```

After that I tried to commit a new project (the first project) from eclipse. 
When I try to commit I receive this error:

```

:cvs add: cannot /xubuntu/nomeProgetto: Permission deniend

```

I searched on the web and I read the problem is caused from permission, so I launche these commands:

```

angelo@angelo-server:/repository/xubuntu/CVSROOT$ sudo usermod -g cvs angelo
angelo@angelo-server:/repository/xubuntu$ sudo chgrp -R cvs /repository/xubuntu/
angelo@angelo-server:/repository/xubuntu$ sudo chmod -R 770 /repository/xubuntu/

```

After these commands I receive this error:

> 
Could not connect to :pserver:angelo@169.254.8.46:/xubuntu: I/O exception occurred: Connection refused: cvs pserver: cannot open /xubuntu/CVSROOT/config: Permission denied
Connection refused: cvs pserver: cannot open /xubuntu/CVSROOT/config: Permission denied


The permission of the folders are:

```

angelo@angelo-server:/repository$ sudo ls -al /repository/xubuntu/
totale 12
drwxrwxrwx  3 root cvs  4096 2009-04-06 22:03 .
drwxr-xr-x 10 root root 4096 2009-04-06 22:03 ..
drwxrwxrwx  3 root cvs  4096 2009-04-06 22:40 CVSROOT

```

Could someone help me?
How can I solve?

Thanks, bye bye.

---

