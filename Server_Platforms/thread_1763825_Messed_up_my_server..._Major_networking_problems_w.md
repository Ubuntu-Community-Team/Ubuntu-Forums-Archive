---
title: "Messed up my server... Major networking problems with hamachi."
date: 2011-05-20
forum: Server Platforms
---

### Post by phRAPeh on 2011-05-20
I have never posted on the ubuntu forums before, so hello! I've got a server that I've set up to be a minecraft server, to connect to it for the moment I've previously had hamachi 0.9.9.9 installed on it. Well some users were complaining that it wasn't working correctly, so I decided to try and upgrade to hamachi2 beta to see if that solved the issues. Somehow after using hamachi for that long I had 4 hamachi network devices (ham0, ham1, etc.) Before I installed hamachi2 I removed all of the network interfaces from ifconfig and then installed hamachi. After the install, hamachi worked, but only on my lan. I then tried to change the routing tables using the route command. I changed the gateway to my hamachi ip address and that was it. Well that made it so I couldn't connect to hamachi over lan anymore, so I deleted the routing table, deleted ham3 from ifconfig and uninstalled and reinstalled hamachi2, now when I run ifconfig ham3 doesn't have an ip address or netmask. I need a little help to get this server running again, I'm overall pretty bad with command line and pretty much a ubuntu noob.

---

