---
title: "Cannot login after install NIS"
date: 2012-08-22
forum: Server Platforms
---

### Post by MocroNL on 2012-08-22
Good afternoon. As you can see, i'am new to this forum and this is my first post. 

I recently tried to install and configure NIS on Ubuntu 10.11 CLI. I still had to mess around a bit because the server kept spamming me with messages that it could connect to a nis server. I continued the next day but noticed that logging in took quite a while.... When I enter my username it takes a while before it answers with asking for my password. When I enter my password it takes up to 30 sec to 1 min before something happens. And the server just gives me a timeout and I cannot login. I tried this remotely and directly connected... Is there way to login or are these servers doomed to reinstalling? 

EDIT: server = poweredge 1750

PS: I have this problem with 2 servers now and its after I try to configure a NIS client.

Thanks in advance

MocroNL..

---

### Post by TheFu on 2012-08-22
a) 10.11 doesn't sound like an Ubuntu release. On a server, using either 10.04 or 12.04 would be recommended. Avoiding non-LTS releases is a best practice for production server systems.

b) You do not need to reinstall. Just use any LiveCD and boot to a recovery console and disable NIS.  When you setup NIS, be certain that you have local accounts that work in addition to NIS+ accounts.  I haven't screwed with NIS in many years, so I can't tell you exactly how, but the settings should be in /etc/pam.d/ .  I was under the impression that all the cool people were using LDAP for authentication these days.  We do from an openLDAP server on the network.  Use it for logins, samba, email, NFS, and about 20 web-apps.  The only thing we don't use it for is VPN remote access.  We have local accounts for when the LDAP server is down during maintenance.

Here's an NIS how to for Ubuntu. [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo) Note how they recommend having local accounts?

---

### Post by MocroNL on 2012-08-22
Thank you for the help I will try it right now with a live CD. And sorry I meant ubuntu 11.10.


I will report back when done.

---

### Post by SeijiSensei on 2012-08-22
This sounds a lot like a DNS lookup problem to me.  Did you give the NIS client the server's hostname or IP address?  Either add an entry to the client's /etc/hosts that maps the server's hostname to its IP address, or use the IP address in the client's configuration.

---

### Post by MocroNL on 2012-11-21
I have booted up with the live cd and removed NIS and now it is working properly.

(A little late answering this but this problem is solved)

Thank you!

---

