---
title: "Disable SSL on XAMPP Apache"
date: 2008-03-11
forum: Server Platforms
---

### Post by Minteh on 2008-03-11
Like many establishments, my school blocks port 22, therefore I have my server's SSH settings setup to listen on port 443, however since Apache insists on trying to start with SSL, I simply get an error message informing me a daemon listening on that port is already started.  I tried going through most of the config files removing any inclusion of the SSL mods, but that didn't seem to do the trick, I also removed the port 443 check from the lampp "startapache" directive, but no luck there either.

Is there a way, and if so how, to completely stop SSL and port 443 listeners/checks being used?

Any help appreciated :)

---

### Post by Minteh on 2008-03-11
Well, seems I went the way of a lot of support requests in this forum, and it's suddenly started working :/  Not entirely sure what I did but not complaining :)

---

