---
title: "VMware Tools breaks networking on Dapper Server???"
date: 2006-11-11
forum: Server Platforms
---

### Post by PilotJLR on 2006-11-11
Hi all,
Here's the problem I'm having...

I have a Edgy Eft desktop computer that is running the newest version of VMware Server. I've installed a guest OS in vmware - the guest is Dapper Server. In the guest, I've installed Apache / PHP / MySql, since it will run a website.
The guest OS has a static IP address as well.

After installing VMware Tools from tarball, I've noticed that services, such as Apache2, stop responding after a few minutes of running. Apache itself does work (I spent hours thinking apache was at fault)... to prove that apache is working, I waited until other client could no longer connect to the  website, then I went into the guest OS command line and did a "telnet localhost 80" followed by "GET", and *poof* there is the website.

So it works on the guest, but simply ceases to work externally. Same for ssh. Not same for ping... the guest ALWAYS responds to ping.


** I think I maybe have fixed this by disabling vmware tools... after disabling it and rebooting the guest, I can no longer duplicate the problem.

Has anyone experienced this?? Any ideas??
thanks!

---

### Post by PilotJLR on 2006-11-11
Ok, I spoke too soon... disabling Vmware Tools does NOT fix the problem.

I'm pretty sure this has something to do with VMware, and I'm pretty confused how to resolve this. Never had this issue before on more complex RHEL based vm's.

And I have no iptables entries at all... should be wide open.

I'd appreciate any help or ideas! Thank you!

---

### Post by PilotJLR on 2006-11-11
FYI - I made a new virtual machine and rebuilt the sites I needed, and this problem has not reoccurred!

Still no idea why it happened in the first place... but it must've been something I did, since a virtually identical new VM does not have the same issue.

---

