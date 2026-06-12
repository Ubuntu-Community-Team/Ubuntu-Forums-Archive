---
title: "Strange  Boot Delay... AppArmor?"
date: 2011-10-14
forum: Server Platforms
---

### Post by nicenerd on 2011-10-14
Hey Guys,

Just upgraded from server 11.04 to 11.10 on one of my test servers and noticed a strange 1-2 minute boot delay problem - which I suspect I related to AppArmor. 

```
Oct 14 02:15:42 vm1 kernel: [   17.450104] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 14 02:15:42 vm1 kernel: [   17.466983] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Oct 14 02:15:48 vm1 kernel: [   22.984017] eth0: no IPv6 routers present
Oct 14 02:17:38 vm1 kernel: [  132.822103] type=1400 audit(1318573058.264:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/named" pid=965 comm="apparmor_parser"
Oct 14 02:17:38 vm1 kernel: [  132.822448] type=1400 audit(1318573058.264:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=964 comm="apparmor_parser"
Oct 14 02:17:38 vm1 kernel: [  132.822740] type=1400 audit(1318573058.264:8): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=966 comm="apparmor_parser"
Oct 14 02:17:38 vm1 kernel: [  132.823220] type=1400 audit(1318573058.264:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=963 comm="apparmor_parser"
Oct 14 02:17:38 vm1 kernel: [  132.825165] type=1400 audit(1318573058.268:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=963 comm="apparmor_parser"
Oct 14 02:17:38 vm1 kernel: [  132.825996] type=1400 audit(1318573058.268:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=963 comm="apparmor_parser"
Oct 14 02:17:38 vm1 kernel: [  132.829460] type=1400 audit(1318573058.272:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=967 comm="apparmor_parser"
Oct 14 02:17:38 vm1 kernel: [  133.091505] type=1400 audit(1318573058.532:13): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1037 comm="apparmor_parser"

```As you can see there's quite a delay there (22->132), during that period I can log in via  SSH fine but none of my other services (apache, bind, etc) are getting started until after apparmor is done doing its 2-minute thing. When I check the runlevel all it returns is "unknown" - so very strange indeed. I've checked pretty much every log and can't find anything that would explain this weird behavior. 

Only possibly-related bug I can find that is reported has to do with custom policies and /var/run, etc. Any extra apparmor profiles are straight from the apt packages, and I've done zero customization to it. So not sure if that would be related or not? 

Just curious if anyone has any thoughts on how to go about fixing this little issue. 

Thanks! :D

**UPDATE:** Not sure why, but when I disabled my eth0:0 interface it boots fine now. Odd. Even weirder - when it did the slow boot it would bring up the secondary interface (if I pinged the IP from outside it worked fine), but it wouldn't show up under ifconfig - only eth0 did. Wonder if some binaries didn't get properly upgraded during the switch to 11.10?

---

