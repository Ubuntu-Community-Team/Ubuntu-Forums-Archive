---
title: "changed default shell on LAMP now permission denied"
date: 2007-05-12
forum: Server Platforms
---

### Post by aricw15 on 2007-05-12
Hello


I just recently set up an Ubuntu 7.04 LAMP server and have added three users.  I was the initial user created during setup but in an attempt to change the default shell I was using, I used this command:

sudo chsh -s /bin/bash [myusername]

It then prompted me for a password as I expected and I typed in the old password I was already using.   Anyway i logged out and tried to log back in but my password no longer works and my permission is denied.  My question is, did I mess up the password somehow through changing my default shell?  My second question is how might i go about fixing this... I attempted logging in with a separate user and using the command:

sudo passwd [myusername] 

But it did not seem to make any changes or bring up any prompt for changing the password.  Well anyway, if anyone knows anything about this it would be greatly appreciated,  thanks.

-Aric

---

### Post by aricw15 on 2007-05-12
update:

when trying to login over ssh i was getting a simple permission denied message but when I try to login at the machine it appears that my password works but I get this error:

Cannot execute /bin/bash/ :  Not a directory

---

### Post by aricw15 on 2007-05-12
Fixed -- thanks for the views but I fixed this by mounting the hard drive through a live cd and editing the passwd config.

---

