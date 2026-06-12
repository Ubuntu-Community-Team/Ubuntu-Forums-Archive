---
title: "web server update from within DMZ"
date: 2008-10-28
forum: Server Platforms
---

### Post by devonps on 2008-10-28
Hi,

I am constructing an Ubuntu (web) server that will be sitting within a DMZ, that is connected to a router then the internet.

I would like to update the server using (sudo) apt-get update command(s) - can anyone tell me if the apt-get update process uses a specific port?

Steve.

---

### Post by cdenley on 2008-10-28
> **devonps said:**
> Hi,

I am constructing an Ubuntu (web) server that will be sitting within a DMZ, that is connected to a router then the internet.

I would like to update the server using (sudo) apt-get update command(s) - can anyone tell me if the apt-get update process uses a specific port?

Steve.

Port 80. I'm pretty sure everything is downloaded using HTTP.

---

