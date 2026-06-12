---
title: "Route Table Empty"
date: 2011-08-17
forum: Server Platforms
---

### Post by johngreenfield on 2011-08-17
Hi all,

I haven't got a vast amount of experience with linux, but I've managed to set up several ubuntu servers before. I was working on my personal one, needed to reboot but once it had rebooted I couldn't connect via SSH or http.

I managed to get on the console via my rackspace account, but ifconfig is not recognised as a command (no such file or directory), and my route table is completely empty.

Any ideas?

Thanks alot!!

---

### Post by dinu90 on 2011-08-17
Are you sure you are running the ifconfig command as root? Try running it with the full path:
```

/sbin/ifconfig

```What error do you get?

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

