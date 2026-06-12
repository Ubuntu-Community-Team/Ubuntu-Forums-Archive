---
title: "Samba users via webmin"
date: 2009-04-20
forum: Server Platforms
---

### Post by GodsDead on 2009-04-20
Hey all, i have had a samba windows home network for ages now, the problem i have is that me and my brother share the same server, etc. But from windows "network" i gotta login with my account info everytime, i tryed setting up a user for him via the samba interface on webmin (which is ausom), but it dousnt seem to work, im a little confuzed since my user credentials work, (main system account) and i created him an system account, and it dousnt work.

And hes does appear in the "Edit Samba users and passwords" :S

---

### Post by GodsDead on 2009-06-13
Bump?

---

### Post by Serangan on 2009-06-13
Have you run "convent unix users to Samaba Users"? I think this is what your after.

---

### Post by GodsDead on 2010-11-06
Yes, i have tryed that, and it didnt work.. well it created the users, but when you try to login from the other end, it refuses.

---

### Post by Vegan on 2010-11-06
I use a console prompt approach as I did not both to use webmin anymore.

The CLI is all I need and I am able to get what I want done easily with it.

```
sudo apt-get install openssl-server
```

The you can use an SSL telnet tool of your choice.

---

