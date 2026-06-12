---
title: "Limit Apache cpu resources"
date: 2016-10-28
forum: Server Platforms
---

### Post by fernandoch on 2016-10-28
Hello,

I have a server with many apache virtual hosts.

The server is not loaded at all during the day.

I have jetpack installed in my wordpress sites to update everything from there.

When I go to update my wordpress plugins with jetpack, to this URL 

wordpress.com/plugins

I get a **** ton of apache connections and my server freezes.

Is there a way to limit the connections to my server?

Thanks

---

### Post by Vegan on 2016-10-28
might be better to add more memory to cope with the load

---

### Post by fernandoch on 2016-10-28
I am only having CPU problems when updating the wordpress sites, why to add memory?

---

### Post by fernandoch on 2016-10-29
OK, I think I solved it by reducing the MaxClients (I had it at 150) if that helps someone else :)

---

