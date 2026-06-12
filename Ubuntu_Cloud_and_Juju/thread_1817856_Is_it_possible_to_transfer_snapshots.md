---
title: "Is it possible to transfer snapshots?"
date: 2011-08-03
forum: Ubuntu Cloud and Juju
---

### Post by Ohm's Lawyer on 2011-08-03
Hello, I have another question...this one should be simple though.

I have set up a whole new cloud, but would like to save my instances (particularly my volumes) from my old cloud. I have snapshots of everything, but I can't seem to figure out how to transfer them. It would seem to me, that snapshots are particularly useful in archiving, so it should be a simple move, but so far the only documentation I've found on it recommends running both clouds simultaneously, firing up identical instances with identical volumes, and basically block dumping the files over using dd or cpipe (or any other large block transfer program). That just seems clunky and defeats the whole purpose of the snapshot. Does anyone know how to just move snapshots from one cloud to another? 

Thanks in advance!

---

### Post by kim0 on 2011-08-06
dd over the network is exactly what I was going to mention :) Also afaik, eucalyptus2 did not have EBS based instances, so I don't think that snapshot contains the machine, it probably contains just a data disk. Cloud instances are supposed to be disposable, you should only care about your data IMO

---

### Post by Ohm's Lawyer on 2011-08-07
Yup, that's all it is. There's no machine data on them, just file data. But it's important data...It just seems to me, IMHO that snapshots should be easy to move around. That way they could be used for backups, archiving, off site safety copies, or just making multiple instances with the same file set. I could have one instance running on my private cloud and a parallel one on Amazon. It just seems like dd is the clunkier option when the snapshots are so convenient.

---

