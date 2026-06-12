---
title: "domains and ports"
date: 2007-04-20
forum: Server Platforms
---

### Post by noone123 on 2007-04-20
Hi, is it possible to make a port redirection? like if you connect from mydomain.com get redirected to port 70 but if im connection from myaddress.com i get redirected to port 71? These ports are only examples!

---

### Post by jtc on 2007-04-20
Are we talking http-connections? I'm not sure we do, but somehow I get that feeling :)

If that's the case Apache's mod_rewrite should be able to do the trick. It's also possible that mod_proxy might be applicable, as a reverse proxy.

---

### Post by noone123 on 2007-04-20
sry forgot to tell, its not apache connections(httpd) its a gameserver connection.

---

### Post by jtc on 2007-04-20
Well, then I guess it depends on what protocol the gameserver use. Most protocols don't handle domains at all. They simply look at the ip-address.

---

### Post by noone123 on 2007-04-20
but there must be some filter that could filter domains to go there and address goes there. Or there isnt?

---

