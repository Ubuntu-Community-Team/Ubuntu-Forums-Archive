---
title: "vsFTPd disconnects ftp after exiting putty"
date: 2013-05-16
forum: Server Platforms
---

### Post by roooii on 2013-05-16
Hi again,

I got a problem with vsFTPd shutting down current FTP sessions. It looks like the service is being shutdown. This happens when I enter "exit" in putty.

Any idea how this could happen?

Thanks for the answers.

**Edit:** There is more going on. I got 2 servers running. One is a test-server without any problems. 
I quit putty on the test-server and the mount keeps existing. When i log back in the mount is still there. I can still connect to the FTP server.
I quit putty on the live-server and the mount disappears. When I log back in the mount is gone. And I can't connect to the FTP server anymore.
Both mounts are setup in the /home/roy/domains/ directory.

Drives me crazy that it is working on one server :S

---

