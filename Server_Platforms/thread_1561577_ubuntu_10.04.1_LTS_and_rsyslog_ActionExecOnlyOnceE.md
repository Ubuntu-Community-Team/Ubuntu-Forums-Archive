---
title: "ubuntu 10.04.1 LTS and rsyslog: ActionExecOnlyOnceEveryInterval not working"
date: 2010-08-26
forum: Server Platforms
---

### Post by gravyface on 2010-08-26
ubuntu 10.04.1 shipped with rsyslog 4.2.0, looks like the latest stable is 4.6.3 and from the changelog, it sounds like the $ActionExecOnlyOnceEveryInterval variable was fixed in 4.4.3 (that was never released, but 4.6 was, shortly thereafter).

Has anyone setup email alerts with Ubuntu 10.04 and rsyslog 4.2.0?  Is the $ActionExecOnlyOnceEveryInterval variable working for you?

---

### Post by gravyface on 2010-08-26
I just grabbed the latest .deb from the Debian repository and installed it instead.  No idea why 10.04.1 LTS is running 4.2 (as the default syslog even!) when there's been newer, more stable releases since June 2009.

---

### Post by Vishal Agarwal on 2010-08-26
I am recently planning to use 10.04 as my server platform for my mail/Internet server.  Kindly advice more experience of yours if you are using UBUNTU 10.04 as server.

---

### Post by gravyface on 2010-08-27
Vishal Agarwal:

This has no impact on Postfix (the mail server that comes with Ubuntu 10.04) for sending and receiving mails; that works fine.  

My issue was regarding the *ommail* module in Rsyslog and more specifically, the ActionExecOnlyOnceEveryInterval variable not working, so I was getting way too many alerts sent to my inbox.

---

