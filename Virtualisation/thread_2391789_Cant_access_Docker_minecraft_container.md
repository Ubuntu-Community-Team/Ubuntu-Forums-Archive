---
title: "Cant access Docker minecraft container"
date: 2018-05-13
forum: Virtualisation
---

### Post by benjbt on 2018-05-13
Hi all, new here and hoping you can help. 

I am setting up a home server to run CRM , media and minecraft via docker. 

I have installed ubuntuserver 16.04 LTS and Docker, also portainer to manage the containers easily.

The trouble I'm having is I cant access some containers even from localhost, most actually.

Portainer is running on 0.0.0.0:9000 fine and I can access it via local IP no problem.

Minecraft installed but not visible on 0.0.0.0:25565 even though I ran it with -p 25565:25565

I was hunting for something blocking port 25565 until I installed nginx on 25565 as a test and it worked fine.

I have tried a few images with the same result, reinstalled docker, removed firewall, flushed iptables, confirmed allow  of new connections. I cant find anyone having a similar problem as most people are asking about external access. 

Same problem on my fedora work station but no joy with help from docker, fedora or minecraft communities.

I have the same problem with other containers like bitnami/suitecrm and wowza but portainer and nginx work.

I'm not strong with networking or linux but learning fast.
Please help.

---

