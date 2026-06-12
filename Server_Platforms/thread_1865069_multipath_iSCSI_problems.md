---
title: "multipath iSCSI problems"
date: 2011-10-19
forum: Server Platforms
---

### Post by craig@locationlabs.com on 2011-10-19
We're running Ubuntu 2.6.32-33-server #72-Ubuntu SMP x86_64.  The server has a two port Intel PRO 1000 adapter that is used for iSCSI traffic (note:  it is not an iSCSI HBA).

We have a dual controller Compellent SAN.  Each controller has four iSCSI ports.  There are two fault domains comprised of two ports from each controller.  Each fault domain has a virtual IP that initiators connect to.  Each fault domain is serviced by an ethernet switch.  The server connects to each switch.

When I bring up open-iscsi and multipath-tools, I can see the LUNs, create volumes, and read/write to disk.  The problem is that when I reboot a switch, the server stops passing traffic on the pathway that is still available.  It waits until the switch comes back up and then begins forwarding over both paths.  That is causing a loss of I/O that can last up to a minute.

I had the same problem on Windows 2008 R2 with their MPIO.  When I changed the policy from round robin to "least queue depth", the server would continue forwarding traffic over the path that was still available with no downtime.

But multipath-tools only supports round-robin.  Am I the only person experiencing this?  That just seems really unlikely to me and I doubt that other Ubuntu users using MPIO iSCSI will tolerate a sixty second pause in I/O every time a switch reboots.

Here is my /etc/multipath.conf file with various options that I've tried at one point or another:

defaults {
        verbosity               4
        user_friendly_names     yes
        path_grouping_policy    group_by_prio
        #features "1 queue_if_no_path"
        path_checker            readsector0
        #selector               round-robin 0
        failback                immediate
        pollint_interval        2
        hardware_handler        "1 rdac"
}

blacklist {
 devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st)[0-9]*"
 devnode "cciss"
}

---

