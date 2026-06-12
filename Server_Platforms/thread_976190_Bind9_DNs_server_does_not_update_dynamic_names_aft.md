---
title: "Bind9 DNs server does not update dynamic names after IP achnage"
date: 2008-11-09
forum: Server Platforms
---

### Post by zeevikn on 2008-11-09
Setup has DHCP3-Server and Bind9 (as name server), on the same server
DHCP is configured to update dynamic names on Bind9.
Everything works OK, names are being updated and resolved.

Until, the MAC address (and thus the IP address) of a specific host is being changed.
In this case, the DNS server fails to update the new name, tieh the following error log messages:
Nov  9 09:18:35 qa-dhcp-01 named[6203]: client 10.55.1.5#57104: updating zone 'qa.lab/IN': update unsuccessful: EPVM.qa.lab: 'name not in use' prerequisite not satisfied (YXDOMAIN)
Nov  9 09:18:35 qa-dhcp-01 named[6203]: client 10.55.1.5#44484: updating zone 'qa.lab/IN': update unsuccessful: EPVM.qa.lab/TXT: 'RRset exists (value dependent)' prerequisite not satisfied (NXRRSET)

any idea how to solve this ? 
(either on the server side, or on client side configuration)

(has this is a test env. for virtual machines, such scenario of mac address change happens a lot).

Thanks,
Zeevik.

---

### Post by zeevikn on 2008-11-12
Any help will be highly appreciated.
Thanks.

---

### Post by n8bounds on 2009-05-18
I wish I knew too. This is sort of a problem for me. I host MS AD zones on bind9. When this happens, I have to delete the record from the zone manually and bounce named.

---

### Post by zeevikn on 2009-05-18
From what I've learned, change of IP is not supported with dynamic update for bind9.
If anyone knows otherwise, I would be happy to be contradicted :p

Zeevik.

---

### Post by windependence on 2009-05-19
To turn on dynamic update:

   /var/named/etc/named.conf:


 ```
zone "server.yourdomain.com." {
    type            master;
    file            "master/db.server.yourdomain.com";
    allow-update    { 192.168.0.254; };
    notify          yes;
};
```

The allow update  IP address is the address of your DHCP server. 

Then, restart bind. The notify lets any slave servers know what the update is.

-Tim

---

### Post by zeevikn on 2009-05-19
Hi Tim

thanks for the reply.
dynamic updates and notifications are already working on my server.

The problem is dynamically updating an existing entry.

AFAIK, for security reasons, if an A record exists for a host, its IP address cannot be updated through dynamic update.

Zeevik.

---

### Post by Despot on 2009-09-12
I'm also running into this problem...anyone come up with a solution?

---

### Post by Despot on 2009-09-14
My stop-gap solution to this problem has been to change the file permissions on the BIND zone files so that the bind daemon did not have permission to modify them. It seems that BIND updates its internal tables (maybe the .jnl files are used for this?) before updating the zone files, so hostname lookups still work for dynamically assigned hostnames, even though the zone files aren't updated.

Interestingly, the hostname mappings seem to survive a restart of the BIND service. So this measure may be effective even if the server is rebooted or the power goes out.

[edit] Seems there is some Mysterious Force that is resetting the file permissions on the zone files. Lame. I vaguely remember this happening to me before, and that core system directories (like /var/lib/bind, where I keep my zone files) has its permissions reset by some system daemon. Can't remember the name of the daemon for the life of me, though. [/edit]

In troubleshooting this problem, I have discovered an interesting message when running the DHCP server in foreground mode:

> Forward map from blah.example.com to xxx.xxx.xxx.xxx FAILED: Has an A record but no DHCID, not mine.


I haven't figured out what it means yet, though.

---

### Post by Despot on 2009-10-06
Although I seem to be talking to myself, I'm going to keep a log of what I find here. Hopefully it'll be useful to somebody else at some point.

I've discovered this is a problem that only appears on my dual-boot system. If I boot into Windows, the DHCP assignment works and the records are updated. When I reboot into Linux, the records aren't updated correctly unless I freeze the zone, edit the file manually, then thaw the zone, and request a new DHCP lease.

---

### Post by ierton on 2010-10-11
Hi. I have same problem:  using wired and wireless interfaces of my laptop results in those 

> ... 'name not in use' prerequisite not satisfied (YXDOMAIN)... bla-bla-bla .. not mine.

I found an interesing HOWTO [1] saying 
> 
dhclient uses a DHCP-ID to indicate that  a DNS record has been updated by a certain client. The DHCP-ID  is either provided by the client as a configured value, or a hash value automatically computed over a combination of the FQDN of the host and its MAC address. Currently the DHCP-ID is stored  in the DNS (by dhclient) as a TXT record (in lack of a proper DNS record). dhclient will only update the record if it either doesn't exist at all, or if the corresponding DHCP-ID matches. Otherwise it's left as  it is. Therefore, if a DNS file contains a static record for a hostname, that you suddenly want to allow dynamic updates to, the record must first be removed manually. If there is another TXT record with the same owner name, the update will not take place.

This DHCP-ID can be changed on the client, using "clientid" option in dhcpcd.conf (see man dhcpcd.conf). This way we probably can force dhcpcd to use some custom string instead of MACs. I'll try it and see what will happen.

[1] - [http://www.ops.ietf.org/dns/dynupd/secure-ddns-howto.html](http://www.ops.ietf.org/dns/dynupd/secure-ddns-howto.html)

---

### Post by tapori2010 on 2010-10-11
same.

---

### Post by Pythong on 2010-11-02
I'm having the same problem at my work where clients switching from wired connection over to a wirless connection or vice versa arn't updating the DNS record, causing forward/reverse lookup to not work.
 
Has anyone come up with a solution to this problem?

---

### Post by rubensmatos on 2010-11-19
> **ierton said:**
> 

This DHCP-ID can be changed on the client, using "clientid" option in dhcpcd.conf (see man dhcpcd.conf). This way we probably can force dhcpcd to use some custom string instead of MACs. I'll try it and see what will happen.

[1] - [http://www.ops.ietf.org/dns/dynupd/secure-ddns-howto.html](http://www.ops.ietf.org/dns/dynupd/secure-ddns-howto.html)


 I had the same problem, but now ddns is working. I used the tip above, plus some other suggestions described in other forums. In summary:

Change this line in /etc/dhcp/dhcpd.conf from:

```
ignore client-updates;
```to 

```
allow client-updates;
```
Uncomment the following line in /etc/dhcp/dhclient.conf (on the client host):

```
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
```replacing the client identifier by some other ID:

```
send dhcp-client-identifier "ftp-server";
```After this, I restarted the dhcp server:

```
sudo service dhcp3-server restart
```and rebooted the client machine (in fact, a Virtual Machine), to force it to get a new IP: 

```
sudo reboot
```Checking in syslog that the DNS entry was updated by DHCP:

```
sudo cat /var/log/syslog | grep dhcp
```The output had the following lines:

```
Nov 19 16:22:22 localhost dhcpd: uid lease 192.168.0.177 for client d0:0d:4a:6a:07:74 is duplicate on 192.168.0/24
Nov 19 16:22:22 localhost dhcpd: if ubuntu.cloud.modcs.org. IN TXT "311ea5999146ca126ab799de1ab50dabfb" rrset exists and ubuntu.cloud.modcs.org. IN A 192.168.0.177 rrset exists delete ubuntu.cloud.modcs.org. IN A 192.168.0.177: success.
Nov 19 16:22:22 localhost dhcpd: if ubuntu.cloud.modcs.org. IN A rrset doesn't exist delete ubuntu.cloud.modcs.org. IN TXT "311ea5999146ca126ab799de1ab50dabfb": success.
Nov 19 16:22:22 localhost dhcpd: removed reverse map on 177.0.168.192.0.168.192.in-addr.arpa
Nov 19 16:22:22 localhost dhcpd: Added new forward map from ubuntu.cloud.modcs.org. to 192.168.0.109
Nov 19 16:22:22 localhost dhcpd: added reverse map from 109.0.168.192.0.168.192.in-addr.arpa to ubuntu.cloud.modcs.org.

```

The IP for ubuntu.cloud.modcs.org was sucessfully changed from 192.168.0.177 to 192.168.0.9.

I hope this tips help other people that have the same problem. ;)

---

### Post by theotheraether on 2010-11-21
Try adding update-conflict-detection false; to your dhcpd configuration file.  Mind that this allows hosts to steal each other's names, but in a well managed network this shouldn't be a problem.

If you've got a lot of guests/visitors on your network I'd look into grouping and whatnot so you can enable the use-host-decl-names option in the guest group.

---

