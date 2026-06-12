---
title: "&quot;locate&quot; command"
date: 2009-07-18
forum: The Cafe
---

### Post by Sealbhach on 2009-07-18
I've noticed since I installed Jaunty that the "locate" command requires sudo powers, if I recall correctly, this wasn't the case in previous releases. Is that correct?

.

---

### Post by dragos240 on 2009-07-18
Weird, I can use it without sudo.

---

### Post by JillSwift on 2009-07-18
> **Sealbhach said:**
> I've noticed since I installed Jaunty that the "locate" command requires sudo powers, if I recall correctly, this wasn't the case in previous releases. Is that correct?

.
I locate just fine on Jaunty without SUper powers. :confused:

---

### Post by sisco311 on 2009-07-18
what's the output of:
```
ls -al /usr/bin/mlocate
```

---

### Post by Yannick Le Saint kyncani on 2009-07-18
You don't need to be root to use locate, however, you won't have access to hierarchies that are normally hidden to you using it.

---

### Post by MikeTheC on 2009-07-18
I've never been able to find the [font=courier]locate[/font] command, sadly.

---

### Post by Sealbhach on 2009-07-18
> **sisco311 said:**
> what's the output of:
```
ls -al /usr/bin/mlocate
```

I get
```

-rwxrwxrwx 1 root mlocate 35352 2009-03-14 18:35 /usr/bin/mlocate
```

I thought iit must be something to do with permissions.

.

---

### Post by sisco311 on 2009-07-18
```
sudo chmod 2755 /usr/bin/mlocate
```

---

### Post by Sealbhach on 2009-07-18
> **sisco311 said:**
> ```
sudo chmod 2755 /usr/bin/mlocate
```

OK, thanks! Works OK now. How might it have got changed?

.

---

### Post by dragos240 on 2009-07-18
you changed the mode so that users can use it. chmod = change mode

---

### Post by sisco311 on 2009-07-18
> **Sealbhach said:**
> OK, thanks! Works OK now. How might it have got changed?

.
[https://bugs.launchpad.net/ubuntu/+source/mlocate/+bug/281471 ?]("https://bugs.launchpad.net/ubuntu/+source/mlocate/+bug/281471 ?")

---

