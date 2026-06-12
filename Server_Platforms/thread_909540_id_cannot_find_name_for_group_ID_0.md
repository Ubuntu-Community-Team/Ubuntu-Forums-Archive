---
title: "id: cannot find name for group ID 0"
date: 2008-09-03
forum: Server Platforms
---

### Post by benauld345 on 2008-09-03
Hi,

for some reason i have started to get the error message:

id: cannot find name for group ID 0

everytime i login as root on my server. I've chmod 433 on /etc/groups and /etc/passwd and chown root.root to them both as well but no luck. any ideas will be much appreciated.

thanks

ben

---

### Post by cdenley on 2008-09-03
Why are you logging in as root?

What is the output of this command?
```

getent group 0

```

---

### Post by promodus on 2008-09-05
can you give the result from:
```
mount
```

is /proc mounted?

---

### Post by benauld345 on 2008-09-05
Hi,

It seems to have fixed itself now :lolflag: cant work out how, just rebooted it and it worked fine!

Thanks for your input!

Ben

---

