---
title: "SMB Network Gateway and File Server - To virtualize or not?"
date: 2008-04-18
forum: Virtualisation
---

### Post by kdkirsch on 2008-04-18
Hello. I would like some input from the community on the merits of using virtualization in a small business server to be used as a network gateway and file server.

The server (Dell PowerEdge 840, Xeon 3040 1.86GHz, 2GB, 2x500GB hardware RAID 1 via 3ware 9650, Ubuntu 7.10) is currently configured as a Samba file server. It is underutilized, and I would like to reconfigure it as a network gateway w/firewall (shorewall), dchp, dns, vpn (openvpn) +  ldap authenticated samba file server. I have done a lot of research on this problem as far as configuration and settings. I found the following sites especially helpful:
[LIST]
[*][Ubuntu 7.10 Small Business Server (version 2.0)]("http://www.rrcomputerconsulting.com/view.php?article_id=3#6")
[*][Installing Xen On An Ubuntu 7.10 (Gutsy Gibbon) Server From The Ubuntu Repositories]("http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories")
[*][XenMyWay-Routed]("http://http://www.shorewall.net/XenMyWay-Routed.html")
[/LIST]
The reason I am leaning towards vitualizing the system (Xen) as opposed to running all of the services in a non-virtualized environment is because my understanding is that I will gain security by isolating the domains with shorewall. Despite the research I have thus far conducted, I have the following questions:
[LIST]
[*]Is virtualization "worth it" in this application?
[*]Is there another virtualization technology I should consider? Please elaborate in addition to simply naming one, citing reasons.
[*]Does virtualization truly enhance security (provided the firewall is implemented correctly)?
[*]Any additional thoughts regarding this plan?
[/LIST]
I really appreciate your feedback. I am planning on beginning testing and configuration once 8.04 is released. Thanks!

---

### Post by HermanAB on 2008-04-18
You do gain a little bit of security, however, that is not the main reason for virtualization.  Virtual servers are easier to manage and provision.  The reason for VMs is because it saves you oodles of time.  To create a new server, just copy a preconfigured VM off a DVD.  To move a busy VM to a bigger server, just tar it up and copy it over.  These things save you immense amounts of time.

---

### Post by kdkirsch on 2008-04-19
> **HermanAB said:**
> You do gain a little bit of security, however, that is not the main reason for virtualization.  Virtual servers are easier to manage and provision.  The reason for VMs is because it saves you oodles of time.  To create a new server, just copy a preconfigured VM off a DVD.  To move a busy VM to a bigger server, just tar it up and copy it over.  These things save you immense amounts of time.

Thanks for your input. I realize that a big advantage of virtualization is the ability to take one VM on and offline without affecting the other VMs. I guess I am still wondering if vitualization is worth it in this context.

---

### Post by HermanAB on 2008-04-19
Once you started using virtual systems, you'll never look back.

---

