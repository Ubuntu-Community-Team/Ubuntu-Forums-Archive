---
title: "Ubuntu Server 20.04 LTS - RT HWE kernel how to?"
date: 2022-04-19
forum: Server Platforms
---

### Post by codrut-popescu on 2022-04-19
I am using:
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.4 LTS
Release:    20.04
Codename:    focal

uname -a
Linux nuc11.altitude-dashboard.com 5.13.0-39-generic #44~20.04.1-Ubuntu SMP Thu Mar 24 16:43:35 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

I need to enable RT support for Docker as a requirement for my testing as detailed here:

[https://github.com/oracle/docker-images/blob/main/OracleDatabase/RAC/OracleRealApplicationClusters/README.md](https://github.com/oracle/docker-images/blob/main/OracleDatabase/RAC/OracleRealApplicationClusters/README.md)


[LIST=1]
[*]Oracle RAC needs to run certain processes in real-time mode. To run processes inside a container in real-time mode, you need to make changes to the Docker configuration files. For details, refer to the [dockerd documentation]("https://docs.docker.com/engine/reference/commandline/dockerd/#examples"). and update the OPTIONS value in /etc/sysconfig/docker to following:
[/LIST]
[COLOR=#24292F][FONT=-apple-system]OPTIONS='--selinux-enabled --cpu-rt-runtime=950000'[/FONT][/COLOR]
So, how do I enable these features in the HWE 5.13 kernel?

I am using the HWE kernel and I need it because it does support my WiFi card.

I have installed the low latency kernel:

[FONT=&amp]sudo apt install linux-lowlatency-hwe-20.04[/FONT]

uname -a
Linux nuc11.altitude-dashboard.com 5.13.0-39-lowlatency #44~20.04.1-Ubuntu SMP PREEMPT Thu Mar 24 17:45:51 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

But starting Docker fails with:

docker create -it \
....
> --cpu-rt-runtime=95000 \
> --ulimit rtprio=99 \
> --name racnode1 \
> oracle/database-rac:19.3.0
Error response from daemon: Your kernel does not support CPU real-time scheduler

---

### Post by codrut-popescu on 2022-04-24
Anyone?

---

