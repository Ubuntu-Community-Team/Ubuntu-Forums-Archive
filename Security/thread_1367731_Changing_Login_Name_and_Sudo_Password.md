---
title: "Changing Login Name and Sudo Password?"
date: 2009-12-29
forum: Security
---

### Post by Fernando Hernandez on 2009-12-29
Hello,

I just got a new laptop for Christmas, and I want to give my old (damaged but still usable) one to my mother.  She's already used mine a few times and likes the configuration, so I figure it would be easier to simply change my name and login password to one for her, rather than set up a new user account for her.  My laptop has Kubuntu 9.04 on it.  What do I have to do to change my username and login/sudo password to a new one?  If there is no way, then how do I set up a new user account that she can log into?

Thanks.

---

### Post by sp0nge on 2009-12-29
usermod will be the way to accomplish your goal. 

to see the options or learn how this works:

```
man usermod
```

---

### Post by Fernando Hernandez on 2009-12-29
Thanks, I was able to change the username and password and both work, but now after a reboot it won't log me in because it says it can't access the home folder.  I set the new home folder to one with her name, and I assumed it would create it, but it looks like it's not working.  Now after I go to log in with the new name and password it tells me

"Cannot enter home directory.  Using /."

Is there any way to fix this?  I can still log into a terminal.

---

### Post by puppywhacker on 2009-12-30
the user's home directory is specified in the /etc/passwd

```
user1:x:1016:1016::/home/user1:/bin/bash

```
The username "user1" has user-id 1016. The directory should also be owned by this user

```
chown user1 /home/user1

```

And the user should have read and write rights and executable (to enter a directory)

```
chmod 700 /home/user1

```

---

