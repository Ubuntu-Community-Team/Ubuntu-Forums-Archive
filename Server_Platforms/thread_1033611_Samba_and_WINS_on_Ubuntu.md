---
title: "Samba and WINS on Ubuntu"
date: 2009-01-07
forum: Server Platforms
---

### Post by TedHale on 2009-01-07
I inherited a samba server that is a PDC. However, I'm having issues with slow browsing of the network shares as well as some errors that are cropping up related to WINS registration. Here is my smb.conf global section and some of the logs.

The WINS server listed below belongs to an affiliate group and they have told me that it is unlikely that my domain is registering with their server (the one marked ***). When the services start up, there is a rejection by said server when trying to register the name.

So my question is, is it required to have a WINS registration and if so, should I enable my Samba server to do that? If not, what do I pull out of the configuration to stop it from chatting up all these error calls and flooding my traffic?

[global]
    # Core Samba Server
    workgroup = DOMAINNAME
    netbios name = DOMAINNAME
    server string = Facility Fileserver
    log file = /var/log/samba/log.%m
    log level = 0
    max log size = 1000
    interfaces = XXX.XXX.48.101/XXX.XXX.48.255
    bind interfaces only = yes
    admin users = samba
    add machine script = /etc/samba/scripts/addmachine %u
    username map = /etc/samba/username.map

    # LDAP Authentication
    [blocked out]

    # Domain Controller
    preferred master = auto 
    domain master = yes 
    domain logons = yes
    wins server = XXX.XXX.254.4 XXX.XXX.126.12***
    logon script = logon.cmd
    logon path = \\DOMAINNAME\profiles\%U
    logon home = \\DOMAINNAME\%U
    logon drive = H:




smb logs:

libsmb/nmblib.c:send_udp(791)  Packet send failed to 255.255.255.101(137) ERRNO=Invalid argument : 288 Time(s)
libsmb/nmblib.c:send_udp(791)  Packet send failed to 255.255.255.101(138) ERRNO=Invalid argument : 120 Time(s)
nmbd/nmbd_namequery.c:query_name(237)  query_name: Failed to send packet trying to query name DOMAINNAME<1d> : 288 Time(s)
nmbd/nmbd_packets.c:send_netbios_packet(163)  send_netbios_packet: send_packet() to IP 255.255.255.101 port 137 failed : 288 Time(s)

Server Logs:

Jan  7 11:07:05 server nmbd[6165]: [2009/01/07 11:07:05, 0] nmbd/nmbd_incomingdgrams.c:process_get_backup_list_request(683) 
Jan  7 11:07:05 server nmbd[6165]:   process_get_backup_list_request: domain list requested for workgroup DOMAINNAME and I am not a domain master browser. 

Thanks!

---

