---
title: "Windows Mail server and Ubuntu webhosting"
date: 2008-04-08
forum: Server Platforms
---

### Post by Naramus on 2008-04-08
Hello first of all,im a beginner in the linux family,i wanted to see if there anybody out there who can help me.
these is my situation:
I have a Ubuntu 7.10 webserver (that is working fine,thanks to all the post that i have found on this forum) and a Windows Server 2003 MailServer that has Exchange on it.
I have been looking online,but havent found on how to connect the webhost server with the mailserver....it sounds terrible,(I Know it would be better just to setup the ubuntu also as a mailserver)but i wanted to see how it will works.:confused:

---

### Post by googlah on 2008-04-09
I would say it would be way easier to just put mail on your Ubuntu box. Just get Postfix on your system, and it will allow PHP and system-users to send mail through it very easily.

When it is installed, the config file will be in /etc/postfix/main.cf. In there, just change "relay_host" to a suitable SMTP-server for you. Then outgoing mail is set up. "my_destinations" are for the incoming mails. Hope that helped. :)

---

