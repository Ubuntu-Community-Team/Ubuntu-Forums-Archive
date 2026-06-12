---
title: "Can't access a server from LAN using its hostname"
date: 2009-05-15
forum: Server Platforms
---

### Post by Sarki on 2009-05-15
Hello, I'm a bit lost here.

As a long time Ubuntu desktop user,I'm currently trying to make the adoption of Ubuntu server inside my company.

I'm in charge of putting live Request Tracker that must be accessible via a sub domain of my company.

At the moment, the network admin managed to put <my prefix>.<the domain> as directly pointing at the server IP address.

In short, the server is accessible via Internet for anyone outside the office, but I can't figure out why we can't do the same inside.
Currently, the server responds on LAN when using its IP but not with <my prefix>.<the domain>.

Does anyone have an idea to help me go further ?

Ps:
For apache2
I added the following line in the **apache2.conf** : (Which I think has no use since it's redundant with the VirtualHost)

```
ServerName <my prefix>.<the domain>
```
I also added in the corresponding VirtualHost:
```
ServerName <my prefix>.<the domain>
```

I completed the entries in **/etc/hosts**:

```
127.0.0.1 localhost.localdomain localhost
127.0.1.1 <my prefix>.<the domain> <my prefix>
<Server IP> <my prefix>.<the domain> <my prefix>
```

---

### Post by timcredible on 2009-05-15
the dns admin has done something wrong.

do you nat to the internet?

---

### Post by Sarki on 2009-05-15
Well, after discussing with the dns admin, everything went well.

Thanks for telling me !

:D

---

