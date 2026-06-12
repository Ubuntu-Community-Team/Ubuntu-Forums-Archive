---
title: "samba stops updating user shares"
date: 2009-01-03
forum: Server Platforms
---

### Post by Shwick2 on 2009-01-03
When I share a new folder on my XP box it isn't picked up by samba after a while.

If I immediately connect to the network and share a folder samba picks it up.  After about 10 minutes if I share another folder samba won't pick it up.

I notice the same problem with smbtree- after a while it doesn't list user shares.


After looking at wireshark I could see that samba stopped sending a "Name Query" to my XP box.  XP was still refreshing it's registration about once every 5 minutes though.

I'm using samba 3.0.28a and have no firewalls on the lan, any suggestions are welcome.
	
smb.conf
```

[global]
        netbios name = SHWICK_GATEWAY
        server string = SHWICK_GATEWAY
        interfaces = lo, eth1
        bind interfaces only = Yes
        map to guest = Bad User
        passdb backend = tdbsam
        syslog only = Yes
        name resolve order = lmhosts hosts wins
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE
        os level = 65
        preferred master = Yes
        domain master = Yes
        dns proxy = No
        wins support = Yes
        invalid users = root

[Media]
        path = /home/ftp/
        create mask = 0640
        directory mask = 0750
        guest only = Yes
        guest ok = Yes

```

---

### Post by Shwick2 on 2009-01-10
Can anyone help?


I tried some stuff from the samba checklist.

The pc could ping both the samba server shwick_gateway and itself shwickhomepc.
The server couldn't ping shwickhomepc: "ping: unknown host shwickhomepc".  It also couldn't ping shwick_gateway.
On the server when i do "smbclient -L shwick_gateway" I get "Connection to shwick_gateway failed (Error NT_STATUS_BAD_NETWORK_NAME)".
On the server when i do "nmblookup shwickhomepc" it returns the right ip.  Also "nmblookup shwick_gateway" is successful.

It seems the netbios lookups are successful from the server and the wins lookups are successful from the pc.  The wins lookups aren't successful from the server.

I have a bind setup on my machine, but I don't tell samba to check it because I want it using the wins server.  I set "dns proxy = no".  I get the same results with "dns proxy = yes".

---

### Post by Shwick2 on 2009-01-16
Can someone please help?

---

