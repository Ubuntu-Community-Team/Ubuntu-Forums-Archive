---
title: "Kvm"
date: 2022-01-22
forum: Virtualisation
---

### Post by ironwill98 on 2022-01-22
Good day!
I started to deal with Linux, in particular Ubuntu, not long ago, I was interested in the topic of KVM and docker
there is a host system on it, KVM was installed and the bridge was configured;
after installing docker on the same system, problems with access to guest systems began.
found out that the docker either rewrites the rules of the roofing felts table ... I found only one solution to this problem - create a file /etc/docker/daemon.json with the contents
```
{
"bridge": "virbr0",
"iptables": false
}
```
and restarting the docker solved the problem at first glance, but I ran into another one about creating a container from the docker hub, everything works, but if the Dockerfile is located locally, then at the time of installation \ download \ update of the program it gives an error that it was not possible to contact the server, I attach an error
```
Step 4/6 : RUN apt-get update &&     apt install -y openjdk-8-jdk openjdk-8-jre &&     apt install -y git &&     mkdir /Blynk &&     git clone https://github.com/IronWillDevops/blynk.git /Blynk
 ---> Running in 8a61282475d5
Err:1 http://archive.ubuntu.com/ubuntu focal InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:2 http://security.ubuntu.com/ubuntu focal-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:4 http://archive.ubuntu.com/ubuntu focal-backports InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists...
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal/InRelease  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


Reading package lists...
Building dependency tree...
Reading state information...
E: Unable to locate package openjdk-8-jdk
E: Unable to locate package openjdk-8-jre
The command '/bin/sh -c apt-get update &&     apt install -y openjdk-8-jdk openjdk-8-jre &&     apt install -y git &&     mkdir /Blynk &&     git clone https://github.com/IronWillDevops/blynk.git /Blynk' returned a non-zero code: 100
ERROR: Service 'blynk' failed to build : Build failed
```
there are suggestions that the addresses are not resolved (there are no errors in the Dockerfile because it was previously launched on a system without kvm and everything works)
I would be very grateful for your help in solving this problem.

---

