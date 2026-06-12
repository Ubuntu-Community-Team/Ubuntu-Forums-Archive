---
title: "DHCP-server will not update scope"
date: 2008-10-16
forum: Server Platforms
---

### Post by frodemt on 2008-10-16
Hi.

I have set up a NAT router based on ubuntu server 8.04.1.

It works well, but when I change IP range scope and restart the server, the changes wont take effect on any client. I have set the lease time to 60 seconds just for testing.

I use windows xp as a client, and I force DHCP recheck with ipconfig /release && ipconfig /renew. This should work or am I overlooking something?

---

### Post by lykwydchykyn on 2008-10-16
Check /var/log/syslog to see if there are any errors restarting the dhcp server or anything odd about the DHCP transaction with the client.  Typically it's all logged.

---

### Post by frodemt on 2008-10-18
It does not give any errors. At least I cant find any in the log.

---

### Post by lykwydchykyn on 2008-10-18
Does it give anything at all?  Usually it logs the transaction, error or no.

EDIT: 
You should see entries like this every time the client renews (This is from one of my dhcp servers):
```

Oct 17 15:20:03 s_all@zaphod dhcpd: DHCPREQUEST for 192.168.170.11 from 00:07:e9:11:87:a6 via eth1  
Oct 17 15:20:03 s_all@zaphod dhcpd: DHCPACK on 192.168.170.11 to 00:07:e9:11:87:a6 via eth1         

```

---

