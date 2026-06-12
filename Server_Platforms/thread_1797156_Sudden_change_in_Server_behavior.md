---
title: "Sudden change in Server behavior"
date: 2011-07-04
forum: Server Platforms
---

### Post by pcarlos853 on 2011-07-04
Hello,

I have been running two Ubuntu 10.10 servers for some time now. My main server is 10.111.1.65 and backup server is 10.111.66. The main server is to host my website and ssh remote access (Key auth). The backup server pulls via ssh key auth what is in my /var/www (among other folders) to the backup home dir (encrypted). For some reason today I checked the uptime and it was 7 hours on both servers. All my other computers on the same power supply have a uptime of over a month. For some reason I now cant access backup via ssh from main's key (I could before) and I can not get to the home dir, see below:

```
carlos@UbuntuSvrDell2400:~$ sh "Access-Your-Private-Data.desktop"
Access-Your-Private-Data.desktop: 1: [Desktop: not found
Access-Your-Private-Data.desktop: 2: Your: not found
Access-Your-Private-Data.desktop: 3: Your: not found
Access-Your-Private-Data.desktop: 7: Security: not found
Access-Your-Private-Data.desktop: 8: X-Ubuntu-Gettext-Domain=ecryptfs-utils: not found

```Also the alias have been wiped out on the backup server. I don't know what happened. Does any one have any ideas?

Thanks
Carlos

---

### Post by Dangertux on 2011-07-04
> **pcarlos853 said:**
> Hello,

I have been running two Ubuntu 10.10 servers for some time now. My main server is 10.111.1.65 and backup server is 10.111.66. The main server is to host my website and ssh remote access (Key auth). The backup server pulls via ssh key auth what is in my /var/www (among other folders) to the backup home dir (encrypted). For some reason today I checked the uptime and it was 7 hours on both servers. All my other computers on the same power supply have a uptime of over a month. For some reason I now cant access backup via ssh from main's key (I could before) and I can not get to the home dir, see below:

```
carlos@UbuntuSvrDell2400:~$ sh "Access-Your-Private-Data.desktop"
Access-Your-Private-Data.desktop: 1: [Desktop: not found
Access-Your-Private-Data.desktop: 2: Your: not found
Access-Your-Private-Data.desktop: 3: Your: not found
Access-Your-Private-Data.desktop: 7: Security: not found
Access-Your-Private-Data.desktop: 8: X-Ubuntu-Gettext-Domain=ecryptfs-utils: not found

```Also the alias have been wiped out on the backup server. I don't know what happened. Does any one have any ideas?

Thanks
Carlos

Have you tried this
```

ecryptfs-mount-private

```That might work better , if not let me know :-/

---

### Post by pcarlos853 on 2011-07-04
Thanks for the quick reply!

I have not done anything and everything seems to be back to normal. I don't know what caused this change in server behavior. 

Thanks,

---

### Post by Dangertux on 2011-07-04
No problem glad it worked out for you.

---

