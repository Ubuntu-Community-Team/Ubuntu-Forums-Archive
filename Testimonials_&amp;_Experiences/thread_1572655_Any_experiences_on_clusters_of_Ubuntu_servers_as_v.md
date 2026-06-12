---
title: "Any experiences on clusters of Ubuntu servers as virtualization hosts?"
date: 2010-09-11
forum: Testimonials &amp; Experiences
---

### Post by Macchi on 2010-09-11
Dear Fellows,

I would be very pleased to read about concrete experiences on running clusters of Ubuntu servers as virtualization hosts for production environments. Performance, reliability, load balancing (manual or automatic) and maintenance needs are important parameters.
The host servers will hold domain controllers, terminal servers and at least one SQL server, among other functions. 


It would be nice if anyone could share their experiences in the area!
Thank you!
Best Regards,

AM
(an IT Manager for an industry in Europe)





PS: As IT manager for a small/medium-sized industry I am leading a modernization project that requires a cost-efficient and resilient group of physical servers that will host several of our virtual servers.
Today we run the environment on physical machines but that will not be feasible in the long run due to reliability risks and increased maintenance costs. 
I am considering Ubuntu as host servers despite hearing lots of recommendations towards just choosing a mainstream solution with Windows. 

Personally I have used Unix and Solaris etc since 1988 and Linux servers and desktops since 2003. I have used extensively vmware and virtualbox in small environments, including providing remote access of virtuam windows machines through NX. Thus I have a strong intellectual bias towards linux and open source. My experiences with Ubuntu used to be very positive but since a year ago we had many problems with all 10 (ten) different test computers and were forced to stop further investments of time on Ubuntu and Linux in our industry. 

My decision on virtual server hosts running Linux has to be based on concrete experiences, thus I hope to see relevant testimonials.

This is a difficult dilemma since few would blame a manager on the eventuality of increased costs and difficulties if I choose a mainstream solution. But the IT-team would be in severe jeopardy if choosing an open source and risking problems and/or increased maintenance costs with Linux.

---

### Post by ukripper on 2010-09-11
Personally I'd go for Centos or Redhat in cluster environment for much better support in virtualisation. And when it comes to "mainstream virtualisation" they are much better than windows solution.

Our backend servers currently running [http://www.redhat.com/virtualization/rhev/](http://www.redhat.com/virtualization/rhev/) and we have never been this happier.

---

### Post by Macchi on 2011-01-14
Thank you for comments. We realized as well that the path of solutions available in Ubuntu for desktops and server virtualization is unfortunately not mature for production environments in our business application areas.

---

### Post by Old_Grey_Wolf on 2011-01-14
We needed management software for our virtualised datacenter that followed ITIL processes. We found that we could get ITIL management software from BMC, HP, and IBM; however, they did not support Ubuntu Enterprise Cloud at the time. They did support more mainstream solutions using VMware ESX/ESXi, Microsoft Windows Hyper-V, etc. They may support it now; however, I haven't look into switching. 

If you are looking to host Ubuntu on a hypervisor, VMware does support Ubuntu as a guest OS. The last time I looked, Microsoft Windows Hyper-V only supported RHEL 5.

---

