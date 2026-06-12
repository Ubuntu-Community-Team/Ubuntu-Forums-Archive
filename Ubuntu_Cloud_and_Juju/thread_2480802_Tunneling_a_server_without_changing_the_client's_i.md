---
title: "Tunneling a server without changing the client's ip"
date: 2022-11-10
forum: Ubuntu Cloud and Juju
---

### Post by mazloom123 on 2022-11-10
Hello
I have two servers, one in Iran and one in the Netherlands. I want to transfer the traffic of the Iranian server to which the clients connect to the Dutch server so that I can use free Net.
So far, I have done the tunnel and I have no problem, but with this method, the Dutch server only receives the IP of the Iran server, and I need the main IP of the user on the Dutch server, which means that I need to know on the server what IP the user is connected to so that I can Control the traffic consumption
I inquired and they said that I should do a reverse proxy with nginx or haproxy so that I can see the main IP of the user on the Dutch server and do the procedure.
Can anyone guide me how to do this?

---

