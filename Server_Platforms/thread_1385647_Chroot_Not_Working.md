---
title: "Chroot Not Working?"
date: 2010-01-19
forum: Server Platforms
---

### Post by deltatux on 2010-01-19
Hey guys,

I'm trying to create a chroot jail for a user (part of a college class lab) and so I followed the instructions from here: [http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny)

For the chroot jail, I made a folder on the / folder called chroot (so the path is /chroot). The user that's to be chrooted was to be called myuser. Fine, so I ran the script from that link to chroot it, but right now the chroot user can navigate out of the /chroot folder to the system root folder.

Right now I have this as my folder structure:
> 
/
/bin
/boot
/cdrom
/chroot
/chroot/bin
/chroot/dev
/chroot/etc
/chroot/home --> /home
/chroot/lib
/chroot/lib64
/chroot/sbin
/chroot/usr
/dev
/etc
/home
/lib
/lib64 --> /lib
/lost+found
/media
/mnt
/opt
/proc
/root
/sbin
/selinux
/srv
/sys
/tmp
/usr
/var


The point of my chroot is so that when logged into myuser, this user cannot navigate or do anything outside of the chroot jail located at /chroot.

When logged in, when I type:
```

echo $HOME

```
The output was correct, it says: /chroot/home/myuser

I'm running Ubuntu Server 9.10 x86-64.

Thanks,
deltatux

---

### Post by Lars Noodén on 2010-01-20
You cannot symlink out of a chroot jail.

---

### Post by bluefrog on 2010-01-20
what's your goal?

allow access to user only via sftp?

in that case

Subsystem sftp internal-sftp
Match User user   (or Group name-of-group)
 ChrootDirectory %h
 ForceCommand internal-sftp

---

### Post by deltatux on 2010-01-20
> **Lars Noodén said:**
> You cannot symlink out of a chroot jail.

So what do you suggest? Place the home directory in /chroot/home instead as a folder and have everything copied there?

> **bluefrog said:**
> what's your goal?

allow access to user only via sftp?

in that case

Subsystem sftp internal-sftp
Match User user   (or Group name-of-group)
 ChrootDirectory %h
 ForceCommand internal-sftp

No, this is for SSH and local access.

Thanks,
deltatux

---

### Post by Lars Noodén on 2010-01-21
> **deltatux said:**
> So what do you suggest? Place the home directory in /chroot/home instead as a folder and have everything copied there?


That's one way.  Another way is to put what you want in the chroot and then symlink from the home folder to the chrooted sub-folder.  You can symlink to a chrooted directory not out of it.

> **deltatux said:**
> 
No, this is for SSH and local access.


SSH or SFTP?

If SFTP is enough then chrooting is easy.  Look for detailed descriptions of chrooting sftp with openssh-server elsewhere in this forum.

---

