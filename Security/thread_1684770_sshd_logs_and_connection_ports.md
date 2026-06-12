---
title: "sshd logs and connection ports"
date: 2011-02-09
forum: Security
---

### Post by sakshaw on 2011-02-09
Hi Guys, 
I am just hoping someone can help me understand what is happening when I log in to my Ubuntu server machine via ssh and putty. I'm new to linux and trying to understand everything, primarily securing my server.

I have specified the ssh server to listen on port 5525, and can login without a problem. When I look at the logs though it says I connected from xxx.xx.xx.xx on port 53602.

What is happening here and why is the logged connection a different port to the one specified in the config file?????

Thanks
sak

---

### Post by cariboo on 2011-02-09
The system you are using to connect to the server uses a random port for outgoing ssh. The port should be different every time you log on.

---

