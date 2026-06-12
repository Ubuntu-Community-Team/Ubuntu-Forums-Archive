---
title: "Firewall Configuration"
date: 2007-02-20
forum: Server Platforms
---

### Post by Blair Cooper on 2007-02-20
I need mentoring in setting up a firewall for a small business that has a single server with exchange server.
I need a cheap solution that will frovide firewalling etc.

I need someone to recommend a solution that will meet these requirements.
I need to know how I can easily configure this firewall to configure ports.
I have experience in netwrking and installed windows firewall solutions in the past.
Due to the cost of this it is not a feasable option.

All help will be greatly appreciated.
Many thanks in advance.
Blair

---

### Post by veloce on 2007-02-20
checkout "pfsense".  Of the open source / easy to setup / cheap hardware solutions, it's the most appropriate for a commercial setting.

---

### Post by Macchi on 2007-02-21
For a solution manually built "from scratch" I would install a Ubuntu Server 6.06 LTS (Dapper), and add: 
OpenSSH server for remote administration, 
FireHOL for easy configuration of a firewall through text files,
DenyHosts for increasing the security of the SSH server.
Of course it would be good to add other security software such as chkrootkit, clamav, etc. 

Many solutions are possible but I am trying to keep you within Ubuntu or Debian, instead of directing you to other BSD systems. Right now I do not have time available for describing the installation and configuration details, but I would encourage you to look at the Ubuntu wiki.

---

### Post by Brazen on 2007-02-21
I'm in the same boat as veloce.  Ubuntu is not the best solution for a firewall appliance, and saying it is will be an exercise in aggravation.

Somebody has already done all the hard work for you, give pfsense a try.  For the hardware, you might pick up a cheap barebones 1U or 2U server from Newegg (you may only have 1 server now, but as you grow you will be glad you went with rackmountable hardware).

---

### Post by Macchi on 2007-02-21
> **Brazen wrote said:**
> ...Ubuntu is not the best solution for a firewall appliance, and saying it is will be an exercise in aggravation.

Dear Brazen, When you write that Ubuntu is an "exercise in aggravation" I cannot understand why you use a negative expression for a good, stable and flexible Debian server. 

I hope that we are not being too dogmatic here but the choice of Ubuntu for a firewall would allow a easy and smooth evolution into a gateway up to a desired level of complexity for the business enterprise in question. OK, I confess that I am not being completely neutral in this issue since my heart is closer to Linux, Debian, and Ubuntu, but far from the fierce fights at the the BSD space.

A pragmatic and safe solution could be to buy a simple box that costs around $50, consumes less than 30W of power and furthermore cannot be hacked with conventional methods. An even add OpenWRT to it.

Please tell us later how pfsense performs, I am curious!

---

### Post by Brazen on 2007-02-21
I did not say Ubuntu is an exercise in aggravation, merely using it as a firewall appliance.  Ubuntu is a great distro and I use it and reccommend it on servers and desktops.  Most of my own servers run Ubuntu and I have an Ubuntu laptop at home.

Recommending any one tool for every job is being more of a fanboi.  I believe in using the best tool for the job, and in the case of a firewall/gateway, Ubuntu is not the best tool.  It's like using a knife, it's great if you want to cut something, and it CAN be used to drive a screw, but you're really better off using a screwdriver to drive a screw.

---

### Post by Macchi on 2007-02-22
The Ubuntu server is a "Swiss Army Knife", a base or set of tools suitable for building and experimenting with solutions on a wide range of systems, including gateways. But not necessarily the most optimal solution for just one particular case. This statement would also fit Debian and BSD systems as well, but they are not so easy to used compared to Ubuntu.

I completely agree with you **Brazen** that it is not good to recommend only one tool for   a job. It is better to point at a toolbox and help people to develop the best solution for that case. Given all the complications and limitations on time, resources, skills, pre- and post-conditions, etc.

Anyway, here is a question:
Veloce, Does pfsense works out of the box?

PS: Just for the record, have you tried Ubuntu 6.06 LTS with FireHOL? I personally like it as a basic Firewall on any server. It is much more intuitive to configure than IPtables and allows administration exclusively through ssh, for increased security.

---

### Post by veloce on 2007-02-22
> **Macchi said:**
> 

Anyway, here is a question:
Veloce, Does pfsense works out of the box?



Yes PFSense works "out of the box". You can either run it as a live cd or install it on the firewall machine.   It starts as a firewall that lets nothing through.  

Firewall Rules are then added by directing a browser to the machine and allowing the traffic you want with a gui interface.  I know almost nothing about IPTables and set up the firewall to do everything nice and easily.

The nice thing about this is that it runs well on low spec hardware.  I also like having a physically separate firewall.

For the record, I use IPCop, not PFSense, for my home firewall and for the virtual firewall for my virtual machines.  This is mainly because it has an add in that allows me to limit the monthly data usage for my kids so that we don't exceed our monthly cap.  IPCop also uses less memory than PFSense but is more a "home/hobby" level offering.

> PS: Just for the record, have you tried Ubuntu 6.06 LTS with FireHOL? I personally like it as a basic Firewall on any server. It is much more intuitive to configure than IPtables and allows administration exclusively through ssh, for increased security.

No I haven't used FireHOL.  I will definitely have a look.

---

