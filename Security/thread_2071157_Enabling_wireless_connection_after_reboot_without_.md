---
title: "Enabling wireless connection after reboot without password authinication"
date: 2012-10-14
forum: Security
---

### Post by big_mu5 on 2012-10-14
Hi all,
I'm running ubuntu 10.04 on an old desktop as a remote (very remote :)) server. and i use a usb wireless dongle for network connection.
The problem is that the server freezes sometimes because of hardware problems, mostly because the wireless dongle just stops working, i tried  many things on the wireless side but it did not     solve the problem.
What i need is just a temporary solution until my next visit to the server, because now i keep on asking somebody to go and restart it for me. 

The problem is that when i reboot the server it asks for authentication, so if i was to automate the reboot process using a shell script i would need to disable password authentication or the server wont connect to the network... How does one do that? also is there a safer solution?

BTW i tried automatic login but it still asks for the login password before it can connect!

Thanks a lot
big_mu5

---

### Post by cariboo on 2012-10-14
If you have a gui, just open a terminal and type:

```
seahorse
```

and blank your keyring password.

---

### Post by big_mu5 on 2012-10-18
Thanks cariboo907, that worked for me :)

---

