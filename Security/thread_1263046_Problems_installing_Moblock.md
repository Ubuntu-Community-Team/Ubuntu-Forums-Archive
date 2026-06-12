---
title: "Problems installing Moblock"
date: 2009-09-10
forum: Security
---

### Post by Chaplipman on 2009-09-10
Hello there,

I'm running Ubuntu Hardy Heron on a AMD64 processor. I recently decided to try out Moblock and install it, but I constantly get errors when trying to start the GUI asking me to verify a specific path. Anyways, can anyone help me out? I'd be eternally grateful. Much thanks.

---

### Post by bodhi.zazen on 2009-09-10
It would help if you would kindly post the exact error message you are receiving.

---

### Post by Chaplipman on 2009-09-10
Sure, it's

"Required configuration file "/var/log/moblock.log" could not be found in the default path.
Please specify a different path."

Anyone know the problem?

---

### Post by bodhi.zazen on 2009-09-10
make the file with :

```
sudo touch /var/log/moblock.log
```

You may need to change ownership and permission on that file (not sure if moblock runs as root or not).

---

### Post by Chaplipman on 2009-09-10
Thanks alot friend. It works as it should now. I'll post back if there are any more problems down the road. Much thanks again.

---

### Post by DarkPhoenix7878 on 2010-05-15
> **bodhi.zazen said:**
> make the file with :

```
sudo touch /var/log/moblock.log
```

You may need to change ownership and permission on that file (not sure if moblock runs as root or not).

thx this fixed my problem in Lucid :)

---

