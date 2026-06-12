---
title: "Passwd change ok, but System Policy password fails"
date: 2013-01-07
forum: Security
---

### Post by Mark Melone on 2013-01-07
I have successfully changed my password on my Ubuntu 12.04 system several times using "passwd <username>".  The password successfully changes, however, I can only log in and make system changes using my old password.  I have changed both the root and user account passwords, but still have the same issue.

For example, let's say my password was:  Password1
I can "change" it to Password2 by
$passwd
Current Password:  Password1
New Password:      Password2
Retype Password:   Password2

However, if I try to apply a network proxy setting system-wide, I must still enter Password1.  This has become a real nuisance, and would like to fix this.

Thanks in advance for your help!!!

---

### Post by steeldriver on 2013-01-07
Hello and welcome

It sounds like your gnome-keyring password has got out of sync with your login password

[https://one.ubuntu.com/help/faq/how-do-i-get-rid-of-the-keyring-password-prompt/](https://one.ubuntu.com/help/faq/how-do-i-get-rid-of-the-keyring-password-prompt/)

I *think* that in 12.04 you can manager the keyring by going to the dash and typing 'Passwords and Keys' - hopefully someone else will chime in

---

### Post by Mark Melone on 2013-01-07
steeldriver,

Thanks for the quick response.  I have updated the gnome-keyring password, but still have the same issue with applying a network proxy system-wide.  :(

---

