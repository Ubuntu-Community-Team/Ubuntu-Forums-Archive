---
title: "Using NIS and NFS to mount only certain directories to certain clients"
date: 2013-07-05
forum: Server Platforms
---

### Post by onebasilikum on 2013-07-05
I'm working with a small to medium sized LAN and we have several servers and clients and using one NIS server to serve automount information to all the machines. So, some servers export certain directories and those directories get automounted everywhere. It all works really well but I'm reaching a point where I really would like to be able to control what directories get mounted on what machine. I can do this of course by editing the file /etc/exports and providing a netgroup or a stricter IP range. But then there will still be an empty directory that gets mounted on every machine and that overrides already existing directories.

So here is my (simplyfied) setup so far:

/etc/auto.master (on NIS server)

```
/home                  auto.home
/project                auto.project
/usr/local/apps      auto.apps         #I want this happening only on certain clients
```

/etc/auto.apps (on NIS server)

```
appXY        -wsize=8192,rsize=8192,proto=tcp host1:/usr/local/appXY
```

/etc/exports (on host1)

```
/usr/local     @myAppGroup(fsid=0,ro,no_root_squash,async,no_subtree_check)

```

/etc/auto.master (on every client)

```
+auto.master
```

Now, the content of appXY will only be mounted on machines in myAppGroup. The proplem is that /usr/local/apps will be mounted everywhere and I can't have a local directory /usr/local/apps on one of the other machines, because it will get overmounted. I already read about a solution that suggested to edit the /etc/auto.master on the client machines so that overmounting doesn't happen. But this would require to make edits on every single client. 

So is there a way to achieve this directly on the NIS server?

---

### Post by TheFu on 2013-07-05
TL;DR ... sorry, I haven't used NIS since 1998.  These days when I have a complex configuration management question, the answer is usually to have a CM system that controls and mandates certain configurations for each server.  Puppet and chef are the common answers for that, but swapping 1 nightmare for another seems like a bad idea to me.  **Ansible** is a similar tool, but much, much easier to understand and get a handle over.  In 15 min, it is possible to have a central ansible box managing simple settings on 2-50 other machines.  The only requirement for clients is python and ssh.  These are part of base installs most places.

BTW, I stopped using NIS due to security concerns. I hope you really mean that you are using NIS+, not pure NIS.  Also, I hope your NFS uses certs, not just IP-based filtering.

---

### Post by onebasilikum on 2013-07-05
OK thanks. I'll have a look at ansible. The thing is that our system runs since always with NIS and I just recently started working there and don't have a lot of experience with either NIS or other similar tools. But yeah, maybe it would be worth it to take a look at some alternatives.

---

