---
title: "Run a script on the server when my workstation starts?"
date: 2008-12-08
forum: Server Platforms
---

### Post by EvilMarshmallow on 2008-12-08
I have a workstation on our plant floor that has mysql installed.  I have set up replication with my server's mysql databases.  However, because the workstation is the master in the replication settings, I have to reset replication on the server any time the workstation is rebooted.

I have written a bash script that handles the reset and placed it on my server.  My question is this:

How can I add something to the workstation's boot procedure that causes the script to run on the server so replication will be reset?  I want it to be seamless; no user interaction required.

---

### Post by hictio on 2008-12-08
I'm not a MySQL expert, perhaps this can be done using MySQL itself, but, perhaps you can also do this thru SSH with public key auth?

---

