---
title: "Confused re Zoneclient and DDNS"
date: 2007-08-28
forum: Server Platforms
---

### Post by tbone02 on 2007-08-28
This is a repost from the Beginner Talk forum because I wasn't getting any responses and it is probably better suited for this forum anyway...

I'm a noobie who has a ubuntu 6.06 LAMP server installed. I've got SSH working and can log onto the server from within my LAN. I've also logged onto the server from outside the LAN. I have a domain name, and have included it as a zone on zoneedit, and I have forwarded ports 22 and 80 for SSH and Apache. Right now I have the domain pointed to the last WAN IP address I had. Of course, the ISP has changed the dynamic IP address and now my domain is no longer pointed at my router/server.

I know I need to run a client to reset the WAN IP address when it changes.

I used zoneedit as my DNS because it had support for doing this. I've been trying to figure out how to use zoneclient, but being a noobie I don't understand the (admittedly basic) instructions on the website.

Does anyone know of a "howto" for zoneclient for a noobie to Linux? Specifically, I need to know how to "install" the python code into the proper file and how to run the code periodically, e.g. hourly. I have found some code for including in the etc/cron-hourly/ directory, but I have tried and could not figure out how to include the code in that directory so that it will run.

Any help is greatly appreciated!

---

