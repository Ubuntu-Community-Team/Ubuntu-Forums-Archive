---
title: "successful system login even with wrong password"
date: 2009-06-13
forum: Security
---

### Post by gits83 on 2009-06-13
Hello everyone

I have this weird problem since a couple of days. :(

At the login prompt I can use any password -right or wrong it doesn't matter- to login in my or any -password protected- user account.

Also, when I try to execute any program which requires gksu/gksudo/sudo the password request appears correctly but again I can input any wrong password and the command is executed as root instead of getting the "bad password" message

The same as above is true for the screensaver password request, too.

I have ubuntu 9.04 with all the updates applied.
Thanks for reading :D

---

### Post by dakal on 2009-06-14
Sounds to me almost like the authentication subsystem (I'm assuming here that 9.04 uses PAM) got messed up somehow. I would suggest going through the files in /etc/pam.d and looking for references to modules that sound overly permissive, and post back with what you find.

This command might help (it will show all PAM-related configuration files that have been changed in the last two weeks), but you could do essentially the same thing manually with any tool that lets you list files in a given directory - anything from "ls -l" to a full-fledged file manager. Also remember that this isn't all-inclusive - tools like "touch" allows the file modification time to be set to an arbitrary value.

```
find /etc/pam.* -mtime -14 -print
```

---

### Post by gits83 on 2009-06-14
=D>=D>=D>=D> :D

everything seems fine now, thank you!

I've looked in /etc/pam.d/ and there where some files *.pam-old
the content of one of them was different from the one without .pam-old

that different file was common-auth
common-auth.pam-old was
```
auth required pam_unix.so nullok_secure
auth required pam_ecryptfs.so unwrap

password required pam_ecryptfs.so
password sufficient pam_unix.so

auth	required			pam_permit.so
```
while common-auth was
```
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
auth	required			pam_permit.so
auth	optional	pam_ecryptfs.so unwrap
```

I've replaced common-auth with the content of common-auth.pam-old and everything *seems* working fine now. I wonder *what* played me a joke bad like this :twisted:

Again thank you very much for pointing me to the right direction ;)

---

### Post by dakal on 2009-06-14
Glad that it worked. Yes, putting in a require on pam_permit.so does sound like it could cause that sort of issues.

---

