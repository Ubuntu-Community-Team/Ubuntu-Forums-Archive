---
title: "CMR and Virtual machine questions."
date: 2009-01-19
forum: Server Platforms
---

### Post by EmanresuusernamE on 2009-01-19
Two real quick questions, or more like two real quick requests for opinions.

1:  What is the best free CRM (Customer Relation Manager) addon for Apache?
I thought of using either SugarCRM, or Drupal, but I wanted to know which would be easier to implement/run better on an Ubuntu server (the second to last release) and Apache.  Or if there where any other good ones out there.

2:  What is a good Virtual Machine program that works well with Ubuntu server?
The company I work for is about to start using Virtual Machines inside of Ubuntu servers so that we can run Windows machines in a safer/faster environment, (reboot them when they go down a lot easier and such things).  We where leaning towards a VM wear machine, but we're not fully able to do so since we plan on using this for multiple customers.  What is a good free Virtual Machine that can run Windows Server editions?

Thanks.

---

### Post by windependence on 2009-01-19
> **EmanresuusernamE said:**
> Two real quick questions, or more like two real quick requests for opinions.

1:  What is the best free CRM (Customer Relation Manager) addon for Apache?
I thought of using either SugarCRM, or Drupal, but I wanted to know which would be easier to implement/run better on an Ubuntu server (the second to last release) and Apache.  Or if there where any other good ones out there.

2:  What is a good Virtual Machine program that works well with Ubuntu server?
The company I work for is about to start using Virtual Machines inside of Ubuntu servers so that we can run Windows machines in a safer/faster environment, (reboot them when they go down a lot easier and such things).  We where leaning towards a VM wear machine, but we're not fully able to do so since we plan on using this for multiple customers.  What is a good free Virtual Machine that can run Windows Server editions?

Thanks.

I am about to test some CRM applications myself. I will let you know what I find out. As far as Virtual Machine software is concerned, I am a big advocate of VMware. You may get some flak from members saying it's not as "free" as they would like, the full source is available, and they aren't any more restrictive than Xen or Virtual Box, all of which are owned by big proprietary companies. By far, VMware is the most mature of the bunch, and supports the greatest number of guest OSs. It also can be run "bare metal" meaning no host OS is needed with ESXi which is totally free of charge and was just recently over $500. My suggestion would be to run ESXi from a flash card. You can get adapters that plug right into the IDE slot and act just like a hard drive. There are even dual flash card adapters out there to run a backup card if you desire. If you need help with VMware, I am a VMware partner, and I have attended VMware boot camp. I would be glad to assist you.

-Tim

---

### Post by EmanresuusernamE on 2009-01-23
Thanks, hope to hear good results soon.  :)

I'm giving Drupal a whirl right now, not going too well since I can't get MySQL to work right.

---

