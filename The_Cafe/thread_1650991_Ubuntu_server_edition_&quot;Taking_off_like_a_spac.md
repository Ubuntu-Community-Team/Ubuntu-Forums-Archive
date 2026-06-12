---
title: "Ubuntu server edition &quot;Taking off like a space shuttle&quot;"
date: 2010-12-22
forum: The Cafe
---

### Post by shafin on 2010-12-22
> **Shuttleworth's Ubuntu makes like Space Shuttle**


By [Timothy Prickett Morgan]("http://forms.theregister.co.uk/mail_author/?story_url=/2010/11/25/ubuntu_server_takes_off/") 

It looks like astronaut and tech magnate Mark Shuttleworth's  investment in the Ubuntu commercial Linux distribution is about to pay  off. Ubuntu is taking off like a rocket, and the [sale of Novell]("http://www.theregister.co.uk/2010/11/22/attachmate_eats_novell/") to Attachmate plus [the higher prices]("http://www.theregister.co.uk/2010/11/12/redhat_rhel6_package_pricing/")  Red Hat is charging for its Enterprise Linux 6 are probably going to  fuel Ubuntu's adoption even more in the data centers of the world.
  The third Long Term Support release, Ubuntu 10.04, came out in April  and seems to have been a turning point for the Ubuntu distribution. With  that release, Canonical demonstrated that it could tame the Debian  variant of Linux and put together a polished desktop and server  operating system with commercial-grade support options like those  available through Red Hat and Novell. On the server front, the server  variant of the 10.04 LTS release had all of the new or impending x64  processors from Intel and Advanced Micro Devices baked into it as well  as a fully integrated variant of the Eucalyptus cloud framework for  creating cloudy infrastructure for applications to romp around.
      []("http://ad.uk.doubleclick.net/jump/reg.software.4159/operatingsystems;tile=2;pos=top;dcove=d;sz=336x280;ord=TRI41cCoAT8AAAM-vaAAAAF1?")  
  Neil Levine, vice president of corporate services at Canonical, said  that the initial LTS release, 6.06, put a stake in the ground,  establishing the five-year support guarantee for servers and three-year  term for desktops. LTS 8.04 saw a healthy uptake among corporations  looking for alternatives to Solaris, RHEL, SUSE Linux Enterprise Server,  and even Windows sometimes and proved the quality of the distro that  Canonical could bring to market. With the 10.04 LTS release, Canonical  proved to companies that the two-year cadence for new LTS releases was  real and that Ubuntu could be trusted to run with the big boys.
 
  So how is Canonical doing money-wise now that 10.04 LTS has been out for seven months? Stellar, apparently.
  "We see a great, great year financially for my division," Levine told *El Reg*  in an interview. The prior two LTS releases as well as the interim  releases are being deployed by programmers and system administrators as  companies build out applications - the same way that proprietary  minicomputers, Unix machines, and Windows boxes all made their way into  the data center in their successive waves over the past three decades.  "When people realize they have a hundred servers running Ubuntu, they  realize they need a commercial relationship with Canonical."
  And thus, for the past three calendar quarters, the number of support  contracts for Ubuntu's desktop and server distributions collectively  have been doubling *each quarter*. Levine is projecting a  three-fold increase in support revenues at Canonical in the company's  current fiscal year, which ends in March 2011. Interestingly, the server  revenue stream is growing a lot faster these days than the overall  support contract revenue growth, says Levine, and is approaching a 50-50  split.
  Server support contracts cost a lot more and are therefore driving  that revenue growth. This was the long-term plan that Shuttleworth  always had, of course. Step One: Build a Windows alternative for  desktops, seed the market with Ubuntu enthusiasts. Step Two: Build a  Unix and Windows alternative for servers, seed the market with more  enthusiasts. Step Three: Profits!
  As you know, Canonical does not put call-home programs in its Ubuntu  Server editions, so it actually is clueless how many people are using  Ubuntu Server. And being a private company, it is certainly not going to  share the revenue numbers and customer counts it has for companies that  have bought Ubuntu Server support contracts. But Levine did provide *El Reg* with some outside data from Netcraft, the Web server counters, to show how Ubuntu is doing at least as well as *El Reg*'s world-famous [PARIS]("http://www.theregister.co.uk/2010/11/11/paris_paper/") Vulture 1 paper spaceplane.
  **The numbers**

  Ubuntu has showed journalists Netcraft trend data on Linux-based  hosts worldwide, but the Linux variant they use to host one or more Web  sites.
      []("http://ad.uk.doubleclick.net/jump/reg.software.4159/operatingsystems;tile=2;pos=top;dcove=d;sz=336x280;ord=TRI58cCoATgAAFpF6KQAAAIF?")  
  The Netcraft data counts up the total hosts supported by a Web  server. Rd hat is flatlining out there on the Intertubes as far as Web  site count is concerned, and in the past several months, Ubuntu has  hockey-sticked so aggressively that if this was an actual hockey game  Canonical would be called for high sticking.
 
  You want to see some stratosphere? Then you would need to take a look at the same data for just the EMEA Web server space.
  Novell's SUSE Linux has done better than RHEL for Web serving because  it was at least a European distro, even after Novell bought it. But  after a very aggressive ramp since the second Ubuntu Server LTS release  in 2008, Canonical's Linux reached parity with RHEL and SLES in terms of  Web site count and in the past two months has exploded almost straight  up.
  Maybe Attachmate should have bought Canonical?
  **Counting clouds**
  When Ubuntu Server 10.04 LTS was launched back in April, Levine said  that as far as Canonical could tell from watching unique IP addresses  hitting its image repository the first time customers fired up its  Ubuntu Enterprise Cloud variant, there were 12,000 clouds running its  code. (UEC embeds the Eucalyptus framework into the server edition for  deploying Xen or KVM virtual machines for hosting virtual server images  in a manner that is compatible with Amazon's EC2 compute cloud.)  Obviously, the great majority of those UEC clouds were prototypes and  proofs-of-concepts, but it is nonetheless a very large number. Levine  says that since 10.04 LTS came out in April, the monthly install rate  looks to be around 1,200, which means by the end of this year, another  10,000 or so clouds will be fired up.
  Even though Canonical will be putting in support for the OpenStack  alternative to Eucalyptus with the 11.04 release next year, Levine said  that Eucalyptus was the first to market and was more established and is  therefore still in demand. It will be interesting to see if over the  next few years, Eucalyptus suffers the same fate as the Xen hypervisor,  which has been usurped by KVM for both Red Hat and Canonical in their  Linux distros.
  Levine cautions against such analogies, saying that OpenStack and  Eucalyptus "are addressing very different parts of the market."  Canonical's philosophy is that whatever customers want to use to build  clouds, it wants them to do it with Ubuntu, not RHEL or SLES.
  In a related announcement, Canonical and open source virtualization  tool maker Convirture are teaming up to take on the ESX Server  hypervisor and vCenter console combination from VMware, offering a fully  open source alternative. While Canonical has the Landscape tool for  managing server images and Ubuntu has the libvirt and virt-manager tools  for managing virtual machines, the latter tools are more like applets  than they are virtualization management consoles.
  And so, Canonical has added the ConVirt 2.0 Open Source console to  the Ubuntu Partner Repository, which is the first step perhaps to  including it in the full Ubuntu distribution in the future like the  Eucalyptus framework is now. ConVirt is a console for provisioning,  managing, and monitoring Xen and KVM virtual machines, and as *El Reg* already [told you back in July]("http://www.theregister.co.uk/2010/07/28/convirture_enterprise_virt/"),  it now comes in an Enterprise Edition that has some closed-source  features that Ubuntu shops probably want. We're talking about  timetable-based provisioning and decommissioning of VMs; role-based  access control for admins and multi-tenant security; a command line  interface and programmable APIs; high availability and disaster recovery  overlays for the Xen and KVM hypervisors; resource limiting; a virtual  appliance catalog for self-service VM deployment; and alerting and  notification features to bug admins.
  If Canonical wanted to do something interesting, it would buy  Convirture and merge the Enterprise version of ConVirt 2.0 with its  Landscape management tool and embed the open source version in Ubuntu  Server. Clearly, Shuttleworth has the money, [after shelling out $31.5m for a New York apartment]("http://www.theregister.co.uk/2010/11/23/shuttleworth_superior_ink/"). ®
 


Good to know that ubuntu is slowly winning the linux server battle too.

---

### Post by kaldor on 2010-12-22
Ubuntu seems more reliable as a server than a Desktop overall.

---

### Post by areteichi on 2010-12-22
Thanks for sharing ;)
Sounds quite exaggerated but at least it is an indication that Canonical is successfully growing.

---

### Post by NCLI on 2010-12-22
> **kaldor said:**
> Linux seems more reliable as a server than a Desktop overall.
Fixed that for ya' :p

Linux is improving a lot though, with the focus slowly shifting towards the desktop.

---

