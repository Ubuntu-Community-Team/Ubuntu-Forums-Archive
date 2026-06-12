---
title: "Docker snap failing to use my dns?"
date: 2020-12-20
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2020-12-20
Topic says it all. When I use the apt based Docker I can edit the daemon.json to include my Dnsmasq and all is well in the world. However when using the Snapd version I'm not sure how to do it. I cannot add my http_proxy via fqdn.

```
docker build -t foo --build-arg http_proxy=http://proxy.mylan.home:3129/ .
```

fails while

```
docker build -t foo --build-arg http_proxy=http://192.168.1.2:3129/ .
```

works flawlessly. In migrating my services I've also found that they don't resolve my dns. In the case of a headless Kodi I recently built to manage the libraries I cannot use ```
sql.mylan.home
``` rather I need to use ```
192.168.1.2
```

I'm not sure why this is. I've had little success searching for how to accomplish this. Typically typing anything involving Docker + snap results in how to install the snapd version. I've opened up my dnsmasq to accept from the Docker ip range but I can't seem to make Docker target it specifically.

---

### Post by kevdog on 2020-12-21
Why are you using Docker snap?  Why don't you just add the official docker repositories to your /etc/apt sources and be done with it.  You get the latest and greatest release directly from docker -- not canonical which acts as a third party.

---

### Post by Tadaen_Sylvermane on 2020-12-21
I've been trying to clean up the host system as much as possible. OCD thing. Moving everything not in ubuntu repositories I can to docker or snaps and eliminating ppas and external repos from the host. I've managed to move all but one of my external repos to docker. Thankfully it's just shell code and some python from the ltsp.org ppa. But I'm even aiming to simplify that and change my network boot machines for RPi's or something as 99% of their use is media center via Kodi. And if I can get my ltsp into a docker well, I may not even bother replacing the machines for the time being. 

I did solve this just an hour ago though.

daemon.json was at this path on my system.

```
/var/snap/docker/current/config/daemon.json
```

Once I restarted the docker daemon

```
sudo systemctl restart snap.docker.dockerd
```

it worked perfectly.

---

