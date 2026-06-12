---
title: "Advice Needed:  Thin client scenario"
date: 2007-03-17
forum: Server Platforms
---

### Post by Sternfan on 2007-03-17
I posted this in the general section, which was probably the wrong place...  (So I copied it here)

Looking for advice on Thin Client (or Hybrid Client). Any comments welcome.

Scenario...

PCs - Low end PC = 500mhz/256mb ram. Average PC = 1gz/256mb ram. These will continue to be upgraded as time allows...

Concurrent Users (avg/max): North = 20/30 Central = 20/30. South = 15/20. Some users occasionally roam (a user based at South may logon to a PC at North for instance).

APPS: vast majority of users will use OpenOffice and Email.

Three locations: North, Central and South.

WAN speeds: Connecting North & Central = full T-1 (1.44mb). Connection between South & Central = 1/2 T-1 (768mb).

LAN speeds: all sites = switched, GB to servers and 100mb to clients. Internet is based out of Central = full T-1.

Goal: One terminal server at Central (not purchased yet - assume it meets speed/space needs). I want centralized backups, etc. There will also be a new email/groupware server at Central.

Printers are spread out - multiple IP printers and shared local printers. Users need to print to multiple different printers as needed.

My questions: Does this seem feasible? Is the bandwidth between the locations enough? In investigating thin clients, I ran across "Hybid Clients" - where a lot of the computing takes place on the remote client (local apps), instead of everything on the server - saving on bandwidth usage. I like this idea, but cannot find much information on it - any book recommendations etc? Also, the issue of shared printing with thin clients confuses me - would a hybrid client solve this? There would be an OS there to install and share the printer (seems easier to me). LTSP 5 appears to have just come out (no docs yet) - anyone have any comment on it? What was your experience with it?

Thanks,
Sternfan

---

### Post by elst on 2007-03-18
I don't think that one central terminal server will be enough for this. The standard advice seems to be that you should provide at least 100Mbps bandwidth for thin clients (i.e. modern switched Ethernet or equivalent), and I would generally be very cautious about relying on WAN links for key functions.

Your desktop PCs are sufficient to support a fat-client Linux desktop, especially if you use a light-weight WM, so I would suggest investing in fairly small servers, 1 per site, for NFS file sharing, LDAP etc. with an additional server in the Central location to provide backup, and redundency for LDAP, DNS etc. If you want to go for thin client then add an additional server per site for that. Thin client configurations are much more server-intensive than thick client setups.

I don't know of any books on Linux thin clients or LTSP beyond the LTSP wiki and documentation itself :(.

WRT printing, each thin client uses a small Linux system obtained from NFS. I believe that printer and local device access is provided by networked services that run on each client, but I don't know very much about this area.

---

### Post by Sternfan on 2007-03-19
Thanks for your help.

I had a feeling about the WAN speed not being sufficient.  My big problem is roaming users - users going to all three locations and logging on etc. and wanting their setting to follow them wherever they logon.  In the windows world this is solved with roaming profiles - I have yet to find a comparable solution in the Linux world.

Would a "Hybrid" client work with lower network speeds?  All the apps running locally on the client - just the data etc on the server?  I can't find much info on this anywhere...  though I found it mentioned on the LTSP wiki etc.

Thanks,
Sternfan

---

### Post by elst on 2007-03-19
> **Sternfan said:**
> Would a "Hybrid" client work with lower network speeds?  All the apps running locally on the client - just the data etc on the server?  I can't find much info on this anywhere...  though I found it mentioned on the LTSP wiki etc.

Thanks,
Sternfan

That is pretty much a "thick" client, but I suspect that it's probably the optimum solution. If you look at stats from real-world LTSP deployments it seems like 20-30 clients per terminal server is normal, but you already have the processing power on the desktops, so you can avoid buying in a bunch of additional servers.

Remember that you can use NFS to export both home directories and directories of applications. An automounter automatically attaches directories to workstations via NFS, and I believe that you could use LDAP to create consistent automount mappings regardless of site, so a user whose home directory is on a server at site A can login at site B and still get their home directory from A.

It's been my experience that using UNIX for LANs is underdocumented, too. I suspect that the reason is that the large deployments are mostly in academia, with home-grown network infrastructure and support arrangments that have evolved over a long period of time. Sun and Novell are probably the only *NIX vendors that provide packaged solutions for managed fat client networks, so you may find a lot of useful info by looking for Solaris docs. LTSP mailing lists and IRC channels are certain to have people with real-world experience who can help you out, too.

Best of luck!

---

