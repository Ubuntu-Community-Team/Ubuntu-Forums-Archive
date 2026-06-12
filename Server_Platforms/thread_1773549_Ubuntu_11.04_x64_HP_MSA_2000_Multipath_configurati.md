---
title: "Ubuntu 11.04 x64 HP MSA 2000 Multipath configuration"
date: 2011-06-02
forum: Server Platforms
---

### Post by rogerappl on 2011-06-02
I am trying to setup a multipath environment.
I am running the new Ubuntu 11.04 Server with xterm (no GUI).
I tried to find this in the setup guide (nadda).

I have a bladeserver(BL 460c g6) with QLogic interfaces (2) and an HP MSA2000 with redundant controllers.

Everything apprears to be working properly and I see two disks in fdisk -l (sdc1 and sde1).
This is correct for this system.

my multipath conf is:
defaults {
    udev_dir        /dev
    pollong_interval    2
    user_friently_names    yes
}
devnode_blacklist {
    devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st) [0-9]*"
    devnode "^(hd[a-z] [[0-9]*]"
    devnode "^cciss!c[0-9]d[0-9]*[p[0-9]*]"
}

devices {
    device
    {
        vendor            "(HP)"
        product            "(MSA2*)"
        path_grouping_policy    group_by_serial
        path_checker        tur
        path_selector        "round-robin 0"
        prio_callout        "/sbin/mpath_prio_tpc /dev/%n"
        failback        immediate
        features        "1 queue_if_no_path"
        no_path_retry        300
    }
}
multipaths {
    multipath {
        wwid            22222
        alias            database
    }
}

I cannot seem to locate the wwid - and none of the posts on the internet seem to work.
I assume I will need to use update-rc to get this to work finally.

Is there a step by step guide anywhere? just in case I have missed something.

---

