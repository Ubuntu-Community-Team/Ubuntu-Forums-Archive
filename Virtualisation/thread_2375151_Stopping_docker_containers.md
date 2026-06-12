---
title: "Stopping docker containers"
date: 2017-10-22
forum: Virtualisation
---

### Post by leed-f on 2017-10-22
I hope I am correct here.

Currently I do Website development using Vagrant Machines to simulate my servers (one machine per project). I've been playing with the idea of replacing this with a docker environment to increase performance and be able to switch between projects faster. 

Docker normally uses ports, this is not so convenient for me, as I'd prefer to setup ip addresses that are linked to hostnames in /etc/hosts/. 

I've figured out, how to create a bridge in Docker and how to assign IP addresses to containers. The containers are visible in the network, but I cannot shut them down. 


```

sudo docker stop leed-mysql
Error response from daemon: Cannot stop container leed-mysql: Cannot kill container 9c06cbe91682f32fae504f7aa4fa6a693fa77ef78859587502bc05fce2f7fb69: rpc error: code = 7 desc = permission denied

```

this is rather annoying, I cannot stop the containers without rebooting my PC. What am I doing wrong?

---

### Post by kevinmatte on 2018-02-18
Wish I knew the answer, but instead of rebooting your PC: sudo service docker restart
I don't think you're doing anything wrong. From other threads, this looks like a Docker bug introduced after Docker 17.03. If you can, install 17.03.

---

