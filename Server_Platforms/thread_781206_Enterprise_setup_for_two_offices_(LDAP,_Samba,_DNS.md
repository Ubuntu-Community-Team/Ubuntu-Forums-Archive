---
title: "Enterprise setup for two offices (LDAP, Samba, DNS, WINS etc.)"
date: 2008-05-04
forum: Server Platforms
---

### Post by VSpike on 2008-05-04
Dear forum-

I need some help with high-level stuff - advice on the best way to approach something and the technology to use.

We have two offices, one in the UK and one in Cyprus. I've installed an Ubuntu server 8.04 at each one, running nothing much more than Samba and SSH at the moment. Both sites have Draytek routers, and I've used those to create a LAN to LAN VPN, so that one location has a 192.168.1.0/24 subnet and the other has 192.168.2.0/24. 

The problem is that this link is only ADSL based and will certainly go down or slow down from time to time, and I'd like to achieve good integration between the sites while allowing them to operate independently when needed.

I'm reasonably familiar with Windows networking although I'm still clearer on NT4/NBT/WINS/PDC/BDC stuff than Active Directory. I'm OK with Samba although have never used it as a domain controller. I'm weak on DNS and LDAP.

The clients on the network will be a mixture of XP and Vista (with a couple of my Linux boxes thrown in but I can worry about those myself).

I'd like to achieve the following:-

* Samba as a domain controller
* PDC in Head Office, BDC in Branch Office
* Windows networking clients able resolve names between the two locations
* Single set of accounts between the two servers

I think that this means I need to set up LDAP on the two servers. My questions on this:-

* Do I choose a single root name (e.g. mycompany.local) to cover both sites?
* Can both machines run an LDAP server, each preferring itself for authentication but keeping the two databases in sync automatically?

I also believe I need to set up WINS to allow windows name resolution to work. Again, questions:-

* Can I run a WINS server in each site, like a PDC and BDC where one just caches the other, or automatically keeps in sync with it?

Although the routers serve DNS and DHCP, I wonder what the advantages would be of getting the servers to do so instead. I think it would allow me to set things for DHCP clients like local domain name, WINS server(s), etc. Also I think I could set it up so that DHCP clients are added to local DNS... is this simple to do? Could this then take the place of WINS, since I know the Windows networking can use DNS for name resolution?

Finally, I'm not sure how much to separate the two locations in terms of organisation. I know in Active Directory you can have parent domains, child domains, domain trust, organisational units, etc. I'm not sure how this translates to my current problem. Should each site have its own DNS domain? Should each site have its own LDAP tree? Should each have its own domain with trust between them?

Any help, experience or advice anyone can offer me really would be a big help, because although I know a lot of the stuff here an awful lot is new to me.  Needless to say, I need to set it up fairly fast, so I don't have the time for a trial and error approach either, and can't afford too many blind alleys. If people can help me get my top level design right, I'm happy to RTFM for the dirty details.

---

### Post by Robstarusa on 2008-05-05
I'd setup openvpn before anything else.  Get the 2 sites connected securely, and THEN your servers....

---

### Post by Chayak on 2008-05-06
As much as people on the forums may start breaking out the torches because I'm saying this...

There isn't much that can beat active directory when it comes to administering windows machines.  The group policies are the key there.

For a setup like that I'd have two machines at the remote location running vmware server on linux so you'll have two active directory servers in case one goes down at the site they don't loose service.  You can then use the AD servers to authenticate linux logins as well.

I know it may not be optimal to what you'd like but with windows desktops in the mix AD does make managing them a whole lot easier

At my current site we have linux on all the hardware and a few windows server VMs hosted on our servers and have windows VMs on the desktops should anyone need to run or test on windows.  I want to move to all of the windows VMs to the servers and just let them remote in when they need to but that's a future project.

---

### Post by windependence on 2008-05-06
Getting this to work reliably without a dedicated line is going to be very difficult if not impossible. You may want to try to run two Linux servers, one at each location, and sync them using a cron job every 5 minutes or so if you are going to use this as a file server environment. You may even be able to sync the PDC and BDC this way.

-Tim

---

### Post by HansWilhelm on 2008-05-06
You could use a setup like this.  One server at each site, one configured as a PDC with the primary LDAP backend
 passdb backend= ldapsam:ldap://site-One/, ldapsam:ldap://site-Two/
Then, a BDC at the other site configure to use
 passdb backend= ldapsam:ldap://site-Two/, ldapsam:ldap://site-One/
Then sync the two LDAP servers using syncrepl.  Of course there is more to it like backups, profiles, shares, user management etc.

I'm no authority on Samba, but I do have some experience since I manage three Samba domains.

Check out the Samba Wiki for replication setup: 
[http://wiki.samba.org/index.php/Replicated_Failover_Domain_Controller_and_file_server_using_LDAP](http://wiki.samba.org/index.php/Replicated_Failover_Domain_Controller_and_file_server_using_LDAP)

Also, Samba 3 by example - Chapter 5 Making Happy Users:
[http://us3.samba.org/samba/docs/man/Samba-Guide/happy.html](http://us3.samba.org/samba/docs/man/Samba-Guide/happy.html)

Mit freundlichen Grüssen
Hans

---

### Post by VSpike on 2008-05-08
Thanks for the info.  I agree, AD works well but it's not really an option here.

I already have a VPN tunnel between the two LANs.

I now have the servers running DNS and DHCP with DDNS updates at both ends.  I also have Samba at both sites.

I agree, I'd identified that I need to set up LDAP servers at both sites and use replication to keep them in step.  Then I can put a PDC at one site and a BDC at the other, each using its local LDAP server for authentication.

I'm wondering with Windows now, if I have DNS working do I actually net Netbios name resolution or WINS?

I know >W2K clients and servers with Active Directory do not require it, unless they need to support NT4 clients (which I don't) so I think the Windows client is more DNS focussed now.

---

### Post by HansWilhelm on 2008-05-09
No, you do not need WINS for Windows XP authentication using a Samba PDC.

---

