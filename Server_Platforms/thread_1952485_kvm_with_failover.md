---
title: "kvm with failover"
date: 2012-04-04
forum: Server Platforms
---

### Post by mutrax on 2012-04-04
Hi all,

I've been trying to wrap my head around this the last few days.

I've got a small upcoming project where 2 physical servers need to be deployed my initial thoughts where;

physical server A 
============
active kvm guest 1 
dormand kvm guest 2 (synced)
daily document snapshots of kvm guest 1 (cron, zipping and sending over from B2)

physical server B
============ 
dormand kvm guest 1 
active kvm guest 2
daily document snapshots of kvm guest 1 (cron, zipping and sending over from A1)


The setting up of kvm machines , services , backup crons, i can do. But the syncing the vm's when server A , B or the guest fails, I'm clueless.

I could do it as simple as sending the qcow2 image over the 1000Gbit line envry night and creating manual starts for the backupmachines via webmin buttons (so unexperienced people can start the failover). But sending a +/- 500Gb disc image over the small home network (2x) daily seems a bit overkill?
or keeping backupguest alive and doing an rsync within them?
or cluster?
or lvm snapshots (unexperienced with lvm, :rolleyes:)
or virsh "migrate" from one host to the other?

For those who might be intrested;
1; 12.04, dovecot/postfix/fetchmail mail, webmin admin, samba, sogo ggroupware (hope v2 ifs final by then)
2; 12.04, webmin, samba, upnp (mediatomb), dlna??


tl;dr , how do you keep a kvm vm in sync for failover purposes?

---

### Post by Dangertux on 2012-04-04
You might consider clustering this in an active / passive fashion.

You could use pacemaker or red hat cluster suite (it's in the repos) to do this.

I also think your VM's need to be shared storage, you will probably also need shared storage (gfs for both) for the quorom disk since it's a 2 node cluster.

Hope this helps.

---

### Post by rubylaser on 2012-04-04
Personally, I'd be doing this with [Proxmox VE]("http://pve.proxmox.com/wiki/Main_Page").  It's Debian based, uses KVM and OpenVZ and has a nice WebGUI to manage it.  Here's it's section about a [HA Cluster]("http://pve.proxmox.com/wiki/High_Availability_Cluster").

---

### Post by mutrax on 2012-04-05
> **rubylaser said:**
> Personally, I'd be doing this with [Proxmox VE]("http://pve.proxmox.com/wiki/Main_Page").  It's Debian based, uses KVM and OpenVZ and has a nice WebGUI to manage it.  Here's it's section about a [HA Cluster]("http://pve.proxmox.com/wiki/High_Availability_Cluster").

Hey, picked that name up here and there. Will surely look into that! thank you.


I was wondering if installing the machine on the second host, 
modifiening the xml for a differnd mac ( static dhcp leases determined by mac)
modifying /etc/udev/rules.d/70-persistent-net.rules and /Etc/hostname,
booting the backup machine at night and doing a rsync (exclude the two files mentioned above)
Would work to, if the proxmox doesn't work out... not 1/1 failover, but manageable atm.

btw, is proxmox open and fully useful for the free version?

---

### Post by rubylaser on 2012-04-05
> **mutrax said:**
> Hey, picked that name up here and there. Will surely look into that! thank you.


I was wondering if installing the machine on the second host, 
modifiening the xml for a differnd mac ( static dhcp leases determined by mac)
modifying /etc/udev/rules.d/70-persistent-net.rules and /Etc/hostname,
booting the backup machine at night and doing a rsync (exclude the two files mentioned above)
Would work to, if the proxmox doesn't work out... not 1/1 failover, but manageable atm.

btw, is proxmox open and fully useful for the free version?

Yes, Proxmox is Open Source and Free, it's based on free software.  There is no charge for using it, and their forums are very helpful.  

I'd at least be looking into shared storage, otherwise, you might as well just take a LVM snapshot of the machine nightly and restore from that, it'd be easier than having to edit config files if the machine ever goes down.

---

### Post by mutrax on 2012-04-05
Hey, thanks rubylaser for the heads up. As far as I can read proxmox is a great solution... but building a ha cluster with only two nodes looks tricky. The setup is not in a data center, but a soho enviroment, where a short network interruption (out of stupidity or something else) is not very unlikely. The hassle needed with the split brain dosn't measure up to the comfort of instant fallback.

I'll be looking in to it more, but I guess intermediate backup (sleep->compress->wakeup->send to other server), drbd on vm's physical partition or even timed rsync is more intresting with only two nodes. If one dies, you could wake the other one via a hartbeat signal or a simple web ui. Right? thoughts?

Anyways, thank you all for the pointers in the right direction. All extra input from now on welcome.

---

### Post by rubylaser on 2012-04-05
I would agree that in a home environment, that amount of work to setup a fencing device is probably not worth it.  Personally, I like the shared storage route (can even be an NFS share if you'd like) makes migration much easier.  [Nesting LVM]("http://pve.proxmox.com/wiki/DRBD") on top of DRDB is probably the most robust method. Although, DRDB can suffer from split brain as well.  

Personally, for home use I'd just build (2) Proxmox frontends, set them up in a cluster (very easy to do), and setup a backup job to take an LVM snapshot however often you'd like (every 3/6/12 hours) to a separate backup volume, so if you have a problem, you can just restore to the other host and fire it up. Or, you could go further and setup Heartbeat.

---

### Post by mutrax on 2012-04-09
> **rubylaser said:**
> <snip!>

Personally, for home use I'd just build (2) Proxmox frontends, set them up in a cluster (very easy to do), and setup a backup job to take an LVM snapshot however often you'd like (every 3/6/12 hours) to a separate backup volume, so if you have a problem, you can just restore to the other host and fire it up. Or, you could go further and setup Heartbeat.

willdo, guess it's a healthy point to start from.

---

