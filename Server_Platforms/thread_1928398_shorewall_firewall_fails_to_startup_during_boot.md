---
title: "shorewall firewall fails to startup during boot"
date: 2012-02-20
forum: Server Platforms
---

### Post by duceduc on 2012-02-20
Running ubuntu server 11.10

Upon checking my boot.log after my pptp wasn't working, I noticed my shorewall is not starting up during boot. I have enable the startup function in the shorewall.conf to 'yes' and also in /etc/default/shorewall to '1'. 

This cmd 'sudo shorewall check' yields the shorewall is stopped. 

The boot.log shows this error.

> fsck from util-linux 2.19.1
/dev/sdb1: clean, 104534/15007744 files, 2089061/59999488 blocks (check in 3 mounts)
#### WARNING ####
the firewall won't be initialized unless it is configured

Please read about Debian specific customization in
/usr/share/doc/shorewall-init/README.Debian.gz.
#################
Starting "Shorewall firewall": done.
 * Stopping Failsafe Boot Delay[122G[ OK ]
 * Stopping System V initialisation compatibility[122G[ OK ]
 * Starting System V runlevel compatibility[122G[ OK ]
 * Stopping automatic crash report generation[122G[[31mfail[39;49m]
 * Starting save kernel messages[122G[ OK ]
 * Starting CPU interrupts balancing daemon[122G[ OK ]
 *   Autostarting VPN 'server'       [128G  * Starting regular background program processing daemon[122G[ OK ]
 * Starting deferred execution scheduler[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Starting virtual private network daemon(s)...       [128G 
[122G[ OK ]

If you noticed it fist says 'firewall won't be initialized...' but after that it says 'starting shorewall...' HOwever, I check and shorewall is not started. What is causing this message?

---

