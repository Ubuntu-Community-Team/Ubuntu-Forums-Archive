---
title: "docker?"
date: 2016-10-20
forum: The Cafe
---

### Post by sam-c on 2016-10-20
what is docker? I installed it.:)

---

### Post by y6FgBn)~v on 2016-10-20
A bit vague, but I'll bite ;-)

[https://www.docker.com/what-docker](https://www.docker.com/what-docker)

---

### Post by Dragonbite on 2016-10-21
Docker is similar but different than Ubuntu Snaps.  
Similar to Virtual Machines, Docker is like a VM for applications only.  
The Container holds not only the bits for the application, but includes its own instance of any system bits the application needs.
There are a number of container technologies out there but the ones getting much recognition are Docker and Ubuntu Snaps.  Snaps, I think, are what the Ubuntu Phone uses  for its applications.

So you don't have to worry about if the version you have in your OS is the right version the application needs.  The version the application needs is included in the Container.

If you have ever had a PC game that works in Windows XP, but doesn't work in 7 it could be that things moved, changed or is no longer compatible.  A Container would include the bit that it needs regardless which in theory would allow the game to run.  This is in theory and for illustration purposes only.

In theory if you have one machine with a Docker container on it, and you wanted to move it to another (even a different distro) it would work because there is little, if anything, that it needs that will notice you running it on a different version, distribution, etc.  This also means that if you have one system to develop in (say Ubuntu) but will deploy it on another system (Red Hat) then you wouldn't have to worry about the different systems so much. Develop on one and then drag-drop-fire up!

It is supposedly enables you to run multiple copies of the same application.  You'd be able to run multiple versions at the same time.

If you are updating a container you download it and turn it on.  If it doesn't work then turn it off. You may not necessarily have to turn off the original one either.  For example if you have a PHP 5 website and you want to see if a PHP 7 version would work on your server you can fire up the PHP 7 version and if it doesn't work just go back to the working PHP 5 version.

Unlike VMs where you carve out a portion of your CPUs and RAM per VM image, Docker Containers heave theoretically access to ALL of your resources just like if you open up Chromium it shares the resources with other applications but if they aren't doing much than that's more for Chromium!

At work I am looking at trying to move the web server over to a Docker Container.  I have 3 servers (Dev, Prod and Fallback) and am looking at making the update process easier (develop on Dev, upload container to Fallback, fire it up to ensure everything works, repeat on Prod) as well as we may be moving from FreeBSD servers to CentOS servers and if containers are cross-compatible then that migration would be made so easy!  

I'm also looking to see if I can use Docker images to consolidate my home's web servers and Minecraft servers.  Right now Minecraft servers run one-world-per-machine (there are ways to run multiple worlds on one instance but I haven't had luck on that).  I want to test and see if I can get multiple Minecraft worlds running on one single box.

I'm looking at using Docker currently because I may or may not be moving to different distros and/or to FreeBSD and I am not sure how well Snap works on non-Ubuntu distros.  I assume that using Docker and Snappy are similar in concept and may turn around and use Snappy at home where I can make my servers all running Ubuntu Server (actually they already are).

---

