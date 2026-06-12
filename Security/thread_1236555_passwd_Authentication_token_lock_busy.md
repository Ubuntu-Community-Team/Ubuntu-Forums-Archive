---
title: "passwd: Authentication token lock busy"
date: 2009-08-10
forum: Security
---

### Post by asbesto on 2009-08-10
passwd for users doesn't work; I obtain this messege:

> passwd: Authentication token lock busy

:confused:

The fs is mounted rw, so mount -o remount,rw didn't solved. 
passwd from root works fine. Users can't change theyr password...

Any hint?

---

### Post by cariboo on 2009-08-10
You seem to be a little short on info, have you tried System > Prefs > About Me > Change Password?

---

### Post by asbesto on 2009-08-16
> **cariboo907 said:**
> You seem to be a little short on info, have you tried System > Prefs > About Me > Change Password?

Short on info? What do you need to know more?

It's a server, so no X, No "System Prefs Whatsoever" stuff.

Users on the system can't use "passwd" to change their own password.
Only root can do it.

> 
asbesto@commercialista7:~$ uname -a
Linux commercialista7 2.6.26-2-686 #1 SMP Thu May 28 15:39:35 UTC 2009 i686 GNU/Linux
asbesto@commercialista7:~$ 
asbesto@commercialista7:~$ passwd
Changing password for asbesto.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
[B]passwd: Authentication token lock busy
passwd: password unchanged[/B]
asbesto@commercialista7:~$
asbesto@commercialista7:~$ su -
Password: 
root@commercialista7:~# passwd asbesto
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
root@commercialista7:~# 



Any hint?

p.s. Can be something PAM-related? A lock file somewhere? 

:(

---

### Post by cariboo on 2009-08-16
You just proved my point, if you had said your were running a server, I wouldn't have given you a gui solution.

To allow users to change their password add chpasswd to /etc/pam.d:

```
sudo touch /etc/pam.d/chpasswd
```

Then edit the file so it contains the following line:

```
@include common-password
```

---

### Post by asbesto on 2009-08-20
Sorry for misunderstanding, I was short on info. :) But again, this doesn't solved the problem :(

> 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: Authentication token lock busy
passwd: password unchanged
asbesto@commercialista7:~$ 


:confused:

ps In every ubuntu system I have, any user can change his password without any pam configuration like that:

> 
asbesto@wopr:~$ passwd
Changing password for asbesto.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
asbesto@wopr:~$ 



:shock:

---

### Post by asbesto on 2009-08-20
I was so stupid not to think about using strace!

**strace passwd ** pointed me to the problem:

> 
open("/etc/.pwd.lock", O_WRONLY|O_CREAT|O_CLOEXEC, 0600) = -1 EACCES (Permission denied)
nanosleep({0, 1000000}, NULL)           = 0
open("/etc/.pwd.lock", O_WRONLY|O_CREAT|O_CLOEXEC, 0600) = -1 EACCES (Permission denied)


and, also

> 
open("/etc/shadow", O_RDONLY|O_CLOEXEC) = -1 EACCES (Permission denied)


So I figured out a misconfiguration in /usr/bin/passwd permissions, that we changed to prevent the free login of our system to change the password :)

It was wrongly 

> 
-rwx-----x 1 root luther 31640 2008-11-22 17:01 /usr/bin/passwd


and now is, correctly 

> 
-rws-----x 1 root luther 31640 2008-11-22 17:01 /usr/bin/passwd


In this way every user except "luther" can change his own password. 

:guitar: :lolflag:

(yes, we offer a free system with an open shell for everyone :) and not only on GNU/Linux, check [http://museum.dyne.org/index.php/Online/en](http://museum.dyne.org/index.php/Online/en) ;) )

---

### Post by cariboo on 2009-08-20
Thanks for the added info.

Adding the file in /etc/pam.d worked for me, it allowed the 3 users on my server to change their own password. My server is just a box stock Ubuntu 9.04 server install with a few services installed.

---

