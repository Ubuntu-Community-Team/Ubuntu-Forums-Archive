---
title: "Help, Ubuntu 20.04 how to run koha library software in docker?"
date: 2021-02-25
forum: Virtualisation
---

### Post by deepakdeshp on 2021-02-25
[COLOR=#333333][FONT=&amp]I referred to [/FONT][/COLOR]https://hub.docker.com/r/digibib/koha

```
 sudo docker image ls|grep kohadigibib/koha                                     latest              7031f17fd22e        20 hours ago        1GB
uma@ubuntu:~$ sudo docker run 7031f17fd22e
Global config ... creating dirs and permission for koha config and zebra index
Setting up supervisord ...
Mysql server setup ...
Usage: ping [-aAbBdDfhLnOqrRUvV64] [-c count] [-i interval] [-I interface]
            [-m mark] [-M pmtudisc_option] [-l preload] [-p pattern] [-Q tos]
            [-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp_option]
            [-w deadline] [-W timeout] [hop1 ...] destination
Usage: ping -6 [-aAbBdDfhLnOqrRUvV] [-c count] [-i interval] [-I interface]
             [-l preload] [-m mark] [-M pmtudisc_option]
             [-N nodeinfo_option] [-p pattern] [-Q tclass] [-s packetsize]
             [-S sndbuf] [-t ttl] [-T timestamp_option] [-w deadline]
             [-W timeout] destination
ERROR: Could not connect to remote db 



```


isnt the database part of the docker image? The Ubuntu 20.04 is a VM, it can connect to the internet and has mysql installed.

---

### Post by deepakdeshp on 2021-02-25
[COLOR=#333333][FONT=&amp]I dropped the docker image and installed Koha on Ubuntu server 20.04 following
[https://technicaldigit.com/install-koha-on-ubuntu/](https://technicaldigit.com/install-koha-on-ubuntu/)[/FONT][/COLOR]

---

