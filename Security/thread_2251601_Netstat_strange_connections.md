---
title: "Netstat strange connections"
date: 2014-11-05
forum: Security
---

### Post by daniels3 on 2014-11-05
Hi guys, Could you please give me idea of the below strange netstat status.
I'm using fail2ban + IPtables. Just opened ports 80,22,25,443 ... 


I also rebooted server, no results the same list of strange connections. Looks like they're reconnecting immediately after reebot. All these connections are UDP connected on higher ports which should be closed (double checked IPTABLES and fail2ban). These UDP connections are marked as dalek.roflcopter.fr:ntp for example. Is it possible that everything is fine and these jobs are run by NTP daemon ? Strange ... I see this for a 1st time.
Rkhunter seems to not finding anything.


I'd appreciate any help




What all these foreign addresse mean ?




netstat -b
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:55503         localhost:11211         ESTABLISHED
tcp        0      0 localhost:11211         localhost:55480         ESTABLISHED
tcp        0      0 localhost:11211         localhost:55503         ESTABLISHED
tcp        0      0 localhost:55480         localhost:11211         ESTABLISHED
tcp        0      0 localhost:11211         localhost:55500         ESTABLISHED
tcp        0      0 localhost:55500         localhost:11211         ESTABLISHED
tcp        0      0 localhost:11211         localhost:55498         ESTABLISHED
tcp        0     52 modernhome.lu:ssh           dsl-212-233-58-18:63199 ESTABLISHED
tcp        0      0 localhost:55498         localhost:11211         ESTABLISHED
tcp6       0      0 localhost:6010          localhost:58834         ESTABLISHED
tcp6       0      0 localhost:58834         localhost:6010          ESTABLISHED
udp        0      0 modernhome.lu:35992         dalek.roflcopter.fr:ntp ESTABLISHED
udp        0      0 modernhome.lu:36428         ntp-2.arkena.net:ntp    ESTABLISHED
udp        0      0 modernhome.lu:37693         diane.ensma.fr:ntp      ESTABLISHED
udp        0      0 modernhome.lu:55082         herbrand.noumicek.c:ntp ESTABLISHED
udp        0      0 modernhome.lu:40394         ntp.tuxfamily.net:ntp   ESTABLISHED
udp        0      0 modernhome.lu:58013         diane.ensma.fr:ntp      ESTABLISHED
udp        0      0 modernhome.lu:59635         ns393034.ovh.net:ntp    ESTABLISHED
udp        0      0 modernhome.lu:43362         box.speed47.net:ntp     ESTABLISHED
udp        0      0 modernhome.lu:43481         ntp.univ-poitiers.f:ntp ESTABLISHED
udp        0      0 modernhome.lu:43768         server6.websters-co:ntp ESTABLISHED
udp        0      0 modernhome.lu:45112         x.ns.gin.ntt.net:ntp    ESTABLISHED
udp        0      0 modernhome.lu:45669         powered.by.root24.e:ntp ESTABLISHED
udp        0      0 modernhome.lu:49132         ntp.univ-angers.fr:ntp  ESTABLISHED
udp        0      0 modernhome.lu:49156         minig.deuza.net:ntp     ESTABLISHED
udp        0      0 modernhome.lu:50550         gw-01.darksky.io:ntp    ESTABLISHED
udp        0      0 modernhome.lu:34492         voyageurs.rail.eu.o:ntp ESTABLISHED

---

### Post by TheFu on 2014-11-05
localhost to localhost is just apps on your system talking to themselves. This is common.
NTP - is the network time protocol. I don't know why the system is looking for so many different NTP server connections. 3 is normally enough and I always use pool.ntp.org - ubuntu has ntp servers too.

I assume that "modernhome.lu" is part of your ISP network-name?

---

### Post by daniels3 on 2014-11-05
Thanks for a quick answer. 
ModernHome.lu is server name - setup on my dedic server in online.net network. 
So can Is it safe to assume that it's normal ? Is there any way / config to limit pool of NTP connections to 3 max 4 ?
I also started to think about blocking all UDP traffic in IPtables (excluting DNS on port 53), but if these connections are safe - it seems to be pointless idea.

---

### Post by TheFu on 2014-11-05
/etc/ntp.conf

If you like, you can block all inbound UDP, but allow outbound DNS, NTP, and openvpn (if you run that). Off the top of my head, I can't think of any others. Clearly, you may want to allow inbound openvpn/udp, if running a server of that type.

modernhome.lu is the name assigned to the public IP?

---

### Post by daniels3 on 2014-11-05
the thing is that I don't have /etc/ntp.conf in my filesystem (debian 14.04 LTS) ... it's a new installation. The only thing I found is /usr/sbin/ntpd and ntpdate executables.
Every time I'm manually running ntpd the list of UDP:NTP connections in netstat is increasing. I'm not a fan of conspiracy theory but is there anything related to [https://www.us-cert.gov/ncas/alerts/TA14-013A](https://www.us-cert.gov/ncas/alerts/TA14-013A) ?

modernhome.lu is the name assigned to public ip (/etc/hosts)

---

### Post by TheFu on 2014-11-05
ntp should only be run as a service.
If there isn't a config file, I'd purge and reinstall the package.

Having the correct time (UTC) is very important for security.

---

### Post by daniels3 on 2014-11-05
installing ntpd, flushing IPTables and reconfiguring all rules adding blocking inbound UDP traffic on 123 port helped. Now netstat is clean. 
No strange UDP:NTP connections. Just some volunteer servers exchanging time when running ntpq -p.
Thanks !!

---

