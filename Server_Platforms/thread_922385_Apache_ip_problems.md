---
title: "Apache ip problems"
date: 2008-09-17
forum: Server Platforms
---

### Post by oakcraft on 2008-09-17
Hi guys, being new to Linux, I have cobbled together a mail sevre running Apache with squirrel mail. Everything works perfectly until I access over the internet. Using SSH, I can access the squirrel mail pages easily from a local adress, but if I use the external ip address, Apache will not load any pictures (such as the squirrelmail logo). If I logon from the servers own web browser, using the external IP adress, it works fine. Login from a windows box using either mozilla or ie, and it just waits, trying to load the pictures.
Any ideas what is going on? I take it has something to do with ip-forwarding, but have not a lot of ideas!
Thanks,

---

### Post by azadpanchi on 2008-09-26
Is the server behind a router or a firewall?

You want to refer to your router's manufacturer to set-up port forwarding.  You should also configure any firewalls to access your apache port, usually port 80.

Although I am a little confused with your description of the issue.  Please add more details and separate each point.

---

