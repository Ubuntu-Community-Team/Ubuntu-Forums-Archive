---
title: "how do i get php working?"
date: 2010-06-22
forum: Server Platforms
---

### Post by buckley310 on 2010-06-22
i have a basic apache2 setup on ubuntu server and from what i can tell i need a file called libphp5.so and do some stuff with it but i cant find it anywhere... i installed php5 from apt. is it there and im not looking in the right spot or do i need to do anything else?

---

### Post by koenn on 2010-06-25
why do you think you need lobphp5.so ?
WHat are you trying to do ?

---

### Post by Ryan Dwyer on 2010-06-25
If you installed php5 from apt like you said then it should all be done. You just need to restart Apache.

---

### Post by new_tolinux on 2010-06-25
> **Ryan Dwyer said:**
> If you installed php5 from apt like you said then it should all be done. You just need to restart Apache.

Just in case, this is how you restart apache:
```
sudo /etc/init.d/apache2 restart
```
Although a reboot should do the trick also.

---

