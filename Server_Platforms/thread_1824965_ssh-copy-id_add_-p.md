---
title: "ssh-copy-id add -p"
date: 2011-08-14
forum: Server Platforms
---

### Post by evarie on 2011-08-14
Hello Everybody,

Can somebody add the function/option portnumber to this commandline program "ssh-copy-id" ?

The program/command "ssh" has already the option -p for a portnumber.

It is strange that the program "ssh-copy-id" have no option -p

!!!


Thanks !

---

### Post by rubylaser on 2011-08-14
It's very easy to do this.  Here's the format...
```
ssh-copy-id -i ~/.ssh/id_rsa.pub '-p port_number user@hostname_or_ip'
```

Hope that helps.  Please mark thread as solved if this works for you.

---

