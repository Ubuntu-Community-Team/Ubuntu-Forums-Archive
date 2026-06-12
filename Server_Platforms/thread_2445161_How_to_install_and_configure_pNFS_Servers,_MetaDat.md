---
title: "How to install and configure pNFS Servers, MetaData Servers, and clients on Ubuntu 20"
date: 2020-06-10
forum: Server Platforms
---

### Post by iamjahandideh on 2020-06-10
[COLOR=#242729][FONT=Arial]Does Ubuntu20.04 support pNFS Server(Data and MetaData) and Client side of pNFS?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]If YES, Then How to install and configure it? Is there any comprehensive guide?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How to install and configure pNFS Servers, MetaData Servers, and clients on Ubuntu 20.04?[/FONT][/COLOR]

---

### Post by LHammonds on 2020-06-10
From what I have read, kernel 4.12+ has supported pNFS which means Ubuntu 18.04 and higher.  NFS protocol 4.1 was the version that had built-in support for pNFS.

I have not done this before but from what I am seeing, there is not a flexible way of setting this up regarding redundancy and scalability.

[https://askubuntu.com/questions/1121663/how-to-configure-the-data-servers-for-a-pnfs-metadata-server](https://askubuntu.com/questions/1121663/how-to-configure-the-data-servers-for-a-pnfs-metadata-server)

I also have not see ANYTHING "comprehensive" regarding this subject.  There are some bits and pieces about setting it up but nowhere have I found someone step thru the entire process and then proceed to show any test results showing how it is any better than a standard NFS design...which has many comprehensive setup guides.

LHammonds

---

### Post by TheFu on 2020-06-10
NFS is a standard protocol.  Any clients and servers which provide the standard are supported.
NFSv4 and NFSv3 are both working on 20.04.  I have a 20.04 desktop that uses NFSv4 to access storage on a 16.04 Server.

[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs)
On the client-mount options, I disagree with including rsize and wsize settings. The NFS client and server will negotiate the best parameters automatically.

---

### Post by LHammonds on 2020-06-10
> **TheFu said:**
> The NFS client and server will negotiate the best parameters automatically.Are you saying the default install of NFS with default export parameters will use Parallel NFS without specifying it???

Here is an article from 2008 about Parallel NFS (pNFS): [https://www.ibm.com/developerworks/library/l-pnfs/index.html](https://www.ibm.com/developerworks/library/l-pnfs/index.html)

LHammonds

---

### Post by TheFu on 2020-06-10
My mistake - when I saw pNFS - I immediately thought that was a typo for **pcNFS**. Sorry for my confusion. Thanks for the link. No great insights from me. Just stuff everyone else can find.

Here's the Ubuntu 20.04 manpage for pNFS : [http://manpages.ubuntu.com/manpages/focal/man4/pnfs.4freebsd.html](http://manpages.ubuntu.com/manpages/focal/man4/pnfs.4freebsd.html) The manpage warns about bugs in kernels BEFORE v4.17-rc2 causing crashes.  Looks like a port from the BSD implementation.  20.04 default kernel is 5.4.x.

pNFS servers are supposed to be backwards compatible with NFSv4 clients according to the manpage. They should just negotiate the protocol down.  The client-side mount options do have some specific requirements.

My rsize and wsize parameter comment was for NFSv4 mounts.  I've tested this. So has another long-time poster here and we saw different results and better performance than specifying the common values all the internet articles say to use.

---

