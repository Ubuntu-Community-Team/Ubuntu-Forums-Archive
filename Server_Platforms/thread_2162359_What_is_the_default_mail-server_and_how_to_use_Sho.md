---
title: "What is the default mail-server and how to use Shorewall instead of UFW?"
date: 2013-07-14
forum: Server Platforms
---

### Post by frankoo on 2013-07-14
Hello,
i plan to run my own mail-server (next to some other application like a web-server and a teamspeak server) on a rented root server (with ubuntu-server).
In the moment iam just playing a bit with a ubuntu-server installation on a virtualbox. Because before iam not absolutely secure about what iam doing (especially about security related things) iam not going to rent a server.

I found this mail server tutorial: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
i like it because it describes the installation of a fully scalable mail server (unlimited domains and users) and the auther seems to be very confident about what he is writing.

My questions are more general and not especially realatet to this tutorial:
1. I noticed during the ubuntu-server installation that there is an option to install a "mail-server" package (or packages), what exactly is that? I read a lot of mail server tutorials and all of them included a lot of manual configuration, so i am wondering what i get when i install that and how i can find information about what i have to configure manually.
2. The tutorial iam using prefers Shorewall for firewall configuration over UFW but even in the basic installation of ubuntu-server UFW is already installed. Is it in any way problematic to remove UFW with apt-get? What about having Shorewall installed next to UFW?

---

### Post by prodigy_ on 2013-07-14
1. I think "mail server" role in Ubuntu Server is based on postfix anyway.
2. UFW is just another package, so:
```
sudo apt-get purge ufw
sudo apt-get install shorewall
```

---

