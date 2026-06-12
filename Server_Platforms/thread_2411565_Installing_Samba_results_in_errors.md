---
title: "Installing Samba results in errors"
date: 2019-01-31
forum: Server Platforms
---

### Post by espressobeanmachine on 2019-01-31
I have Ubuntu 18.04 running on baremetal and I am using it as an LXD host. One of the LXD containers I am using Ubuntu 18.04 image and want to install Samba server. This is a clean install with nothing else on it. I am hitting weird errors during the installation:

```
Setting up samba-libs:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.6) ...
Setting up samba-vfs-modules (2:4.7.6+dfsg~ubuntu-0ubuntu2.6) ...
Setting up python-samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.6) ...
Setting up samba-common-bin (2:4.7.6+dfsg~ubuntu-0ubuntu2.6) ...
Setting up samba-dsdb-modules (2:4.7.6+dfsg~ubuntu-0ubuntu2.6) ...
Setting up samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.6) ...
Samba is not being run as an AD Domain Controller, masking samba-ad-dc.service.
Please ignore the following error about deb-systemd-helper not finding samba-ad-dc.service.
Created symlink /etc/systemd/system/multi-user.target.wants/nmbd.service &#8594; /lib/systemd/system/nmbd.service.
Failed to preset unit: Unit file /etc/systemd/system/samba-ad-dc.service is masked.
/usr/bin/deb-systemd-helper: error: systemctl preset failed on samba-ad-dc.service: No such file or directory
Created symlink /etc/systemd/system/multi-user.target.wants/smbd.service &#8594; /lib/systemd/system/smbd.service.
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for systemd (237-3ubuntu10.11) ...
Processing triggers for ufw (0.35-5) ...

```

running status on the samba service:

```
root@storage:~# systemctl status nmbd
&#9679; nmbd.service - Samba NMB Daemon
   Loaded: loaded (/lib/systemd/system/nmbd.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2019-01-30 15:53:11 UTC; 2min 0s ago
     Docs: man:nmbd(8)
           man:samba(7)
           man:smb.conf(5)
 Main PID: 1430 (nmbd)
   Status: "nmbd: ready to serve connections..."
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/nmbd.service
           &#9492;&#9472;1430 /usr/sbin/nmbd --foreground --no-process-group


Jan 30 15:53:11 storage systemd[1]: Starting Samba NMB Daemon...
Jan 30 15:53:11 storage systemd[1]: Started Samba NMB Daemon.
Jan 30 15:53:11 storage systemd[1]: nmbd.service: Failed to reset devices.list: Operation not permitted
Jan 30 15:53:11 storage systemd[1]: nmbd.service: Failed to reset devices.list: Operation not permitted
Jan 30 15:53:12 storage systemd[1]: nmbd.service: Failed to reset devices.list: Operation not permitted
Jan 30 15:53:12 storage systemd[1]: nmbd.service: Failed to reset devices.list: Operation not permitted
Jan 30 15:53:13 storage systemd[1]: nmbd.service: Failed to reset devices.list: Operation not permitted
root@storage:~# systemctl restart nmbd
root@storage:~# systemctl status nmbd
&#9679; nmbd.service - Samba NMB Daemon
   Loaded: loaded (/lib/systemd/system/nmbd.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2019-01-30 15:55:24 UTC; 7s ago
     Docs: man:nmbd(8)
           man:samba(7)
           man:smb.conf(5)
 Main PID: 1611 (nmbd)
   Status: "nmbd: ready to serve connections..."
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/nmbd.service
           &#9492;&#9472;1611 /usr/sbin/nmbd --foreground --no-process-group


Jan 30 15:55:24 storage systemd[1]: Starting Samba NMB Daemon...
Jan 30 15:55:24 storage systemd[1]: Started Samba NMB Daemon.

```

Why is this happening?

---

