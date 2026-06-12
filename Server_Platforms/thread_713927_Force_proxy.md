---
title: "Force proxy"
date: 2008-03-03
forum: Server Platforms
---

### Post by frodemt on 2008-03-03
I want to have one bastion server in my network. How do I force all users to use that proxy without them chaning any settings on their computer?

---

### Post by twistedtwig on 2008-03-03
as far as I understand it (which is limited) I think you need to redirect all the traffic through the proxy server.

So for squid (HTTP) you would redirect port 80 to go to port 3128.

I hope that might help, sorry I can not give a better answer

---

### Post by astrotech226 on 2008-03-03
Set the server up as a transparent proxy and you won't have to do anything to the clients.

---

### Post by frodemt on 2008-03-04
> **astrotech226 said:**
> Set the server up as a transparent proxy and you won't have to do anything to the clients.

How to do that?

---

### Post by frodemt on 2008-03-04
Never mind. I googled around ;)

---

