---
title: "Small Non-Profit UEC Architecture - Sanity Check"
date: 2010-12-02
forum: Ubuntu Cloud and Juju
---

### Post by flickerfly on 2010-12-02
I'm trying to figure out how to convert to a UEC central architecture for a small non-profit (read very tight budget). I have a server that is in use that I could convert for this purpose if I had enough hardware to convert the OS over first. 

**What I Have**
Dell PowerEdge 2900 (future NC?)
[INDENT]Intel Xeon E5404, 2Ghz
4G Ram
150G SCSI HD
Note: Not available until OS gets virtualized[/INDENT]

**My Current Plan**
Setup UEC in Managed-Novlan mode with a CLC/CC/WS3/SC machine and a cross-over cable to the NCs.

Buy a PowerEdge T110 for CLC, CC, WS3, SC.
[INDENT]Intel Xeon X3430, 2.4 GHz
2Gb Ram
4 500Gb HD in RAID 5
[/INDENT]

Buy a Dell PowerEdge T410 for NC purposes.
[INDENT]Intel Xeon E5620, 2.4Ghz
4Gb Ram
2 250Gb drives in RAID 1
[/INDENT]
Implement the PE2900 as an NC after that's running.

**What I want in the cloud**
Samba Server w/ 10 users and up to 1Tb of storage.
Primary Domain Controller
Backup Domain Controller
Windows Application Server (currently on PE2900 above, but can reduce requirements)
LAMP Server
Nagios Server

---

### Post by kim0 on 2010-12-03
Well, the major advantage UEC provides is being multi-tenant and EC2 API compatible. For your case, assuming this is a single organization (no multi-tenants) and you're managing everything yourself. Then UEC is probably an overkill for such a small environment. No need to buy that much extra servers. You can just install Ubuntu server on the PE machine, and install the servers you described as direct KVM VMs on top that you manage with virt-manager. A single machine should be enough (might need to raise RAM to 8G) however.

If however you need your VMs to be HA, then either buy a second similar box, setup DRBD disk synchronous replication. That way if any of both servers fail, you can start the VM instantly on the other node (if you start it on both servers however, it can corrupt, so care is needed). Another perhaps simpler option is a separate NFS storage box (could be oldish with lots of spindles). It really all depends on the level of protection and your failure tolerance. For example, a single server would be enough if you're backing everything to tape, and a recovery time of 6 hours or so acceptable :)

---

