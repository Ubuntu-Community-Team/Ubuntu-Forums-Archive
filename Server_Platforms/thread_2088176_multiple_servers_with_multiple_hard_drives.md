---
title: "multiple servers with multiple hard drives"
date: 2012-11-25
forum: Server Platforms
---

### Post by aronwalker on 2012-11-25
Hi there

I've only been using ubuntu for About 3 years. I have just receved 4 quite old blade servers with 12 750GB (you read that right) hard drives each. However, I don't know what do do with these servers. I was thinking of making a cluster or cloud with these. Or I rent them out to my frends at school (they want a private minecraft server). My internet is quite fast (I've got it upto 120 mbps). What should I do. Should I cluster them together, create a cloud (as my dad says I should do), make them as virtual servers or just 1 file server and the others as a mega minecraft server. I might also have a media server. Please help. I have no experience with clustering or clouds but have build my own file, lamp, mail and dns servers in the past. 

Please help and thankyou in advance

Aaron Walker

13

Manchester

---

### Post by chadk5utc on 2012-11-25
I dont have any experience with "CLOUD" computing, however I dont see any reason why you couldnt do any or all of it and spread it across the lot of them if that makes sense. There would certainly be enough CPU power and storage,Sounds like a great project!!!

Found a Howto for Cloud
[http://www.ubuntugeek.com/run-your-own-ubuntu-enterprise-cloud-guide.html](http://www.ubuntugeek.com/run-your-own-ubuntu-enterprise-cloud-guide.html)

And Clustering (maybe a bit dated but worth a read)
[https://help.ubuntu.com/community/Clustering](https://help.ubuntu.com/community/Clustering)
[http://labtu.blogspot.com/2010/06/how-to-create-cluster-on-ubuntu-1004.html](http://labtu.blogspot.com/2010/06/how-to-create-cluster-on-ubuntu-1004.html)

---

### Post by FCarlo on 2012-11-25
How about starting a small business renting servers (maybe minecraft servers)?

---

### Post by personalpc on 2012-11-25
I would say Highly Available KVM stack for redundancy no matter what service or virtual machine it provides. using drbl you can mirror the systems and even use the Openstack compute and nova environments which are based on drbl and kvm. See links bellow

[HA KVM]("http://crunchtools.com/kvm-cluster-with-drbd-gfs2/")
[Openstack 12.04]("http://www.hastexo.com/resources/docs/installing-openstack-essex-20121-ubuntu-1204-precise-pangolin")

---

### Post by sandyd on 2012-11-26
If you want something slightly easier, you can use proxmox to setup HA.

Works quite well :D

---

