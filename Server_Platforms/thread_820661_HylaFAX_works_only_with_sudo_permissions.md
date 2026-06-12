---
title: "HylaFAX works only with sudo permissions"
date: 2008-06-06
forum: Server Platforms
---

### Post by raid996 on 2008-06-06
Hello,

I've setup a Fax server with Hylafax. My problem now is that I can only send faxes with sudo permissions (that is sudo sendmail...). This is a problem since clients like Avantfax or Gfax are going to need sudo password, obviously that's not good for stabilty and security reasons. I want the clients to use only the defined password in my /etc/hylafax/hosts.hfaxd file.

I sent a fax using a client efax-gtk but again in order to make it work I had to start the client with sudo permissions: gksu efax-gtk.

How can I fix this? Did I do something wrong?:mad:

---

### Post by quelx on 2008-06-06
Disclaimer:I don't have a modem.

With that, what are the permissions on the modem?
```
ls -l /dev/ttyS*
```

Are normal users able to at least launch **efax-gtk** without *sudo*?

If not what are the permissions on **efax-gtk**? (I'm guessing on the path in the second command, check the first)
```
whereis efax-gtk
ls -l /usr/bin/efax-gtk
```

Is there a **fax** group?
```
cat /etc/group|grep fax
```

---

