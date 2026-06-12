---
title: "Nautilus is very slow to launch"
date: 2020-09-04
forum: Ubuntu/Debian BASED
---

### Post by Jerrac on 2020-09-04
Hey all,

For some reason, Nautilus is extremely slow to launch. It takes about a minute from clicking the icon, or hitting enter on the command line, before the window shows up. I've also seen slowness when launching file save dialogs.

I've found a few posts on the internet talking about NFS mounts slowing things down. Usually in relation to Tracker. I do have a NAS, and I use autofs to mount some NFS shares. But if I disable autofs and unmount my shares, Nautilus is still slow to start.

Here is what I see in syslog between when hit enter on the command line to start nautilus, and when the nautilus window finally shows up:

```
Sep  4 18:18:41 localhost dnsmasq-dhcp[2067]: DHCPREQUEST(virbr0) <windows 10 vm v4 ip> <windows 10 vm mac> 
Sep  4 18:18:41 localhost dnsmasq-dhcp[2067]: DHCPACK(virbr0) <windows 10 vm v4 ip> <windows 10 vm mac> win10-nessa
Sep  4 18:18:47 localhost systemd[1944]: home-myusername-shares-downloads.mount: Succeeded.
Sep  4 18:18:47 localhost systemd[4222]: home-myusername-shares-downloads.mount: Succeeded.
Sep  4 18:18:47 localhost systemd[1]: home-myusername-shares-downloads.mount: Succeeded.
Sep  4 18:18:47 localhost dbus-daemon[4247]: [session uid=1000 pid=4247] Activating via systemd: service name='org.freedesktop.Tracker1' unit='tracker-store.service' requested by ':1.1' (uid=1000 pid=4238 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
Sep  4 18:18:47 localhost systemd[4222]: Starting Tracker metadata database store and lookup manager...
Sep  4 18:18:47 localhost dbus-daemon[4247]: [session uid=1000 pid=4247] Successfully activated service 'org.freedesktop.Tracker1'
Sep  4 18:18:47 localhost systemd[4222]: Started Tracker metadata database store and lookup manager.
Sep  4 18:19:15 localhost dbus-daemon[1371]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.888' (uid=1000 pid=2175744 comm="nautilus " label="unconfined")
Sep  4 18:19:15 localhost systemd[1]: Starting Hostname Service...
Sep  4 18:19:15 localhost dbus-daemon[1371]: [system] Successfully activated service 'org.freedesktop.hostname1'
Sep  4 18:19:15 localhost systemd[1]: Started Hostname Service.
Sep  4 18:19:17 localhost tracker-store[2175888]: OK
Sep  4 18:19:17 localhost systemd[4222]: tracker-store.service: Succeeded.
```


I'm 90% sure the dnsmasq lines have nothing to do with this.

I'm at a bit of a loss where the "home-myusername-shares-downloads.mount" comes from. I have that configured in autofs, but the other mounts in autofs don't show up like that. I know systemd has some automount stuff in it, but I've never configured it. 

The final odd thing I've noticed is that Nautilus lists each of my mounts in the left hand column twice. A) Why does Nautilus list them in the first place? They are managed by autofs, not Nautilus, so I'd expect Nautilus to treat them as normal folders. B) Listing them twice?? 

Thanks in advance!

My system:
[LIST]
[*]OS: Pop_OS! 20.04
[*]Nautilus Version: 3.36.3-stable
[*]OS Drive: Intel 660p nvme
[*]NAS: Virtualized FreeNAS
[*]NAS Nic: VirtIO, so 10gig I believe
[/LIST]

Edit:

I've been tailing syslog for a while now. the systemd lines about the .mount and tracker stuff keep showing up over and over again. About every minute or two. Same with the dbus-daemon, and tracker-store lines. So those lines are not triggered by starting Nautilus. Hm...

---

### Post by ajgreeny on 2020-09-05
*Thread moved to **Ubuntu/Debian BASED**.* which is more appropriate and a better fit.

Pop_OS is based on but is not a Ubuntu system so many things may be different from Ubuntu.

---

