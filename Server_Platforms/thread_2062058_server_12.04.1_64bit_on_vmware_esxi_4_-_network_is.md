---
title: "server 12.04.1 64bit on vmware esxi 4 - network issues: dhcp vs static"
date: 2012-09-24
forum: Server Platforms
---

### Post by leifeste on 2012-09-24
greetings.  the shop i work in currently runs vmware esxi 4 (u3, i believe).  we have been a red hat shop on the linux side, and have a fair number of rhel guest systems, but we were recently asked to set up an ubuntu server.  i chose 12.04.1 since it an lts release.  i'm not really a vmware person, but they helped me through it and now i can create new guests with no problem.  unfortunately, i'm having a problem with ubuntu and i can't figure it out.  (i've installed a lot of *nix systems over the years, so this isn't my first rodeo.  just my first vmware one :)  i've even installed ubuntu a few times on standalone hardware.)

the initial installation went fine.  it used dhcp and got an ip, gateway, dns, etc.  i set up ssh, logged into the box, did some local admin stuff, etc.  (i was attempting to build a template version, so adding some local accounts, ldap auth, etc.)  installed vmware tools, etc. everything was fine.

once done, i cloned it.  the new clone used dhcp and got an ip, gateway, etc.  i then went into /etc/network/interfaces and changed eth0 from dhcp to static, and set the various other required values.  (i'll skip over how long it took me to figure out the new way resolv.conf is created, but i got that figured out too.)  anyway, the issue is that after i change to static the guest starts dropping about 20% of it's receive packets.  nothing shows up in any logs, but eventually (between minutes to an hour or two) services stop responding from outside, and eventually ping as well.  restarting network services from console brings everything back, but then the same thing happens.  everything looks fine as far as i can tell: resolv.conf, ifconfig, route, etc.

i even went so far as to copy *exactly* the values just given to me by the dhcp server, but enter them as static values.  but as soon as i restart networking services or reboot i get packet drops.  we also switched between using a vmxnet3 vmware nic and an e1000 vmware nic.  no change.

this is not related to any mac address issues from the udev persistent thing mentioned by some people that i can tell (it doesn't move from eth0 to eth1, etc., there is no mac value stored in any udev files, etc.).  it's just that if i use dhcp i get no dropped packets, if i use static i get dropped packets.

just for fun, i spun up a new 12.04.1 guest and made no changes at all to it, except to set a root password.  then i set values in the interfaces file to make it static.  same problem.  so i installed an 11.10 guest and did the same thing (but i could edit resolv.conf directly on it).  same problem.  so i installed a 10.04 guest and did the same thing (again, editing resolv.conf directly).  it worked just fine, as i would expect a system to - static ip, no dropped packets.  i even re-used ips across these (bringing the old one down before bringing a new one up, of course).  i then did another 12.04.1 install and stopped it before it could get an ip via dhcp, and manually entered values, just to see if maybe that would make it behave differently.  same thing.  but if i switch it to dhcp - no dropped packets.  (all these are 64 bit server versions.)

i've googled and googled this, and i've not been able to find anything that has revealed to me what i might do to fix this.  i hate asking for help in general, but i'm hoping someone here either can point out something obvious, or from experience with ubuntu 64-bit server on vmware esxi 4 can tell me what i might be doing wrong.  i'm at a loss, and the vmware guy that normally does the red hat guests doesn't know what i might be doing wrong either.  (the rhel servers have always spun up fine, and taken static ips on these same subnets just fine.)  if you'd like me to post any values from config files or output of any commands, just mention them.  in the meantime, i guess i'm going to get the dhcp server to always give the same ip to this specific mac address so i can get a static ip via dhcp - but that's not really a solution, just a workaround.  thanks!

---

