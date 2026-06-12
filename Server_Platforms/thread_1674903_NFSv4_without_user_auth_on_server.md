---
title: "NFSv4 without user auth on server"
date: 2011-01-24
forum: Server Platforms
---

### Post by chrism0dwk on 2011-01-24
Hi all,

I'm trying to migrate our small HPC cluster over to NFSv4 from NFSv3.  In my current (NFSv3) setup, the server exports /export/homes which the clients (frontend and execution nodes) mount as /home.  The frontend node acts as an NIS server to allow the execution nodes to authenticate the users.  This means that when a user is added (on the frontend node), a home directory is created *via* the NFS share on the fileserver, with the directory UID set according to the frontend's /etc/passwd file.  The result is that the users on the frontend do not exist in the /etc/passwd on the fileserver.   This is deliberate, as I don't want users to be able to ssh from  the frontend into the fileserver -- there is simply no need.   Hence, the fileserver has a bunch of directories with UIDs that do not actually exist in its /etc/passwd.

The problem: having tried out NFSv4 for /home on the frontend, all the file ownerships default to 'nobody' (apart from myself, I have an account on the fileserver for obvious reasons).  Reading around, I assume that this is because the users don't actually exist on the fileserver.  Is there any way to replicate the simple UID to UID mapping that NFSv3 uses in NFSv4?  

Thanks,

Chris

---

