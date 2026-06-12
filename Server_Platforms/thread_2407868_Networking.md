---
title: "Networking"
date: 2018-12-10
forum: Server Platforms
---

### Post by i-hughes76 on 2018-12-10
Hello,

Posting here because I am trying to find some guidance on the networking end of Ubuntu Server before I decide to do an overhaul backup and wipe. I want to start from the very beginning of how my configuration is setup, so that everyone can get a much better understanding of what may be going on.

I am running a Dell Poweredge 2950 server out of my home to provide myself and others with local storage, media services, etc. The server is running VMWARE Vsphere Hypervisor (ESXi), "unsure of the version at the moment." Installed to this Hypervisor are 4 different virtuals, however, my issue is with Ubuntu Server 17.10. Back in June, I had shut the server down as I would be away for sometime due to work and did not want to leave the server unattended. Friday of last week, I powered her back up with no problems. I knew there would be many updates that would need to be done. When I booted up the Ubuntu Server VM, I had an internet connection but noticed that I could not pull through any updates. However, accessing the web, external network files, etc. was no problem.

After letting the server sit and run for about 2 days, I came back to notice that Ubuntu no longer had an ethernet connection and that all of my past configurations were gone. I have done mast amounts of research of how to reconfigure my connection to no avail and am now stumped and scratching my head. DHCP nor Static assignments seem to work. Any assistance from the community would be very helpful.

Thank You,
Ian

---

### Post by howefield on 2018-12-10
Thread moved to the "*Server Platforms*" forum.

---

### Post by SeijiSensei on 2018-12-11
Ubuntu 17.10 no longer has support.  Only the Long-Term Release versions of Ubuntu like 14.04, 16.04, and 18.04 receive updates.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I suggest you upgrade to 18.04.1 which will be supported through April, 2023.  I would transfer files from the 17.04 VM to a brand-new 18.04 VM rather than using do-release-upgrade.  Regardless of the method you choose make sure you have a backup.  Does your VM provider take daily snapshots of your machine?  

Do you have access to the hypervisor level so you could copy files directly from one VM to another?  That would work even if you can't establish a network connection.

[http://cdimage.ubuntu.com/ubuntu-server/bionic/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-server/bionic/daily-live/current/)

---

