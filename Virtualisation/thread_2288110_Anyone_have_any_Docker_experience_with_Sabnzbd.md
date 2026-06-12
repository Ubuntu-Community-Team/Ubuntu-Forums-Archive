---
title: "Anyone have any Docker experience with Sabnzbd?"
date: 2015-07-24
forum: Virtualisation
---

### Post by npinn001 on 2015-07-24
I'm racking my brains here. After playing with KVM, I got round to Docker and I think its fantastic. I've set up lots of containers for different uses and got them all running on my server without at hitch, but the one I cant get working it Sabnzbd. 

I used the Tim Haak image from Github, and can install it fine. I thien enter the command (modified for my directories)

[HTML]docker run -d -h your_host_name -v /your_config_location:/config -v /your_videos_location:/data -p 8080:8080 -p 9090:9090 --restart=always sabnzbd
[/HTML]

I've opened ports 8080 and 9090 but cant connect up. I checked with netstat if any of the ports are already in use and they arent. 

Cant think what else it might be, other than an issued with the Docker image itself? I tried to build one myself and the docker file just kept crashing.

Any ideas?

---

### Post by KillerKelvUK on 2015-07-25
What's the URL you're using to try and connect to sab?

---

### Post by npinn001 on 2015-07-25
> **KillerKelvUK said:**
> What's the URL you're using to try and connect to sab?

http://<my-IP>:9090/sabnzbd

I'm wondering if its related to systemd. I recently switched my base os to Debian from ubuntu. Might have to swap back.

---

### Post by KillerKelvUK on 2015-07-26
[https://docs.docker.com/articles/networking/](https://docs.docker.com/articles/networking/)

Reading the docker docs the daemon creates a virtual adapter on the host and uses the 172.16.x.x range to assign IP's to the docker containers you create/start.  So when you say <my-IP> is that the IP of the host and is this in the same subnet as the docker0 virtual adapter created by the docker daemon?

---

### Post by Habitual on 2015-07-27
http://<host>:9090/sabnzbd or http://<guest>:9090/sabnzbd ?

---

