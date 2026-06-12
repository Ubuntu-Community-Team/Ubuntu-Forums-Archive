---
title: "Firewalls Beware - Solved"
date: 2013-01-07
forum: Security
---

### Post by bayvista on 2013-01-07
I thought I would tighten up the security on my desktop and install the UFW Firewall. Afterwards, my 2 wireless printers disappeared. It took me a day to work out why. Apparently a Firewall can stop your wireless access. I removed the Firewall and the printers are back.

I don't know why, but will look into it sometime.

---

### Post by leclerc65 on 2013-01-08
My settings is Deny In, Deny Out so I have to add the following entries
 192.168.0.0/24 (Out)
 xxx.xxx.xxx.xxx Allow In,  protocol UDP 
 xxx.xxx.xxx.xxx Allow Out, protocol UDP where xxx.xxx... is the IP address of the printer. Also that address is fixed in my router settings.
  
Living without a firewall is dangerous.

---

### Post by haqking on 2013-01-08
The purpose of a firewall is not to prevent or allow something per se, it is to to give you control over the ingress and egress, meaning it is upto you to configure it correctly.  Security is a process not a product.

it is up to you to configure your firewall for your traffic and requirements, either directly with IPTables or via an interface such as UFW/GUFW.

See here for more information:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

[http://ubuntuforums.org/showthread.php?p=11461477](http://ubuntuforums.org/showthread.php?p=11461477)

---

