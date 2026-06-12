---
title: "Two-way mirroring of Web Servers Sites"
date: 2007-07-11
forum: Server Platforms
---

### Post by JCorrea920 on 2007-07-11
I have a Load Balanced High-Availability Web Cluster with 3 nodes. Therefore all 3 nodes must have the identical websites otherwise there will be inconsitencies with what appears on the browser with each http request. To keep the web sites consitent on all web servers I originally used rsync in a circular loop which caused many problems when files were created, deleted, or modified on a particular web server node. As you can imagine some changes were overwritten since rsync is one-way mirroring software. To make matters worse in order to get rsync to run automatically I had set up cronjobs to run every 5 minutes. Can you imagine someone uploading a file to one of these nodes and having to wait up to 10 minutes for them to replicate to the other nodes, and that is if it wasn't overwritten/deleted by the rsync process itself.

So I started to experiment with Unison. It achieves the two-way mirroring I need, but not the continuos part. It has a --repeat option that can be used for continuos replication but it does not operate in the background so it locks up your terminal window, for servers that have no GUI installed and administered remotely would eventually have the problem that the connection will time out not to mention the security risk of leaving a remote terminal window open (CTRL-C breaks the command and grants access to the shell :shock: ).

As a small band-aid solution I have created cronjobs to run unison on one of the nodes as it syncs with the other two every minute (Hub and Spoke topology as recommended by Unison docs). But still changes may take as long as 2 minutes to propagate to all nodes. Recently Unison has cease to exist in development and there is no support for it. :mad:

What I need is continuos two-way mirroring for these three nodes so that files on the websites are consitently the same. Either a daemon or background process that can achieve this will be greatly helpful. I was looking into Pavuk but the commands are horribly long and when I sent a message on their mailing list about it having two-way mirroring capabilities I received no reply, after 3 weeks!

All machines (3 nodes + 2 load-balancers):

Ubuntu 6.06 Server (no X-Windows/GUI)
Apache 2
Mysql 5
Php 5

Any suggestions or help would be greatly appreciated. Thanks for your support.

Jorge

---

### Post by rickyjones on 2007-07-11
I'm no expert in clustering or anything of the sort, but it seems like this could be solved by having shared disk between all the servers. Perhaps a fourth fileserver that serves NFS mounts to the servers? Then each server is pointed to the same disk - any changes will be available immediately to all servers.

Hope it helps!

-Richard

---

