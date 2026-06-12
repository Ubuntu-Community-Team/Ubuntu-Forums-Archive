---
title: "Running shell commands from Apache"
date: 2011-06-03
forum: Security
---

### Post by Plasma2002 on 2011-06-03
Ok, so I have a few web apps that need to run shell commands. Heres a great example of one:

```
$commandLine->execute("amixer get Master");
```

This is a PHP script getting my system volume. Herein lies the problem... **www-data doesn't have permission to do this!**


I changed my apache config to use MY account as the web user, and it does in fact work the way I want it to.


Obviously, I dont want to leave apache running as me, and want it to keep using www-data.... heres my question... **how can I give permission for www-data to execute certain programs**?

---

### Post by bodhi.zazen on 2011-06-03
php will do this, but this is a huge security hole you are opening, so if you have to ask, don't do it.

---

### Post by Plasma2002 on 2011-06-03
> **bodhi.zazen said:**
> this is a huge security hole

ok....... then what would you do? Using my above example, how would you get the system's volume from php?

And let me make it more clear... im already doing it. So it's kind of pointless to tell me not to. Im running apache with my own local account. Im coming here to learn how to make it safer and do what I need to do while using the best practices.

---

### Post by Lars Noodén on 2011-06-04
> **Plasma2002 said:**
> ... **how can I give permission for www-data to execute certain programs**?

That's what [sudo](http://www.bsdly.net/~lars/Lectures/Network-06-sudo.odp) is for.  However, since you will also be using sudo's NOPASSWD tag, you'll absolutely need to include in /etc/sudoers all the parameters exactly as Apache will call them.  

Which user do you want to run the program as?

You might also look at suexec.

---

