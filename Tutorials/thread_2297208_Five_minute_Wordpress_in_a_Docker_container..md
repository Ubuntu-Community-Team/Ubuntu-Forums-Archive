---
title: "Five minute Wordpress in a Docker container."
date: 2015-10-01
forum: Tutorials
---

### Post by Habitual on 2015-10-01
*[COLOR=Red]Environment[/COLOR]*
Ubuntu mini.iso in a Virtualbox v4.3.18 host w\20G hd.
**No tasksel packages other than ssh** during install.

*[COLOR=Red]Prerequisites[/COLOR]*
Docker requires a 64-bit installation regardless of your Ubuntu version. 
Additionally, your kernel must be 3.10 at minimum. 
The latest 3.10 minor version or a newer maintained version are also acceptable.

*[COLOR=Red]Installation[/COLOR]*
```
curl -sSL https://get.docker.com/ | sh && docker version
``` should give you this output:
```
    Client:
     Version:      1.8.2
     API version:  1.20
     Go version:   go1.4.2
     Git commit:   0a8c2e3
     Built:        Thu Sep 10 19:19:00 UTC 2015
     OS/Arch:      linux/amd64
    
    Server:
     Version:      1.8.2
     API version:  1.20
     Go version:   go1.4.2
     Git commit:   0a8c2e3
     Built:        Thu Sep 10 19:19:00 UTC 2015
     OS/Arch:      linux/amd64
```


*[COLOR=Red]Enable UFW forwarding[/COLOR]*
```
vi /etc/default/ufw
``` and set
DEFAULT_FORWARD_POLICY="ACCEPT"

*[COLOR=Red]Enable UFW Firewall[/COLOR]*```

sudo ufw enable && ufw reload
```

*[COLOR=Red]Allow incoming connections[/COLOR]*
```
ufw allow 2375/tcp
ufw allow from 192.168.1.3 to any port 22

```# 192.168.1.3 is my desktop host. If you don't need to ssh in, then omit this. Seems unlikely however. ;)

*[COLOR=Red]Configure a DNS server for use by Docker[/COLOR]*
```
sudo vi /etc/default/docker
```and use 
DOCKER_OPTS="--dns 8.8.8.8 --dns 8.8.4.4"

```
restart docker
```

*[COLOR=Red]Pull and run a mysql container[/COLOR]*
```
docker run --restart=always --name mysql -P -e MYSQL_ROOT_PASSWORD=<secret_mysql_rootpassword> -d mysql:5.7
```

*[COLOR=Red]Pull and run the latest wordpress container[/COLOR]*
```
docker run --restart=always --name wordpress --link mysql -p 8080:80 -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=<secret_mysql_rootpassword> -d wordpress
```

*[COLOR=Red]Check Wordpress application[/COLOR]*
http://<ip_of_virtualbox_host>:8080

The "--restart=always" options allow for persistence across reboots of the VM.

All done as root user during this install.

Enjoy the Goodness.

---

