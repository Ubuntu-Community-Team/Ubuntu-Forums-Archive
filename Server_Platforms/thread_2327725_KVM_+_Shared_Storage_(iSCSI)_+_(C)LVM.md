---
title: "KVM + Shared Storage (iSCSI) + (C)LVM"
date: 2016-06-13
forum: Server Platforms
---

### Post by FiVAL on 2016-06-13
Hi All,

I am experimenting with a new setup, but somehow I can not find good documentation for the Ubuntu platform. And
this makes me also question myself if my goal is somehow wrong / old fashion or not "meant to be" on a Ubuntu Server.

First of all, I have a lot of experience with 'stand-alone' KVM (Ubuntu) servers where the VMs have there own local storage-pool
by a LVM Volume-Group and each VM there own LV. A basic setup and I guess most of you also have some experience with this.

But now I want to build 'bigger' on this concept and add shared-storage to these KVM Servers (Ubuntu Server 16.04) by mounting
by multi-path to a shared-LUN of an iSCSI SAN. Make on this LUN a LVM-Volume group so I can give the VMs there own LV
(logical volume) within this storage-pool, with access from all the (hardware) servers, so I can migrate the VM live to other hardware
and have all the features a LVM has.

Installing Ubuntu, network configurations, KVM/QEMU, iSCSI connections, multi-path and LVM are no issue for me.
I am familiar with the theoretical concept of shared storage, locking, cluster of hardware, heartbeats, etc...

But I can not figure out how to configure this on a Ubuntu Server. Most How-To's on the Internet are for RedHat and CentOs. The basics
are the same but then there are missing packages or missing config files in Ubuntu. Also most of these RedHat papers are about HA
where they also mirroring the (iSCSI) SAN to a second SAN and/or let a manager migrate the VMs automatic between hardware for the
best performance...

I am (first) only looking for good documentation or an example configuration to get Cluster-LVM working over multiple Ubuntu Servers
with a shared storage by an iSCSI-LUN. So I can migrate my VMs manually between the hardware and still use the (C)LVM flexibility.

Is there anyone who can help ?

Kind regards...

---

### Post by MAFoElffen on 2016-06-15
Initially, I was wondering if I should move this to the Virtualization Section, but then thought to not move it.

Reason-- This is more a question about iSCSI/LVM installation/configuration initiator/target question than about KVM storage pools. Once the iSCSI/LVM LU is set up, then pointing the storage pool of the VM's in KVM is a moot point, no matter what distro it is on.

I have not seen missing packages (as you mention), but here is the info I used:
[http://www.rushiagr.com/blog/2014/09/05/iscsi-administration-on-ubuntu-quick-start/](http://www.rushiagr.com/blog/2014/09/05/iscsi-administration-on-ubuntu-quick-start/)
[https://linhost.info/2012/05/configure-ubuntu-to-serve-as-an-iscsi-target/](https://linhost.info/2012/05/configure-ubuntu-to-serve-as-an-iscsi-target/)
[https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)
[https://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target](https://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target)
[http://www.server-world.info/en/note?os=Ubuntu_16.04&p=iscsi](http://www.server-world.info/en/note?os=Ubuntu_16.04&p=iscsi)
[http://www.server-world.info/en/note?os=Ubuntu_16.04&p=iscsi&f=2](http://www.server-world.info/en/note?os=Ubuntu_16.04&p=iscsi&f=2)
[http://www.server-world.info/en/note?os=Ubuntu_14.04&p=iscsi](http://www.server-world.info/en/note?os=Ubuntu_14.04&p=iscsi)
[https://www.berrange.com/posts/2010/05/05/provisioning-kvm-virtual-machines-on-iscsi-the-hard-way-part-2-of-2/](https://www.berrange.com/posts/2010/05/05/provisioning-kvm-virtual-machines-on-iscsi-the-hard-way-part-2-of-2/)
[https://libvirt.org/storage.html](https://libvirt.org/storage.html)

---

### Post by FiVAL on 2016-06-16
Hi MAFoElffen, thanks for your reply.
And I agree, this topic will fit better here, in the Server Section.


But I think you misunderstood the goal of my test-setup.

I want to use a LVM VolumeGroup as Storage Pool in KVM.
Underneath this LVM VG is a Linux LVM Partition on a iSCSI LUN
and LVMd (filtering) can only find this LVM device through the
multipath mapper in /dev/disk/by-id/...

This way KVM doesn't know anything about a iSCSI device!
The OS where KVM is running on handles (only) the iSCSI connections
AND very important also the multiple routes to the LUN (multipath).


This setup is already running on a couple of (hardware) test-servers
with a Dell PowerVault as iSCSI storage device. On these test-servers
I have multiple test-VMs running with KVM. I can do live-migrations
and the performances are very nice!


Only the (big) problem now is the LVM Metadata changes...
...for my current setup I have completely locked this changes for every machine. (readonly)

When I want to add a Logical Volume to a Volume Group I do this all
manually and do a "pvscan --cache; vgscan --cache; lvscan --cache;" on
every other server in the cluster. Also I have to enable this LV on every
server in the cluster with lvchange...


So I am looking for documentation / example configurations / user experience
to use ClusterLVM (CLVM) with Distributed Lock Manager (DLM) and CoroSync...
Or something like this... (This is not completely clear for me...)

---

### Post by MAFoElffen on 2016-06-16
> **FiVAL said:**
> So I am looking for documentation / example configurations / user experience
to use ClusterLVM (CLVM) with Distributed Lock Manager (DLM) and CoroSync...
Or something like this... (This is not completely clear for me...)

Yes, Ubuntu used the same infrastructure as Red Hat and Centos ... using CMAN, Corosync and DLM. So the config file settings should be the same, although with different flavor caveats.

In your /etc/lvm/lvm.conf there is a line in that for locking_type. Default is 1, for local locking. 2 is external. But 3 is for built-in clustered/managed locking. In notes, I see 2 other setting in that files that are affected by that setting-- wait_for_lock and filter.

You are right, I don't see a lot of documentation on that at all. It is sort of all in pieces, with not much on how to get the pieces working together.

---

### Post by FiVAL on 2016-06-16
But the CentOS & RedHat "CMAN" is the "Corosync" for Ubuntu ?

So to be complete, my next step would be to install & configure: clvm corosync dlm ?

Also there is one thing which could very very very important and this would be a fence-agent / fencing.

But is fencing necessary in my setup ?
Cause my guess is, when the configured cluster is incomplete, just lockdown (readonly) LVM metadata write access at all!
In my setup the VMs will keep on running (except the ones running on the missing server) but there is no change on a split-brain configuration.

And my guess would be that CLVM can not write metadata by default when the cluster is incomplete...

---

### Post by MAFoElffen on 2016-06-16
> **FiVAL said:**
> But the CentOS & RedHat "CMAN" is the "Corosync" for Ubuntu ?

So to be complete, my next step would be to install & configure: clvm corosync dlm ?

Also there is one thing which could very very very important and this would be a fence-agent / fencing.

But is fencing necessary in my setup ?
Cause my guess is, when the configured cluster is incomplete, just lockdown (readonly) LVM metadata write access at all!
In my setup the VMs will keep on running (except the ones running on the missing server) but there is no change on a split-brain configuration.

And my guess would be that CLVM can not write metadata by default when the cluster is incomplete...
DLM is the Locking Manager mechanism and works with corosync to handle locking in your cluster (CLVM).

Corosync (itself) synchronizes the metadata between the nodes of the CLVM.

Are you saying you want to stay read-only? Because if you want all your nodes to be "read-only," then you work is almost done. You only need to change one line in your /etc/lvm/lvm.conf file. Look at my snippet here on the lvm.conf file:
```

# Type of locking to use. Defaults to local file-based 
# locking (1).
# Turn locking off by setting to 0 (dangerous: risks metadata 
# corruption if LVM2 commands get run concurrently).
# Type 2 uses the external shared library locking_library.
# Type 3 uses built-in clustered locking.
# Type 4 uses read-only locking which forbids any operations 
# that might change metadata.
locking_type = 4

```
But if you want it to all sync on it's own with fall-over, then I see clvm, dlm, and corosync, with fences defined in the /etc/cluster/cluster.conf file ... see attached.

---

### Post by FiVAL on 2016-06-17
[I]Are you saying you want to stay read-only?
Because if you want all your nodes to be "read-only," then you work is almost done.
You only need to change one line in your /etc/lvm/lvm.conf file.[/I]

This is what I meant with:

[I]Only the (big) problem now is the LVM Metadata changes...
...for my current setup I have completely locked this changes for every machine. (readonly)[/I]

To get to my current setup I had to switch to readonly and force LVM to scan only the mulitpath device(s).
(else he finds the same LVM metadata by every path to the iSCSI Storage again and again...)
```
locking_type = 4
filter = [ "a|^/dev/sda7$|", "a|/dev/disk/by-id/dm-name-IT-Cluster.*|", "r|.*/|" ]
global_filter = [ "a|^/dev/sda7$|", "a|/dev/disk/by-id/dm-name-IT-Cluster.*|", "r|.*/|" ]
```


I want to sync all LVM metadata over the servers so I can manage the LV's with VirtManager.
But if the cluster is "broken" (the servers lost connection to each-other) I want these servers
to lockup there _OWN_ LVM metadata (locking_type = 4). So no harm can be done which would probably
lead up to corruption of the file system.  **_---> Is this fencing ? And how do I configure this ??_**


I do **NOT** want (on this moment):
* Let the cluster try to reboot the missing system...
* Let the cluster try to bring the missing VMs online again on different servers...
* Let multiple OS instances interact (read and write) with the same logical volume... (some sort of Cluster FS)
* Mirror the LUN live with another SAN with tools like DR:BD... (some sort of HA configuration)


So are **clvm**, **corosync** and **dlm** the only tools I have to configure / focus on ?
Or is there more to it ? Like cman (not available any more in Ubuntu?) or peachmaker and fence-agent ?

I like to test and try...
But I do not know where to start and where to end....



By the way...

It seems in Ubuntu Server 16.04 that there is **NO** _/etc/cluster/cluster.conf_ when you install corosync,
BUT a _/etc/default/corosync_ and _/etc/corosync/corosync.conf_

These files do not even look like the cluster.conf, I guess the cluster.conf is part of the cman tool (not available in Ubuntu) ?!



It is getting stranger:

```
$ sudo service clvm status

&#9679; clvm.service - LSB: start and stop the lvm cluster locking daemon
   Loaded: loaded (/etc/init.d/clvm; bad; vendor preset: enabled)
   Active: active (exited) since Fri 2016-06-17 13:40:31 CEST; 999ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 20538 ExecStop=/etc/init.d/clvm stop (code=exited, status=0/SUCCESS)
  Process: 20545 ExecStart=/etc/init.d/clvm start (code=exited, status=0/SUCCESS)

Jun 17 13:40:31 agathe systemd[1]: Starting LSB: start and stop the lvm cluster locking daemon...
Jun 17 13:40:31 agathe clvm[20545]:  * clvmd: cluster not configured. Aborting.
Jun 17 13:40:31 agathe systemd[1]: Started LSB: start and stop the lvm cluster locking daemon.
```

So i search on "clvmd: cluster not configured" and I find this: [https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/1550946](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/1550946)

So to better understand the error, I open the file: _/etc/init.d/clvm_ and find this:

```

if [ ! -f /etc/cluster/cluster.conf ]; then
        log_failure_msg "clvmd: cluster not configured. Aborting."
        exit 0
fi

```

But corosync is already up and running and knows / talks to the members...
...what do I have to configure now in _cluster.conf_ ?

---

### Post by MAFoElffen on 2016-06-18
Been busy doing some research for you.

I guess I was a bit dated. (My apologies / things change.) Seems that cman, at least in Ubuntu, went away and didn't make it past Ubuntu 12.04. It was replaced in 14.04 by Pacemaker. So for you, teamed with corosync and clvm. I am assuming that dlm is still needed, because that is what clvm uses for locking. 

Instead of in the past, configuring fences with cman, now you do it in Pacemaker. But Ubuntu is still missing some of the basic tools/utilities that rhel has for fencing, so another required piece is Ubuntu package "fencing-agents" I found this for you:
[http://clusterlabs.org/quickstart-ubuntu.html](http://clusterlabs.org/quickstart-ubuntu.html)

After that I found a thread on the Pacemaker mailing list ... where someone was trying to do something similar to what you want to do ... and was having troubles with fences... that you might want to read through.
[http://oss.clusterlabs.org/pipermail/pacemaker/2014-November/023099.html](http://oss.clusterlabs.org/pipermail/pacemaker/2014-November/023099.html)

Then, after finding those, I found something closer to your whole idea:
[https://rarforge.com/w/index.php/2_Node_Cluster:_Dual_Primary_DRBD_%2B_CLVM_%2B_KVM_%2B_Live_Migrations](https://rarforge.com/w/index.php/2_Node_Cluster:_Dual_Primary_DRBD_%2B_CLVM_%2B_KVM_%2B_Live_Migrations)

---

### Post by FiVAL on 2016-06-20
well your research and some of my own research resulted in a brief moment that the "cluster" did work!
And I could change LVM metadata on both ends and the changes where directly visible and applied!
I installed new fresh VM's on the "A" side and the live-migrations to the "B" side worked all from the VirtManager...

One of the key steps I had to configure where:
```

	## disable STONITH
	sudo crm configure property stonith-enabled=false

	## We also want to disable quorum-related messages in the logs:
	sudo crm configure property no-quorum-policy=ignore

```
```

	cat <<CONF | crm configure
	primitive dlm ocf:pacemaker:controld
	primitive clvm ocf:lvm2:clvmd
	group g dlm clvm
	clone c g meta interleave="true"
	property cluster-name="kvmcluster"
	property stonith-enabled="false"
	property no-quorum-policy="ignore"
	commit
	CONF

```
Sources:
[http://clusterlabs.org/quickstart-ubuntu.html](http://clusterlabs.org/quickstart-ubuntu.html)
[https://www.digitalocean.com/community/tutorials/how-to-create-a-high-availability-setup-with-corosync-pacemaker-and-floating-ips-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-high-availability-setup-with-corosync-pacemaker-and-floating-ips-on-ubuntu-14-04)

Because most of the How-To's on the internet are about DR:BD configurations
in CentOS or RedHat, this was difficult to find...

**BUT** of course a but ;-(

While the examples do talk about the importance of FENCING and STONITH the most of them just disable them "for now".
And because I followed the different tutorials I also believed I disabled this (for now), because of the _stonith-enabled=false_

Well, I learned that this setting does not play with DLM and / or CLVM.
So at the moment my systems seems to be STONITH and the DLM will not start anymore on both of my cluster-machines:
(even after a couple of reboots)

```

$ sudo crm_mon -1
Last updated: Mon Jun 20 16:07:09 2016		Last change: Mon Jun 20 15:07:16 2016 by root via cibadmin on node-a.example.com
Stack: corosync
Current DC: node-a.example.com (version 1.1.14-70404b0) - partition with quorum
2 nodes and 4 resources configured

Online: [ node-a.example.com node-b.example.com ]

 Clone Set: c [g]
     Resource Group: g:0
         dlm	(ocf::pacemaker:controld):	FAILED node-b.example.com
         clvm	(ocf::lvm2:clvmd):	FAILED node-b.example.com (unmanaged)

Failed Actions:
* clvm_stop_0 on node-b.example.com 'unknown error' (1): call=26, status=Timed Out, exitreason='none',
    last-rc-change='Mon Jun 20 15:40:00 2016', queued=0ms, exec=20002ms
* dlm_monitor_0 on node-b.example.com 'unknown error' (1): call=23, status=complete, exitreason='none',
    last-rc-change='Mon Jun 20 15:40:00 2016', queued=0ms, exec=59ms
* dlm_start_0 on node-a.example.com 'not configured' (6): call=12, status=complete, exitreason='none',
    last-rc-change='Mon Jun 20 15:10:40 2016', queued=0ms, exec=28ms

$ sudo corosync-quorumtool -s
Quorum information
------------------
Date:             Mon Jun 20 16:13:20 2016
Quorum provider:  corosync_votequorum
Nodes:            2
Node ID:          1
Ring ID:          308
Quorate:          Yes

Votequorum information
----------------------
Expected votes:   2
Highest expected: 2
Total votes:      2
Quorum:           1  
Flags:            2Node Quorate WaitForAll LastManStanding 

Membership information
----------------------
    Nodeid      Votes Name
         1          1 node-a.example.com (local)
         2          1 node-b.example.com


```

```

$ sudo service clvm status
&#9679; clvm.service - LSB: start and stop the lvm cluster locking daemon
   Loaded: loaded (/etc/init.d/clvm; bad; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:systemd-sysv-generator(8)

$ sudo service dlm status
&#9679; dlm.service - dlm control daemon
   Loaded: loaded (/lib/systemd/system/dlm.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2016-06-20 15:38:57 CEST; 31min ago
  Process: 9294 ExecStart=/usr/sbin/dlm_controld --foreground $DLM_CONTROLD_OPTS (code=exited, status=1/FAILURE)
  Process: 9290 ExecStartPre=/sbin/modprobe dlm (code=exited, status=0/SUCCESS)
 Main PID: 9294 (code=exited, status=1/FAILURE)

Jun 20 15:38:27 node-a systemd[1]: Starting dlm control daemon...
Jun 20 15:38:27 node-a dlm_controld[9294]: 4939 dlm_controld 4.0.4 started
Jun 20 15:38:27 node-a systemd[1]: Started dlm control daemon.
Jun 20 15:38:57 node-a dlm_controld[9294]: 4969 fence request 2 pid 9310 startup time 1466429906 fence_all dlm_stonith
Jun 20 15:38:57 node-a dlm_stonith[9310]: stonith_api_time: Found 2 entries for 2/(null): 0 in progress, 0 completed
Jun 20 15:38:57 node-a systemd[1]: dlm.service: Main process exited, code=exited, status=1/FAILURE
Jun 20 15:38:57 node-a systemd[1]: dlm.service: Unit entered failed state.
Jun 20 15:38:57 node-a systemd[1]: dlm.service: Failed with result 'exit-code'.

```


The thing I do not get: Do Ubuntu SysAdmins not use these kind of setups in there network ?

Well if you (or anyone else) have some more information about CLVM / DLM and FENCING / STONITH

please leave a post...
...I will if I know more :-)

---

