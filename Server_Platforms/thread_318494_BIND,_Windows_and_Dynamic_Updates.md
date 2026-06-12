---
title: "BIND, Windows and Dynamic Updates"
date: 2006-12-14
forum: Server Platforms
---

### Post by genesis[OFT] on 2006-12-14
Hi there everyone!

I'm having some issues getting BIND9 to cooperate with Microsoft Windows XP SP2 clients - specifically the way that from where I stand, I can't for the life of me get XP to dynamically update its A record in the DNS zone on the BIND server when it's IP changes.  Details are below:

I have just 1 nameserver at the moment, ns1.internal.lan however, I have done all the server configuration to support a second, namely ns2.internal.lan - this is not the problem though.  Both these nameservers are authoritative for my internal domain, 'internal.lan' and for both this zone and its associated reverse pointers zone, 'allow-update { any; };' is in the zone configuration in the 'named.conf.local' file.  Whenever, with my XP clients having their Primary DNS Server set to the BIND server, I execute 'ipconfig /registerdns' on a XP box, nothing happens.  And after 15 minutes, nothing is registered on the eventlog either.  Nothing appears in /var/log/daemon.log either.

Has anyone else experienced this problem?  I am coming from a Windows 2000 AD environment where this was quite easy to setup so BIND is very confusing for me.  As a piece of side information, I appear to have sucessfully got my DHCP Server communicating with my (one active) DNS Server - the DHCP server is able to automagically update the DNS records when a new lease is dished out.  However, I want to know if this same thing is possible, except instead of a Linux based DHCPD Server, using an XP client instead.  All the obvious "Register this connection's addresses in DNS" checkboxes are already checked on the XP clients, so I really don't know why it's not working.  I've been googling for the last 2 days to no avail - has ANYONE EVER got an XP Client dynamically updating its DNS A records to a Linux BIND DNS Server?

Thanks for the help!

---

### Post by genesis[OFT] on 2006-12-14
*bump*

This is kinda important - I'm sure someone has or hasn't got a solution\suggestion as to running BIND(9) with DHCP and\or a Windows XP client, in terms of dynamic updates.

---

### Post by chrisfay on 2006-12-15
I was trying to get this working on my system, only instead of having xp clients dynamically update my bind server, I wanted my linux clients to update via ddcleint. I was unsuccessfull in configuring bind to accept the updates partially due to convoluted documentation, zero responses from forum members and my laziness. I ultimately went back to using ddclient with zoneedit for my external domains. 

I have come across a few windows update scripts that would essentially provide a method for updating Bind but disregarded them due to my previously explained intentions. I'll see if I can find them.  Sorry I couldn't be more help...

---

### Post by iverger on 2006-12-19
1) On the bind server in /var/log/messages, do you see requests coming from the client to updated named but are being rejected with "access denied"?  If no, then the client has not been configured to send updates. By default XP is configured to send the updates. Can be disabled in the network config or by a Policy on the Windows Domain.

2) Along with 1) you will need to "allow-update" in the zone conf file.
 SAMPLE: /etc/name.d/mydomain.com.conf
###################
zone "mydomain.com" in {
        type master;
        file "master/mydomain.com.zone";
        allow-update { 10.10.1.0/24; };
};
###################

3) Repeat 2) for the reverse zone conf file.


HTH
Bob

---

### Post by iverger on 2006-12-19
Should add that you will need to use the [COLOR="Red"]nsupdate[/COLOR] command from that time forward to update an zone info for static entries.

---

