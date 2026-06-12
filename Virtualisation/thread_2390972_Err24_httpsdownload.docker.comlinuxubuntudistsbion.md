---
title: "Err:24 https://download.docker.com/linux/ubuntu/dists/bionic/stable bionic Release"
date: 2018-05-04
forum: Virtualisation
---

### Post by overgara on 2018-05-04
Hi all, where can I get support for installation the docker CE in Ubuntu 18.04(Bionic) ? I have this error when add repository: 

sudo add-apt-repository \
>    "deb [arch=amd64] [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) \
>    $(lsb_release -cs) \
>    stable"

Err:24 [https://download.docker.com/linux/ubuntu/dists/bionic/stable](https://download.docker.com/linux/ubuntu/dists/bionic/stable) bionic Release
  404  Not Found [IP: 216.137.41.39 443]
Err:25 [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Err:26 [https://download.docker.com/linux/ubuntu/dists/bionic/stable/binary-amd64](https://download.docker.com/linux/ubuntu/dists/bionic/stable/binary-amd64) bionic Release
  404  Not Found [IP: 216.137.41.39 443]
Err:27 [https://download.docker.com/linux/ubuntu/dists/bionic/stable/binary-amd64/Release](https://download.docker.com/linux/ubuntu/dists/bionic/stable/binary-amd64/Release) bionic Release
  404  Not Found [IP: 216.137.41.39 443]
Err:28 [https://download.docker.com/linux/debian](https://download.docker.com/linux/debian) bionic Release
  404  Not Found [IP: 216.137.41.39 443]
Err:29 [https://download.docker.com/linux/ubuntu//dists/bionic/stable/binary-amd64](https://download.docker.com/linux/ubuntu//dists/bionic/stable/binary-amd64) bionic Release
  404  Not Found [IP: 216.137.41.39 443]

---

### Post by tinylagarto on 2018-05-04
I am not sure about the repository you are trying to add but docker is in the default Ubuntu repositories. Just install it from there either using the software center or via command line:

```
 sudo apt install docker.io
```

---

### Post by deadflowr on 2018-05-04
I see the archives here:
[https://download.docker.com/linux/ubuntu/dists/bionic/]("https://download.docker.com/linux/ubuntu/dists/bionic/")
See if they've been updated since you first tried.

Also you need to remove the ubuntu-make ppa as it has no version for bionic... yet.

---

### Post by overgara on 2018-05-04
ok thanks, I already solve the problem. I had to disable ppa. and run edge version : 18.05.0-ce release is for the edge

[https://github.com/docker/for-linux/issues/290](https://github.com/docker/for-linux/issues/290)

Thanks anyway 4 your support..

---

