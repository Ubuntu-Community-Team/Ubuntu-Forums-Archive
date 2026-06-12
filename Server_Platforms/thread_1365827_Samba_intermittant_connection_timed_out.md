---
title: "Samba intermittant connection timed out"
date: 2009-12-27
forum: Server Platforms
---

### Post by CareySchug on 2009-12-27
I set up a server with software raid, older machine, about 1 GHz cpu, three 5500 RPM IDE disks in RAID5.  I installed Samba, and copied about 100 GB of stuff from my desktop to the server with no problems.

I did some elimination of duplicate files (well, some remotely some locally on the server, IIRC, though that shouldn't make any difference)  In any event, there is now presumably some fragmentation on the server, maybe making it a tiny bit slower.

Now, when I when I copy stuff over from my desktop, sometimes I get 

Error while copying xxxxxx
There was an error copying the file into smb://xxxxx
V show more details
Connection timed out.

It gives options for cancel, skip all or skip.  If I press skip, it continues with the next tile (why couldn't it have a button for retry?) and it will continue with the next file.

This is intermittent, Today I copied a 5.6 MB file and it failed at 2.7 M, a while later it failed at 1.9 MB and the third time it worked.

It SEEMS to fail less when I copy a directory with many small files than the same amount of data in one big file.

I also copied a directory with 100 MB in small files, and it only failed once (on one of the bigger files), but in another directory with a small number of 5-10 MB files it failed on almost every one.

My main Ethernet switch is supposed to be 100 MB/S but seems to only be working at 10 MB, but it was the only one with enough ports for all my museum unix machines.  I tried moving just that client and the server to a 10/100/1000 MB/S switch, but that did not help.  I'm guessing the raid on the server just isn't fast enough, but I could not find any way to configure either the client or the server to be more patient.

---

### Post by nkhumishe on 2010-08-27
I got same problem. Does anyone know how to resolve this?

---

### Post by Funkey Monkey on 2010-11-12
Bumping with Hope

---

### Post by s1nch4n on 2010-11-12
> **Funkey Monkey said:**
> Bumping with Hope

try to add this line in your [FONT="Courier New"]smb.conf[/FONT]

```
socket options = TCP_NODELAY
```

and then restart your samba...

---

### Post by rmadla on 2011-08-02
I encountered this problem when I switched from DSL to FiOS and so installed a new wireless router. I would try to upload a file from my laptop to my home server, and the home server would lose its connection to the network partway through the transfer, resulting in a "connection timed out" error on my laptop. The server would thereafter fail to respond to ping requests, print requests, etc., even from the router itself, and could not access the network. Rebooting either the server or the router would restore connectivity, but the problem would recur if the file transfer was attempted again.

After several hours of troubleshooting, I found that the default "maximum transmission unit" (MTU), which the new router automatically set to 1500, was too large a packet for my network to handle. I changed the MTU to 1400 and the problem was solved.

I don't fully understand the source of the failure, but hopefully my workaround will be helpful to someone!

---

