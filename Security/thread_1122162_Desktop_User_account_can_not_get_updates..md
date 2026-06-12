---
title: "Desktop User account can not get updates."
date: 2009-04-10
forum: Security
---

### Post by starcannon on 2009-04-10
Hello all,

I am currently setting up a laptop for someone, and what I would like very much to be able to achieve is getting a Desktop User account set up so that they can not administer the system, BUT, still be able to get the system updates from the Update Manager.

I am not new to Ubuntu, but I am new to setting up a more secure system.

Any help would be appreciated; I have googled, but can only figure that I am not asking google the correct question for the desired answer.

Thanks in advance.

Rob aka starcannon

---

### Post by bodhi.zazen on 2009-04-10
updating requires far ranging system access so ...

You could try to configure sudo to allow the user to run update manager.

See : [http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by starcannon on 2009-04-10
Bodhi.Zazen

Thanks, I'll look into that. Also, do you know if its something I could manage through the Users and Groups utility?

---

### Post by bodhi.zazen on 2009-04-10
No, you have to manually edit /etc/sudoers using visudo 

```
sudo visudo
```

---

