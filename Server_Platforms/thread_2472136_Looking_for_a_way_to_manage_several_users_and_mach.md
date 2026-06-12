---
title: "Looking for a way to manage several users and machine deployed in 3 locations"
date: 2022-02-18
forum: Server Platforms
---

### Post by Gerlosv on 2022-02-18
Hello,
I'm looking for a way to centralise the management of ~50 PCs that will be running Ubuntu Desktop (perhaps 20.04 LTS) that will be used by ~40 users in 3 locations. 

Currently we have one Ubuntu 20.04 LTS server providing dns, dhcp and samba file sharing to 5, single-user, Ubuntu 20.04 LTS desktops. Everything is running in our headquarters. 

It's the first time I'm asked to do something similar, so I'm quite confused and I'm not sure what I need to setup. 

Thanks in advance for any helpful hint.
-Gerlos

---

### Post by MAFoElffen on 2022-02-18
This page was just updated last month: [Ubuntu Documentation- SingleSignon]("https://help.ubuntu.com/community/SingleSignOn")

---

### Post by Gerlosv on 2022-02-18
Thanks, I'm giving it a good read! 

From a first look I'm not sure if this approach should be used on LAN only or over the Internet too - any hint?

Thanks!

---

### Post by volkswagner on 2022-02-18
You’ll want VPN (site to site) to make it secure.

---

### Post by MAFoElffen on 2022-02-19
Yes a VPN or any other kind of encrypted tunneling between sites. I was a Cisco CCENT and CCNA. To me, and knowing networking, site to site is just an extension of an Enterprise network.

---

### Post by SeijiSensei on 2022-02-19
Each site will probably work best if you install a server there to handle DHCP, DNS, and routing, with a VPN connection to the main office. I'd put each office in a separate subnet. With 255 hosts in a class-C subnet you should be able to arrange things like this:

192.168.0.0-255 = main office
192.168.1.0-255 = remote 1
192.168.2.0-255 = remote 2
[etc.]

If the remotes don't need to communicate among themselves all that often, I'd probably send all their traffic for 192.168.0.0/16 to the main office router and let it sort out where to go next.

Point-to-point VPNs are really simple to create with OpenVPN. [https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

---

### Post by MAFoElffen on 2022-02-19
> **SeijiSensei said:**
> Each site will probably work best if you install a server there to handle DHCP, DNS, and routing, with a VPN connection to the main office. I'd put each office in a separate subnet. With 255 hosts in a class-C subnet you should be able to arrange things like this:

192.168.0.0-255 = main office
192.168.1.0-255 = remote 1
192.168.2.0-255 = remote 2
[etc.]

If the remotes don't need to communicate among themselves all that often, I'd probably send all their traffic for 192.168.0.0/16 to the main office router and let it sort out where to go next.

Point-to-point VPNs are really simple to create with OpenVPN. [https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

Depending on the mask of the top network, and how many client IP addresses are available in that main/top network hierarchy, their may already be enough addresses for all in that network LAN, depending on how you want to segregate traffic load and security between different 'groups' or suborgs, may bring up considerations if he wants to use subnets or vlans. Remember he is only talking about 50 current clients, not thousands.

But point to point can be done just fine and secure via router to router, and let a router or bridge do it's job. And then alternate routes... These are all network planning issues, that are being brought up that are now blurring the main issue, which is building the foundation infrastructure to support all that, right? Once that is in place, along with a good network plan, it shouldn't matter if the other sites are on another floor of a building, next door, or on another continent.  

What SeijiSensei brought up about a small server at each site, even though it does not need to be thought of as required for the tunnel between sites, it does bring up another very valid consideration, it could be a on the same domain or a (site sub-domain of the main domain for that: "What happens and what do the sub-site clients do, when the site-to-site link is down?"

It would add 3 more servers, one at each site, maybe in a sub-domain, to manage, but if the link fails between sites, is that whole site down at that locale, or if it had a local (fail-over) server, does it go on with business, providing temporary local access control, and caching certain things so that the lights stay on? That is a very valid consideration.

Even though all those are considerations... The first thing to do is to plan and design a good, open infrastructure 'foundation' that supports all of that. All the bells and whistles do not have to be day-one, but should allow them to happen in the growth of that infrastructure. An infrastructure should never be thought of as being finished, with no more work to do on it. There should always be administration & maintenance of, evolving with technology, and room for growth.

Sorry. I'm an IT Consultant. Some times I think too much about the what if's...

---

### Post by TheFu on 2022-02-22
Always use 'slightly odd' subnets when you need to have remote access and perhaps VPN access from people working in hotels, cafes, and homes.

I avoid 192.168.x.x subnets in a business.
I avoid 10.1.x.x subnets.
I avoid 172.16.x.x subnets.

All of those are private networks and meant to be used in this way, but if you are on another network with the same subnet for any network you are trying to reach at a remote location, you won't be able to get there, at least not easily. It is a routing thing.

The easy fix is to use an odd, but still private, subnet.  I use 172.22.21.x, 172.22.22.x and 10.9.9.x.  When I'm in a hotel with a 10.1.1.x subnet or diner with 192.168.1.x subnet, my VPN doesn't have any issue getting to my 172.x.x.x LAN networks.

Add me to the tiny local server idea. Most enterprises don't have redundant GigE or better network connections between sites. If you do, then you can treat each as a LAN subnet. If not, you'll want to keep people working locally even when the WAN is down. When I was connecting remote offices with 150-300 people into our WAN, I'd get redundant ATM connections with redundant DS3 (35Mbps) links into redundant layer-2 switches/routers. That was 20 yrs ago.  If you can get MetroEthernet - go with that. Other broadband like connections have much greater latency which matters, especially if you plan to use VoIP communications.

If you are on a shoe string, you can still get redundant networking using low-end business fibre or cable connection - either get 1 of each and have the router use the one that is "primary" for all traffic until it fails.  If a location cannot get both fiber and coax internet, make the secondary connection some sort of cellular data. Around here, that's $50/month for 50Mbps wireless connectivity. That's less than 1 hour of 1 person's cost per month so people can keep working.

And don't forget backups.  If it were me, I'd prevent any users from being able to save company data on a local storage at all. Make all the software write to storage with RAID1 or RAID10 and proper backups in the main office.

Lots of other considerations, like blocking all external internet access  and forcing it to traverse through the VPN first, then through a proxy. Basically, desktops should never be able to get to the internet directly. They shouldn't ping 1.1.1.1 and get any response. Computer security begins with network architecture.

If there is lots and lots of data accessed by the remote locations, you probably want a local caching server regardless of the file storage/sharing method.
NFSv4 supports both Kerberos and encryption which is deemed secure enough to be used over the internet.  NFS autofs can be fully integrated into Linux logins so that user workstations configure themselves to the user sitting there on that login. This is very powerful and works really well.
I would never use Samba over the internet.  
sshfs really is too slow to be used routinely.
If there are project files to be shared by people in ad-hoc teams, check into a NextCloud server. This can replace Samba/NFS for client access and NC supports SSO + 2FA with little more than a checkbox install and toggle.  Buy some Yubikeys for the people.

In the 1990s, I was a network admin with NIS controlling logins, netgroups, and storage mounts.  NIS was really poor at security, but easy to setup.  In 2008, I setup SSO for a few small companies with fewer than 10 employees. I was less than thrilled with the LDAP DB manager, since every time it was updated, I'd have to completely remove the LDAP POSIX schema first, do the system upgrade, then put everything back.  OTOH, integration with our email, DMS, CSM, CRM, PM and a few other systems and for POSIX logons was relatively easy.  I didn't integrate ssh.  Users had to be taught to only change their SSO password through the email interface, not in any other interface. It was surprising how well that all worked.  Alas, the hassle was just too great and when I left the main company, I don't know what they did.  For my two small businesses, I decided it was too much hassle and ended the SSO.

Getting a centralized, POSIX, user and group DB working again has been on my project list for the last 5 yrs.  For a long time, snap packages didn't work with NFS storage, which I use all over the place here. So you'll definitely want to test that if you use (or are forced into using) snap packages.  The snapd manager has some hardcoded locations for where things are allowed to be which do not align with common locations for user HOME directories under NFS/autofs control and centralized management.  Last month, I asked my LUG where their companies mount HOME directories under NFS ... none of them used where snaps require.  There are over 2500 users in the LUG.

---

