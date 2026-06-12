---
title: "Configuring LXD Daemon without interactive menu?"
date: 2016-06-30
forum: Virtualisation
---

### Post by schachte1 on 2016-06-30
I'm trying to configure the LXD daemon without going through the interactive display because it's going to be automated. I've tried sudo dpkg-reconfigure debconf and selected nonteractive, but the screen still comes up. I'm also curious as to how I would feed these values into the config. Is there a file I can generate and move somewhere? Just looking for different options. Thanks

---

### Post by MAFoElffen on 2016-07-01
Are you trying to configure the Server LXD Daemon or the goblal config default for containers?


Since you said the "LXD daemon," so... you can set the damon's option by using the LXC tool from the CLI, by key/vales:
```

lxc config set <key> <value>

```
The LXC daemon has about 18 keys that that you can set values of, These are the key names that you can set for the daemon.
```

core.https_address, core.https_allowed_origin, core.https_allowed_methods, 
core.https_allowed_headers, core.proxy_https, core.proxy_http, 
core.proxy_ignore_hosts, core.trust_password, storage.lvm_vg_name	string, 
storage.lvm_thinpool_name, storage.lvm_fstype, storage.lvm_volume_size,
storage.zfs_pool_name, storage.zfs_remove_snapshots, images.compression_algorithm
images.remote_cache_expiry, images.auto_update_interval, images.auto_update_cached

```
The LXC tool has key/value validation. There are files that can be edited... but the preferred method is to use the LXC tool so that someone doesn't inadvertently break the system.

Beyond that, then have have container configuration and  device configuration. All the keys / values pairs are documents fairly well up at github / LXC, LXD. For containers and devices, you can set up saved profiles and apply multiple profiles to a container.

If that the info your were asking about?

---

