---
title: "Ubuntu 32-bit: Docker not working anymore"
date: 2014-10-27
forum: Virtualisation
---

### Post by sanderj on 2014-10-27
Ubuntu 14.04.1 LTS 32-bit.

Until this weekend, docker was working OK. It started automatically, and I could run 32-bit Docker images. 

However, today I got this message:

```
$ sudo docker -d
[2014-10-27T18:28:52.844742427+01:00] [info] docker daemon:  ; execdriver: native; graphdriver: 
[2014-10-27T18:28:52.845440998+01:00] [1a7bd961] +job serveapi(unix:///var/run/docker.sock)
WARNING: The Docker runtime currently only officially supports amd64 (not 386). THIS BUILD IS NOT OFFICIAL AND WILL NOT BE SUPPORTED BY DOCKER UPSTREAM.[2014-10-27T18:28:52.849023375+01:00] [info] Listening for HTTP on unix (/var/run/docker.sock)
[2014-10-27T18:28:52.884543980+01:00] [1a7bd961] +job init_networkdriver()
[2014-10-27T18:28:52.941506909+01:00] [1a7bd961] -job init_networkdriver() = OK (0)
[2014-10-27T18:28:52.942033812+01:00] [fatal] log.go:64 Could not locate dockerinit: This usually means docker was built incorrectly. See http://docs.docker.com/contributing/devenvironment for official build instructions.
```

I googled, and so far I only found messages from 2012.

Tips appreciated.

In the meantime I will try to google more.

EDIT:

Ah, more fun (trying to remove docker.io):

```
Ign https://get.docker.com docker/main Translation-en_US                       
Ign https://get.docker.com docker/main Translation-en                          
Err https://get.docker.com docker/main i386 Packages                           
  HttpError403
Fetched 1295 kB in 15s (82,9 kB/s)                                             
W: Failed to fetch https://get.docker.com/ubuntu/dists/docker/main/binary-i386/Packages  HttpError403

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by sanderj on 2014-10-27
OK, solved:

Remove all files pointing to docker (ppa?) in /etc/apt/, ran update and upgrade, ran "sudo apt-get remove docker.io", and ran "sudo apt-get install docker.io". And after that everything was OK again:

```


$ sudo docker version
Client version: 1.0.1

sander@haring:~$ sudo docker run -i -t shawn/ubuntu-precise-i386 /bin/bash

root@ebc983c644d0:/# uname -a
Linux ebc983c644d0 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014 i686 i686 i386 GNU/Linux
root@ebc983c644d0:/#
```

Version 1.0.1 is not 1.3, but probably good enough for now.

---

