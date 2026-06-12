---
title: "Snappy Ubuntu running Docker: Permission denied on 'run'"
date: 2015-03-12
forum: Ubuntu/Debian BASED
---

### Post by s.gerard on 2015-03-12
I have a Snappy Ubuntu Core running in a Virtual Box v.4.3.24. For this I used the official OVA listed [here]("http://www.ubuntu.com/cloud/tools/snappy#snappy-ova").
It's up to date , installing docker and pulling images from the dockerhub works fine as well.

What I want to do is to run a simple hello-world java file in a docker container. However, already starting the java container via ```
docker run java
``` fails. 
To test whether the problem was the java container itself, I pulled another image, this time crccheck/hello-world which is supposed to be a small webserver. Running it also failed with the same error message, which is the following:

> 
[3852.627527] aufs au_xino_create:745:docker[635]: open /dev/shm/aufs.xino(-13)
[3852.628840] aufs au_xino_create:745:docker[635]: open /dev/shm/aufs.xino(-13)
2015/03/12 14:01:56 Error response from daemon: permission denied


Any hints to what might cause the problem or how to resolve it would be greatly appreciated.

---

### Post by Daniel_Ford on 2015-03-16
I have the same issue.  I'm getting this log message via "dmesg | grep docker"

audit: type=1400 audit(1426536721.720:21): apparmor="DENIED" operation="mknod" profile="docker_docker_1.3.3.001" name="/dev/shm/aufs.xino" pid=656 comm="docker" requested_mask="c" denied_mask="c" fsuid=0 ouid=0

I'm an AppArmor newbie, but I did a bit of poking around and comparing.  I noticed that on my main (14.10) development machine that there was an AppArmor configuration file for docker in /etc/apparmor.d/docker that seemed to specify how to deal with docker.  There was no such equivalent file on my "snappy" machine.  And, with the file system "read-only," I was unable to copy over the file to try things out.

I'm running ubuntu-core/devel-proposed #333 (from March 16'th, 2015).

It seems a bit strange that something as fundamental as this would be missing and nobody (except us) noticed yet.

Dan

---

### Post by s.gerard on 2015-03-17
> **Daniel_Ford said:**
> 
It seems a bit strange that something as fundamental as this would be missing and nobody (except us) noticed yet.

Especially because snappy is advertised as specifically working with docker.

I also tried the learn/tutorial image which is supposed to only run a command, for example echo. Interestingly, when I don't specify a command, I get
> 
Error response from daemon: No command specified

so there is some checking of the prerequisites of the image that is supposed to be started, but after specifying a command I get the same error as before.

---

### Post by Daniel_Ford on 2015-03-24
I managed to get docker to run on build 341 (March 24,2015) of ubuntu-core/devel-proposed.  But, while trying to download a ubuntu image, it timed out and then subsequenly I received a 502 error (Bad Gateway) each time I tried to do anything with the docker repository.

---

