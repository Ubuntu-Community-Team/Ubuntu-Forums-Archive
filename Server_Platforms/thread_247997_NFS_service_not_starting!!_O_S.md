---
title: "NFS service not starting!! :O :S"
date: 2006-08-31
forum: Server Platforms
---

### Post by dragze on 2006-08-31
Hi all, i have installed nfs-common and all dependencies on two pc's and they have all worked fine, no problem and no extra configuration, install nfs on an old imac (500mhz) and the service wont start :O :S.

I dont have a clue why it wont start had a look through some logs and the only thing i could see was in dmesg which gave:
Quote:
[ 108.935614] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[ 109.799130] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[ 109.802819] NFSD: recovery directory /var/lib/nfs/v4recovery doesn't exist
[ 109.802848] NFSD: starting 90-second grace period

Which means nothing to me?? so plz somebody tell me why this isnt starting.

If u need any more info just ask!

Thanks in advance,
dragze.

---

### Post by dragze on 2006-08-31
anybody?? somebody?? please!!!

i really am stuck with this one and i really really need it to work cause this machine is supposed to be hosting files to other linux boxs on the network!

please please please help!!

Thanks in advance,
dragze.

---

### Post by Uluen on 2006-08-31
```
[ 109.802819] NFSD: recovery directory /var/lib/nfs/v4recovery doesn't exist
```Well, does it exist? :)

---

### Post by dragze on 2006-08-31
no the directory didnt exist but i just made it but it doesnt exist in the working machines, anyway nfs-common still fails to start. I tried a reboot as well! :(

Please help!

Thanks,
dragze

---

### Post by dragze on 2006-08-31
just did dmesg again after reboot and no mention anywhere of nfs :O

nfs still not working and i dont know why!!

Cheers,
dragze

---

### Post by dragze on 2006-09-01
ok im really startin to get peed off wid this one!! i have posted this in the mac section of the forums aswell and have had no reply at all!!!

Someone please help me!! if only i new why the damn thing aint starting at least i could try and tackle it, but i dont have a clue why??

Come on people please please help me im in need here!!! :( :(

Thanks in advance,
dragze

---

### Post by Uluen on 2006-09-01
Is portmap installed and running? What about nfs-kernel-server? You did install these?

---

### Post by dragze on 2006-09-02
hi yes portmap is running and yes i installed nfs-kernel-server but not to sure if is running, when i type 'sudo /etc/init.d/nfs-common-server start' it doesnt give any message about starting service or service already started, it says nothing!

---

### Post by dragze on 2006-09-02
p.s excuse typo in last post i did type nfs-kernel-server in console not common.

what is the best way to find if nfs-kernel-server is running??

cheers 
dragze.

---

