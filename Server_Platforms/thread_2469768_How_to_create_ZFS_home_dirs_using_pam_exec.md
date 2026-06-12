---
title: "How to create ZFS home dirs using pam_exec"
date: 2021-12-08
forum: Server Platforms
---

### Post by allcoms on 2021-12-08
How do I get pam_exec.so to create a new home dir ZFS dataset for each user who logs in via LDAP? I'm running Ubuntu 20.04, using GDM and nslcd for LDAP auth.

pam's mkhomedir library doesn't have native support for ZFS yet so I've filed a feature request for this on gh. Until that gets implemented, I'll have to hack this together myself.

Here's what I've tried:

I added the following line to the end of /etc/pam.d/common-session

```
session        optional        pam_exec.so /usr/bin/sudo /bin/bash /usr/local/sbin/mkzfshome.sh
```

pam_exec.so has a seteuid option but I've read that only applies to running binaries so it looks like I'll have to use sudo and/or zfs allow to do this. Here's my script to create the dataset: 

/usr/local/sbin/mkzfshome.sh

```
#!/bin/bash

if [ ! -d "/home/$PAM_USER" ]
then
    /usr/sbin/zfs create astarray2/home/$PAM_USER
fi

exit 0
```

I've added this line to the end of /etc/sudoers using visudo:

```
ALL ALL=(ALL) NOPASSWD: /usr/local/sbin/mkzfshome.sh
```

Maybe I'll need to do the same for the zfs command too but that's a last resort. I've tried using `zfs allow` to give all users access to the zfs create and mount commands:

```
# zfs allow -e create,mount astarray2/home
```

Script permissions:

```
-rwxr-xr-x 1 root root 106 Dec  8 11:42 /usr/local/sbin/mkzfshome.sh
```


GDM doesn't let the user login with this config, I just get returned to the login screen and the users home dataset doesn't get created.

Thanks

---

### Post by allcoms on 2021-12-09
I now have this working from the terminal now but not from gdm or lightdm.

[https://askubuntu.com/questions/1379930/how-to-create-zfs-home-dirs-using-pam-exec](https://askubuntu.com/questions/1379930/how-to-create-zfs-home-dirs-using-pam-exec)

---

### Post by allcoms on 2021-12-10
It's working with GDM now. It was the simplest thing catching me out - directory ownership! :D

I've updated the askubuntu question with the working script.

---

### Post by LHammonds on 2021-12-10
I am glad you figured it out because I sure didn't know what to say about it.  Congrats and thanks for letting others know how to resolve it too.

LHammonds

---

