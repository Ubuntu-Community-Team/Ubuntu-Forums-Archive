---
title: "Best guide to setup server 16.04 - Timemachine"
date: 2017-06-01
forum: Server Platforms
---

### Post by mattiash on 2017-06-01
I need to configure a Ubuntu Server 16.04 to be able to let MacOS machine to use Time Machine against it.
Were do I find the best most current guide?

---

### Post by howefield on 2017-06-01
Thread moved to the "*Server Platforms*" forum.

---

### Post by cariboo on 2017-06-01
OSX is unix based, so you can use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") or [Samba]("https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated%2C%20Simple%20and%20Brief%20Way%21").

---

### Post by mattiash on 2017-06-01
@cariboo Samba? Got a guide for that?

---

### Post by cariboo on 2017-06-01
> **mattiash said:**
> @cariboo Samba? Got a guide for that?

Click the link in my post.

---

### Post by TheFu on 2017-06-05
> **mattiash said:**
> @cariboo Samba? Got a guide for that?

Samba doesn't support full Unix permissions like NFS does. NFS is also faster.
I don't know anything about Apple stuff, but Unix likes NFS.

---

