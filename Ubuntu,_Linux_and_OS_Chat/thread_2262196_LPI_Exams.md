---
title: "LPI Exams"
date: 2015-01-23
forum: Ubuntu, Linux and OS Chat
---

### Post by nigel11 on 2015-01-23
Hello All,

Without making it too boring, here's a little info on myself: I was a 1st-3rd level Sys Admin for mostly windows users and windows servers for a medium sized company for 3 years. I then switched to a company where the other two IT guys were to say the least, very anti-microsoft. Indeed it seems a lot of IT guys in Germany have a massive Linux preference, and after a year of working for this company, I would like to think my Linux knowledge has come leaps and bounds. My particular favoruite being Ubuntu. 

Unfortunately, these other two guys have abruptly left the company and I am now IT group leader for a 70+ user company. So, this Linux experts have left the house... And here is where the title comes into play. I would like to gain a much deeper understanding of Linux. These guys had a big preference to Gentoo, since they could compile exactly what they wanted, which dependencies and libraries etc. - However, I much prefer a system like Ubuntu which provides a running system that won't take down your machines for a day after an update.

So, my question is - Should I pursue the LPI exams as a way of furthering my Linux knowledge. To be honest, I wanted to just learn as I go as I have been doing. But my workload is at a high point where I do not have the time to read through man pages and take notes during work hours - and our Linux based services run almost flawlessly and do not need much maintenance. I am afraid if things keep going, I will not learn too much. Are the LPI exams worth pursuing? Has anyone else found them beneficial? If so, could you direct me towards any decent material?

Cheers

---

### Post by TheFu on 2015-01-23
Your questions ask for opinions. Treat all the answers as such, not as facts.

Gentoo inside a business for normal server use is a huge, huge, mistake, IMHO.  My experience proved to me that all the claims about Gentoo being faster because it was built for "my specific hardware" wasn't true.  The kernel performance tuning teams at Redhat, Suse, Canonical, and other distros are much smarter than me.  I did a few side-by-side tests on the same machine and found Gentoo to be slower.  Don't get me started about the maintenance nightmare for gentoo systems.  Even slackware is more user friendly than Gentoo.
If you have specialized HW and minimal resources, then using gentoo can make sense, but not for a typical, generic, server on normal hardware.

LPI certs aren't well respected, at lease not in North America.  RHCE is the cert you want to further a Linux career and put more money into your wallet, usually 15% more annually. The LPI materials that I've got were 10 yrs behind on most things and 30 yrs behind on others. Some of the topics are about config files I've never, ever, ever, ever, seen in use anywhere since 1991. I've seen thousands and thousands of Linux servers, BTW.

If you want just the knowledge and want to be cross-distro, [http://edx.com](http://edx.com) has Linux Foundation classes for free. These are taught online like university courses.  Talk with your company about training.  Set some goals for them to support your efforts. If you don't want to become a Linux guru, that will be enough to get by.  If you want deeper level knowledge, then you have to live with Linux daily, for all possible computer uses - desktop, server, HTPC, NAS, routing, everything you do on a computer. After a year of this and you've gone through the LF courseware, then start on the RHCE training.  Get the company to pay for this.  Look for a raise based on being certified and if they don't provide one, move on.

I would stop deploying anything on gentoo and begin an active project to migrate to either Debian or CentOS for the servers. It isn't like gentoo was providing any real support, so CentOS (CentOS is binary compatible with REHL) is fine.  Ubuntu for desktops is fine and some folks run it for servers.

As with everything, true mastery takes time and effort. 
While I know you only asked about certs, here's my considered ideas about learning Linux: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) meant mainly for non-professionals, people who just want the knowledge and don't need a cert.

---

### Post by nigel11 on 2015-01-23
I do agree with what you say. Gentoo was not my decision. The guys that deployed this are both developers who have their own linux kernel and who really prefer and understand what is going on with their OS. I however, do not. Therefore I would also prefer a Ubuntu or some other more complete flavour of Linux for my infrastructure. 

My job is extremely supportive and understand my lack of Linux experience. They would pay for whatever I ask, this is why I asked about the LPI's. I am more infrastructure/vmware/windows expert with now a touch of Linux. And would like to expand on the Linux. I think Gentoo is an excellent way to really understand and custom build what you want, but I don't like it in production. I will check out your links.

Cheers :)

---

### Post by TheFu on 2015-01-23
Migrating off ESX/ESXi will easily pay for your training for the next 5 yrs. Using libvirt and KVM for a small infrastructure is an easy choice (small = less than 50 physical servers).  Plus the savings from all the vSphere add-ons that aren't needed anymore because with Linux as the VM host, backups are built-in, failover is built-in, clustering is built-in .... no extra licenses needed ... er ... no licenses needed at all.  It is just a matter of knowledge, not license fees.  KVM is rock solid and routinely shown to be faster than VMware's options. Check the SPEC-virt data.

Of course VMware can do some thing the others cannot.  vMotion when there isn't shared storage is sort cool - don't know anyone using it in production.  Also, their large scale support blows away what libvirt/KVM or even OpenStack can do.  Migration of VMware infrastructure is 100000x better than OpenStack's non-migration support.  If the price for VMware is worth it is for the bean counters and CxO guys to figure out.  In my little company, we decided to dump all VMware and go with Xen and KVM initially. KVM has proven less trouble in our environment, so after a few years, we dumped Xen. Out of about 30 VMs, only 2 are MSFT, but those run just fine too.

Knowledge helps you and the company, license fees helps other vendors.

---

