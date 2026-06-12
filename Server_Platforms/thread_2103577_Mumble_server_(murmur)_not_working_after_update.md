---
title: "Mumble server (murmur) not working after update"
date: 2013-01-10
forum: Server Platforms
---

### Post by Nysaan on 2013-01-10
Hi.
A few days ago my I saw in webmin that there were a bunch of packages that need to be updated. So I did and everything works fine.. except for the mumble server.
 
I've tried removing it completley and re-installing it but that didn't do the trick.
I've also tried starting it via /etc/init.d/mumble-server but no luck.
 
When i use the command "sudo service mumble-server start" i don't get any confirmation that it was successfully ran. Neither when I change start to stop, restart etc.
But after I've entered the command "sudo service mumble-server start" I can see the service has started via Webmin but still no response when trying to join, and django-mumble can't find the server either. And when I look in all the programs that should start on boot, i says on mumble-server "status = unknown"
 
I'm running Ubuntu 12.04 LTS, No GUI

---

### Post by d0m1nation on 2013-04-10
Exact same issue here. Have tried everything and I cant' get it to start..

---

