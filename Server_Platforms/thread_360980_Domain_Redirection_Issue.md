---
title: "Domain Redirection Issue"
date: 2007-02-13
forum: Server Platforms
---

### Post by shawnlogic on 2007-02-13
Hello Everyone,

The current problem I'm having with my new Ubuntu LAMP server is that I've redirected my domain name, assume [www.mydomain.com](www.mydomain.com), to my server.  It works fine.

But when I add a directory to the default apache2 folder, and set the proper viewing and executing permissions, i type in [www.mydomain.com/folder/](www.mydomain.com/folder/) and the server redirects to [www.mydomain.com](www.mydomain.com)

But if I put my IP address in the browser, ex, [http://ip_address/folder/](http://ip_address/folder/)
it works and goes to the proper page.

Does know what  I've done wrong with my setup?

---

### Post by shawnlogic on 2007-02-15
bump.

---

### Post by jtc on 2007-02-15
By redirecting, do you mean using some kind of service like no-ip.com or similar?

If that is the case I'd guess that you have set it up so your server is simply loaded into a frameset running on their server.

Before making suggestions on how to solve the situation perhaps you could confirm if this is the case?

---

