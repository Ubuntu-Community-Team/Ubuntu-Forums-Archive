---
title: "/etc/hosts and resolv.conf revert to old data after reboot"
date: 2008-08-16
forum: Server Platforms
---

### Post by elyse on 2008-08-16
I'm trying to set up some servers in Ubuntu 8.04. 

Changes made to /etc/hosts and /etc/resolv.conf are not being maintained across reboots, regardless of whether they are made manually or using the Network Management tool.

I tried loading the resolvconf package but it does not seem to make a difference. 

I can't even figure out where the old data is being stored: before I loaded resolvconf, I removed the line "search data-raptors.com" from resolv.conf and grepped everything under /etc for that line, without finding it. But it was back in the file after a reboot.

I tried using the Network Management GUI tool to remove the search line, set the domain name value, and add a line to the hosts list. And after a reboot all of my changes had reverted. I even logged in as a real root user, to see if the changes would stick better than with kdesu, etc. involved, and I tried logging root into a Gnome session in case that GUI worked where the one in KDE did not. Still no dice.

I have worked with and admined UNIX-variant systems since 1985, and while I like many aspects of the Ubuntu distro, the broken admin feature (which seems to get worse with each release) is about to drive me to something that doesn't try as hard to emulate the Windows not-adminnable-by-humans feature.

Could someone tell me what files I need to delete, edit of lock to make the changes I need. 

In particular, I need to have hostname and hostname -f behaving according to spec, so I need to know where the data from the  Domain Name field on the General tab of the Network settings widget is supposed to be stored.

---

### Post by elyse on 2008-08-16
Additional data: I switched my machine to a static IP, and now the resolv.conf file is updating when I make changes in the Network settings tool, but everything is completely lost across a reboot: I have to re-enter everything but the machine name. 

Is there a file where I can put the data so that resolvconf will pick it up?

I have saved the settings as a 'location'. Is there a way to force that to be loaded at boot by default? The documents didn't mention anything about that.

I am still not getting valid behavior from hostname -f. It just returns the hostname, not the FQDN. There are tools and commands I need (like 'net ads join') that seem to be fussy about the values returned by hostname vs. hostname -f.

---

### Post by StickyStyle on 2008-08-17
by any chance do you have a DHCP server on your network that may be resetting the files?

---

### Post by windependence on 2008-08-17
> **elyse said:**
> 
I have worked with and admined UNIX-variant systems since 1985, and while I like many aspects of the Ubuntu distro, the broken admin feature (which seems to get worse with each release) is about to drive me to something that doesn't try as hard to emulate the Windows not-adminnable-by-humans feature.



You wanna explain what you mean by broken admin feature?

-Tim

---

### Post by elyse on 2008-08-17
Regarding dhcp servers: As I noted in my second message, I switched the machine to a static IP and the data is now getting nuked rather than stepped on, but the settings I create are still getting over-ridden. There doesn't seem to be any way to set a default configuration that won't get stepped on during boot.

Regarding broken admin functionality: my settings are getting over-ridden  and I have found no documentation explaining, in enough depth to allow troubleshooting, where the data gets set from. An opaque admin interface is broken by any sensible definition: that's part of the problem with the Windows registry.

I am also adding an RHEL server to the same AD domain. It took about an hour, and only because the documentation I was using gave me some odd winbind settings I needed to tune. No strange error messages that blocked the process. No spending a weekend with config files changing behind my back with no way to track where the changes are coming from.

I like Ubuntu as a working environment, but that does me no good  if I can't set up and rely on the environment I need for my work.

---

### Post by elyse on 2008-08-18
Googling, I have found a LOT of people complaining about resolv.conf getting overwritten. And no clear instructions on how to fix it in the general case. 

I haven't figured out what keeps putting invalid line formats in my /etc/hosts.

At the moment, I'm suspecting that the vmware host connections are setting off the dhcp client updater of resolv.conf even though the host has a fixed address outside the dhcp range and the vmware dhcp config doesn't supply the necessary values.

I've seen references to putting something in /etc/dhcp3/dhclient-enter-hooks.d, but not details of what is needed, or what to do (safely) if there are already scripts in hooks.d that do things to make_resolv_conf.

I think I'm going to try sudo chattr +i /etc/resolv.conf and sudo chattr +i /etc/resolv.conf, but I still haven't found settings that make resolver happy and generate the correct hostname -f output.

---

### Post by johndoe32102002 on 2008-12-02
After installing the latest version of KVPNC, I noticed it fails to clean the clean the /etc/resolv.conf, keeping the VPN DNS servers in the file.  I was unable to change it without a reboot wiping it back to the VPN DNS servers.  Running a sudo chmod 444 /etc/resolv.conf was a futile effort.

Solution:
Press Ctrl+SysRQ+E (where the SysRQ is usually on the PrtSc button).
Then, in terminal, type init 6 (to reboot saving the changes to runlevels)

Hope this helps,
John

---

