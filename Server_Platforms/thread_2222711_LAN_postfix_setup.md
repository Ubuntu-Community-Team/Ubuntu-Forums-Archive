---
title: "LAN postfix setup???"
date: 2014-05-07
forum: Server Platforms
---

### Post by owemeacent on 2014-05-07
I want to setup a mail system for my schools computer lab and I don't know how.  I don't want to setup bind or domain names or anything. Just something that I would enter the user@host from any computer on the network and it would appear in their mail folder. Is there anything that would work that way? Would I have to configure postfix in a way to do so?

---

### Post by owemeacent on 2014-05-07
I am trying to get postfix to work on a server in my schools computer lab. Let me give you a clearer idea of what I want:

One "admin" computer, it has the ability to send mail to any of the client computers, and has total authority over them.
Multiple client computers, they can receive mail, but not send back any, they have no LAN privleges.

The problem is I don't know how to get postfix to work.  I don't want to have make domain names for each or anything, so I'm just going to use hostname, like the ones in /etc/hostname. I can use those to ssh, so understandibly, I would also be able to use those to send mail, or even the IP addresses. But apparently not, I am unable to send any mail from the admin computer to any of the client computers, but I can send any messages to the root and the normal user on the admin computer itself. I have not messed with anything in the main.cf. I really hope you are able to help me in some way. And any help is greatly appreciated.

---

### Post by QIII on 2014-05-07
Is this the same question you asked [here]("http://ubuntuforums.org/showthread.php?t=2222711")?

---

### Post by owemeacent on 2014-05-07
Yea, no one answered it like at all, so I thought I might have to ask it somewhere else

---

### Post by QIII on 2014-05-07
Threads merged.

Please do not start multiple threads on the same subject in different areas of the Forums.  It dilutes the community's efforts to help and causes confusion. 

Also, please remember that the Forums community is world-wide and people live in all 24 time zones.  Do not bump your threads any more often than every 24 hours.  Four hours is far to short a time to become impatient.

---

### Post by nerdtron on 2014-05-08
Try installing [http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html) on the server.
This will be a mail server and then the clients will be able to receive/send email on your local domain using web mail.

---

