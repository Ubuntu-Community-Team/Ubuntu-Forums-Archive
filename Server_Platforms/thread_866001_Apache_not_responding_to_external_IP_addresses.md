---
title: "Apache not responding to external IP addresses?"
date: 2008-07-21
forum: Server Platforms
---

### Post by gwjacc on 2008-07-21
Hi, I'm running a LAMP server on Ubuntu 8.04 (everything up-to-date) and have an odd problem with our server.

Everything seems to be running correctly. We can view web pages served by Apache from the internal network. However, when we try to access the server form the outside, it says that the server could not be found. I cannot figure out why this might be. We don't have any firewall software running on the Ubuntu LAMP server, and when I do (to monitor the traffic), it says that it is receiving port 80 requests from the external IP address I am testing from. However, it just doesn't feed the web pages back to that external IP address.

Does the Apache server need to be set up somehow to allow connections to computers outside of the internal network? Oh, and the config file ("000-default" in the "sites-enabled" directory) has the "allow from all" option.

Also, it isn't anything fishy with our firewall/router box, because when we direct the traffic to our other server (by just changing the IP on the firewall box) the other server works fine with external connections. Also, like I said, when I run a firewall program on my Ubuntu machine, it logs that it is receiving a request on port 80 from the remote location.

Any thoughts?

Thanks in advance.

---

### Post by TreeFinger on 2008-07-21
Are you sure your router/firewall is setup correctly to accept connections from port 80 and forward those requests to your apache server?

---

### Post by gwjacc on 2008-07-21
I figured out the problem. Thanks for the response.

It turns out that the firewall program on Ubuntu was running even without showing the icon in the upper right-hand corner. For some reason I assumed it wasn't running when I had the admin window closed (dumb error on my part- the icon disappeared [also never appeared] so long as the admin window was closed). I totally disabled the firewall and Apache is running fine.

---

