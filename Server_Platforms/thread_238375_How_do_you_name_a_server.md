---
title: "How do you name a server?"
date: 2006-08-17
forum: Server Platforms
---

### Post by cocotu on 2006-08-17
Hello friends, here at work we set up a LAMP server for our Intranet. For now we can access it by typing the IP address, but we wanted to just type "intranet" or something else instead of the IP. I've looking to this answer in the apache website, but I'm a newbie in Apache so I have not figure it out yet. Thanks for your help..

---

### Post by chonger on 2006-08-17
What you want to do is make sure everyone machine on the intranet knows the name of your server, and how it maps to the IP.

Does your intranet have a DNS? Or some other kind of naming service?

---

### Post by cocotu on 2006-08-17
Yes chonger I believe we do, because when I type "intranet" in my browser I get from Novell(which is what this organization uses) saying:

STARGATE NetWare Management Portal

And is asking me for a login name.
Can I set this to any other name. I need to make this easy for the users here at work. We are about 25-30 users.

These are the changes that I made:

In the file /etc/hosts and /etc/hostname I changed to this:

10.0.3.107       localhost.localdomain   localhost intranet

In the httpd.conf:

ServerName intranet.10.0.3.107

Any suggestions?

---

### Post by chonger on 2006-08-17
Cool. So someone (your network administrator) has configured your network so that any computer on the network, when looking for the 'intranet' address, ends up going to the computer that runs this "STARGATE NetWare Management Portal".

You can ask the same admin to configure the naming service to set up a name for your server. You just have to him give the name you want, and the IP of your server.

However, you will most likely not be able to use the name "intranet" for your server. The person running your network is using that name for his machine, and he is unlikely to want to change that.

Keep in mind that any changes you make to /etc/hosts will only affect your own machine. So,

1. Think of a new name (like "fuzzykitty") for your server.
2. Find out the IP of your server (which appears to be 10.0.3.107). Make sure the IP does not change.
3. Tell your network admin to point "fuzzykitty" to 10.0.3.107. This is what tells every computer on your network that requests for "http://fuzzykitty/" should go to your server.

---

### Post by cocotu on 2006-08-17
Thanks chonger, I will give it a shot!

---

