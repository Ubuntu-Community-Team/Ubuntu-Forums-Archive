---
title: "Create network-only samba account"
date: 2006-03-15
forum: Server Platforms
---

### Post by fermulator on 2006-03-15
Hi!

I'd like to create samba access for a particular user account for samba sharing.
Currently, I create samba accounts using: "smbpasswd -a local_username"

Unfortunately, this requires that there be an actual UNIX account present to create it.  Since this is the case, how can I DENY that unix account for loging in at the local shell, or connecting ssh?

Basically I'd like this user to be able to see samba shares, but not login to the server using any other means...

(This is just like the Windows "DENY LOCAL LOGON" policy.....which is how I would do it in Windows.)

Any tips would be appreciated!

Thanks

---

### Post by kronepils on 2006-03-15
In /etc/passwd you have all the entries with your users. Both system and regular users. To remove their ability to login, change their homedir to /dev/null and their shell (the shell is what's called upon login) to /bin/false. Someting like this:

USERNAME:x:UID:GID::/dev/null:/bin/false


Hope it works for you. It does for me, but I'm not using samba. But I do use it...

---

### Post by derelict on 2006-03-15
And the command will be something like:
```
useradd -s /bin/false -d /dev/null *username*
```
To modify existing users:
```
usermod -s /bin/false -d /dev/null -L *username*
```
The -L switch locks the user's password, Windows' equivalent is "User cannot change password". But we won't be able to login to change the password in the first place.

---

