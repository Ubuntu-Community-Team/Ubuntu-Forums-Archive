---
title: "pam.d: smbfs and logon scripts"
date: 2007-05-11
forum: Server Platforms
---

### Post by Kryben on 2007-05-11
2 questions !

I'm using Ubuntu as a client pc connected to a NT4 domain. As authentication mechanism i'm using samba, winbind and pam.d. While loging in, PAM does an authentication using Winbind and  afterwards, if, passwd. Then it creates a homedirectory with /etc/skel as its skelet. And then it mounts 2 secured Windows network shares to subdirectories in the homedir.

It works fine, but I want to expand it by adding 2 things, my 2 questions:

- is it possible to copy and store a file (script) from the DC server BEFORE pam.d starts mounting the shares? As you might know, /etc/security/pam_mount.conf has the ability to let the users have their very own ~/.pam_mount.conf file, with their own mounts specified in this file. If possible, I want to copy this user-specific file from the server, store it in the users' homedir and then having pam.d mounting all shares USING THE SAME PASSWORD TYPED DURING LOGIN.

OR... if there is another solution... ?
I also tried by creating my own script .logon that is called from .profile (or .bash_profile). It does the copy and the mounting, but I have to reenter the users' passwords and above all, the passwords are stored in plaintext (visible, readable; and that's ugly).

- look, this is my common_auth file:
```
auth    required        pam_mount.so
auth    sufficient      pam_winbind.so use_first_pass
auth    required        pam_unix.so nullok_secure use_first_pass
**session required        pam_mkhomedir.so umask=0077 skel=/etc/skel**
session optional        pam_mount.so
```
Check the bold rule, it creates a homedir everytime ones authenticates on this machine. Now, I have a share defined in /Etc/samba/smb.conf:
```
[mytestshare]
comment = My Test Share
writable = no
locking = no
path = /var/tmp
public = no
available = yes
browsable = yes
preexec = echo "%u: connected to %S from %m (%I)" >> /var/tmp/yourloginname.txt
```
I noticed that everytime someone on the network browses to this share, PAM creates a homedir for this user, if it doesn't exist already. Very annoying because there are over 2000 accounts and I don't want to have over 2000 homedirs on every machine with shares.
My question: is there an option, a workaround or a solution for this purpose?

Apologies for my english :) and thanks in advance

---

