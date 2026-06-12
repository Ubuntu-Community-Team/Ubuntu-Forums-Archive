---
title: "How to disable the root user account and add a normal user?"
date: 2007-06-29
forum: Server Platforms
---

### Post by tibbe on 2007-06-29
When you install Ubuntu Server 7.04 the installation creates a user account with the username and password you specify. The root account is disabled. I just got a VPS account with Ubuntu preinstalled where there's no user account but the root account is enabled. I would like to have it act like a default install. How do I:

[LIST=1]
[*]Create a user account just like the default install would? With the same groups, etc. as the default install would have added? I know how to create a normal account but I would like it to have the same permissions, etc. as the default one would have had.
[*]Disable the root account and use sudo instead?
[/LIST]

Johan

---

### Post by dreadlord_chris on 2007-06-29
> **tibbe said:**
> When you install Ubuntu Server 7.04 the installation creates a user account with the username and password you specify. The root account is disabled. I just got a VPS account with Ubuntu preinstalled where there's no user account but the root account is enabled. I would like to have it act like a default install. How do I:

[LIST=1]
[*]Create a user account just like the default install would? With the same groups, etc. as the default install would have added? I know how to create a normal account but I would like it to have the same permissions, etc. as the default one would have had.
[*]Disable the root account and use sudo instead?
[/LIST]

Johan
First, create the accoun (reaplce NAME with the desired account name)t:
```

useradd -Gadm,dialout,cdrom,floppy,audio,dip,video,plugdev,scanner,netdev,lpadmin,powerdev,admin NAME

```
The above should all be one line - with no spaces after each comma.
Next, give it a password:
```

passwd NAME

```

Log out of root and into you new account.
Now to lock root:
```

sudo passwd --lock root

```
That should fix you up...

---

