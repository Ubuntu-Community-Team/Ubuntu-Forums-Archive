---
title: "NFS Specific Question"
date: 2006-11-21
forum: Server Platforms
---

### Post by Chado on 2006-11-21
I'll be honest off the bat that the server is Debian Sarge, not Ubuntu, but the client machines are Xubuntu.

Anyway what I'm wonder is if there is any way to allow users to access shared files by user name AND IP. 

For example:
I have a machine (dell1) with 6 logins (4 QBasics, one CPP, and one Java)
I want to make it so that I can only allow qbasic11 (Dell1, login1) at whatever IP to access his files on the server stored at /home/beast/QBasic/qbasic11

The same for all 6 accounts. There are then 24 machines in the network labelled dell1- dell24.

I hope someone understands me. Any suggestions are welcome and appreciated.

Chado

---

### Post by Chado on 2006-11-27
Anyone?

---

### Post by Chado on 2006-11-28
OK how about another program or setup?

---

### Post by JoesGrindingTeeth on 2006-11-28
You can only limit to IP with NFS, to do the rest you need to rely on file permissions (and that UIDs/GIDs map the same on all machines) to only allow certain users seeing files in those shares :(

Have you considered using Samba instead of NFS? - You could achieve the IP/Username restrictions your looking for with that fairly trivially I think.

---

### Post by Chado on 2006-11-28
If Samba works Linux to Linux then that wouldn't be hard. I thought it was Linux to Windows only (and I've been using it for a few years). Well if that's the case then it wouldn't be hard.
I'll let you know what becomes of it all.
Thanks

---

