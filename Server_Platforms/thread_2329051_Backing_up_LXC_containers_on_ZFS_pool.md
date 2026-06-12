---
title: "Backing up LXC containers on ZFS pool"
date: 2016-06-27
forum: Server Platforms
---

### Post by Darren_Landrum on 2016-06-27
First, a little background. I have a server that is a dedicated container server, which is currently running two containers (a database server and an apps server). When I set up LXD, I made a 1.2TB ZFS pool, then went through the rest of the setup, and now my two containers are in production, despite my being new to LXC/LXD, and especially ZFS.

I came into this with no experience with ZFS, and little when it comes to LXC (I'm an experienced admin otherwise), but I'm a big believer in pushing myself beyond my comfort zone in order to learn new skills. Unfortunately, I might have bitten off more than I can handle. I am now faced with how to backup and restore containers.

The snapshot function is great, and will be useful for rolling back containers as needed. However, I really need to figure out an off-site backup for containers for disaster recovery, like if I have to restore a container to a completely different server if this one is suddenly destroyed. I've been reading up on ZFS, but right now, I'm still making sense of its capabilities. I can't help but think I should have just stuck with directory containers.

Any help would be greatly appreciated. Thank you!

---

### Post by MAFoElffen on 2016-06-27
So you are already doing ZFS snap shots and incremental right? Then if just snapshots
```

zfs send zpool-name/filesystem-name@snapshot-name > dump-file-name  # the target file will contain the entire ZFS file system: files and all the metadata. 

```
If with incrementals, there is an -i option for incremental with send to send an incremental difference of snapshots. caveot is that the source snapshot has to exist.

Re: [https://docs.oracle.com/cd/E18752_01/html/819-5461/gbchx.html](https://docs.oracle.com/cd/E18752_01/html/819-5461/gbchx.html)

---

### Post by Darren_Landrum on 2016-06-27
Thank you for the reply. I was referring to the LXC snapshot function, which I am using, but it just saves the snapshots locally on the server. I need to get them off the server to somewhere else that can and probably will have a different filesystem. It's definitely looking like exploring the ZFS tools is what I need.

I wish I could have gotten LXD to make one ZFS pool per server container. It seems to want to have only one per host machine.

---

### Post by MAFoElffen on 2016-06-27
With Xen Server, you define your LVM or ZFS Pool. Then you do pre-define an LVM VG Group or ZFS zvol for a new domain. Then point the creation of that domain to the path of the new storage container... Logically, you can say were a LXC template image will reside right? Would be the same logic.

Or since most LXC containers are instances of templates, ZFS snapshots of the LXC snapshots(?) Or are you doing/saving to persistent images?

---

### Post by Darren_Landrum on 2016-06-27
AHA! I might have this figured out.

I can actually see the snapshot of the container I made (on my smaller test server) using zfs list -t snapshot. So, I should be able to use zfs send to serialize and gzip it, then use zfs receive to restore it. Hopefully. It gives me something to play with anyway. Thank you for your help.

---

### Post by MAFoElffen on 2016-06-27
You are very welcome.

Please tell us how it goes ... and when solved, mark the thread as solved. (Upper right of page, "Thread Tools" > "Mark Thread as Solved") that will help others to find answers to their similar questions.

---

### Post by Darren_Landrum on 2016-06-29
Just to give an update... I'm still trying to figure out how to restore a snapshot. So far, it's been a huge headache figuring out how to do container backups using this method. I've even managed to screw up the ZFS pool on my test server to the point that I needed to re-load the OS. (Yes, I'm doing all this on a test server, for these reasons.)

Honestly, the one method that I had success with both backup and recovery was just stopping the container, going into /var/lib/lxd/containers, and tarring and gzipping the container I want (with the --numeric-owner option). I'll experiment with this more. It would've been nice to have a method that would work without stopping the container, but this is not an uptime-critical system, and can live with five minutes of downtime a week.

---

### Post by MAFoElffen on 2016-06-29
(i mostly support the Virtualization Section, and teetered on moving this to that section for better exposure ... but felt with ZFS and backiups, is was more server related).

Not sure how you could restore live/hot, because of exclusive file locks, and things not being exactly the same, but... I have an idea. You could always shorten the time it is down...

What if you restore to a temp directory in the filesystem, then stop/destroy ... then move the restored image into the image directory (much faster because it is just a rename of the node), then bring it up... you would just be down about 5-15 seconds, plus the time to boot.

And if you would write yourself a script to take the container name (as a parameter) to automatic the move, you could shorten the time to type the commands.

---

### Post by Darren_Landrum on 2016-06-30
I found a method that works. Basically:

To backup: Stop container, tar/gzip /var/lib/lxd/containers/container.zfs/* (with --numeric-owner option), save it somewhere.
To restore: Create new container with same name, delete everything in .../lxd/containers/container.zfs/*, restore files from tar file, start container.

I did these steps several times with different containers across two separate servers with different hardware, and it worked every time.

I'll mark this thread as solved. Thank you!

---

### Post by Darren_Landrum on 2016-06-30
To clarify something: the key for me is that I really needed a file that I could drop on another server that could have any file system. We have servers that have automatic off-site backup for exactly this sort of thing. I was able to make a file from a snapshot using the ZFS tools, but I could not figure out for the life of me how to restore that file back to a working container.

---

### Post by MAFoElffen on 2016-07-01
Glad it all worked out for you.

---

### Post by Darren_Landrum on 2016-07-01
Thanks! Well, I got something to work, anyway.

I'll tell you, some times I feel like a power user, and other times, I feel like a complete newb. Thank you for your help!

---

### Post by votsalo on 2016-08-17
Why not export the container as an image, export the image to a tarball, and save that?  That way you'd work within LXD tools, independently of zfs:

lxc publish <my-container> --alias=<my-container-image>
lxc image export <my-image>

You'd need to stop the container in order to publish an image.  Then restart it.  There is a --force option that does this for you, but I did it manually.
The resulting tarball has the name of its hash, instead of the image name.

If you enable remote access of LXD, you can perhaps copy the image directly between two LXD machines, without exporing it.  Or publish the image directly to/from another LXD daemon.  Or copy the container without creating an image.  I haven't tried this.  Creating a tarball image seems simpler and more versatile for backup (you can just treat it as a file).

To restore the container from the tarball:
lxc image import <tarball> --alias=<my-image>
lxc launch <my-image> <my-container>

I have tried this, and it worked (on the same machine, after deleting the original container and image).
I also use zfs, and I was surprised that lxc publish took a long time.  I thought it mostly copied the container, which should be very fast with zfs.

---

