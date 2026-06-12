---
title: "Small network design."
date: 2006-06-18
forum: Server Platforms
---

### Post by david_7872 on 2006-06-18
Hello,

[This was posted to [email]ubuntu-users@lists.ubuntu.com[/email], but did not get much response.]

I am volunteering at a small school to help them set up a ~10 user office/admin network, and was hoping to get some advice from you folks before proceeding. (Learning as I go here....)

Here is what we have on hand:

Hardware:

- About 8 Dell Desktops P4 2.2 Ghz and faster.
- A few laptops to be used at the office and at home.
- Two laser printers with attached NetGear mini-printservers.
- A SnapServer storage appliance.

I might be able to get funds for a cheap desktop to run as a "server", but as I think a Windows Server license will not happen now, perhaps Ubuntu would be an option.

Software:

- Sufficient quantity of Windows XP volume licenses.
- Sufficient quantity of Office volume licenses.
- Sufficient quantity of Symantec Corporate AV licenses.
- Sufficient quantity of Symantec Ghost licenses.


Right now, all machines are in one room, but they need to expand to a 2nd location in a different building. Both locations have broadband Internet access, so I am planning to link them with a couple of SOHO VPN routers. (Maybe a wi-fi link in the future... some complicating factors right now.)

The current setup has the SnapServer running in "peer-to-peer mode" with a manually configured user account for each machine that needs access. Microsoft Office is installed individually on each machine. Symantec AV/Ghost are not installed yet.

I would like to wipe all machines and start fresh, but I am need of some guidance to help me create a "maintainable" network.

I have free reign to redesign the network from the bottom up, and I would like to do things right. So, the more detailed advice I can get, the better.

The network needs to be simpler to maintain than it is now.

Here are four things that the current setup does not have:

1) A single install image I can use to re-image a machine if/when it gets trashed by a user.

2) Centralized user authentication management. (Not the peer-to-peer mess we have now.)

3) Traveling user desktops, so that any user can use any of the machines.

4) Centralized management of updates for Windows/Office/AV/etc.

Any and all advice welcome.

Thanks,
David

---

### Post by spyke01 on 2006-06-19
I can only help a small amount, but here goes
1) ghost is what you need, i dont know if there is a linux equivalent
2) Active Directory(AD) in windows(2000 usually) will take care of this, im sure that the same thing can be done in ubuntu, just manage all users on it and use it as a domain for the xp boxes
3) i like freenx for this, its secure and runs on ubuntu and windows
4) share a directory on the ubuntu server, you can use samba to share it with xp

hope this helps, im by far no expert, and i hope you can get some good answers on this one

---

### Post by Glut on 2006-06-19
For roaming desktops and WSUS (Windows updates) you need a proper windows based server. Samba can do central authentication, but not much else. Ghost seems to be your poison of choice for redeployment, although windows server comes with RIS which is a poor man's substitute. It works alright. 

So Linux by itself can do authentication. You need to decide if roaming profiles, etc. are worth the cost of windows server.

---

### Post by dk_pa on 2006-06-19
I'm not sure if you'll like this software or not but the Trinity Rescue Kit has a cloning utility.

[Trinity Rescue Kit Usage Page](http://trinityhome.org/trk/usage.php)

It's very easy to use and very fast.  Basically boot into the disk on two computers.  Set one up to recieve and the other sends.  Next thing you know it's done.  I think it took around 10 minutes using 600 MHZ PIII's.  It was pretty slick and didn't have any problems.

Obviously the downside is that you have to be able to connect to the network and you don't have an image to tote around with you but if you will be doing all your imaging through the network (or on the network) it could work very well.

---

### Post by david_7872 on 2006-06-20
[QUOTE=Glut]For roaming desktops and WSUS (Windows updates) you need a proper windows based server. Samba can do central authentication, but not much else. Ghost seems to be your poison of choice for redeployment, although windows server comes with RIS which is a poor man's substitute. It works alright. 

So Linux by itself can do authentication. You need to decide if roaming profiles, etc. are worth the cost of windows server.[/QUOTE]


Hmm.. So Windows Server it is.

But I will need to learn quite a bit before deploying that.

Any leads on where to learn about windows network design and deployment?

Thanks,
David

---

### Post by dughutch on 2006-06-21
There are entire course curriculum teaching windows and network design... than being said, it would appear your situation could be solved with a single switch and everything attached to it.

Before jumping in with a Windows server, especially for a project like this, please check out contribs.org and SME7 server.  It is a linux server based on CentOS 4.3 (Generic Red Hat Enterprise Server 4.3) made for just what you are doing, small workgroups tied to a single server.  I have had great success with it from back in the SME6 days.  SME7 can act as your Windows domain controller (for Windows authentication), can provide file and print services, act as your firewall to protect your workgroup, act as a proxy cache for internet traffic, act as your mail server, provide webmail, email antivirus, anit-spam, etc.  It is a very useful distro.

I'm actually an MCSE for both NT4 and W2K (but not 2K3 as I've now seen the light! ;).  You might be tied to Windows clients, but you really can replace almost everything else with open solutions.  Feel free to contact me if you'd like more help on setting this up.

Douglas

---

### Post by spifbv on 2006-06-21
[QUOTE=david_7872]
Here are four things that the current setup does not have:

1) A single install image I can use to re-image a machine if/when it gets trashed by a user.

2) Centralized user authentication management. (Not the peer-to-peer mess we have now.)

3) Traveling user desktops, so that any user can use any of the machines.

4) Centralized management of updates for Windows/Office/AV/etc.

Any and all advice welcome.

Thanks,
David[/QUOTE]

Start here:

[http://howtoforge.com/samba_setup_ubuntu_5.10](http://howtoforge.com/samba_setup_ubuntu_5.10)

Pay particular attention to page 4 for advice on setting up roaming profiles.

Now, on an item by item basis:

1) If you're intent on running Windows on the desktops and laptops, then Ghost should work fine.  For Ubuntu I believe using a preconfiguration file is the preferred method:  [http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html](http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html)

2) The HowToForge article I linked to above should take care of this.

3) Ditto

4) I'm not sure what you are looking for that isn't provided by Windows Update and your AV software's update feature.

---

### Post by dughutch on 2006-06-21
spifbv

     Thanks for the links.

     I'd like to know about setting up a network with only Ubuntu clients... any tips / tricks to centralized authentication (like Fedora Directory Server?) and user accounts, folder repliciation (like Novell iFolder), etc... I've plenty of experience doing that with Windows, but I'm in a unique spot of being able to start a network from scratch for someone who is anti-MS...  It would appear Novell has a bundled solution ([http://www.novell.com/products/openworkgroupsuite/](http://www.novell.com/products/openworkgroupsuite/)) but I'd love to do this all open... 

     Any ideas?

---

### Post by spifbv on 2006-06-21
[QUOTE=dughutch]spifbv

     Thanks for the links.

     I'd like to know about setting up a network with only Ubuntu clients... any tips / tricks to centralized authentication (like Fedora Directory Server?) and user accounts, folder repliciation (like Novell iFolder), etc... I've plenty of experience doing that with Windows, but I'm in a unique spot of being able to start a network from scratch for someone who is anti-MS...  It would appear Novell has a bundled solution ([http://www.novell.com/products/openworkgroupsuite/](http://www.novell.com/products/openworkgroupsuite/)) but I'd love to do this all open... 

     Any ideas?[/QUOTE]

My advice is, if you have the budget to get a vendor supported solution, do it.  Ultimately it will better serve the cause of Linux adoption, especially if you aren't already a Linux expert.  Later on you can introduce other distributions etc. as you learn how to do complex configuration management in Linux.

That said, iFolder is open source; here's how to set it up on Ubuntu:

[https://help.ubuntu.com/community/iFolder](https://help.ubuntu.com/community/iFolder)

---

### Post by Pnut on 2006-06-21
i have  a small office / home office (soho) network and i have a ubuntu dapper file server for my files with centralized authentication using m0n0wall that i built from one really old compaq LOL.  it allows wireless on a dedicated interface (monowall OPT interface) then i have lan and wan interfaces respectivly.  Im using compact flash memory 128mb with an 40 pin ide converter.  I have radius for authentication and i created a vpn gatway to my LAN so i can access everyting it from the outside world.  maybe monowall could work for you centralized authentication/network firewall??  Just a suggestion

---

