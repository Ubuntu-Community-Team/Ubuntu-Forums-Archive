---
title: "Don't know username or password"
date: 2009-06-03
forum: Security
---

### Post by jzig on 2009-06-03
I had to let an employee go and unfortunately, he wouldn't leave me the username and password for his workstation.  It is my machine and I have complete physical access to it, but I am not a linux person.  Is it possible for me to gain access to his account or any account on the machine?
Thanks.

---

### Post by rookcifer on 2009-06-03
You don't happen to be the boss of the guy who started the "How Did He Login To My Computer" thread just right below this one are you? ;)

At any rate, you should be able to follow this tutorial here:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Another option is to use a livecd.  There is a thread that's two down below this one where another guy asked this same question.  There are some good answers in it as well.

---

### Post by cdenley on 2009-06-04
Just boot into recovery mode, and choose the "root shell prompt" if asked. You can get the username with:
```

getent group admin

```
It should be listed after the last ":". Then to reset the password:
```

passwd [username]

```

---

### Post by nebileix on 2009-06-04
> **rookcifer said:**
> You don't happen to be the boss of the guy who started the "How Did He Login To My Computer" thread just right below this one are you? ;)

At any rate, you should be able to follow this tutorial here:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Another option is to use a livecd.  There is a thread that's two down below this one where another guy asked this same question.  There are some good answers in it as well.

LOL!!! I think likewise as well...

---

