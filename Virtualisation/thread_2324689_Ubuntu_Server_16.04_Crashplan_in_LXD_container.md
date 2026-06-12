---
title: "Ubuntu Server 16.04 Crashplan in LXD container?"
date: 2016-05-15
forum: Virtualisation
---

### Post by jay116 on 2016-05-15
I've re-purposed my last build as a file/media server and backup. I'm using Ubuntu server headless but am trying to figure out how I can implement Crashplan. I know it will work if I install it on my main server OS (in headless mode), but would it be better to install it inside a lxd container and mount the Host drive inside that container? Or should I install it on the host OS and give Crashplan reduced rights on the file system as read-only. I'm new to Linux to some degree. I've been reading on lxd which looks interesting but is there a flaw in the logic to let the container see a file system in the host OS? I know I can mount the FS in the container as read-only. I haven't searched for a solution to run Crashplan on the main OS with reduced rights, but lxd seems better from that point. I'd like to run other apps in a container as well, such as a Plex server. Then again it needs to access a drive that doesn't exist in the container and I cant copy 2TB of movies to the container FS.

Any advise would be great. 

Thanks.

---

### Post by MAFoElffen on 2016-05-16
These tutorials might help(?):
[https://support.code42.com/CrashPlan/4/Configuring/Using_CrashPlan_On_A_Headless_Computer](https://support.code42.com/CrashPlan/4/Configuring/Using_CrashPlan_On_A_Headless_Computer)
[https://www.liquidstate.net/installing-crashplan-on-a-headless-linux-server/](https://www.liquidstate.net/installing-crashplan-on-a-headless-linux-server/)
[https://www.tech-knowhow.com/2015/08/how-to-setup-crashplan-headless-on-ubuntu-linux/](https://www.tech-knowhow.com/2015/08/how-to-setup-crashplan-headless-on-ubuntu-linux/)

---

