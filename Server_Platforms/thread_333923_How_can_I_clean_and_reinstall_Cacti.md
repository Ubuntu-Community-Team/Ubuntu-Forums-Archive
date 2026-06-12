---
title: "How can I clean and reinstall Cacti ?"
date: 2007-01-08
forum: Server Platforms
---

### Post by albuemil on 2007-01-08
Hy.

I have Ubuntu 6.10 server installed, and I've tried installing cacti, but made some mistake the first time around and sadly I don't even remember what I did wrong ](*,) .

I've found a tutorial on how to install cacti and it works great since I've managed to install cacti on another server (in a virtual machine) but I don't want to reinstall the main server if there's a way around it.

How can I completely remove it from the server and install it as if it was never installed before :confused: ? (like on a new server installation).

Note that I've tried this in order to completely remove cacti :
```
apt-get remove cacti
apt-get autoremove
apt-get clean
```
and I've also deleted all files that seemed to belong to cacti, I've used the ```
locate cacti
```

Is there anything else i should do ?

P.S.
I've set a password for mysqladmin's root user, should i remove that before trying to remove cacti ?

Thanks in advance.

---

### Post by Jussi Kukkonen on 2007-01-08
apt-get remove --purge cacti

---

### Post by albuemil on 2007-01-08
Thanks, this worked like a charm \\:D/.

I did have to reinstall cacti (with all the errors) before i could run your command, but afterwards it installed without a hitch (well, except for the fact that i had to create the cacti table in MySQL by hand, but that's another story :-))

So, here's what i did :
```
apt-get remove --purge cacti
apt-get autoremove --purge
mysqladmin -uroot create cacti
apt-get install cacti
```

After that it worked. now I just have to figure out how to configure cacti, but that's not going to be a problem (hopefully :D)

---

