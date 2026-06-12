---
title: "Adding a new user"
date: 2011-12-02
forum: Server Platforms
---

### Post by wingdom on 2011-12-02
I am fairly new to running my own Ubuntu server. I tried to add a second user to the server with the following command:
```
sudo useradd -d /home/user -m user -p 12345
```
When I log into this account, the only prompt I get is:
```
$
```
Opposed to what I should get:
```
user@ubuntu-server:~$
```
No commands work, except exit. What did I do wrong, and what can I do to fix it?

---

### Post by lykwydchykyn on 2011-12-02
Sounds like /etc/skel did not get copied over to the new user's home.  If you "ls -al" the contents of the home directory, do you see any files?

Also sounds like a valid shell was not assigned.

Can you post the output of 
```

grep user /etc/passwd

```

(where "user" is the username you created)

---

### Post by wingdom on 2011-12-02
Output of "grep user /etc/passwd"
```
user:x:1001:1001::/home/user:/bin/sh
```

ls -al
```

folders:
.cache

files:
.bash_logout
.bashrc
.profile

```

---

### Post by lykwydchykyn on 2011-12-02
Try these commands to see if it sorts out the user:

```

rsync -av /etc/skel/ /home/user/
usermod -s /bin/bash user

```

That will make sure /etc/skel was copied to the user's home directory, and change the default shell from sh to bash.

I typically use the adduser command instead of the useradd since it does a little more for you.  It's hard to remember which is which, though.

---

### Post by papibe on 2011-12-02
I would recommend using the command 'adduser' instead of 'useradd'.


While the last one is low level utility (partial work), 'adduser' does the complete job (as expected).

Hope it helps,
Regards.

---

### Post by wingdom on 2011-12-03
> **lykwydchykyn said:**
> Try these commands to see if it sorts out the user:

```

rsync -av /etc/skel/ /home/user/
usermod -s /bin/bash user

```

That will make sure /etc/skel was copied to the user's home directory, and change the default shell from sh to bash.

I typically use the adduser command instead of the useradd since it does a little more for you.  It's hard to remember which is which, though.

That did it, thanks! In the future I will use adduser.

---

