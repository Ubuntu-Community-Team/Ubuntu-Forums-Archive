---
title: "lightdm/greeter 12.04: Username and guest session"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Lebowski1 on 2012-04-01
Hi,

i'm trying 12.04 and have one question concerning the greeter and lightdm configuration.
The /etc/lightdm/lightdm.con looks like
```

[SeatDefaults]
user-session=gnome-shell
greeter-hide-users=true
greeter-session=unity-greeter
allow-guest=true

```
So the guestuser-session is allowed by *allow-guest=true*. Also there should be no userlist displayed: greeter-hide-users=true.
But with this configuration, i can only choose the guestuser-session on loginscreen. There is no possibility to enter the username. 
If i disable guestuser with  *allow-guest=false*. I can enter a the username and can login.

But i need both: To login as guest and to be able to enter a valid username and password. But no userlist.
How can I achieve this?

And now for something completely different: How can I achieve the complete userlist displayed, when i use a ldap-server. (all users from ldap should be displayed)


Thanks, Lebowski

---

### Post by coffeecat on 2012-04-01
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

