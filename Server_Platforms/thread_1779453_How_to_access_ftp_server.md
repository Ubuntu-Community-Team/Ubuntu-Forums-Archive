---
title: "How to access ftp server?"
date: 2011-06-10
forum: Server Platforms
---

### Post by friendlybacon on 2011-06-10
Greetz, ubuntu users!

I am currently attempting to setup an ftp server using the vsftpd daemon.

I have read countless articles and tutorials on setting up and editing the config files to restrict access, handle permissions, etc.... 

What none of them have mentioned, however, is how to actually access the ftp server. can someone please point me in the right direction here? i really am kinda clueless with networking in linux......

try to keep it simple, please, in case you can't tell, i are noobish.

---

### Post by papibe on 2011-06-10
If your are familiar with the terminal, you can type:
```
$ ftp myserver
```

Also, I believe all up to date web browsers (like Firefox) can use the ftp protocol by using an address like:
```
ftp://myserver
```
Hope it helps.

---

### Post by friendlybacon on 2011-06-10
hmmmm, terminal spits out the following message:

ftp: myserver: No address associated with hostnameftp> 

and firefox 404's out on me.

i'm guessing i did something wrong in the setup / config files. any suggestions?

Thanks for helping a noob.

---

### Post by papibe on 2011-06-10
The name myserver was an example. Use the name of your server/machine.

Regards.

---

### Post by aphatak on 2011-06-10
And if name is not resolved, try using the ip address.

---

### Post by friendlybacon on 2011-06-10
Many thanks to both of you, i was able to connect.

now i just have to figure out how to change the servers content directory, but i think i already know how to.

Thanks again!

---

