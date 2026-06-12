---
title: "username password help requested"
date: 2009-03-04
forum: Security
---

### Post by emjcpt on 2009-03-04
OOPS... Another newbie who couldn't leave it alone!

I have a dual boot system WinXP and Ubuntu 8.04.1.

 The installer had username and password set to: newuser. Against his advice I went in and changed both. I thought I remembered them but apparently not. I have tried all combo's and cases so I guess a reset is in order.

 I have read other threads and have figured out how to get to the root shell and to the message "NEW UNIX PASSWORD". I believe I successfully entered a new password. However I cannot find or change my username. Any help would be appreciated.

 Lastly, after making a change what is the proper way to reboot from the root prompt?:(

---

### Post by brian_p on 2009-03-04
> **emjcpt said:**
> 

However I cannot find or change my username. Any help would be appreciated.

/etc/passwd has a list of users.

> Lastly, after making a change what is the proper way to reboot from the root prompt?:(

```
reboot
```

would do it.

---

### Post by LegendofTom on 2009-03-04
You could also do runlevel 1 from grub to set a root passwd, and get in that way.

---

