---
title: "View MySQL Connections?"
date: 2007-11-02
forum: Server Platforms
---

### Post by tocleora on 2007-11-02
I have a server with multiple web sites on it, and I've been recently getting a lot of too many connections errors.  I'm pretty sure everything is closed up, so I honestly don't know where to look for the error.  is there a command that I can use to see what connections are open?  I know show status tells me the number of open connections (which is constantly growing) but I'd like to know which username those open accounts are.  TIA...

---

### Post by dantrevino on 2007-11-03
mytop is nice and in the repos

or

show processlist;

But obviously this wont be so useful for web apps that use a single user for db connections.

dan

---

### Post by GigaVolt on 2007-11-03
I use:
```
show full processlist;
```

---

