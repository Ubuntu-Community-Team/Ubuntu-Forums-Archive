---
title: "NFS Question"
date: 2010-10-27
forum: Server Platforms
---

### Post by zjagannatha on 2010-10-27
I'm trying to setup kiosks in my school's Math Department running Ubuntu 10.04LTS. Previously, I had them setup so that they all imported /home and /usr from a server on startup. The problem was that the kernel tries to mount /usr before starting up the network, so we had to press escape and manually start DHCP before mounting any of the networked file systems. In addition, trying to do anything on the computers is extremely slow.

So I've decided to only mount /home on startup, so that users can have their information stored independently of the computer they are working at.

The issue I see is that having /usr on each computer would make installing programs a major pain, since we'd have to go around to each computer and install programs on each one.

Is there an easy way to tell each client to get install requests from the server and install things automatically?

I could simply hack something together with sockets in C but I'd think that it'd have some major security flaws.

Help much appreciated,
- zjagannatha

---

### Post by the_original_billq on 2010-10-27
There are many ways to setup a distributed workstation configuration, based on the needs of the customer (user).

NFS server, configured to serve up "file & print" to a set of "fat" workstations.  Usually also the NIS/LDAP/DNS/NTP server, though that could run on another machine(s).  Some scripts could also be kicked off from this server to run updates on your workstations using ssh trust accounts.  There are also tools like "webmin" that make this more GUI-friendly.  Running autofs (automount) on the client workstations, and setting up the automount maps in NIS makes home directory maintenance a no-brainer.

Alternatively, and based on the needs of your users, you could look at a thin client/ulta thin client/x terminal type architecture.  There are many solutions out there that provide zero (or near-zero) administration on the client side.

Hopefully, this will give you some idea where to start looking - perhaps at solutions you had not yet considered.

-Bill

---

### Post by koenn on 2010-10-27
AFAIK, you *should* be able to mopunt /usr off an NFS share. 
-> [http://www.pathname.com/fhs/pub/fhs-2.3.html#PURPOSE18](http://www.pathname.com/fhs/pub/fhs-2.3.html#PURPOSE18)

so maybe it is possible to tweak the init/startup scripts so that /usr gets (re-)mounted after network is functional. 


Alternatively, using parallel and/or scripted ssh sessions with password-less, key-based authentication, might be an effective way to install software over multiple hosts. 

think something like (pseudo, check syntax !)
```

for host in list; do
  ssh root@host  apt-get install package
done

```

or have a look at  pssh (parrallel ssh)
[http://code.google.com/p/parallel-ssh/](http://code.google.com/p/parallel-ssh/)

---

### Post by SeijiSensei on 2010-10-27
You can keep /usr synchronized with rsync:

```

cd /
rsync -av server:/usr .

```

Run it hourly or daily from cron.  (To run it without intervention, you'll need a shared SSH key for the root user on both ends, or start an instance of rsync in "daemon mode" on the server.  "man rsync" for details.) 

You also might want to considering mounting /usr read-only in /etc/fstab as well to prevent someone from hacking common applications.  In that case you'd need a script that first remounts /usr as read/write, then runs rsync, then remounts /usr as read-only again.  Something like this might work, but I'm not promising...

```

cd /
mount -o remount,rw /usr
rsync -av server:/usr .
mount -o remount,ro /usr

```

---

### Post by annoyingrob on 2010-10-27
You can pass network parameters to the kernel in grub, and then tell your network init config to NOT automatically configure your ethernet adapter (eth0 manual), as it's already up. You can then mount /usr over nfs. I used to use it on testing machines to mount / as nfs.

---

