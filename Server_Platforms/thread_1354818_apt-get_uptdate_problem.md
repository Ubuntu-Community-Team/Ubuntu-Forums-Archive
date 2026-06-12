---
title: "apt-get uptdate problem"
date: 2009-12-14
forum: Server Platforms
---

### Post by starfleetcaptainrob on 2009-12-14
Hello, I'm having a bit of a problem updating a server here at my company.  It's a server that was set up before I started and is often neglected.  However, it does require an update as a security scan revealed some flaws.

Anyhow, when I try to run the apt-get update I get this over and over:

```
W: Failed to fetch ftp://ubuntu.mirrors.tds.net/ubuntu/dists/hardy-security/restricted/source/Sources.gz  The server refused the connection and said: OOPS: vsftpd: cannot locate user specified in 'ftp_username':ftpubuntu

```

Obviously the ftp address is a little different each time, but it's the same message.  I'm not even sure if vsftpd is installed on this machine because I can't find the .conf file in /etc to see if there's anything wrong there.  When I try to install vsftpd it gives me the same message.  

Anyone have any ideas?

---

### Post by Frogging101 on 2009-12-14
I know this is a bit obvious, but is there an internet connection?

Also, try changing the repository by going to System -> Administration -> Software Sources -> Download from

---

### Post by ajgreeny on 2009-12-14
> **Frogging101 said:**
> I know this is a bit obvious, but is there an internet connection?

Also, try changing the repository by going to System -> Administration -> Software Sources -> Download from
This is a server, so I presume there is no gui to work with, only apt-get.  Unfortunately I am not sure how to change the server settings from the cli, but no doubt others will know how to do it.  That may help, but I think it would also help to see your **/etc/apt/sources.list** file to see if there is anything there that looks wrong.

---

### Post by starfleetcaptainrob on 2009-12-14
Ah, not sure why I didn't check the sources.list file (seems like whenever I post here someone always comes back with something really obvious).  It seems that someone was screwing around with that at one point and it didn't look right.  So I looked up a default version of the file and replaced it, now it seems all is right with the world.  Thanks!

---

### Post by ajgreeny on 2009-12-14
Great!  Glad my thoughts were helpful.

---

