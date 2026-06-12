---
title: "mountall: Plymouth command failed in AWS ebs backed Ubuntu 10.04"
date: 2010-07-16
forum: Server Platforms
---

### Post by wickett on 2010-07-16
We have two instances launched in AWS using the exact same AMI.  When a box was launched in zone us-east-1b it would fail (see bad log below) and if it was launched in us-east-1c, it would be ok (see good log below).  Both get fully launched, EBS backed instances with attached ebs disks.

We opened a ticket with Amazon and they said that it wasnt their problem and that it was an issue with Ubuntu.  [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/559761](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/559761)

The funny thing is that the instances in 1b work today after a reboot.  Which leads me to believe it is Amazon's problem and they changed something with EBS in the 1b zone, however I have noticed other comments in the forums about the mountall: Plymouth command failed.  Has anyone else seen this? In AWS or outside of it? What causes this?  

This is really odd behavior and thought the community might have some ideas on preventing this in the future.

-----------------------------------
"bad" log: 
[ 1.896324] Write protecting the kernel read-only data: 6416k

init: console-setup main process (79) terminated with status 1


%Ginit: plymouth main process (61) killed by SEGV signal

init: plymouth-splash main process (285) terminated with status 2

cloud-init running: Thu, 15 Jul 2010 22:49:51 +0000. up 56.45 seconds
Generating locales...
en_US.UTF-8... up-to-date
Generation complete.
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Plymouth command failed
mountall: Disconnected from Plymouth
init: ureadahead-other main process (434) terminated with status 4
 
<lockup> 


--------------------
"good" log:  

init: console-setup main process (79) terminated with status 1


%Ginit: plymouth-splash main process (270) terminated with status 2

init: plymouth main process (61) killed by SEGV signal

cloud-init running: Fri, 16 Jul 2010 15:45:55 +0000. up 7.13 seconds
init: ureadahead-other main process (349) terminated with status 4

init: ureadahead-other main process (354) terminated with status 4

init: ureadahead-other main process (357) terminated with status 4

init: plymouth-log main process (364) terminated with status 1

* Starting AppArmor profiles 
[80G Generating public/private rsa key pair.

[74G[ OK ]

---

### Post by ubudog on 2010-12-29
I get the same errors when trying to setup my servers... weird.

---

