---
title: "Getting Link-Local NetBIOS name broadcast working [Ubuntu 16.04 LTS + Patches]"
date: 2017-04-14
forum: Ubuntu/Debian BASED
---

### Post by brianddk on 2017-04-14
I'm working with an Ubuntu Xenial release that has been re-bundled to  play nice with various embedded (SoC) systems that are not fully  integrated upstream.  I'm comparing the Xenial system to a different  system running a Debian Jessie release.  Debian seems to work out of the  box, but I'm struggling to get Xenial working as well.  Hoping for tips  on how to config the Xenial SMB stack.
  What I am trying to accomplish is the following headless config:
  
[LIST=1]
[*]Manage from Windows 10 Laptop.
[*]Connect to SoC with a Cat5 crossover cable.
[*]Windows machine and SoC both derive Link-Local 169.254 addresses.
[*]A windows request to ping soc-hostname resolves without extra work.
[/LIST]
  Now this works on Jessie.  I assume (danger) the magic has to do with  NetBIOS or LLMNR or something like that.  Basically, I think the idea  is that both parties somehow broadcast their host name without a DNS.  A  kind of peer-to-peer name resolution.
  Tried to replicate the Windows/Jessie success with Xenial-SoC without success.
  Here's what I tried.
  
[LIST=1]
[*]Xenial-SoC has dhclient. Didn't mess with that.
[*]Installed following apt-get install avahi-autoip winbind libnss-winbind
[*]Added "dns proxy = yes" to smb.conf
[*]Added "hosts:   files wins ... dns" to nsswitch.conf
[*]Added "LLMNR = yes" to resolved.conf
[/LIST]
  Still no luck.  I get about halfway there.  Here's where I end up:
  
[LIST=1]
[*]Windows machine gets link-local IPv4.
[*]Ubuntu SoC gets link-local IPv4.
[*]From windows I can do a NetBIOS probe nbtstat -a soc-hostname
[*]The probe succeeds and I can harvest the IP from the ARP table.
[*]Windows ping ping soc-hostname does NOT resolve.
[/LIST]
  So I feel I'm about halfway there, but it feels like somehow the  Ubuntu SoC is not properly broadcasting enough information for the  Windows machine to decode.  I was surprised that the NetBIOS stack saw  the host, but the TCP/IP stack did not.
  Thoughts?

---

