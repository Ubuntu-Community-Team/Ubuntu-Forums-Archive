---
title: "Docker installed via Snap: Nextcloud container has no access to internet"
date: 2023-04-07
forum: Server Platforms
---

### Post by japtar on 2023-04-07
Hello, all.  Apologize if this forum isn't the best place to ask for these sort of highly specific questions, but I've been trying to host NextCloud via Docker from my Ubuntu server.  The good news is that I've been mostly successful...except for the fact that the container itself is unable to connect to the internet.  As such, Nextcloud doesn't have a method to install apps.

```

$ sudo docker ps
CONTAINER ID   IMAGE
7b693dbd8936   nextcloud
# ... Snip other containers ...

$ sudo docker exec -it 7b693dbd8936 /bin/bash

root@7b693dbd8936:/var/www/html# curl google.com
curl: (6) Could not resolve host: google.com

```

My [FONT=courier new]docker-compose.yml[/FONT] file for Nextcloud looks like:

```
version: '3.8'

volumes:
  nextcloud:
  db:

services:
  db:
    image: mariadb:10.6
    restart: always
    ports:
      - 3306:3306
    command: --transaction-isolation=READ-COMMITTED --log-bin=binlog --binlog-format=ROW
    volumes:
      - db:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=pass1
      - MYSQL_PASSWORD=pass2
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud

  app:
    image: nextcloud
    restart: always
    ports:
      - 8383:80
    depends_on:
      - db
    volumes:
      - /media/www/nextcloud/data:/var/www/html/data
      - /media/www/nextcloud/config/example.config.php:/var/www/html/config/example.config.php:ro
      - nextcloud:/var/www/html
    environment:
      - MYSQL_PASSWORD=pass2
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
      - MYSQL_HOST=10.0.0.171:3306

```

From a search with Stack Overflow, it sounded like the problem might be related with Snap (which is how I installed Docker.)  I was wondering if there's a way to get Snap to allow Docker containers to connect online.

For my part, I've tried:

[LIST]
[*]Added in the [FONT=courier new]docker-compose.yml[/FONT] file the following:```
networks:
  default:
    name: nextcloud_default
    driver: bridge
    ipam:
      config:
        - subnet: 172.25.0.0/16
          ip_range: 172.25.0.1/24
          gateway: 172.25.0.1
``` 
[*]Change the default linking of [FONT=courier new]resolv.conf[/FONT] to:```
$ ls -l /etc/resolv.conf
lrwxrwxrwx 1 root root 32 Apr  7 04:17 /etc/resolv.conf -> /run/systemd/resolve/resolv.conf
``` 
[*]Edit /var/snap/docker/current/config/daemon.json to:```
{
    "log-level":        "error",
    "storage-driver":   "overlay2",
    "dns": ["10.0.0.171", "1.1.1.1", "8.8.8.8"]
}
``` 
[*]Forcefully mount Ubuntu's [FONT=courier new]resolv.conf[/FONT] onto the container:```
volumes:
  - /media/www/nextcloud/data:/var/www/html/data
  - /media/www/nextcloud/config/omiyagames.config.php:/var/www/html/config/omiyagames.config.php:ro
  - nextcloud:/var/www/html
  - /run/systemd/resolve/resolv.conf:/etc/resolv.conf:ro
``` 
[/LIST]
All methods do not allow the container to connect online.  When I access [FONT=courier new]/etc/resolv.conf[/FONT] in the container, I get:
```
root@7b693dbd8936:/var/www/html# cat /etc/resolv.conf 
search invalid hsd1.il.comcast.net
nameserver 127.0.0.11
options ndots:0
```
Which obviously is not what I want (exception: the last method overwrite [FONT=courier new]resolv.conf[/FONT]'s content, but has no discernible effect to the container's connection.)

---

### Post by ameinild on 2023-04-07
This is pretty strange. A first question would be: Do you have this problem with other containers as well? 

I would try and test with another container, and find out if the problem persists across containers (then it's a Docker problem), or if it's a problem with the specific container.

I'm running Nextcloud with Docker (apt version) with no issues whatsoever.

---

### Post by japtar on 2023-04-07
So of all the the containers I can run either curl or ping to, only Jellyfin (whose network is configured to host mode) has external internet connection.  I've tried this on Vaultwarden, Gitea, Gollum, and of course, Nextcloud and Jellyfin.  So it's a problem with containers under default bridge network.  I seem to recall putting containers to host mode can lead to port conflicts, which I do want to avoid.

ETA: I forgot to mention the host Ubuntu is running Caddy locally to handle URLs.  So for example, Nextcloud url right now is configured to [FONT=courier new]https://example.com/cloud[/FONT] by Caddy.

---

### Post by japtar on 2023-04-08
I figured it out.  I didn't enable docker containers to [forward their bridge networks]("https://docs.docker.com/network/bridge/#enable-forwarding-from-docker-containers-to-the-outside-world"):
```

#!/bin/bash

sudo sysctl net.ipv4.conf.all.forwarding=1
sudo iptables -P FORWARD ACCEPT

```
I've created a script with above content and updated Systemctl to call that script.

---

