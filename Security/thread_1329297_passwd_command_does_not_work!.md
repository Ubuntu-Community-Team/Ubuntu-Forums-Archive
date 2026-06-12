---
title: "passwd command does not work!"
date: 2009-11-17
forum: Security
---

### Post by snakeman21 on 2009-11-17
This is very strange:  

```
sean@karmic:~$ passwd
Changing password for sean.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

```

But then, when I try to open administrative apps, or when I log out and log in,  it will not accept the new password.  It still only recognized the old one.  I tried it again using "sudo passwd" and got the same results.  WTF?

Edit:  Nevermind, I rebooted in recovery mode and used a shell prompt.  For some reason, it worked that way.  ???

---

### Post by kloubik on 2009-11-17
> **snakeman21 said:**
> This is very strange:  

```
sean@karmic:~$ passwd
Changing password for sean.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

```But then, when I try to open administrative apps, or when I log out and log in,  it will not accept the new password.  It still only recognized the old one.  I tried it again using "sudo passwd" and got the same results.  WTF?

Edit:  Nevermind, I rebooted in recovery mode and used a shell prompt.  For some reason, it worked that way.  ???

I have the same issue....your workaround works for me, thanks. 
I changed my passwd in recovery mode, but I see this a big issue if Ubuntu handles passwds such a strange way.... BTW, after I changed the passwd in Gnome, the application "Password and Encryption Keys" worked only with new password, but login to system only with old password.

---

### Post by snakeman21 on 2009-11-18
Glad to hear that helped you out!  Now I don't feel so bad about posting a question 5 minutes before stumbling upon the answer!

---

