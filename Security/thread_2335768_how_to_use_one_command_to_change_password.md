---
title: "how to use one command to change password"
date: 2016-09-01
forum: Security
---

### Post by zerop2 on 2016-09-01
i use this command to change password and return succeed to change password in ubuntu 14
but, when i login with root , it can use old password login with sudo su


first password linuxpassword is not the old password i use
second password linuxpassword is the new password 

echo -e "linuxpassword\nlinuxpassword" | sudo passwd root

strangely it can run successfully and return changed password

then i try again,

the new password can use when su root , but different from sudo su

---

### Post by steeldriver on 2016-09-01
It's hard to follow exactly what you're asking, but if you have unlocked the root account (i.e. set a regular password for it) then

```

su root

```

will require root's password; whereas

```

sudo su

```

will require *your* password (like any other sudo command)

---

### Post by sisco311 on 2016-09-01
Please check out: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and [https://ubuntuforums.org/showthread.php?t=1486138](https://ubuntuforums.org/showthread.php?t=1486138)

By default, the root account password is locked in Ubuntu. This means that you can't log in directly as root into the GUI or CLI and you can't su to root because  su prompts for the target user's (in this case for the root) password.

By default, sudo is configured to allow admin users to run a command or even start login shell as root or another user. So, you can use sudo to run commands as root because sudo prompts for the invoking user's password.


I hope that this clears some things up.



PS: In my experience most Ubuntu users tend to keep the root account password locked and that's what I would suggest for you too. However if you want to keep your root account unlocked, then I would suggest you to read more about the issue. The links I posted are a good start.

---

