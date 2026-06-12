---
title: "HELP----Ubuntu Sunfire V240 master cluster server"
date: 2014-06-19
forum: Server Platforms
---

### Post by J_Riebel on 2014-06-19
*Edited* 
Looking for any ideas/suggestions/assistance anyone can provide. I've got a Sunfire v240 I plan on using as the the master for a kerrighed cluster, the Sunfire is currently Solaris, but i can't leave the OS on it as its licensed to a company, and I'm not that company. I've got two HP DL385s (1x G2 and 1x G5), and 4 dell PE 1950s, and a few OLD towers i plan on using as slaves in the cluster, but they will need to be network booted as they do not have harddrives, and my budget is $0.00. First step is going to be clearing Solaris off and replacing with Linux, preferably Ubuntu, but any distro with a GUI, that i can netboot with (though creating bootable USBs is an option too and may be a better choice anyway), use Kerrighed to cluster, run a raid 5 with the sunfire's 4x 300Gig SCSI HDs, access via a remote desktop service, run VMware, and Cisco VIRL and GNS3, but there is no video out or cd/dvd drive on the Sunfire, need to console in and figure out how to get it to boot from USB.  IDEAS? Suggestions? 
*Edited*

---

### Post by lisati on 2014-06-19
*Thread moved to **Server Platforms**.*

Please do not start multiple threads for the same question in different sections of the forum, it dilutes the community's ability to help.

---

### Post by J_Riebel on 2014-06-26
Sorry, I was just attempting to cover the largest range of experience possible. Won't do it again. Still looking for some help though. Anyone know the sunfire v240 server well enough to know if it has a manipulative boot order, or how i can create a ubuntu bootable USB customized with some sort of remote desktop option like xrdp or vnc, and a static IP, so that i can remote in from another workstation? Thank you.

---

