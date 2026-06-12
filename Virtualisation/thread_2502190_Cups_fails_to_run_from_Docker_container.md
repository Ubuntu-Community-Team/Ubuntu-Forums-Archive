---
title: "Cups fails to run from Docker container"
date: 2024-11-04
forum: Virtualisation
---

### Post by nhasian on 2024-11-04
I hope this is the correct place to ask for assistance.

When I try to run a docker container with cups, cups fails to launch with the message:

```
lpadmin: Unable to connect to server: Bad file descriptor
```

I have two different containers with Cups that are failing. It used to work in Ubuntu 24.04 but hasn't worked since we upgraded to 24.10.
One of the containers is:

```
docker run -d -p 631:631 --name cups anujdatar/cups
```

I can run Cups within Docker on Ubuntu 24.04, and it also runs on NixOS Unstable.

On both Ubuntu 24.10 (where cups fails) and NixOS Unstable channel (Cups succeeds) they have the same Docker version:

Docker version 27.3.1
Docker Compose version v2.29.7

What would be preventing this from working in Ubuntu 24.10? I have tested with the Linux kernel 6.11, 6.10, and 6.6. Any help would be appreciated!

---

