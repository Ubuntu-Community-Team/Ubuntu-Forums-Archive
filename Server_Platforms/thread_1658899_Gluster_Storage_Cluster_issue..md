---
title: "Gluster Storage Cluster issue."
date: 2011-01-03
forum: Server Platforms
---

### Post by jus71n742 on 2011-01-03
I am trying to learn some about clustering and network administration.  Once I understand this better I will transfer the skills learned to a web cluster I am planning on using for testing/learning purposes.  
Here is the current set up:

IBM T42 laptop (lucid desktop) 40GB
HP dc5100 (Lucid 32-bit server) 80 GB x4

Since I have permission to work on this at work with old equipment so long as I don't plug into the wired network I have the wireless shared from the T42 to the other 4 HP desktops.  

I also followed this tutorial on building the high availability storage cluster.
[http://www.howtoforge.com/high-availability-storage-cluster-with-glusterfs-on-ubuntu-p2](http://www.howtoforge.com/high-availability-storage-cluster-with-glusterfs-on-ubuntu-p2)

When I finish and run
```

glusterfs -f /etc/glusterfs/glusterfs-client.vol /mnt/glusterfs 

```

and the desktops will give the error:
> 
glusterfs -f /etc/glusterfs/glusterfs-client.vol /mnt/glusterfs/
Volume 'unify', line 70: type 'cluster/unify' is not valid or not found on this machine
error in parsing volume file /etc/glusterfs/glusterfs-client.vol
exiting


The IBM mounts just fine.  So what have I done wrong on the desktops?

here are the config files
> 
# file /etc/glusterfs/glusterfs-client.vol 
### Add client feature and attach remote subvolume of server1
volume brick1
        type protocol/client
        option tansport-type tcp/client
        option remote-host xx.xx.xx.xx
        option remote-subvolume brick
end-volume

### Add client feature and attach remote subvolume of server2
volume brick2
        type protocol/client
        option tansport-type tcp/client
        option remote-host xx.xx.xx.xx
        option remote-subvolume brick
end-volume

### Add client feature and attach remote subvolume of server3
volume brick3
        type protocol/client
        option tansport-type tcp/client
        option remote-host xx.xx.xx.xx
        option remote-subvolume brick
end-volume

### Add client feature and attach remote subvolume of server4
volume brick4
        type protocol/client
        option tansport-type tcp/client
        option remote-host xx.xx.xx.xx
        option remote-subvolume brick
end-volume
volume brick5
        type protocol/client
        option transport-type tcp/client
        option remote-host xx.xx.xx.xx
        option remote-subvolume brick
end-volume

### Add client feature and attach remote subvolume of server1
volume brick1-ns
        type protocol/client
        option tansport-type tcp/client
        option remote-host xx.xx.xx.xx
        option remote-subvolume brick-ns
end-volume

### Add client feature and attach remote subvolume of server2
volume brick2-ns
        type protocol/client
        option tansport-type tcp/client
        option remote-host xx.xx.xx.xx
        option remote-subvolume brick-ns
end-volume
volume afr1
        type cluster/afr
        subvolumes brick1 brick4
end-volume
volume afr2
        type cluster/afr
        subvolumes brick2 brick3
end-volume
volume afr-ns
        type cluster/afr
        subvolumes brick1-ns brick2-ns
end-volume

volume unify
        type cluster/unify
        option scheduler rr # round robin
        option namespace afr-ns
        subvolumes afr1 afr2
end-volume

And
> 
#file: /etc/glusterfs/glusterfs-server.vol

volume posix
        type storage/posix
        option directory /data/export
end-volume

volume locks
        type features/locks
        subvolumes posix
end-volume

volume brick
        type performance/io-threads
        option thread-count 8
        subvolumes locks
end-volume

volume posix-ns
        type storage/posix
        option directory /data/export-ns
end-volume

volume locks-ns
        type features/locks
        subvolumes posix-ns
end-volume

volume bricks-ns
        type performance/io-threads
        option thread-count 8
        subvolumes locks-ns
end-volume

volume server
        type protocol/server
        option transport-type tcp
        option auth.addr.brick.allow *
        option auth.addr.brick-ns.allow *
        subvolumes brick brick-ns
end-volume        

any other needed information just let me know and I will get it up.

---

### Post by lukeiamyourfather on 2011-01-03
Do you have FUSE and GlusterFS installed on the desktops? You might have better luck with a GlusterFS specific forum or mailing list. When I was working with GlusterFS about a year ago there was a very kind and knowledgeable developer by the name of Harshavardhana who helped me tremendously, though not sure if he is still with the project?

---

### Post by jus71n742 on 2011-01-03
> **lukeiamyourfather said:**
> Do you have FUSE and GlusterFS installed on the desktops? You might have better luck with a GlusterFS specific forum or mailing list. When I was working with GlusterFS about a year ago there was a very kind and knowledgeable developer by the name of Harshavardhana who helped me tremendously, though not sure if he is still with the project?

I will look into it and share here what I find.
Yes I have all the same packages installed on all 5 machines.  I used SSH into each of them and did each step on each machine necessary as I went.

---

### Post by hagarth on 2011-01-03
> **jus71n742 said:**
> 
When I finish and run
```

glusterfs -f /etc/glusterfs/glusterfs-client.vol /mnt/glusterfs 

```and the desktops will give the error:


The IBM mounts just fine.  So what have I done wrong on the desktops?



Are you using the same version of glusterfs on both laptop and the desktops? cluster/unify is deprecated in glusterfs 3.0.x and hence this error is seen.

---

### Post by jus71n742 on 2011-01-04
> **hagarth said:**
> Are you using the same version of glusterfs on both laptop and the desktops? cluster/unify is deprecated in glusterfs 3.0.x and hence this error is seen.

Ahh, I am using the latest release.  So what has replaced cluster/unify?

---

### Post by hagarth on 2011-01-04
> **jus71n742 said:**
> Ahh, I am using the latest release.  So what has replaced cluster/unify?

testing/cluster/unify replaces cluster/unify in newer versions.

However with newer versions, using cluster/distribute is recommended and usage of testing/cluster/unify is deprecated.

---

### Post by jus71n742 on 2011-01-07
Finally got to work on it some and that was the issue.  right at the bottom of the client.vol file.

Thanks

---

### Post by boomertsfx on 2011-02-01
> **jus71n742 said:**
> Finally got to work on it some and that was the issue.  right at the bottom of the client.vol file.

Thanks

You're not supposed to use client vol files anymore (in 3.1).  All you need is the glusterfsd.vol and you should be set.

[http://gluster.org/pipermail/gluster-users/2010-November/005668.html](http://gluster.org/pipermail/gluster-users/2010-November/005668.html)

---

