---
title: "how to setup own server to have my site running on my computer with UBUNTU 12.04 Inst"
date: 2012-06-09
forum: Server Platforms
---

### Post by saurabh chhabra on 2012-06-09
Hi everyone,
                 Please help me out I want to have my website running on my computer to be there on internet as i wish to use it as a server, I have downloaded and installed ubuntu 12.04 but have no idea of commands of linux and to do what i intend please help me out . If some how someone can help me for the same and what are the requirements to have my computer as a server on internet including hardware needed and also guide me for each and everything

Thanks and regards for everyone in advance..

---

### Post by spynappels on 2012-06-09
Hi there.

Have you installed Ubuntu Desktop Edition or Ubuntu Server Edition?

In general, the following are required:

Static Internal IP address, so the server can always be accessed at the same IP address.

Port 80 forwarded from your modem/router to the IP address of your server.

Content placed in the /var/www folder on the server, assuming a default install of Apache.

There is a lot more to securing and hardening the server, I would suggest you also look at the security stickies here:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

