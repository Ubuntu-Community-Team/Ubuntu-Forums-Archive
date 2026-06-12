---
title: "How do I give credentials for a user to access Ubuntu VM?"
date: 2022-05-05
forum: Virtualisation
---

### Post by Complete on 2022-05-05
How do I give credentials for a user to access Ubuntu VM?

I am using VMware to set up a Ubuntu 22.04 as a virtual machine.* The host computer is a Windows 10 Enterprise OS.

After getting 403 Forbidden errors while doing simple updates at the command line, I did some research and it seems that my company network admins need to do something on their end for me.* I have been asked to "share the credential to access the VM and also the IP address"

When I right button click on the machine name in the VMware Workstation and select settings, for Network Adapter it shows I have the radio button clicked for NAT and Used to share the host IP address.

[IMG]https://communities.vmware.com/t5/image/serverpage/image-id/95126i3AD201090F48E300/is-moderation-mode/true/image-dimensions/2000?v=v2&px=-1[/IMG]

This did not seem to be useful for him.

And, so, here I am on this web forum for help and answers.* Where can I find the credential to access the VM and where can I find the IP address of the Virtual Machine and/or where can I set these values?

From the terminial app (the command line) I have typed

> ip addr show

I hope this is useful informationi for the Linux system administrator.  But I would still like to know the answer to the credentials question

---

### Post by wildmanne39 on 2022-05-05
Moved to Virtualization sub-forum.

---

### Post by TheFu on 2022-05-05
You cannot use NAT as the network type for VMs if you want to allow remote access. Use a bridge.

None of the stuff below is specific to any VM. VM or physical system, we treat them the same.

I provide users with ssh logins over the phone and talk them through how to setup ssh-keys and copy those keys from their local workstation to the server (ssh-copy-id). Then I warn them that their password will be locked, so they don't have any choice but to use ssh-keys for access going forward.  Passwords are a security failure.

I also setup DNS entries with static IPs for all the servers.  That's part of being an Admin.  In a company, it may be handled by a different, networking, group.

If they want a GUI, which we don't usually provide on any servers, then they can use **x2go**. x2go, is faster than any VNC or RDP remote client and uses ssh for system authentication.  Providing end-users access to the VM host is a security failure. Don't do it.

We don't allow remote access to Windows systems. The security is just too poor for that. I suppose, if the CEO demanded it, they'd have to connect to our VPN first, then they could use any RDP client from their local workstation to connect to a Windows system going through the company VPN.  We won't put any Windows computers on the internet or in the server DMZ subnet zone.  When I want access to a Windows desktop, I use x2go into my main Linux desktop, then from there run some rdp client to connect to the Windows system. Works well enough for quick needs.  I used x2go for a few years daily to connect to my main Linux desktop all day, every day, from the office and from 4 other continents. The worst experience was from Patagonia, but internet there was spotty already. Every where else with at least ISDN connection speeds, working on spreadsheets or doing email was fine. From inside the same building, the performance for office stuff was quite excellent, since our office is Gbps wired.

If the user is fired or needs to have access revoked, then I have a script that locks their account and another script that finds any ~/.ssh/authorized_key*  files and moves those to a different name to prevent remote ssh. This closes the ssh access off.  ssh authentication bypasses the entire password expiration and validation checks, so beware of that.

---

### Post by TheFu on 2022-05-06
Re-read the OP.  I think your IT team is looking to ensure your efforts aren't a huge security problem.  Where I've worked, we'd hunt down unapproved servers and take the hardware away.  If an unapproved wifi AP showed up in any building, it would be taken within 15 minutes. We had wifi monitoring systems on every floor of every building to prevent "power users" from causing security failures for the entire corporation.

If you didn't get approval for the server and weren't provided with a static IP and DNS settings for it, you might be able to talk them out of taking the hardware, but your boss will be notified.  If he was ok with it, then you have cover, which is good. Putting a server on a desktop LAN is usually a bad idea inside a company.  All sorts of things just aren't handled correctly - physical security is one. Backups is another. LAN performance could impact everyone on the same LAN segment and possibly for the entire building.  For under 20 users, just accessing data, it probably wouldn't matter, but the lack of physical security would be a major concern by a professional IT organization.  Remote access over the internet wouldn't be allowed and were I've worked, active steps would be taken to prevent that. Only approved remote access methods using 2FA and going through our VPN concentrators was allowed.  Some people didn't hook up PC-Anywhere to a phone line or try to use those remote desktop 3rd party tools, goToMyPC, etc., which we blocked. RAT isn't allowed.

The IP for any Ubuntu that is supported is shown using the **ip a** command.  But using NAT won't show anything useful for the IT team and you won't have any remote access.  The _virtualbox manual_, chapter 6 explains the different network options. Google will easily find it.

---

