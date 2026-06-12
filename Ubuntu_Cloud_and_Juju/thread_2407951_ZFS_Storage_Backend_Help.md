---
title: "ZFS Storage Backend Help"
date: 2018-12-11
forum: Ubuntu Cloud and Juju
---

### Post by quartzeye on 2018-12-11
I have been looking for an answer to my problem and just have not found one.

The config I have is the following.  I have a single 20TB raid 60 storage server.  I have a separate 4 blade C6100 server.  Each blade in the C6100 has a single 120GB SSD boot disk, a dedicated 40GB infiniband connection to the storage server, and a 40GB shared infiniband subnet. I want to mount a dedicated directory from the storage server to each blade for all non-OS storage.  Using NFS, I can do all this with out issue.

The problem is, I want to run OpenStack-on-LXD across the the 4 blades so that I can run containerized VM's and pure containers. All good except the storage back-end for LXD.  I could use the directory back-end option, and that may be my only real option, but I prefer to use ZFS.  I cannot find anything that talks to using network attached storage as the basis for ZFS.

First, I cannot determine if it would be correct to have each blade host it's on ZFS pool, or should I have one ZFS pool on the storage server and access via the network.  I know with a directory approach, each blade would have to have it's own dedicated mounted directory from the storage server.

I am at a road block trying to figure out how to use ZFS and LXD on the 4 blade c6100 so that I can run OpenStack and use the entire cluster as a unified OpenStack environment.  This type of architecture is talked about a lot but in broad strokes and I have not found any real detailed discussions on implementing it. Any guidance would be appreciated.

---

