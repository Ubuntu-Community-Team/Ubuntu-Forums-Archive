---
title: "Profiling Docker daemon using AppArmor complain mode + aa-logprof"
date: 2015-03-01
forum: Security
---

### Post by max91 on 2015-03-01
[FONT=Arial]Hi.[/FONT][FONT=Arial]
[/FONT]
[FONT=Arial]I'm trying to create a AppArmor profile on Ubuntu Server 14.04.2 LTS for Docker daemon (version 1.5.0), but after I have created a base profile in complain mode using aa-autodep every Docker command I run fail with this error:[/FONT]
[FONT=Arial]_stat .: permission denied INFO[0038] read parent: connection reset by peer_
[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]The procedure that I followed to create the profile is:[/FONT]
[FONT=Arial]create a base profile using: aa-autodep /usr/bin/docker[/FONT]
[FONT=Arial]restart the docker daemon: service docker restart (if I don't restart the daemon I don't get any problem but it's not the correct way to do it. Take a look at this example of profiling Nginx [ https://www.digitalocean.com/community/tutorials/how-to-create-an-apparmor-profile-for-nginx-on-ubuntu-14-04]("https://www.digitalocean.com/community/tutorials/how-to-create-an-apparmor-profile-for-nginx-on-ubuntu-14-04"))[/FONT]
[FONT=Arial]try docker build on any kind of Dockerfile.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]To check if there was some conflict with the AppArmor profile that Docker applies to its containers I changed Docker code to skip the creation of docker-default profile, but this didn't help.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Thanks.[/FONT]

---

