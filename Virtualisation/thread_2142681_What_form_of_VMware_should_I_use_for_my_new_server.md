---
title: "What form of VMware should I use for my new server?"
date: 2013-05-06
forum: Virtualisation
---

### Post by morecw on 2013-05-06
[COLOR=#333333][FONT=Arial]Hi all,[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]I'm going to make the leap from Windows 2008 to Ubuntu 12.04 LTS Server as I did some recent testing and there really is a dramatic improvement in web server response times when hosting on a Linux server.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]This server will be a single guest o/s dedicated to hosting OTRS and SugarCRM CE for 10-20 agents/users (plus 5 OTRS customers at any one time). Not an huge demand but still enough to run a little slugish under our current older windows server.[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]The new production server will be:[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]Dell Poweredge R300[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Quad Core Xeon L5410 (2.33GHZ)[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]8GB RAM[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]**My question is: **Which Ubuntu o/s should I install on the server to run VMware on?I imagined I would use Workstation 9 running on Ubuntu desktop (12.04) and the guest to be Ubuntu server (12.04).[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]Thanks in advance for any advice.[/FONT][/COLOR]

---

### Post by Cheesemill on 2013-05-06
Why do you need to install VMware?

Can't you just run Ubuntu Server natively?

---

### Post by morecw on 2013-05-06
> **Cheesemill said:**
> Why do you need to install VMware?

Can't you just run Ubuntu Server natively?

I had at first considered that but of course there's many advantages of running it within vmware and I'm hoping it should be possible to still get a decent performance from the web server

---

### Post by Cheesemill on 2013-05-06
If you are only going to use the server to host VM's then I wouldn't use a host OS at all. Running a host OS brings with it a whole range of performance and security issues.

Instead I would probably go for [ESXi]("http://www.vmware.com/products/vsphere-hypervisor/overview.html") which is a bare-metal hypervisor as this would mean that your VM(s) would run at full native speed, there is no host OS overhead.

---

### Post by morecw on 2013-05-16
> **Cheesemill said:**
> If you are only going to use the server to host VM's then I wouldn't use a host OS at all. Running a host OS brings with it a whole range of performance and security issues.

Instead I would probably go for [ESXi]("http://www.vmware.com/products/vsphere-hypervisor/overview.html") which is a bare-metal hypervisor as this would mean that your VM(s) would run at full native speed, there is no host OS overhead.

[COLOR=#575757][FONT=arial]Thanks for your feedback and sorry that I've only now had chance to respond. I take your point about esxi. Having done some other research it seems like the only rational approach to running vmware on a server and keeping the unnecessary resource drains out of the picture. For the guest server I'll install Ubuntu server 12.04LTS.
[/FONT][/COLOR]
[COLOR=#575757][FONT=arial]
[/FONT][/COLOR]
[COLOR=#575757][FONT=arial]I'm now trying to decide if the free esxi will suffice for a product environment or I need to look at a paid version. Will running vSphere 5.1 Hypervisor be a limitation on performance of my guest? I do not require more than 8GB, however wouldn't the 1 processor really limit the server's performance?
[/FONT][/COLOR]
[COLOR=#575757][FONT=arial]
[/FONT][/COLOR]
[COLOR=#575757][FONT=arial]I would like to be able to remote manage the server, take snapshots, make backups. If I've understood correctly none of this is possible with the free version?[/FONT][/COLOR]

---

### Post by Cheesemill on 2013-05-16
Where did you read about the CPU limitation? AFAIK the only limitation of using the free vSphere hypervisor is a RAM limit of 32GB for the host machine, however, even if this is the case your machine only has one socket so this limitation wouldn't apply.

The ***only*** way to manage a guest OS using VMware is remotely using the vSphere client, you don't have any local access to the guest OS.

If you want another solution to take a look at then check out [Proxmox VE]("http://www.proxmox.com/products/proxmox-ve"), it's an open source virtualisation solution that has many of the features that you would have to pay for if you were using vSphere.

---

### Post by morecw on 2013-05-29
In the end I installed esxi hypervisor and Ubuntu Server as suggested by you. So far I'm extremely pleased with the performance and relative ease it was to install. I was wrong, it has actually got all the basic facilities I needed. 1 processor was actually no performance limit of course because the server has only 1 processor (but quad core which I was able to select). All the remote control facilities were there too. I really think this is the perfect solution for small/medium sized businesses. Thank you so much for the advice.

---

### Post by Cheesemill on 2013-05-29
Glad you got it working, that's the setup I use on my server at home.

---

