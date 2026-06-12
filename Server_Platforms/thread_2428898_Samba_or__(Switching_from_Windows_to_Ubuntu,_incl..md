---
title: "Samba or ?? (Switching from Windows to Ubuntu, incl. Active Directory)"
date: 2019-10-10
forum: Server Platforms
---

### Post by SiliconDragon on 2019-10-10
I want to ditch Windows entirely, replacing servers with Ubuntu and workstations with Ubuntu and Mint. I currently run Windows Server 2012 R2 with Active Directory (AD) with all the bells 'n whistles.

According to my reading, Samba seems to be the logical choice to build a single-server domain controller. The Samba [installation guide]("https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller") says DNS is included, but I see no mention of DHCP. Would I have install DHCP myself and, if so, before or after installing Samba? I'll be adding a time service to my sever as well, sync'ing to NIST nightly; I assume that's not part of Samba either? :)

I'm a senior security developer for a large aerospace company and I know AD inside 'n out. I build my own PCs & network, manage DNS, DHCP, etc. just fine on Windows, so just need a little advice and confirmation from some Ubuntu AD SMEs. :)

Many thanks in advance

---

### Post by DuckHook on 2019-10-11
> **SiliconDragon said:**
> &#8230;I'm a senior security developer for a large aerospace company&#8230;
*Thread moved to **Server Platforms** as the more appropriate forum.*

I'm no server guru, so will leave the suggestions/recommendations to those who are. As a seasoned IT pro, I assume you are aware of how big a project this is&#8230;

A migration of this magnitude is not for the faint of heart.

The only item I'm only remotely qualified to comment on is the network time issue. The following may help: [https://help.ubuntu.com/lts/serverguide/NTP.html](https://help.ubuntu.com/lts/serverguide/NTP.html)

---

### Post by mastablasta on 2019-10-11
have a look at the Zentyal project (Ubuntu based). OpenLDAP can be used insetad of AD.

or Nethserver (CentOS based).

---

### Post by TheFu on 2019-10-11
WARNING: Opinions follow.

Unix has used NIS and NIS+ long before AD existing anywhere.  NIS isn't secure and shouldn't be used, though it is really easy to setup for users, groups, hosts, and NFS maps.  NIS+ only has client tools for Linux, Sun kept the NIS+ server proprietary - Solaris only.

AD is a Windows thing.  AD doesn't scale to the entire Internet, whereas almost all Unix services do. They are designed from the ground up to scale.  Samba is for Windows, not Unix.  Nobody uses Samba in an enterprise if Windows isn't involved.
Network management isn't at the user level. It is system to system.  If you want DHCP, then yes, you should load a DHCP server or let a router handle it.  Same for DNS.  If you are comfortable with virtual machines, it would be smart to compartmentalize by risk and complexity the services into different VMs.

If I were deploying a centralized user management system I'd use FreeIPA.

Let's make a list of commonly needed infrastructure services and a few options:
* Time - There are some competing servers. NTP has been around 30+ yrs. PTP is a newer solution with more security. Coming from Windows, you might be shocked that usec accurate time is possible, unlike the +/- 5 min AD standard.
* Users and password login authentication - openldap, FreeIPA if you want a GUI. I would avoid phpldapadmin, but if you must, only allow localhost connections. Use an ssh tunnel to get to the LDAP server.
* DNS - BIND or run a tiny LAN router in a VM that has DNS capabilities, there is also ZeroConf implemented in Avahi
* DHCP - dhcpd or run a tiny LAN router in a VM
* File sharing - NFS is normal, but there are 20 other methods. Use NFSv4 with server-to-server Kerberos if you care about security. NFS is not user-to-server.
* ssh key/cert management.  I'd love to learn about a solid F/LOSS project that handles this.  ssh is how Unix administration is done.  Without ssh, I couldn't do my job, I couldn't backup any systems, I couldn't use my DevOps tool, or remotely edit system files or quickly mount remote storage over an internet-secure pipe or deploy updates to my websites via rsync or git.  ssh-keys are core to almost all my system to system connections, except when NFS is already setup for system shared storage on the same LAN.

There are almost always 5-20 options for each need, so don't take my list as the only possible answers. On Unix, there are almost always 50 ways to solve any need.  Flexibility is both a curse and the greatest thing about Unix.

I'm not a fan of all-in-one distros like Zentyal (is like MS-SBS was). They don't segment by risk and who would put an authentication server on a firewall and shared storage server?  Just because something is possible, that doesn't mean it is a good idea.

OpenLDAP management is only through LDIF files or complex, picky, network requests that no human should manually have to enter, so if you don't want to be creating LDIF for any DB updates, FreeIPA is the most capable option, but a pain to setup.  FreeIPA is the name for a group of separate F/LOSS projects that Redhat glued together using 50 languages. There are clients for almost every platform. The server was created for RHEL/CentOS and took about 10 yrs to port to Debian/Ubuntu due to the glue programs.  The implementation is not elegant, but the GUI is. I would deploy FreeIPA into a CentOS VM, not Ubuntu, but I've never attempted it on Ubuntu.

BTW, most of the server people here don't work in corporate environments. We are retired or freelancers deploying services to VPS for clients.

---

### Post by LHammonds on 2019-10-11
> **TheFu said:**
> I'm not a fan of all-in-one distros like Zentyal (is like MS-SBS was). They don't segment by risk and who would put an authentication server on a firewall and shared storage server?  Just because something is possible, that doesn't mean it is a good idea.I think those systems are all-in-one in terms of a single ISO image containing all the bits.  When deploying, I think you deploy the base OS and install the package you want...so you could setup a server to act as just a gateway, another to be email, another to do authentication, etc.  Or if you are a mom-n-pop shop with one computer, run it all on one machine.

I have not seen anyone saying it can/cannot be deployed like that or how they would integrate after being separated (such as email authentication connecting to the separate auth server).  This has been in the back of my mind to setup Zentyal or NethServer as a separated, enterprise-type configuration and document how I'd set it up like I've done for Ubuntu and various apps.  If I come across a need for doing something like that, I will document it and put it on my website.

LHammonds

---

### Post by TheFu on 2019-10-11
> **LHammonds said:**
> I think those systems are all-in-one in terms of a single ISO image containing all the bits.  When deploying, I think you deploy the base OS and install the package you want...so you could setup a server to act as just a gateway, another to be email, another to do authentication, etc.  Or if you are a mom-n-pop shop with one computer, run it all on one machine.

I have not seen anyone saying it can/cannot be deployed like that or how they would integrate after being separated (such as email authentication connecting to the separate auth server).  This has been in the back of my mind to setup Zentyal or NethServer as a separated, enterprise-type configuration and document how I'd set it up like I've done for Ubuntu and various apps.  If I come across a need for doing something like that, I will document it and put it on my website.

LHammonds

I hope you are right, but I fear that over 99% of the deployments would be to a single server without understanding the risks involved.  I'd rather run wordpress for 3 months, unpatched, than run an all-in-one Zentyal box.

---

### Post by DuckHook on 2019-10-11
This discussion neatly illuminates the difference between the practices artifically forced upon us through proprietary licensing versus the inherent freedom of FOSS software.

Back in the day, I made a desision to purchase MS SBS because, in the proprietary world, licencing was so expensive that we were forced to shoehorn everything into one box to save on licensing costs.

In the FOSS world, because licensing costs don't exist, we have the freedom to split dangerous tasks across physically separate devices. And since present-day HW costs have basically also been reduced to non-issues, FOSS deployment can be done far more rationally&#8212;and safely&#8212;than in the proprietary world.

@OP

I enthusiastically agree with TheFu here: if you are considering a massive redeployment anyways, it makes sense to make use of Linux's strengths rather than port over Windows' shortcomings. As previously stated, I'm no server guru, but AD and concentrating everything into one box are at best questionable practice and at worst awful. Since you would no longer be handcuffed to such shortcomings, consider embracing the freedom offered by better protocols and distributed hardware (and thereby, reduced risk).

---

### Post by LHammonds on 2019-10-11
> **TheFu said:**
> I hope you are right, but I fear that over 99% of the deployments would be to a single server without understanding the risks involved.  I'd rather run wordpress for 3 months, unpatched, than run an all-in-one Zentyal box.
Well, I'm not going to speculate how most mom-n-pop shops have them installed.

Even if you have one server, a hypervisor might be able to be installed and thus multiple, separate virtual machines could co-exist on the same hardware but separated virtually.

LHammonds

---

### Post by SiliconDragon on 2019-11-10
RE: LHammonds and Fu:

I'm familiar with MS AD and appreciate its DHCP+LDAP integration; I'd like to replicate that if possible, but it's not a requirement.  I'm currently running ESXi on a beefy server and, like Fu, prefer services in separate VMs.

IMHO, Samba is not the best path. I'll look into FreeIPA, but I'm not adverse to rolling my own...after all, I'll learn more from it.

Guys, thx for the tips & opinions, I appreciate both.

---

