---
title: "Is LAMP needed on 10.04 LTS for OpenVZ installation?"
date: 2012-03-22
forum: Virtualisation
---

### Post by Bradyhawke on 2012-03-22
I'm experimenting with setting up a VPS server for the first time and after a bit of research and reading I've settled on a game plan to follow - I just have two questions that I couldn't find an answer for (even after doing the google)...

1) I'm starting with a basic Ubuntu 10.04 LTS 64-bit installation - no other items installed.  I'm planning on following the howtoforge.com guide ( [http://www.howtoforge.com/installing-and-using-openvz-on-ubuntu-10.04](http://www.howtoforge.com/installing-and-using-openvz-on-ubuntu-10.04) ) for the installation, but I cannot seem to find out if I need more than the basic installation.  Do I need LAMP installed before I install OpenVZ?

2) Partitioning structure. I am currently experimenting with this installation using the following setup:

2 x 320GB hdds setup in a RAID1 array during the o/s installation (software RAID).
"/boot" partition
"swap" partition
"/ " (root) partition
"/var" partition
"/home" partition

When the OpenVZ installation is complete and I start setting up "containers" will each container follow my partition layout or will everything (within each container) reside within a single partition?  I'm more curious about how this part works out when it comes to setting up backups within a container - might be getting a bit ahead of myself and will get to that part when I get there but it was nagging my brain so I thought I'd ask...


That's all for now, thanks in advance guys!


- Bradyhawke :guitar:

---

### Post by gordintoronto on 2012-03-22
I suggest you do some more reading. Spending about eight minutes on it, I *think* you need to install Apache in any container which will be functioning as a web server, and MySQL/PHP as required. Also, it appears to me that all the containers take their disk space from the host system's /var. But I'm no expert, use lots of Google, such as: openvz tutorial

I think of RAID as one more thing that can go wrong. I would rather do real backup.

---

### Post by Bradyhawke on 2012-03-23
> **gordintoronto said:**
>  I *think* you need to install Apache in any container which will be functioning as a web server, and MySQL/PHP as required.

Yes, from what I've read from "the google" searches I've done, and from the tutorial section from the openvz.org wiki (especially the part pertaining to the templates), I've figured out that I can install templates into each container - and those templates can have ubuntu, apache, mysql, php, etc. as part of their template/installation.

But what I have not been able to find is info on whether or not LAMP is required for the installation.  I'm more curious if a LAMP installation is required as part of the server installation BEFORE I install Open VZ - and if the software that would be installed within each container (when the time comes) would be dependent upon that software being part of the initial server installation? Maybe I'm over-thinking this, I just don't want to install too much software that isn't required in the first place or not install something that will be needed later on...


- Bradyhawke :guitar:

---

