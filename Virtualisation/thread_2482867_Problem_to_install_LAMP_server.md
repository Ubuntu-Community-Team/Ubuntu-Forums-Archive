---
title: "Problem to install LAMP server"
date: 2023-01-12
forum: Virtualisation
---

### Post by satimis on 2023-01-12
I'm following below document to install LAMP on Ubuntu22.04 VM

How To Install Linux, Apache, MySQL, PHP (LAMP) Stack on Ubuntu 22.04
[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-22-04)

Step 1 &#8212; Installing Apache and Updating the Firewall
$ sudo apt update
$ sudo apt install apache2

went throught without complaint

$ sudo ufw app list```

Output
Available applications:
  Apache
  Apache Full
  Apache Secure
  
```
OpenSSH missing
  
OpenSSH is not on repo but ssh is on repo

$ apt policy OpenSSH/openssh```

N: Unable to locate package OpenSSH/openssh

```

$ apt policy ssh```

ssh:
  Installed: (none)
  Candidate: 1:8.9p1-3ubuntu0.1
  Version table:
     1:8.9p1-3ubuntu0.1 500 (phased 60%)
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
     1:8.9p1-3 500

```

$ sudo ufw allow in "Apache"```

Skipping adding existing rule
Skipping adding existing rule (v6)

```

I can't proceed further.  Please help.  Thanks

Regards

---

### Post by howefield on 2023-01-12
Thread moved to the "*Virtualisation*" forum, if no reponse can move it to the "*Server Platform*" forum, either way, both are better for this thread than "*General Help.*"

---

### Post by deadflowr on 2023-01-12
openssh in Ubuntu is broken into two distinct packages,
openssh-server and openssh-client.
ssh is a metapackage which will install both.

Apache should only need ports 80 and 443 open.
(80 is the port for http and 443 is port for https)

ssh default port is 22 but you can change that in the sshd_config.

---

### Post by satimis on 2023-01-12
> **deadflowr said:**
> openssh in Ubuntu is broken into two distinct packages,
openssh-server and openssh-client.
ssh is a metapackage which will install both.

Apache should only need ports 80 and 443 open.
(80 is the port for http and 443 is port for https)

ssh default port is 22 but you can change that in the sshd_config.
Hi,

Thanks for your advice.

On Terminal run;
$ sudo apt install openssh-server
$ sudo apt install openssh-client

$ sudo systemctl status ssh```

&#9679; ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; ve>
     Active: active (running) since Fri 2023-01-13 07:26:44 HKT; >
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 4457 (sshd)
      Tasks: 1 (limit: 11861)
     Memory: 1.7M
        CPU: 17ms
     CGroup: /system.slice/ssh.service
             &#9492;&#9472;4457 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-1>

Jan 13 07:26:44 lamp0 systemd[1]: Starting OpenBSD Secure Shell s>
Jan 13 07:26:44 lamp0 sshd[4457]: Server listening on 0.0.0.0 por>
Jan 13 07:26:44 lamp0 sshd[4457]: Server listening on :: port 22.
Jan 13 07:26:44 lamp0 systemd[1]: Started OpenBSD Secure Shell se>
lines 1-16

```

$ sudo ufw status```

Status: active

To                         Action      From
--                         ------      ----
Apache                     ALLOW       Anywhere                  
Apache (v6)                ALLOW       Anywhere (v6)             

```

Missing;```

OpenSSH           ALLOW       Anywhere     
OpenSSH (v6)      ALLOW       Anywhere (v6) 

```

Regards

---

### Post by MAFoElffen on 2023-01-13
Is your LAMP Server Apache pages outward facing? If so then there is a BOT attack that affects DOS & Brute Force attacks on ssh ports. If so then I would suggest "Limited" through UFW, which would "Allow" but also would deny connections from an IP address that has attempted to initiate 6 or more connections in the last 30 seconds. A good practice to get into...
```

## ufw limit ssh various usage ##
ufw limit ssh
 
ufw limit ssh/tcp
 
ufw limit ssh comment 'Rate limit for openssh server'
 
### if sshd is running on tcp port 2022 add ####
ufw limit 2022/tcp comment 'SSH port rate limit'

```

---

### Post by satimis on 2023-01-14
> **MAFoElffen said:**
> Is your LAMP Server Apache pages outward facing? If so then there is a BOT attack that affects DOS & Brute Force attacks on ssh ports. If so then I would suggest "Limited" through UFW, which would "Allow" but also would deny connections from an IP address that has attempted to initiate 6 or more connections in the last 30 seconds. A good practice to get into...
```

## ufw limit ssh various usage ##
ufw limit ssh
 
ufw limit ssh/tcp
 
ufw limit ssh comment 'Rate limit for openssh server'
 
### if sshd is running on tcp port 2022 add ####
ufw limit 2022/tcp comment 'SSH port rate limit'

```
This is my PC, not open to public

Regards

---

### Post by MAFoElffen on 2023-01-14
Then 
```

ufw allow ssh/tcp comment 'SSH port open'

```

---

### Post by satimis on 2023-01-14
> **MAFoElffen said:**
> Then 
```

ufw allow ssh/tcp comment 'SSH port open'

```
$ ufw allow ssh/tcp comment 'SSH port open'```

ERROR: You need to be root to run this script

```

$ sudo ufw allow ssh/tcp comment 'SSH port open'```

Rule added
Rule added (v6)

```

Regards

---

