---
title: "Samba on Gutsy 64bit"
date: 2007-10-24
forum: Server Platforms
---

### Post by trmentry on 2007-10-24
I'm working on config of a 64 bit install of Gutsy in a vmware machine to test to make sure all my software that I want to migrate from my old Gentoo box will work on it fine.  

Anyway, when I installed Gutsy, I selected LAMP, Mail Server, SSH, and Samba.

I copied over my smb.conf from my exisiting Gentoo box that works fine.

```

[global]
        workgroup = HOME
        server string = Samba Server %v
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        ldap ssl = no
        create mask = 0664

[files]
        comment = Misc Files and Programs
        path = /shares/files
        valid users = @users
        admin users = @admin
        write list = @admin

```

I then added my logon account to smbpasswd

```

smbpasswd -a trmentry
smbpasswd -e

```

I made sure 'trmentry' is in the admin and users groups in /etc/group

After that I logged onto my Windows XP box and attempted to attach to \\server\files

It thinks for a min, then prompts me for a password... which is odd as it has the same passwd as my windows logon so shouldn't.  My Gentoo box doesn't prompt me as my smbpasswd is same as windows.

Anyway, I'm not seeing anything in /var/log/samba/log.smbd other than the following.

```

#tail log.smbd
[2007/10/24 00:37:27, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2007/10/24 00:37:29, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2007/10/24 00:37:29, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2007/10/24 00:37:30, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2007/10/24 00:37:30, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users

```

Does anyone have any pointers on where I've gone wrong with this?

Thanks

---

### Post by trmentry on 2007-10-25
Ok I finally got it to be seen by my XP machine.

```

[files]
        comment = Misc Files and Programs
        path = /shares/files
        read only = yes
        create mask = 644
        directory mask = 755
        force user = nobody
        force group = nogroup
        #valid users = @users
        #admin users = @admin
        #write list = @admin

```


I made the above changes.

Now my question is, I want the share to be read only for everyone except for admins.   When I uncomment the admin users and write list, its still read only for my account which is in the admin group.

Any pointers now?

Thanks

---

### Post by trmentry on 2007-10-27
I changed my stanza to the following.
```

[files]
        comment = Misc Files and Programs
        path = /shares/files
        create mask = 644
        directory mask = 755
        write list = user1

```
yet I still can't write to the share as user1.  this is a serious fault as I can't setup the shares the way that is needed to make sure they are readonly for all except for the few exceptions.    Setting up a share to be readonly for all or write for all is kinda bad if you truly want to setup permissions on the shares similar to a windows box.

Again, I can do this on a gentoo server so seems that something isn't quite right with samba on ubuntu.  I've even gone as far as removing my smb.conf and using my gentoo one but still no dice.


Does anyone have any pointers or advice?  

Thanks

---

### Post by sot3 on 2007-10-28
I had the same problem, and it appears to be some sort of glitch with smb.conf though I haven't had time to figure out exactly what yet.

I say that because I fixed it as follows:

sudo apt-get remove samba
sudo apt-get remove samba-common
sudo mv /etc/samba/smb.conf /tmp
sudo apt-get install samba

Then I re-customized the new smb.conf that it created for me, which fortunately isn't too difficult.  I'll take a closer look at the old vs. new when I have time later today, but thought others may benefit from this.

---

### Post by trmentry on 2007-10-28
> **sot3 said:**
> I had the same problem, and it appears to be some sort of glitch with smb.conf though I haven't had time to figure out exactly what yet.

I say that because I fixed it as follows:

sudo apt-get remove samba
sudo apt-get remove samba-common
sudo mv /etc/samba/smb.conf /tmp
sudo apt-get install samba

Then I re-customized the new smb.conf that it created for me, which fortunately isn't too difficult.  I'll take a closer look at the old vs. new when I have time later today, but thought others may benefit from this.

That did it.  THANK YOU!!

---

### Post by Loevborg on 2008-01-16
> **sot3 said:**
> I had the same problem, and it appears to be some sort of glitch with smb.conf though I haven't had time to figure out exactly what yet.

I say that because I fixed it as follows:

sudo apt-get remove samba
sudo apt-get remove samba-common
sudo mv /etc/samba/smb.conf /tmp
sudo apt-get install samba

Then I re-customized the new smb.conf that it created for me, which fortunately isn't too difficult.  I'll take a closer look at the old vs. new when I have time later today, but thought others may benefit from this.

Thanks from myself, too. Very helpful. It seems it was a leftover from an old debian installation. It's also useful to remove winbind, if it isn't used.

---

### Post by duren on 2008-02-16
Glad I found this post. Followed the instructions, moved my smb.conf back to /etc/samba, restarted the service and boom, I was in.

Gutsy 32bit,
2.6.22-14-server #1 SMP,
Samba version 3.026.

Thanks again guys.

---

### Post by BenderIII on 2008-03-10
Thanks a lot for this.  It's saves me one more day without having my network access running.

I too have an AMD64 installation of 7.10
It looks like the standard installation during setup has a quirk with the 
tdbdsam.  Or it shouldn't have to convert it after reinstall.
tdbsam_open: Converting version 0 database to version 3.

And now to the nice part of the day...
:popcorn:

---

