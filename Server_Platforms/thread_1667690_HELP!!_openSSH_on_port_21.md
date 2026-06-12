---
title: "HELP!! openSSH on port 21"
date: 2011-01-15
forum: Server Platforms
---

### Post by DanHorniblow on 2011-01-15
I have just done a clean install of ubuntu server 10.10 with no packages, I would rather install them seperatly.

I followed [this tutorial]("http://www.jonathanmoeller.com/screed/?p=2305") to set a static IP.

I then ran **sudo aptitude update && sudo aptitude dist-upgrade** to update the system.

I then ran **sudo apt-get install openssh-server** to install the openSSH server.

then I changed the port value from 22 to 21 in the **/etc/ssh/sshd_config** file.

Now I cant SSH to my server on any port, it just gives me an error message saying **Connection to host 192.168.1.25::21 was closed.**

Any ideas what has gone wrong?

---

### Post by DanHorniblow on 2011-01-15
Fixed, silly mistake by me, my client noticed that the server was using a different RSA key (because of the reinstall) and was refusing the connection

---

