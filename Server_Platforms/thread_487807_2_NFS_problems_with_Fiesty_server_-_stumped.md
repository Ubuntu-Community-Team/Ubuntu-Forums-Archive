---
title: "2 NFS problems with Fiesty server - stumped"
date: 2007-06-29
forum: Server Platforms
---

### Post by ndeubert on 2007-06-29
Hey Everyone,
First a little information...I'm using Ubuntu server as a NIS and NFS client, dual NIC load balancing, and have about 10 nfs mounts from 2 other linux boxes(not ubuntu). I have tried mounting these with all different combinations of options but the way they are right now is rw,rsize=8192,wsize=8192,hard,intr,nfsvers=2. I mount these shares on several other machines and they are all fine, so I think everything is ok on the server side. I installed autofs and uncommented /etc/auto.net in /etc/auto.master assuming it was needed for mounting nfs shares on boot, however then I noticed the mountnfs script in /etc/network/if-up.d and wondered if that should have been doing it? Is the autofs /etc/auto.net only needed on an nfs server?

My first problem is the first NFS share in my fstab is not getting mounted on boot. I have like 10 nfs shares to mount and the rest are all getting mounted but not the first one no matter which ones I put first. My first thought was, might autofs be trying to mount them too soon and by the time the first one times out the network has finally come up so all the others mount fine? Why would this be the case? Is there a way to mount nfs shares on boot without autofs?

My second problem is really odd. If I make a small executable in a share on my nfs server and then mount that share on my Ubuntu server then when I try and execute the file it tells me "-bash: ./a.out: No such file or directory". However, if I compiled the same file to create the executable from my Ubuntu server, on the same mounted nfs share, then it runs fine. There seems to be some weird permissions thing going on. Anyone have any idea what would cause this?

---

### Post by ndeubert on 2007-07-02
Nobody has any suggestions to try? Workarounds? Should I ask this somewhere else?

---

### Post by ndeubert on 2007-07-03
more info for anyone who has similar problems...
[https://answers.launchpad.net/ubuntu/+question/9092](https://answers.launchpad.net/ubuntu/+question/9092)

and seemed to have solved the mounting at boot issue by using auto option for each nfs mount int fstab.

---

