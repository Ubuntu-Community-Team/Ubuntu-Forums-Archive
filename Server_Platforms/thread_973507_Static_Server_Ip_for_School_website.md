---
title: "Static Server Ip for School website"
date: 2008-11-06
forum: Server Platforms
---

### Post by vbcoderx on 2008-11-06
Hello all, I am a student in a program called EASTLab. I know ubuntu pretty well, run it at home, and have a server myself running it at home. My EASTLab teacher asked my to set up a website for the Lab, and i installed ubuntu server 8.10 on one of our servers. DHCP works fine, but, we have certain internal ips, that have external ips linked to them. For example, 10.23.1.5 is linked to an external IP that i will not post for security reasons, but, it won't let me set the internal IP! Every time i try in /etc/network/interfaces, it fails to bring up eth0 when i restart it with /etc/init.d/networking restart. I have tried the same exact configuration on one of our windows workstations, and it works fine, able to browse the internet and show up as the external ip, but for some reason, won't work on linux, as i have also tried on Centos 5... I have also set static DNS servers in /etc/resolv.conf. We have enterprise HP switches feeding our classroom btw. I really don't want to use windows server, as the server will be live on the internet, and we all know how great windows servers are >.<

also, i forgot to say, if i reinstall ubuntu server and manually set the network settings with the information, it accepts it, and computers on the immediate local network can see it (ssh and http), but outside the immediate network, one switch up, it won't work.... But, when i assign it to a windows workstation, it works fine, and can be seen from the internet and up as far as we could check...

---

### Post by gombadi on 2008-11-06
> 
but, it won't let me set the internal IP! Every time i try in /etc/network/interfaces, it fails to bring up eth0 when i restart it with /etc/init.d/networking restart


A little more information would be helpful.

What error are you getting when you restart it?
What is the config you are setting (cat /etc/network/interfaces)

---

