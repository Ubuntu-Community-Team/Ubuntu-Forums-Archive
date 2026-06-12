---
title: "Trouble getting squid-deb-proxy working...."
date: 2012-05-14
forum: Server Platforms
---

### Post by memilanuk on 2012-05-14
So... I'm trying to get squid-deb-proxy working on my 'gateway' VM for a virtual LAN (inside VirtualBox).  Basic server install, 12.04 LTS, set up NAT, dhcp-server, and UFW (configured to deny everything on eth0, and allow everything on eth1 - the 'internal' interface).

NAT and DHCP are working fine.  Other machines on the network are able to connect thru the gateway machine as they should.  squid-deb-proxy, avahi-tools, and squid-deb-proxy-client are installed on the gateway vm, and squid-deb-proxy-client is installed on two other vms on the same internal network, running Xubuntu & Lubuntu.

I *thought* squid-deb-proxy was working as advertised - its supposed to be 'zero config' - and went ahead and updated the Lubuntu vm.  It updated alright - completely skipping squid-deb-proxy as far as I can tell.  No activity from squid on the gateway server as observed on htop, and no change in the size of /var/spool/squid/ (and no entries).  I fiddled around, removed *everything* squid-related, purged, autoremoved, and reinstalled the packages and rebooted just to be safe.  This time I saw squid-deb-proxy show up in the Starting service... list, and it shows up with 9 or 10 threads in htop.  

This time I took a snapshot of the Xubuntu VM and then started the update/upgrade process on it.  Squid was doing *something* - CPU usage shot up to 90-100%, system load started creeping up... but when it was all said and done, still nothing in /var/spool/squid/.

What am I missing here?

---

### Post by ryantierp on 2012-05-14
Having some what the same problem, but I'm using squid3 and it seems that all scripts used during installation still uses the word squid instead of squid3.

After changing all squid references in my setup to squid3 I made it work. Hope this might help you.:)

---

### Post by memilanuk on 2012-05-14
Yes, the above should be '/var/spool/squid3'.  Still doesn't change that squid-deb-proxy, which is supposed to be a zero-conf system, doesn't seem to be caching anything...

---

### Post by memilanuk on 2012-05-15
Okay, found the issue.  squid-deb-proxy uses a separate config file, log files, and cache from the 'normal' instance of squid, to maintain separation.  Most of the pertinent details are described in /etc/squid-deb-proxy/squid-deb-proxy.conf.  Specifically, the cache is stored under /var/cache/squid-deb-proxy.

Hope this saves someone down the road some frustration... this sure is a slick package!

---

### Post by ryantierp on 2012-05-15
Nice to see that it all worked out for you.

---

