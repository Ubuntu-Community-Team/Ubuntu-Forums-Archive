---
title: "Portforwarding router ubuntu server"
date: 2021-03-29
forum: Server Platforms
---

### Post by remag03 on 2021-03-29
So I am trying to set up Ubuntu server and I have wordpress installed and active on the home server and I have a domain, I also changed the ip of the NIC that the apache2 server is on. All I have to do is port trigger my router on 80 and 443 right? That way when the domain name connects to my router it forwards the connection to my apache2 server?

---

### Post by ameinild on 2021-03-29
That sounds about right. You can port forward directly to the webserver, or if you want more flexibility to a reverse proxy server. With a reverse proxy you can redirect subdomains to different webservers and services.

---

### Post by remag03 on 2021-03-29
Thank you for the timely response I will mark this as solved, I will look further into reverse proxy servers

---

### Post by ahbart on 2021-03-30
Do not forget to close the server with a firewall.

---

