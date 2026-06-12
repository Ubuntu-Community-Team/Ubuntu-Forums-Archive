---
title: "Best practice for remote file access"
date: 2009-07-22
forum: Server Platforms
---

### Post by Indemnity83 on 2009-07-22
I'm working on setting up an Ubuntu server for a Real Estate office and one of the key components will be the ability for Agents to remotely access files. 

Agents should have access to both their home folder (~) and a few other folders, idealy based on permissions (same folders are being shared through samba for local access).

My first thought is to setup an FTP server, and web utility like Net2FTP. But I'm not sure how to setup the FTP server to show the user all the shares, and their home folder while at the same time locking them out of browsing around the rest of the server. 

I'm open to suggestions too for better methods. 

Please, and thank you.

---

### Post by juancarlospaco on 2009-07-22
[**AjaXplorer**]("http://www.ajaxplorer.info")

---

### Post by Indemnity83 on 2009-07-22
Thanks, that looks pretty cool. I'll give it a try on a development system. It appears to solve the problem of getting users to both semi-public and /home folders.

However, it looks like that uses its own user system though? Which wont work for me since I'm using samba internally.

---

