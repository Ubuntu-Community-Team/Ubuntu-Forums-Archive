---
title: "Login Problem"
date: 2009-10-03
forum: Security
---

### Post by Dark Sorrow on 2009-10-03
I am new to ubuntu, just installed it yesterday. In excitement i changed the password(using random password generator) and now i forgot it, so i am unable to login. Is there any other way i can login. I do not wish to format as i have already installed the updates. **Please Help**!!!

---

### Post by ajgreeny on 2009-10-03
Start in Recovery mode from the grub menu and choose to drop to the root shell.  Now in the terminal, type ```
passwd username
```using your username, of course.  You will then be prompted to set a password, and then confirm it again.  Job done.  Reboot and login with new password, and this time either make it something you can remember, or write it somewhere very private.

---

### Post by Dark Sorrow on 2009-10-03
Thank You, ajgreeny.

---

### Post by alimoni on 2009-10-03
> **ajgreeny said:**
> Start in Recovery mode from the grub menu and choose to drop to the root shell. Now in the terminal, type ```
passwd username
```using your username, of course. You will then be prompted to set a password, and then confirm it again. Job done. Reboot and login with new password, and this time either make it something you can remember, or write it somewhere very private.
 
 
I came here with a very similar question. Except I lost the paper where I wrote down both the username and password. Is this fixable? Also, how do you start in recovery mode? 
 
Please let me know if I should have started a new thread. Thanks.
 
Edit: I found the answer after more searching.  I like this ubuntu! Thanks!!!

---

