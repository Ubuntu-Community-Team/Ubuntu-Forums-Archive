---
title: "How to make a blank password"
date: 2005-03-01
forum: Server Platforms
---

### Post by macjones on 2005-03-01
Hi,

I need to make a user "guest" with a blank password.

It seems everywhere I turn I "must" enter a password.  ](*,) 

Any ideas ?

Either that or I need to be able to SU with a password

(su --command="startx" guest mypassword)

Regards
Mac
New Zealand

---

### Post by Jad on 2005-03-01
I'm not sure about blank passwords, but there is option to allow password less login for some users. 

go to 
Computer ->system configuration -> login screen setup -> general tab
There is a choice available to allow for automatic login.

---

### Post by kathurian on 2005-03-15
[QUOTE=macjones]Hi,

I need to make a user "guest" with a blank password.

It seems everywhere I turn I "must" enter a password.  ](*,) 

Any ideas ?

Either that or I need to be able to SU with a password

(su --command="startx" guest mypassword)

Regards
Mac
New Zealand[/QUOTE]
 create a guest user with any passwordd and than go edit /etc/passwd and delete the x in the line of guest and you will no longer be required to type password for guest.

this will be something like below

guest:x:501:502:Guest:/home/guest:/bin/bash

just remove this x so that it looks like 

guest::501:502:Guest:/home/guest:/bin/bash

and you are done

---

### Post by SilverMast on 2005-12-18
So I've tried editing /etc/passwd and deleting the x, and I've gone into shadow and deleted the encrypted password.  I've done all four possible combinations of keeping and deleting these fields, and still no luck.  What am I doing wrong?  gdm won't let me in and nor will "su - username".  Please help!

---

### Post by fct on 2005-12-18
If you get to it, remember to disable ANY service that allows remote logins, or you are in for a wave of successful remote attacks.

---

### Post by LordHunter317 on 2005-12-18
I'm pretty sure you need to edit /etc/pam.d/common-auth and change the line with pam_unix.so on it to have 'nullok' on the end.  Otherwise, it always rejects null passwords.

However, to prevent security issues with remote services, you should copy that file and name the copy /etc/pam.d/common-auth-local.  Make the change, and then edit any services you want to allow passwordless logins from to use the modified file (look for and change the correct include directive).  This way, newly installed services won't allow the passwordless guest account by default, which is far safer than anything else.

Also, some services like SSH and Samba that use their own authentication mechanisms may need more configuration for passwordless accounts to work.  The above just covers services that use PAM and only PAM.

---

### Post by _David on 2006-11-27
I want to run ubuntu as root when logging in all the time since I am the only one using this machine. Can this be done?

---

### Post by faithsnathan on 2006-11-27
> **_David said:**
> I want to run ubuntu as root when logging in all the time since I am the only one using this machine. Can this be done?
Try [this thread]("http://ubuntuforums.org/showthread.php?p=1813043#poststop").

Hope this helps!

---

### Post by _David on 2006-11-27
> **faithsnathan said:**
> Try [this thread]("http://ubuntuforums.org/showthread.php?p=1813043#poststop").

Hope this helps!

Thank you very much

---

