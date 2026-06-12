---
title: "how many damn users come pre-installed on intrepid???"
date: 2009-02-19
forum: Security
---

### Post by graysky on 2009-02-19
I just did looked at my /etc/passwd and noticed there are 32 users not counting the two that I added.  Can others confirm this?

---

### Post by ajgreeny on 2009-02-19
Ha-ha! I've got 33.  Don't worry about it because it's sems to be quite normal and includes a lot of system users, as far as I can make out.  They are not all normal users who could log in, or at least, I assume not, as they presumably have no password.  Interesting to see, nonetheless, and I wonder how many other ubuntu users have.

---

### Post by cariboo on 2009-02-19
You should have a look at /etc/shadow,  this will tell you which users have passwords, there should only be users you have set up. You'll need to be root to see the output:

```
sudo cat /etc/shadow
```

Jim

---

### Post by gombadi on 2009-02-19
No damn users here 

```

human@zagbot:~/down$ grep -c damn /etc/passwd
0

```


sorry Friday afternoon - couldn't resist :-)

---

### Post by pirate_tux on 2009-02-19
> **gombadi said:**
> No damn users here 

```

human@zagbot:~/down$ grep -c damn /etc/passwd
0

```


sorry Friday afternoon - couldn't resist :-)

lol

---

### Post by jerome1232 on 2009-02-20
> **gombadi said:**
> No damn users here 

```

human@zagbot:~/down$ grep -c damn /etc/passwd
0

```


sorry Friday afternoon - couldn't resist :-)

That was good lol, on another note if you look at /etc/passwd you'll notice most of those system users have a shell of /bin/false or if you look at /etc/shadow you'll notice those system users all have passwords that start with * or ! meaning they are locked and cannot be used to login.

---

