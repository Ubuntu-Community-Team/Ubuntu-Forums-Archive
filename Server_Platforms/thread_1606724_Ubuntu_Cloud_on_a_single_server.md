---
title: "Ubuntu Cloud on a single server?"
date: 2010-10-26
forum: Server Platforms
---

### Post by JeSTeR7 on 2010-10-26
I would LOVE to play with the cloud server setup in 10.10, but I want to know if it's possible to do this on a single server.  From my reading, I'm seeing that you need at least 3 different roles to get the cloud up, but I just don't have the money (or space) to setup 3 servers.

---

### Post by yesrno on 2010-10-27
Hmm I myself actually haven't used the cloud server. But i'm not sure what there would be to play with if you only have 1 server. You could run 3 of them in a virtualisation tool.

---

### Post by kim0 on 2010-10-28
hey guys
You should ask this in the cloud forum :)

- First, you need 2 servers not 3 for a supported configuration
- If you don't have 2 servers at least, You can launch an ec2 instance and install everything on that. I have a nice little guide at
[http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html](http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html)
Of course performance and what you can do will suffer a lot

- Your third option is to try to adapt the script above to work on a physical server rather than an ec2 instance. If that works, let me know

---

### Post by Thirtysixway on 2010-10-29
As yesrno said, it wouldn't be too difficult to run 2 or 3 visualized ubuntu servers.  Performance may suffer depending on the specs of the host machine.  Look at something like virtualbox or vmware.

---

