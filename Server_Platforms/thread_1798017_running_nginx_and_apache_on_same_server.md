---
title: "running nginx and apache on same server"
date: 2011-07-05
forum: Server Platforms
---

### Post by scooterskin on 2011-07-05
hi, i want to run a Zsync server off a vhost sub domain at present i have my vhoshs on apache however i can can only seem to limit the connections across the whole of apache and i need to limit the connection of just this sub domain, so they will move onto other mirrors. i know you can do this with nginx.

So my question is can i run nginx just on one domain without it effecting the other domains that i have? also to note i only have one ip address.

---

### Post by rudelgurke on 2011-07-06
Except using different ports, doubt 2 services can share the same listener port.
Though a solution is maybe setting up Nginx on Port 80 as reverse proxy for all your Apache Vhosts, serving the Vhost you want to limit directly.

---

