---
title: "using Local provider (re LXC) can Juju-gui be deployed in the Host"
date: 2014-04-28
forum: Ubuntu Cloud and Juju
---

### Post by bmullan2 on 2014-04-28
I have created an ubuntu 14.04 server "instance" on an OpenStack at work.

This server has 2 IP addresses one of which is public facing and reachable from the Internet.

On this server I've installed juju for lxc, configured juju for Local provider (re lxc).

What I'd like to do is have juju-gui deployed into the Host and _not_ in a container...  
but later when using juju-gui via a browser I'd like the rest of the "services" I deploy to be installed into LXC containers.

My reason is I'd like the juju-gui web interface to be reachable over the Internet via the Instance's Public IP address but I'd like all the "services" deployed afterwards by Juju to run in LXC containers.

However, deploying juju-gui puts juju-gui in an LXC container also where it gets a 10.x.x.x IP address and is not reachable by the internet.

Does anyone know how this could be configured.

---

### Post by bmullan2 on 2014-05-04
setting up NGINX reverse proxy on the Host almost gets this working.   The juju-gui login screen starts to initialize but just keeps spinning on "Connecting to juju environment" message and never actually presents the login & password entry fields.

---

