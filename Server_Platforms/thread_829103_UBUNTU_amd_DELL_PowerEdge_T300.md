---
title: "UBUNTU amd DELL PowerEdge T300"
date: 2008-06-14
forum: Server Platforms
---

### Post by brunobbmagalhaes on 2008-06-14
Hi folks,

I've been a reader of this forum for quite a long time, and also, course, a Ubuntu user since 6.x brand. And, now I think it´s time for our little company to step in into the Linux world, without never going back.

We just acquired a brand new DELL PowerEdge T300, with a Intel Core 2 Duo processor, 4GB RAM, and two 250GB RAID1 (SAS6IR controller) hot swap hard disks, that will be used as a development and testing server, basic the Ubuntu Server LAMP package, with the SSH, a ftp server and also a SVN server. [http://www.dell.com/content/products/productdetails.aspx/pedge_t300?c=us&cs=555&l=en&s=biz]("http://www.dell.com/content/products/productdetails.aspx/pedge_t300?c=us&cs=555&l=en&s=biz")


My questions are:

1) Have anyone installed Ubuntu 8.04 Server within this server with this particular configuration? The DELL websites states that it's compatible with Red Hat Linux Enterprise v5 ES x64 and SUSE Linux Enterprise Server 10 x86-64, but nothing about Ubuntu or others distros?

2) Will I have any kind of hardware compatibility problems? Like with SAS6IR controller, onboard video, or anything like that?

3) Any suggestions or directions?


Thanks a lot, in advance, I really appreciate any help!

Best Regards,
Bruno B B Magalhães

---

### Post by brunobbmagalhaes on 2008-06-20
Hi you all,

no one has any suggestions regarding this system specifications?

Best Regards,
Bruno B B Magalhaes

---

### Post by gtdaqua on 2008-06-20
It should work. Even though "Core 2" is not server platform, it is 64-bit capable. For Linux server, this processor should be good enough. 

SAS6iR question is quite complicated, but don't have to worry too much about it. But if you are seriously considering high-end servers and Linux, you should try HP. They are certified to run on Debian-based OSes (like Ubuntu). Dell can acknowledge only RHEL and SUSE. It supports Ubuntu only on the desktop level.

---

### Post by fhubu on 2008-06-30
Hello,
I post the same question : got a new Dell T300 , hard to know if i can settle a Debian Etch on it. Will it get the right drivers ? Will it be able to manage the RAID 1 configuration ?

---

### Post by peio on 2008-07-22
I am just know trying to install debian etch r3 in a T300 with a SAS6 raid device. 
I only have one problem( big one), and It's that the debian instaler doesn't detect broadcom NICs. 
SAS6 raid device is harware device so is invisible for the OS.
Does someone install ubuntu in one of this servers?
p.,

---

### Post by maerlma on 2008-07-22
i just installed server 8.04.1 (amd64 version) on a poweredge t300 with no problems at all. the only difficulty i had was figuring out which of the 4 ethernet ports on the back was eth0.

---

### Post by sweanders on 2009-03-27
Hi!

What is the disk configuration on the T300 you have installed Ubuntu on?

I have installed Ubuntu on a few machines and running VMWare server on top of it for Windows VM's. Looking into running this same setup for a remote office.

---

### Post by linux_tech on 2009-03-28
> **maerlma said:**
> i just installed server 8.04.1 (amd64 version) on a poweredge t300 with no problems at all. the only difficulty i had was figuring out which of the 4 ethernet ports on the back was eth0.

which controller was that?

---

### Post by spage on 2009-07-24
I'm having a lot of trouble staying connected to the internet. My T300 functions as a LAMP server which I recently switched over from SLES 10 for ease of administration. Occasionally it dumps the ethernet connection and becomes unreachable on all ports. I know that the the cable and router is good, because nothing has changed from when it was running SLES 10, and I never had problems with it then. The problem is completely unpredictable and lasts usually about 2minutes, but then it comes right back without any intervention on my part.

Any ideas?

---

