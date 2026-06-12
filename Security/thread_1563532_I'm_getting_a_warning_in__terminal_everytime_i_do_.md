---
title: "I'm getting a warning in  terminal everytime i do a commaned now."
date: 2010-08-29
forum: Security
---

### Post by KEE on 2010-08-29
was this from a new update? everytime i use the terminal i get this warning right after i enter commands ```
WARN: /etc is world writable!
WARN: /etc is group writable!
WARN: /lib is world writable!
WARN: /lib is group writable!
WARN: /usr is world writable!
WARN: /usr is group writable!
```

---

### Post by Rinzwind on 2010-08-29
I hardly believe an update will change the right to /etc.



Did you use chmod?

Check with 
ls -l /
what the rights are for these directories en change them from rwxrwxrwx to rwxr-xr-x ;)

---

### Post by KEE on 2010-08-29
> **Rinzwind said:**
> I hardly believe an update will change the right to /etc.



Did you use chmod?

Check with 
ls -l /
what the rights are for these directories en change them from rwxrwxrwx to rwxr-xr-x ;)

k thanks

---

### Post by KEE on 2010-08-29
> **Rinzwind said:**
> I hardly believe an update will change the right to /etc.



Did you use chmod?

Check with 
ls -l /
what the rights are for these directories en change them from rwxrwxrwx to rwxr-xr-x ;)

ok i changed it but i cant use sudo anymore now?  ```
sudo: /etc/sudoers is mode 0755, should be 0440
sudo: no valid sudoers sources found, quitting

```

---

### Post by asp314 on 2010-08-29
> **KEE said:**
> ok i changed it but i cant use sudo anymore now?  ```
sudo: /etc/sudoers is mode 0755, should be 0440
sudo: no valid sudoers sources found, quitting

```

Reboot from a LiveCD, and mount the partition in question. 

```

sudo mkdir /mnt/drive
sudo mount -t ext4 /dev/sda1 /mnt/drive

```

Replace /dev/sda1 and ext4 with the appropriate partition and filesystem type (you can find these out by opening the Partition Editor).  Then chmod the etc/sudoers inside the mount point.

```

sudo chmod 440 /mnt/drive/etc/sudoers

```

Reboot and it should work.

---

### Post by OpSecShellshock on 2010-08-29
If you didn't make the change in permissions on all those directories in the first place, then it would be a good idea to reinstall the OS completely and restore from backups. This would not have been caused by any updates from the repositories.

Even if you did make the initial changes it might be faster to reinstall than to go back through and identify everything that has been messed up and correct it.

---

