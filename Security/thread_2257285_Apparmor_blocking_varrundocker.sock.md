---
title: "Apparmor blocking /var/run/docker.sock"
date: 2014-12-18
forum: Security
---

### Post by srhadden on 2014-12-18
I'm working on getting docker running inside an LXC container. It appears to work fine if I disable apparmor profiles, so now I'm trying to determine if it is possible to keep the LXC secure and run docker inside, or if trying to get docker to run inside an LXC will break security for the LXC container. After all, the purpose here is to run processes in the nested docker container to isolate processes from the LXC container itself.

One specific block is the access to this socket. /var/run/docker.socket.

What apparmor rule would allow me to enable access to this device from an LXC container?

Thanks so much.

---

