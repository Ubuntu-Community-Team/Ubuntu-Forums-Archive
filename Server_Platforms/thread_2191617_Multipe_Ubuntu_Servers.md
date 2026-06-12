---
title: "Multipe Ubuntu Servers"
date: 2013-12-03
forum: Server Platforms
---

### Post by yasser2 on 2013-12-03
Hello there,I'm installing two Ubuntu servers as a virtual machines, and i'm installing a simple application for sharing files on Server " A " , my aim is if the server A goes down, the Server B can take the lead and have the same files, i have been looking in internet, and i didn't find anything special, a lot of information and i'm confused, it someone can help me, and just direct me to something, that would be great.Thank you So much guys :)

---

### Post by nerdtron on 2013-12-03
That would depend on what you would like to replicate? The whole server or just certain folders for your application such as the mysql folders, or ftp folders?

---

### Post by volkswagner on 2013-12-04
Terms you will want to search "High Availability Linux File Server".


This will get you some info allowing you to ask more specific questions (samba, nfs, etc.).

---

### Post by rossguil on 2013-12-04
If you would only like to replicate the data, one possible solution would be to use rsync. A simple google search will easily get you some nice pieces of advice on that topic: [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

