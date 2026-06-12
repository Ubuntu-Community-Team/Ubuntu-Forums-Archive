---
title: "File Server"
date: 2005-03-08
forum: Server Platforms
---

### Post by Myles3 on 2005-03-08
Hi

I am setting up a simple file sever at my house.

The main problem is that I want to keep all my computers sync with only the /home dirctory. Basicly I want to be able to login to any computer and see the same thing as in every other computer. I was thinking a shell script launched at startup and boot down that uses rsync or cvs.

Thanks

---

### Post by Gravedigger on 2005-03-08
I want to do the samething but  want to add raid1 to file server drives two 250gb hdd with a third 10 gb hdd for operatieing system. I don't know where to start.

Thank You

---

### Post by alastair on 2005-03-08
Look at something like putting /home on the server, and mount /home via NFS on every workstation. Very common config.

---

### Post by Myles3 on 2005-03-08
[QUOTE=Gravedigger]I want to do the samething but  want to add raid1 to file server drives two 250gb hdd with a third 10 gb hdd for operatieing system. I don't know where to start.

Thank You[/QUOTE]

What dose raid1 do?

---

### Post by alastair on 2005-03-09
"raid1" mirrors disks - but is actually irrelevant to your actual question. To find out about RAID, do a web search - there are lots of docs/pages about it around that will enlighten you.

---

### Post by Myles3 on 2005-03-09
I have found a webmin module that might do the trick @ [http://sourceforge.net/projects/syncmin](http://sourceforge.net/projects/syncmin) . It uses rsync.

---

