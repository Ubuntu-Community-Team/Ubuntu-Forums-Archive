---
title: "Ubuntu Server 6.10 - want to send mail from cron"
date: 2007-07-01
forum: Server Platforms
---

### Post by James79 on 2007-07-01
I've been going around in circles trying to accomplish this. There seems to be dozens of different ways of accomplishing one thing as usual :)

Initially I didn't even have a /usr/bin/mail. This is a basic LAMP server install. In my attempts, I've apt-get'd mailx, mailutils, nail, and others I can't remember. I somehow ended up with something called postfix which decided it wanted to run as a service :confused: Anyways I think I managed to remove that..

I *don't* want to run a mailserver. All I want to do, is be able to send a simple email from the CLI using my ISP's SMTP server.

What's the easiest way to do this?

Thanks in advance!

---

### Post by gborzi on 2007-07-01
Try ssmtp, it's in the repositories.

---

### Post by James79 on 2007-07-02
Awesome! Thank you so much :)

---

