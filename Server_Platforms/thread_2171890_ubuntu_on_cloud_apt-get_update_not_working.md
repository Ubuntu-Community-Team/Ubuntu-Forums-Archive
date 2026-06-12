---
title: "ubuntu on cloud? apt-get update not working"
date: 2013-09-02
forum: Server Platforms
---

### Post by Tommy_Maersk on 2013-09-02
Hey
I just got my first cloud hosting account, created my first server with ubuntu 12.04 from image provided from the cloud provider.

However when running an sudo apt-get update, it freezes from the start.
First line is:0% [Connecting to default.clouds.archive.ubuntu.com ....

And nothing happens - what am I doing wrong or forget to set up?

I can ping the server, and ping from the server, so there is internet on the machine.

Thanks

---

### Post by nerdtron on 2013-09-02
> **Tommy_Maersk said:**
> Hey

I can ping the server, and ping from the server, so there is internet on the machine.

Thanks

What does this mean? How did you make sure that internet is working on the machine?
Let's try to isolate the problem.
Can you ping [www.google.com](www.google.com) just to make sure the server can connect to the internet.
And please post the content /etc/network/interfaces file and also post the output of the command "ifconfig".

---

### Post by Tommy_Maersk on 2013-09-02
I found the solution, it was trying to work with ipv6 when updating, i disabled ipv6 and it worked:)

---

