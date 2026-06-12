---
title: "ProFTPD - How do I login?"
date: 2006-12-15
forum: Server Platforms
---

### Post by esf8 on 2006-12-15
Hi!

I followed this guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server)

It installed fine, I made all the changes...

Now how do I login?! :D Which user/pass? How do I create additional users for the ftp server?

---

### Post by djearwig on 2007-03-13
Yeah, I 've got the same problem.  Any helps for us would be greatly appreciated.

Thanks

---

### Post by nucklebone on 2007-03-13
it's not apparent from your post as to HOW you are trying to log in.

i would use an ftp client and use your hostname or ipaddress as the host, your account username as the user and your account user password as the password. port should be 21 unless you're using ssh then it's port 22.

nucklebone

---

### Post by nucklebone on 2007-03-13
it's not apparent from your post as to HOW you are trying to log in.

i would use an ftp client and use your hostname or ipaddress as the host, your account username as the user and your account user password as the password. port should be 21 unless you're using ssh then it's port 22.

you can download gFTP from using Synaptic Package Manager ( I think you need to turn on multiverse repositories first though)

or in the command line (after you turn on multiverse repositories) run:
```
sudo apt-get install gftp
```

then it will be in your Applications > Internet

or just use the command line to type:
```
gftp
```

nucklebone

---

### Post by rangerxlt8 on 2007-03-15
Thanks everyone for the help. My friend configured the router incorrectly, addressing the FTP to the wrong IP.....

---

