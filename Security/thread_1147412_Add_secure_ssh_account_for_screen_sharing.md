---
title: "Add secure ssh account for screen sharing"
date: 2009-05-03
forum: Security
---

### Post by helino on 2009-05-03
Hi everyone,

I'm wondering if it's possible to add a user that only can do one command, for example cat. The reason I'm wondering is because I want to share my terminal screen with some friends while developing, and one really nice way to do that is with screen, see [http://www.linux.com/feature/56443](http://www.linux.com/feature/56443).

Now, I only want the user that ssh to my box to be able to do one thing, and that is:
```
screen -x
```

Is this possible to set up? The reason for this is that I want all my friends to share a single ssh key, and this key can quite easily fall into other peoples hands if someone attacks my friends computers...

---

### Post by bodhi.zazen on 2009-05-03
Yes you can set this up.

Security is of course the issue.

What you will need to do is ssh into the box and start a shared screen session. This is where you set your options (screen acl).

You then give keys to the guests.

See this blog for a road map : 
[http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/](http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/)

---

### Post by helino on 2009-05-05
Wow, thanks alot, I will read this when I get home

---

