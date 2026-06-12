---
title: "Ubuntu virtual machine apache webhost down at times"
date: 2015-11-05
forum: Virtualisation
---

### Post by youngin on 2015-11-05
[INDENT] 					I'm running Ubuntu 14.04 on vmware virtual machine. I'm hosting a  website there for a team of debuggers and designers to make changes, and  have assigned a public IP address.
When the web browser is loading any site(eg google.com), the locally  hosted website is accessible via the public IP address on any network.  However, once I leave the browser idle, especially after work I get a  404 error.
Note: The virtual machine is powered on 24/7. 
Any help as to what could be causing this will be appreciated. 				
[/INDENT]

---

### Post by TheFu on 2015-11-05
Which vmware? They make 6 virtualization hypervisors.

---

### Post by youngin on 2015-11-07
I'm using vmware 12

---

### Post by TheFu on 2015-11-07
Workstation? Player? Fusion?
ESXi? Some other tool?

Would someone who can help know?  I don't keep up with all the different versions of all the VMware products. Sorry. It is my failure.

---

### Post by youngin on 2015-11-07
I'm on vmware workstation pro, running a linux 14.04 virtual machine. In your experience, could it be an issue with the virtual machine or with the workstation? 
It was my first configuration and I followed guidelines from internet sources.
Debugging tips will be helpful.

---

### Post by TheFu on 2015-11-07
What is the hostOS?

I've never seen this with ESXi.
Haven't used Workstation since the 1990s.
These days we deploy almost all VMs onto KVM infrastructure. VMware was simply too expensive.

Bridged adapter?
Manually created?
Is the host machine RAM constrained? Is RAM over-committed?
Sorry - that's all I have.

---

### Post by youngin on 2015-11-09
It's on 4gb ram.
Thank you!

---

### Post by youngin on 2015-11-10
Kindly note that it also shows a grey screen when I try a remote desktop connection.

---

### Post by tripp98 on 2015-11-14
When this occurs are you able to ping the virtual server?  Need to find out if its a virtual problem or a server problem

---

