---
title: "Newbie Dapper Server User - How to setup a domain"
date: 2007-01-24
forum: Server Platforms
---

### Post by daniminas on 2007-01-24
Hi all,
I'm newbie at 'servers' setups, etc.. I have my own server running fine :), (firewall, mail, web, etc..) but from now i'm using a IP address to access to. I'm also have a domain registred wich i want to use(for this server). 

Now, my question is how can i setup my domain in my Ubuntu Dapper Server?


Thanks verry much in advance, and sorry my english (i'm speak spanish)

Daniel

---

### Post by jtc on 2007-01-24
> **daniminas said:**
> Hi all,
Now, my question is how can i setup my domain in my Ubuntu Dapper Server?

Assuming you've got the default install and that you're only using one vhost you really don't have to do any setuping on the server. Any connection, no matter what domainname they used, to your server will get the default vhost.

What you will have to do is to tell your domainregistrant to point domainname towards your ip-number.

Still, it never hurts to tell Apache which domainname is used against it. Add the following line to your /etc/apache2/sites-available/default

```
ServerName your.domain.name
```

It should be somewhere in between <VirtualHost *> and </VirtualHost>. Preferable at the top, just for the order of things.

---

### Post by daniminas on 2007-01-28
Yes, i know about apache... my question is about how to setup a domain.. i need some dns server?.. 


Thanks!

---

### Post by Koybe on 2007-01-28
Something to do with this : [http://www.ubuntuforums.org/showthread.php?t=347465](http://www.ubuntuforums.org/showthread.php?t=347465)

:)

---

