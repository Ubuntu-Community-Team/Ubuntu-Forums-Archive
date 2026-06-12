---
title: "MySQL update did something odd with the root password..."
date: 2010-04-01
forum: Server Platforms
---

### Post by uberlinuxnerd on 2010-04-01
Hi all,

We have quite a few ubuntu servers running in my place of work. I was running updates today and on one of the servers MySQL updated. The MySQL daemon restarted and all of a sudden the app server (Wordpress blog in this case) could now longer connect via the root password?!? 

Now I have resolved the issue by ignoring the grant tables and changing it back to what is expected. The point of this post is the try and track down what may have happened if anybody can shed any light on the matter.

Server is running Ubuntu 8.04.4 LTS

Thanks in advance

Dave

---

