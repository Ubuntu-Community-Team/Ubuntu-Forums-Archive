---
title: "Sudoers file"
date: 2011-12-21
forum: Server Platforms
---

### Post by atb-nl on 2011-12-21
Hello, i have a problem.

i have 2 users user1 and user2,

i want user1 to su to user2 and execute a script as user2 without having to use a password.

i know this can be done in the sudoers file the only problem is how,
i tried several things but they all resulted in a parse error of the sudoers file.

can you help me ? :confused:

Ubuntu server 11.10 64 bit

---

### Post by Lampi on 2011-12-21
```
sudo visudo -f /etc/sudoers.d/user12
```
paste this syntax into the file, adjust to your needs, then save and quit
```

user1 <PASTEYOURHOSTNAMEHERE>=(user2)NOPASSWD:/path/to/your/script
```
Syntax meaning:
The User called user1
can run on your host only
as user2
without a password
/path/to/your/script

Now check if it works:

```

user1@YOURHOSTNAME:~$  sudo -l
Matching Defaults entries for user1 on this host:
    env_reset, env_keep+="PASSWD USER"

User user1 may run the following commands on this host:
    (user2) NOPASSWD: /path/to/your/script

```

Edit: don't forget to chown user2:user2 /path/to/your/script

---

### Post by atb-nl on 2011-12-21
Thanks for your quick reaction,

visudo gives a syntax error near line 0 at the user12.rules file ?

---

### Post by atb-nl on 2011-12-21
fixed it :

user1 <host>=(user2)NOPASSWD:/home/user2/test.sh

to

user1 host=(user2)NOPASSWD:/home/user2/test.sh

but the sudo -l doesnt give the proper output

---

### Post by atb-nl on 2011-12-21
When i paste the line directly to my sudoers file it works ..

---

### Post by Lampi on 2011-12-21
> **atb-nl said:**
> When i paste the line directly to my sudoers file it works ..
that means the #include sudoers.d line in /etc/sudoers has to be moved up or down a notch ... maybe it has to be at the bottom - I don't recall this one, so it's up to you to try it.

---

### Post by atb-nl on 2011-12-21
> **Lampi said:**
> that means the #include sudoers.d line in /etc/sudoers has to be moved up or down a notch ... maybe it has to be at the bottom - I don't recall this one, so it's up to you to try it.

It works, Thank you for your help :D

---

### Post by atb-nl on 2011-12-21
one last question before i close this again, how do i execute the command, i tried to bash /path/to/my/script ,but when i echo $(whoami), the output is user1 and not user2 .....

---

### Post by Lampi on 2011-12-21
it still has to be sudo /path/to/your/script

the only difference is: now you won't be prompted for your password anymore

edit: maybe you can put "whoami" into your script, then you should get the output of user2

---

### Post by atb-nl on 2011-12-21
doesnt it need to be: ```
sudo -u user /path/to/your/script
``` ??

---

### Post by Lampi on 2011-12-21
yep, you are right :)

sudo -u user2 /path/to/your/script

---

### Post by atb-nl on 2011-12-21
> **Lampi said:**
> yep, you are right :)

sudo -u user2 /path/to/your/script

OK, I know enough now thanks again, it is of great value to me, thank you :D

---

