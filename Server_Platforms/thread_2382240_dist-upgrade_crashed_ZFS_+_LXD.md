---
title: "dist-upgrade crashed ZFS + LXD"
date: 2018-01-10
forum: Server Platforms
---

### Post by raceface2nd on 2018-01-10
[EDIT]The reason is that the loop devices that are the zfs pool are not setup on boot. So it's not solved but the reason is found.

I created a upstart conf to setup the loop devices which does not seem to work, maybe anybody has an idea for the reason?
```

[LEFT][COLOR=#222222][FONT=Consolas]start on mounted MOUNTPOINT=/data
task

[/FONT][/COLOR][COLOR=#222222][FONT=Consolas]exec [/FONT][/COLOR][COLOR=#222222][FONT=Consolas]losetup /dev/loop2 /data/lxd/device01.img
exec losetup /dev/loop3 /data/lxd/device02.img
exec losetup /dev/loop4 /data/lxd/device03.img
```[/FONT][/COLOR][/LEFT]

[/EDIT]

Hi,

I am running an ubuntu server with 16.04 and performed a dist-upgrade today. After reboot I recognized that my LXC containers are not running, zpool shows no pools and the network bridges of lxc are gone.

syslog shows me several errors:

**HDPARM**
```
systemd-udevd[481]: Process '/lib/udev/hdparm' failed with exit code 5.
systemd-udevd[478]: Process '/sbin/mdadm --incremental /dev/sdb2 --offroot' failed with exit code 1.
```

**ZFS**
```
zfs-import-cache.service: Main process exited, code=killed, status=6/ABRT
Failed to start Import ZFS pools by cache file.
zfs-import-cache.service: Unit entered failed state.
zfs-import-cache.service: Failed with result 'signal'.
```

**LXD**
```
lxd.service: Main process exited, code=exited, status=1/FAILURE
lxd-containers.service: Start operation timed out. Terminating.
Failed to start LXD - container startup/shutdown.
lxd-containers.service: Unit entered failed state.
lxd-containers.service: Failed with result 'timeout'.
lxd.service: Start-post operation timed out. Stopping.
Failed to start LXD - main daemon.
lxd.service: Unit entered failed state.
lxd.service: Failed with result 'timeout'.
lxd.service: Service hold-off time over, scheduling restart.
Stopped LXD - main daemon.
```

**REDIS**
```
redis-server.service: PID file /var/run/redis/redis-server.pid not readable (yet?) after start-post: No such file or directory
Failed to start Advanced key-value store.
redis-server.service: Unit entered failed state.
redis-server.service: Failed with result 'resources'.
redis-server.service: Service hold-off time over, scheduling restart.
Stopped Advanced key-value store.
```

**SPREED**
```
spreed-webrtc.service: Main process exited, code=exited, status=255/n/a
spreed-webrtc.service: Unit entered failed state.
spreed-webrtc.service: Failed with result 'exit-code'.
spreed-webrtc.service: Service hold-off time over, scheduling restart.
Stopped Spreed WebRTC server.
```

As it looks like systemwide problems I honestly do not know where to start researching the problem. Most urgent would be to get ZFS and LXD/ LXC running again.

I have installed LXC with ZFS in the pool lxd, when I perform zdb -C lxd I get
```
zdb: can't open 'lxd': Value too large for defined data type
```

zdb itself shows me
```
lxd:
    version: 5000
    name: 'lxd'
    state: 0
    txg: 4
    pool_guid: 892745190134463677
    errata: 0
    hostname: 'server1'
    vdev_children: 3
    vdev_tree:
        type: 'root'
        id: 0
        guid: 892745190134463677
        create_txg: 4
        children[0]:
            type: 'disk'
            id: 0
            guid: 17662338607834602496
            path: '/dev/loop2'
            whole_disk: 0
            metaslab_array: 38
            metaslab_shift: 32
            ashift: 9
            asize: 536866193408
            is_log: 0
            create_txg: 4
        children[1]:
            type: 'disk'
            id: 1
            guid: 9365780060088454945
            path: '/dev/loop3'
            whole_disk: 0
            metaslab_array: 36
            metaslab_shift: 32
            ashift: 9
            asize: 536866193408
            is_log: 0
            create_txg: 4
        children[2]:
            type: 'disk'
            id: 2
            guid: 14425449703670450167
            path: '/dev/loop4'
            whole_disk: 0
            metaslab_array: 34
            metaslab_shift: 32
            ashift: 9
            asize: 536866193408
            is_log: 0
            create_txg: 4
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data
```

zdb -C | grep path gives me
```
            path: '/dev/loop2'
            path: '/dev/loop3'
            path: '/dev/loop4'
```

Any help to recover the system is appreciated!

Thx in advance!

Andy

---

### Post by darkod on 2018-01-11
I haven't used lxd but if I'm not mistaken that is used to work with containers. And if i understand your post correctly, the zfs is inside lxd, no?

If that is the case, I have one question regarding the design. Shouldn't the zfs be outside the lxd? The basic storage should be the first layer and then on top of it comes the virtualization/containers.

---

### Post by raceface2nd on 2018-01-11
Hi,


ZFS is outside LXD. I found the reason why it's not working but I didn't find a solution. . .


I have 3 image files that should be mounted to /dev/loop2 /dev/loop3 and /dev/loop4. I need to mount them after a specific mountpoint in fstab is mounted. To have them ready for ZFS they need to be mounted directly after the other mountpoint.


So I created a upstart script, which seems not to be run
```
description     "Setup loop devices after filesystems are mounted"
start on mounted MOUNTPOINT=/data
task
exec losetup /dev/loop2 /data/lxd/device01.img
exec losetup /dev/loop3 /data/lxd/device02.img
exec losetup /dev/loop4 /data/lxd/device03.img

```When I try to run this script manually with service losetup start I get
```
Failed to start losetup.service: Unit losetup.service not found.

```When I try to update the upstart config with initctl reload-configuration I get the following error
```
Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
```
When I try to mount the loopback devices in fstab the system doesn't boot. In fstab I tried
```
/data/lxd/device01.img /dev/loop2 auto loop,defaults 0 0
```

That's kind of weird.

Andy

---

