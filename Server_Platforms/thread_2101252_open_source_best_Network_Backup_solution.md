---
title: "open source best Network Backup solution"
date: 2013-01-04
forum: Server Platforms
---

### Post by gauravjain on 2013-01-04
I have installed Ubuntu-server 12.04.1 in my server pc. I want to take backup some of files from windows machines every week. can anyone will suggest me open source or free backup solution with GUI. All machines are under one network.

---

### Post by fdrake on 2013-01-04
> **gauravjain said:**
> I have installed Ubuntu-server 12.04.1 in my server pc. I want to take backup some of files from windows machines every week. can anyone will suggest me open source or free backup solution with GUI. All machines are under one network.
ubuntu server doesn't have a gui , so you cannot use a buckup program with a gui while using ubuntu. Unless of course you mean something else.

---

### Post by ginge6000 on 2013-01-04
You could try [DeltaCopy]("http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp").  It needs an rsync daemon to be running on the server.

You simply install DeltaCopy on your Windows machine an schedule the backup as you need.  I've used it for a while now with great success to back up My Documents folders and disk images from my Windows PC once a week.

---

