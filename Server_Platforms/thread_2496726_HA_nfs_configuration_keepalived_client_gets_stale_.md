---
title: "HA nfs configuration keepalived client gets stale file handle when VIP failsover"
date: 2024-04-09
forum: Server Platforms
---

### Post by eclay on 2024-04-09
I'm trying to configure two NFS servers with replicated data that are accessed by a VIP that keepalived manages/fails over between the two nodes.  I'm able to mount the exported fs without issue on the initial active node.  When the VIP is failed over to the standby node the client gets a 'Stale file handle' error.  If I unmount/mount the exported fs on the client using the VIP now on the standby node, I can access the exported fs.  Before I unmount/remount I'm able to see that ARP on the client is updated with the MAC of the new active host.  

Does anyone know if there is a way to make this work with nfsv4 on ubuntu 22.04 servers?

All servers/client are running Ubuntu 22.04 with latest patches.

---

### Post by eclay on 2024-04-10
I did a tcpdump between the client and VIP that keepalived manages.  It seems like I get a NFS4ERR_BADSESSION status followed by a NFS4ERR_STALE_CLIENTID.  I think a unmount/mount of the exported filesystem is the fix for this.  Anyone aware of anything I can try to make this work without having to unmount/mount the eported filesystem?

---

### Post by MAFoElffen on 2024-04-10
You didn't say what you were using for your keep-alive did you? 

thinking out-loud, the logic to make that work. In PaceMaker, it is event driven. So if you created a script to unmount/mount your shares, then create an alert to call that script... Then that would happen, right?

RE: [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_and_managing_high_availability_clusters/assembly_configuring-pacemaker-alert-agents_configuring-and-managing-high-availability-clusters](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_and_managing_high_availability_clusters/assembly_configuring-pacemaker-alert-agents_configuring-and-managing-high-availability-clusters)

---

### Post by eclay on 2024-04-11
I'm using keepalived to manage a floating/VirtualIP address.  Both nfs servers are configured with the same exports.  I was trying to not use something more complicated like pacemaker if possible.

---

