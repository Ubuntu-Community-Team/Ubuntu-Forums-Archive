---
title: "Issue with LDAP/Samba/PDC"
date: 2008-12-19
forum: Server Platforms
---

### Post by TedHale on 2008-12-19
I stepped into a position where there was no overlap with my predecessor. Just as a way of introducing the situation. The server that I inherited runs Samba as a PDC with LDAP for authentication. I rebooted the server today, the last time that I did was ~10/25/08. When the server came back up, the LDAP directory was 'empty.' Looking at my daemons, both LDAP and Samba appear to be running. Looking back at my logs I see a string of errors which google searches have pointed me towards a connection issue with Samba. Here's the block that repeats in the syslog example:

Nov 26 06:27:42 'servername' nmbd[6170]: [2008/11/26 06:27:42, 0] libsmb/nmblib.c:send_udp(791)
Nov 26 06:27:42 'servername' nmbd[6170]:   Packet send failed to 255.255.255.101(137) ERRNO=Invalid argument
Nov 26 06:27:42 'servername' nmbd[6170]: [2008/11/26 06:27:42, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
Nov 26 06:27:42 'servername' nmbd[6170]:   send_netbios_packet: send_packet() to IP 255.255.255.101 port 137 failed
Nov 26 06:27:42 'servername' nmbd[6170]: [2008/11/26 06:27:42, 0] nmbd/nmbd_namequery.c:query_name(237)
Nov 26 06:27:42 'servername' nmbd[6170]:   query_name: Failed to send packet trying to query name 'DomainName'<1d>
Nov 26 06:27:42 'servername' nmbd[6170]: [2008/11/26 06:27:42, 0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_wins(327)
Nov 26 06:27:42 'servername' nmbd[6170]:   become_domain_master_browser_wins:
Nov 26 06:27:42 'servername' nmbd[6170]:   Attempting to become domain master browser on workgroup 'DomainName', subnet UNICAST_SUBNET.
Nov 26 06:27:42 'servername' nmbd[6170]: [2008/11/26 06:27:42, 0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_wins(341)
Nov 26 06:27:42 'servername' nmbd[6170]:   become_domain_master_browser_wins: querying WINS server from IP 0.0.0.0 for domain master browser na
me 'DomainName'<1b> on workgroup 'Same as DomainName'
Nov 26 06:28:03 'servername' nmbd[6170]: [2008/11/26 06:28:03, 0] nmbd/nmbd_become_dmb.c:become_domain_master_query_fail(252)
Nov 26 06:28:03 'servername' nmbd[6170]:   become_domain_master_query_fail: Error 0 returned when querying WINS server for name 'DomainName'<1b>.

Now, I've not changed anything in either of these service configurations. I have, however, changed a few passwords for security reasons. Could this be an issue of one of the admin passwords being changed. If so, where/what can I look at/do to fix this. 

Here is what is in the log.smbd file:

[2008/12/14 06:25:09, 0] param/loadparm.c:map_parameter(2649)
  Unknown parameter encountered: "valid_users"
[2008/12/14 06:25:09, 0] param/loadparm.c:lp_do_parameter(3394)
  Ignoring unknown parameter "valid_users"
[2008/12/14 07:53:12, 0] lib/util_sock.c:get_peer_addr(1217)
  getpeername failed. Error was Transport endpoint is not connected

which also goes on repeating.

Thanks for any help and ideas.

---

### Post by gpredrag on 2008-12-20
In your smb.conf:

what is set for wins server (if it's 255.255.255.101 that's not valid host address)?

is there set "valid_users" for some share, shouldn't it be "valid users"?

"testparm -v" should complain about that and other configuration errors.

If you have changed LDAP admin password, have you remembered to notify samba about it using "smbpasswd -W"?

---

### Post by TedHale on 2008-12-20
> **gpredrag said:**
> 

If you have changed LDAP admin password, have you remembered to notify samba about it using "smbpasswd -W"?

This was exactly the problem. The issue is resolved now. The fact that the LDAP database appeared to be empty via phpldapadmin was a red herring as to what was happening. Examining the boot logs actually tipped me off that the samba password was out of sync with the LDAP admin password via an error describing Samba's inability to connect to the LDAP server as root. I appreciate the response!

---

