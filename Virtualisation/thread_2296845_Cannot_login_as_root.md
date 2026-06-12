---
title: "Cannot login as root"
date: 2015-09-29
forum: Virtualisation
---

### Post by sunveer on 2015-09-29
I have setup a LXC container using libvirt and I can't login as root using "virsh console <container>".  I can login as non root successfully but not as root.  I have set root password.

<container>/var/log/auth.log contains

```

Sep 29 17:07:45 ubuntu login[1454]: pam_securetty(login:auth): access denied: tty '/dev/pts/0' is not secure !
Sep 29 17:07:48 ubuntu login[1454]: FAILED LOGIN (2) on '/dev/pts/0' FOR 'root', Authentication failure

```

Please suggest, tty1 and :0 is enabled in /etc/securetty.

---

