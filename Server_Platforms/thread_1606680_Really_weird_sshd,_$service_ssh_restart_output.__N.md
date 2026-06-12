---
title: "Really weird sshd, $service ssh restart output.  No ok message"
date: 2010-10-26
forum: Server Platforms
---

### Post by MechaMechanism on 2010-10-26
I go and restart ssh and I get this weird message.  I thought I should be getting ok or fail message, at least thats how I remember it.  What do you think?

nate@universal-mechanism:~$ sudo service ssh restart
ssh start/running, process 16191

---

### Post by carl.davis on 2010-10-26
My results are the same when I enter:

```
service ssh restart
```

Perhaps you used to type something similar to:

```
sudo /etc/init.d/ssh restart
```

Which returns:

```

 * Restarting OpenBSD Secure Shell server sshd
   ...done.
```

---

### Post by CharlesA on 2010-10-26
That's normal, OpenSSH uses upstart now, instead of init.d scripts.

---

### Post by MechaMechanism on 2010-10-26
> **carl.davis said:**
> My results are the same when I enter:

```
service ssh restart
```Perhaps you used to type something similar to:

```
sudo /etc/init.d/ssh restart
```Which returns:

```

 * Restarting OpenBSD Secure Shell server sshd
   ...done.
```

Ah, ok.  This makes me feel better.

> **CharlesA said:**
> That's normal, OpenSSH uses upstart now, instead of init.d scripts.
Thanks for the why.

---

