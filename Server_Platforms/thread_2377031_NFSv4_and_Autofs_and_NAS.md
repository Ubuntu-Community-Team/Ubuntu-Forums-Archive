---
title: "NFSv4 and Autofs and NAS"
date: 2017-11-08
forum: Server Platforms
---

### Post by zkab on 2017-11-08
I use Autofs on my Ubuntu workstation and have mounted some NFS4 shares with Autofs.

```
loke@loke:/nfs$ cat /etc/auto.nfs 
FARBAUTE		-fstype=nfs4   farbaute:/home/jurka/my_data
NASSE-FARBAUTE		-fstype=nfs4   nasse:/volume1/FARBAUTE
```
------------------------------------
1) FARBAUTE is on a Ubuntu server
2) NASSE-FARBAUTE is on a Synology NAS

Then I created a file 'junk' on both NFS shares.

1) Ubuntu server
```
loke@loke:/nfs/FARBAUTE$ touch junk
loke@loke:/nfs/FARBAUTE$ ls -l junk 
-rw-rw-r-- 1 loke loke 0 nov  8 12:50 junk
```

2) NAS server
```
loke@loke:/nfs/NASSE-FARBAUTE$ touch junk
loke@loke:/nfs/NASSE-FARBAUTE$ ls -l junk 
-rwxrwxrwx 1 1024 users 0 nov  8 12:51 junk
```

What I don't understand is '1024 users' for 'junk' on NAS
When I try to change ownership of 'junk' ... it can't be done

```
loke@loke:/nfs/NASSE-FARBAUTE$ sudo chown loke:loke junk 
chown: changing ownership of 'junk': Operation not permitted
```

I want to have the ownership 'loke loke' for 'junk' on NAS like it is for 'junk' on Ubuntu server.
Is it an Ubuntu/NFS or Synology NAS issue ?

---

### Post by DuckHook on 2017-11-08
I don't use a Synology NAS, but am guessing that your issue is there, and not with Ubuntu. How is the Synology export set up? You will have to SSH into the Synology to make your desired change. A client using sudo will not be permitted to make a change on a server for obvious security reasons.

I have also moved your thread to the Servers forum as a better fit for your issue.

---

### Post by zkab on 2017-11-09
Thanks - I will check with Synology

---

### Post by zkab on 2017-11-09
BTW - I SSH into NAS and /etc/exports shows following:
```
/volume1/FARBAUTE	192.168.0.45(rw,async,no_wdelay,crossmnt,insecure,all_squash,insecure_locks,sec=sys,anonuid=1024,anongid=100)rajan@nasse:/etc$
```

Just to clarify:
192.168.0.45 is my workstation
rajan is user on NAS (belongs to admin group)
nasse is computer name of NAS

---

### Post by DuckHook on 2017-11-10
I'm no server guru and am too far from home right now to effectively research this. Let's see if a server expert is around to shed some further light.

---

### Post by curts on 2018-02-03
I wouldn't call myself an expert on this, but the the user and group IDs have to match on both the NFS client and server. I had to hack root shell access for my old Hammer Storage NAS to get this sorted, as the supplied web GUI didn't extend to this level of control.

---

### Post by zkab on 2018-02-03
OK - thanks

---

### Post by TheFu on 2018-02-03
Not all NAS devices implement the full NFS/CIFS command set.  Check which level your specific NAS is supporting.  I suspect the anonuid=1024,anongid=100 config params are involved.  Make the UID/GID match on all devices.  That's a basic thing for all NFS.

---

### Post by zkab on 2018-02-04
The Synology NAS that I have gives support for NFSv4

---

