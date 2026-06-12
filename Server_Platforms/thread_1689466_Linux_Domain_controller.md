---
title: "Linux Domain controller"
date: 2011-02-16
forum: Server Platforms
---

### Post by crazy4laptops on 2011-02-16
I have 35 windows clients and I have an LDAP based network (Mac) and Active Directory is too expensive so I'm looking for a more economical option. Ubuntu is the most popular distro of linux according to distrowatch, so what can the U do for me as a domain controller?

I have found Mandriva Directory Server as a potential LDC, but I am considering all options for my network. I am trying to get hold of RedHat about their Directory Server, but their 800 number is hard to find. I've looked at SLES, but it cannot host Windows 7 domains.


3 things I need from a Linux based Domain controller-

Windows 7 domain/PDC hosting natively or via package add-on.
Able to connect and replicate a LDAP/Open Directory server. 
Support during normal USA business hours.

If Ubuntu can't help me in the ways I need, I am open to any and all other distribution suggestions. 

Thanks!
-C

---

### Post by koenn on 2011-02-17
what's a Windows 7 domain ?

---

### Post by crazy4laptops on 2011-02-18
A windows domain is similar to a Workgroup where a peer to peer network connection is established for sharing files/printers etc. 

The domain is hosted by a server and all windows clients connect to it to access printers, authenticate to the network, and access shared files/databases. 

The reason I specified Windows 7 is that it uses a newer version of Samba and it has trouble connecting to some of the distros with the older samba installed. 

Did that make better sense?

---

### Post by Vegan on 2011-02-18
The latest version of SAMBA is very powerful, read the manuals closely and you will discover a lot of helpful features.

---

### Post by lykwydchykyn on 2011-02-18
AFAIK there isn't anything available for Ubuntu that isn't available for other Linux distros.  Ubuntu hasn't really taken the directory services bull by the horns.

You can install openLDAP, of course, and various tools to manage it, but you're probably better off going with something a little more "productized" such as the options you've mentioned.

---

### Post by rudelgurke on 2011-02-18
> **crazy4laptops said:**
> Support during normal USA business hours.

Sounds like you're looking for real support, maybe ask what RedHat, Canonical and Novell want and then do your decision.
Problem may be that if you do it yourself with the help of various Howto's, Boards and Mailing Lists you maybe run into problems one day, be it just because LDAP uses a different BDB backend and the data isn't exported to LDIF before the upgrade. Then your clients may complain, you'll have a lot of stress and nothing seems to work.
Maybe then a support contract will be of great use - until of course you've found someone who can deliver the bascially same services.

---

### Post by koenn on 2011-02-18
> **crazy4laptops said:**
> 
Did that make better sense?
Yes.
I know what an Active Directory domain is - I found your post confusing cause directory services and domain control is only available on Windows Server :)

Samba 4 does file sharing and Active Directory-like stuff. There's also OpenLdap and Kerberos. And the Directory services you mention. 
From the sound of your posts, I also think that you should get professional help with this from Canonical, RedHat, ... or one of their local partners or system integrators near you.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-20
I think koenn's idea of samba4 is pretty good :) ive tested this hundreds of times on different distros - and i always choose this over server 2003_R2 or 2008_R2 domains, i just prefer the ability to tune and lockdown aswell as the more secure underlying OS. Samba4 isnt actually ready for production environments yet (One of the only big features missing is printing, of which im expecting to be nearly completed), but ive found it extremely stable, theres a howot here: [http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO) - also, remember to install acl ( sudo apt-get install acl ) and modify fstab ( sudo gedit /etc/fstab ).
While modifying fsatb, remember to add:
,acl,user_xattr,noatime
after defaults or errors=remount-ro

---

### Post by crazy4laptops on 2011-03-22
Sorry for the delay, I was commissioned on another project/system upgrade. Anyways, I am striking out with Mandriva Directory Server. No one on Mandriva's team or forums is interested in helping me solve a problem connecting to their samba/PDC server :(

Anyways, Redhat says that their DS does not host Samba/PDC domains.

Are there any other linux distributions that have a nice GUI for managing directory services and hosting Samba/PCD domains?

---

### Post by lykwydchykyn on 2011-03-22
Try ClearOS (Based on CentOS) or possibly Zentyal (based on Ubuntu).

---

### Post by crazy4laptops on 2011-03-22
I've seen Zentyal, but contacting/calling them is hard for pre-sales technical questions...

ClearOS may just be the ticket! Thanks for the suggestion!

---

### Post by bmullan on 2011-03-31
> **crazy4laptops said:**
> Sorry for the delay, I was commissioned on another project/system upgrade. Anyways, I am striking out with Mandriva Directory Server. No one on Mandriva's team or forums is interested in helping me solve a problem connecting to their samba/PDC server :(

Anyways, Redhat says that their DS does not host Samba/PDC domains.

Are there any other linux distributions that have a nice GUI for managing directory services and hosting Samba/PCD domains?

I recently ran across the ***Resara*** project.

[http://www.resara.org/]("http://www.resara.org/")

I think they've been around for a while working in the education space but they just announced Resara 1.0 release.

They DO have Ubuntu PPA's for Resara.

There is a commercial and a community edition although I don't see that much of a feature difference myself.

Resara says they provide:
[LIST=1]
[*]Open Source
[*]File Sharing
[*]Manage Users & Groups
[*]Auto Drive Mapping
[*]DHCP/DNS Management
[*]Samba 4 Domain Controller
[/LIST]

I contacted them and they are using the latest Samba4 files not the older Samba4 files in the Ubuntu repository.

The Resara website is pretty new as I think it just went up a couple weeks ago.   They are just now getting some documentation out there including an Installation Manual and a User Manual.  Just be aware that the website is a bit thin on info yet.

The source code is there, so is a Resara vmware virtual appliance.  I just added the Resara PPA to my sources and used Synaptic to install the Resara apps I needed.

It did install without mishap and I was able to login via web browser to the Control console.

I just haven't had time to try to connect any Windows Servers yet.

---

