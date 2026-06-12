---
title: "Open Grid Scheduler qmaster host error"
date: 2012-12-05
forum: Server Platforms
---

### Post by borjamf on 2012-12-05
Hi all,

im trying to build an easy Cluster for some tests with two virtual Machines running Ubuntu 12.04 Server and ubuntu 11.04 Desktop. I've installed Open Grid Engine on my Ubuntu Server, it will be the Master Node.

Server:
```
sudo apt-get install gridengine-client gridengine-master gridengine-exec grid-engine common gridengine-qmon
Cellname = celulaborja
qmaster = prueba.borja

```The problem comes running qmon and some options: Host Configuration, Job...

Error:
```

error: commlib error: got select error (Connection Refused)
error: unable to contact qmaster using port 6444 on host "prueba.borja"
```I've checked the server host config and I can't see any issue:

```

hostname -f: prueba.borja

/etc/host.conf
   127.0.0.1         localhost
   127.0.0.1         prueba.borja
   172.25.80.144  prueba.borja #qmaster
   172.25.80.140  clienteprueba1 #qclient

```

I dont know what to do. Any help? I've restarted de qmaster but still does not working.

---

