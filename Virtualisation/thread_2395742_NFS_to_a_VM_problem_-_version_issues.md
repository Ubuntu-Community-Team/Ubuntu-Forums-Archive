---
title: "NFS to a VM problem - version issues?"
date: 2018-07-06
forum: Virtualisation
---

### Post by undecidable on 2018-07-06
I have a Kubuntu 14.04 host (vbox 4.3) with multiple Kubuntu 14.04 guests.
I use NFS (1.2.8) to communicate between the guests and the host, with no problem.

I set up  test Xubuntu 18.04 host running an Xubuntu 18.04 guest and one of the Kubuntu 14.04 guests
(virtualbox 5.2.10, NFS 1.3.4).

NFS works as expected between the 18.04 host and the 18.04 guest.
If I try to mount an exported dir, it mounts.
If I try to mount an un-exported dir, 
the guest gives the message:
```
mount.nfs: access denied by server while mounting...
```
and the host system log shows:
```
refused mount request from ... for ... : not exported
```
All correct.
	
But for the 14.04 guest on the 18.04 host:
if I try to mount an exported dir, I get the message:
```
mount.nfs: access denied by server while mounting...
```
and there is nothing in the host system log.
As though it didn't happen.

The NFS config is exactly the same between the 14.04 and 18.04 guests,
and the 14.04 guest works perfectly on a 14.04 host.

Anybody understand the problem?

I would like to migrate the hosts to 18.04 first,
then gradually migrate the guests.  
But this means I need to use 14.04 guests for a while as I migrate.

---

### Post by TheFu on 2018-07-06
IDK, but didn't the default NFS version change from v3 to v4 over the years?  Don't you need to specify v3 if that is the version you want on later servers?  [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) says:
>  the startup scripts in recent versions of Ubuntu use the rpcinfo command to discover NFSv3 support, and this will be disabled if localhost is unable to connect. 

Just a guess.  There are also issues if a userid is a member of more than 16 groups.

---

### Post by SeijiSensei on 2018-07-06
Do you have the correct network and mask for all the clients in the /etc/exports file?

Are you mounting drives as a user or as root with no_root_squash?  If as a user, do the users have identical UIDs and GIDs on both machines?

Have you tried "sudo mount -o nfsvers=3 server:/share /mountpoint"?

---

### Post by undecidable on 2018-07-08
hi SeijiSensei, TheFu

Thanks for the ideas.

I did try nfsvers=3, but no difference - still get 
	> mount.nfs: access denied by server while mounting..

nfsstat -m shows version4 (on the 1404 guest i the 1404 host)
so likely also v4 on the 1804 host and guest.

The userid is not a member of more than 16 groups.  My life is not that complicated ;-)

I'm exporting with root_squash on the host/server and mounting with sudo mount on the vm/client.  
As the man nfs says:
> no_root_squash  ...This option is mainly useful for diskless clients
Even so the user /group is the same on the host and on the vm.

the export line to the vmk43 vm is:
```
/0docs/vk/109	vmk43r(rw,sync,root_squash,subtree_check)
```
the mount line on vmk43 is
```
sudo mount  -t nfs  -o rw,hard  vmhost:/0docs/vk/109   /0m/109
```

---

### Post by TheFu on 2018-07-08
vmk43r is a typo?   Can the client and server ping each other by the names used?  vmk43r, vmk43 and vmhost
Hard mounts can be dangerous. The sync option has huge performance impacts too.

I think NFSv4 isn't trivial to enable.  You have to setup certs, so if you haven't done that, I don't think it works. Both the client and server need the v3 option.

Users and groups matching is good, but that isn't enough.  The uid/gid must match. The names/letters don't matter. It is the numbers which matter. Just saying this for clarity.

---

### Post by undecidable on 2018-07-09
Key point:
nfs works between the 14.04 host and the 14.04 guest (vmk43r).
nfs works between the 18.04 host and the 18.04 guest (vmx80).
nfs does not work between the same 14.04 guest (vmk43r) and the 18.04 host.
The host and guest can ping each other.  uid, gids are the same.

So I think nfs is set up correctly - it has been working between the 1404 host & guests for 2 years.

The most likely possibility is something in the VM version change (4.3 -> 5.2) 
or the  nfs version change (1.28 -> 1.3.4)

In any case I am going to give up on this,
I have almost finished converting 2 hosts to 18.04
will now create full 18.04 guests to replace the 14.04 guests.
More pain than I wanted, but probably less than I deserve.

---

