---
title: "Possible system compromise"
date: 2007-02-06
forum: Server Platforms
---

### Post by bg11 on 2007-02-06
Hi,

I logged in to a machine using ssh and found 2 processes running which I didn't initiate myself: 

```

>ps x
21473 pts/15   S      0:00 /bin/ksh /etc/local/check_login
21475 pts/15   S      0:00 ypmatch myusername rgycmds 

```

Is this something to be concerned about, or is it just normal password checking?  If the latter then why are ypmatch and check_login being ran under my own username and not root?

---

### Post by kpatz on 2007-02-06
Did you install NIS (Network Information System) on your system?  

I have to wonder about that /etc/local/check_login.  /etc/local isn't a normal location for things to be placed.  Is there anything else in /etc/local?  What's in your .bashrc file?

---

