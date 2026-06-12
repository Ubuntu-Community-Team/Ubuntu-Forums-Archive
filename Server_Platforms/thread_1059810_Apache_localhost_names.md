---
title: "Apache localhost names"
date: 2009-02-04
forum: Server Platforms
---

### Post by Zillion on 2009-02-04
Hi 

I have Apache running on a small Ubuntu server in my home network. In /etc/hosts it says :

```

127.0.0.1     localhost
127.0.1.1     myserverbla 
```

Now on a Windows PC in my network I can just type [http://myserverbla/](http://myserverbla/) but on my Macbook Pro it can't find the server. If I type [http://192.168.1.10/](http://192.168.1.10/) it can find it. How can I let the Mac also find it, or does one in general assign local host or domainnames?

---

### Post by dgoosens on 2009-02-04
you should also let your MAC know that [http://myserverbla](http://myserverbla) has the IP address (192.168.1.10).
you should edit your "hosts" file on your MAC aswell
192.168.1.10     myserverbla

(I don't know where you should do this on a MAC though)

---

### Post by Zillion on 2009-02-04
Thanks. I added in /etc/hosts on the Macbook 

```

192.168.1.10 myserverbla

```

and now it works. :)

---

