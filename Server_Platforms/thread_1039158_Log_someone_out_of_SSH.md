---
title: "Log someone out of SSH"
date: 2009-01-14
forum: Server Platforms
---

### Post by magicman5421 on 2009-01-14
I run an ssh server off of xubuntu 8.04. One of the complaints I get is that people close their terminal windows without typing exit, and the system thinks they're still logged in. Since I have logins restricted to one per user, is there some way I could log them out? There is no command that I know of that will do this.
Also, is there a way to terminate someone's ssh connection to my server while they are logged in?

---

### Post by mregister on 2009-01-14
I found this example to make some sense:

[http://systembash.com/content/tag/ssh-server/](http://systembash.com/content/tag/ssh-server/)

---

### Post by magicman5421 on 2009-01-14
Thanks!
That worked perfectly!

---

### Post by Dr Small on 2009-01-14
I have an old alias for doing this:
```
alias killuser='sudo skill -KILL -u'
```

---

### Post by magicman5421 on 2009-01-14
that works too. thanks a lot!

---

