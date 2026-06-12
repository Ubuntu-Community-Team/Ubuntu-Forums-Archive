---
title: "Samba as Domain Controller (sudo problem)"
date: 2005-11-28
forum: Server Platforms
---

### Post by sami83 on 2005-11-28
I have a slight problem setting up samba PDC using Ubuntu.

I cant seem to be able to get Samba to add an accounts automatically for machines upon joining a domain becouse of sudo, since you need to be logged in for sudo to work. The add machine script is like this:

add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u

I tried to set the sudoers file so that one user wouldnt have to type in password at all when using sudo but that wont work since you need to be initially logged in...

If i add the machine accounts by hand Samba as a PDC works just fine.

---

### Post by LordHunter317 on 2005-11-28
Samba is logged in when sudo runs, and it will work.

Normally, these actions would be performed as root.  You have two options:[list=1][*]Add a user the 'admin users' rist globally in /etc/samba/smb.conf.  That user will perform all operations on the Samba server as root, and will be able to add machines.[*]For whoever is the domain admin(s), add this line to /etc/sudoers:```
user ALL = (root) NOPASSWD: /usr/sbin/useradd
```and then edit 'add machine script' to use sudo.  This will work, but you must connect as the user listed in /etc/sudoers when adding the account.

---

### Post by sami83 on 2005-11-28
[QUOTE=LordHunter317]Samba is logged in when sudo runs, and it will work.

Normally, these actions would be performed as root.  You have two options:[list=1][*]Add a user the 'admin users' rist globally in /etc/samba/smb.conf.  That user will perform all operations on the Samba server as root, and will be able to add machines.[*]For whoever is the domain admin(s), add this line to /etc/sudoers:```
user ALL = (root) NOPASSWD: /usr/sbin/useradd
```and then edit 'add machine script' to use sudo.  This will work, but you must connect as the user listed in /etc/sudoers when adding the account.[/QUOTE]

Thank you very much for the reply, this did the trick (looks like i still have some studying to do on Samba :) )

---

