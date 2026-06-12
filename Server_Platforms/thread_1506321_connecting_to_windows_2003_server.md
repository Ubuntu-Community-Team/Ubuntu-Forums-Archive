---
title: "connecting to windows 2003 server"
date: 2010-06-10
forum: Server Platforms
---

### Post by Ceiber Boy on 2010-06-10
Hello all

I'm trying to connect ubuntu 10.04 to a windows 2003 server, i have had a look around for some documentation but am still a bit confused.

I've used ubuntu for a number of years now but never needed to connect to a server! any help offered would be appreciated

Thanks

---

### Post by Bachstelze on 2010-06-10
What do you mean by "connect"?

---

### Post by Ceiber Boy on 2010-06-10
'connect' 'log on' 'gain access', i know what my log on name and password is but how do i get to the point where i type these things in, if I've missed something really obvious I'm sorry but your help is appreciated

thanks

---

### Post by Bachstelze on 2010-06-10
What you want is probably a "remode destop" connection. You can use rdesktop for that, it is in the repos:

```
sudo apt-get install rdesktop
```

---

