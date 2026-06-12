---
title: "Problems with kerberos ticket renewal (krenew)"
date: 2015-01-27
forum: Server Platforms
---

### Post by philipp.antczak on 2015-01-27
Hi All,

So I have the following problem:

Got a Ubuntu Server 12.04.5 running happily. It is connected the active directory and logging in is no problem. 
I also have a network attached storage server sitting somewhere providing HDD space to the users of the server. 
The way I have configured it, the link to the storage server is established when you first log in via .profile where somewhere towards the bottom I call for the given user ```
mount.cifs //chronos/username /home/username/chronos -o sec=krb5
```
In my fstab file I have the following:
```

//chronos/username /home/username/chronos cifs users,sec=krb5 0 0

```

Obviously this way, at some point my ticket may expire, which I found out can be renewed using the krenew command.
I therefore call for each open terminal ```
krenew -L -K 10 -b -p $KXC
``` where ```
KXC=${KRB5CCNAME:5}.pid}
``` so I can kill the krenew command called by the terminal when the terminal is closed. I also remove the created files associated with that temporary file. 

Now to the problem, this all works great, as long as I am not connected for too long (i.e. >1week). After about a week, the krenew command that the terminal called initially is not running anymore. I can't figure out what happens to the command and hence I find it difficult to fix this issue. 

If anybody has an idea on how to make this a little more permanent - so that being connected over longer periods of time won't cause it to crash that would be great!

Thanks
Phil

---

