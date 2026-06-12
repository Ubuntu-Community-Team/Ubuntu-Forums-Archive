---
title: "FTP NAT problem"
date: 2019-10-04
forum: Server Platforms
---

### Post by qubaa on 2019-10-04
Have PC on LAN configured as FTP (Windows 10, Firewall OFF) - 192.168.1.20
Between pc's on LAN work ok but where connecting behind SERVER got logs:

```

10/04/2019 18:24:08 (not login 156.67.113.86<--192.168.1.20:21) "220 Xlight FTP Server 3.9 ready..."
10/04/2019 18:24:08 (not login 156.67.113.86-->192.168.1.20:21) "USER backupall"
10/04/2019 18:24:08 (not login 156.67.113.86<--192.168.1.20:21) "331 Password required for backupall"



```

And thats all. After that connection is closed.

masquerade is on

POLICY
```

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

```

On server got rule on firewall
```

iptables -I FORWARD -p tcp -d 192.168.1.20 --dport 21 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -i enp4s0 --dport 2000 -j DNAT --to 192.168.1.20:21
iptables -I FORWARD -p tcp -d 192.168.1.20 --dport 50000:50100 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -i enp4s0 --dport 50000:50100 -j DNAT --to 192.168.1.20:50000-50100

```

Please help...

---

### Post by TheFu on 2019-10-04
Don't use plain FTP. Use sftp, which uses the same port that ssh uses.  ssh needs 1 firewall rule.   Port/tcp.  If it is on the internet, not using port 22 will really help your attack logs be smaller.  I pick some high port, like 63590/tcp, setup that port in my ~/.ssh/config file and never worry about it again.  All ssh-based tools from that client, using that userid, will pick up the non-standard port automatically. That includes sftp, scp, rsync, rdiff-backup, sshfs, and any other backup tool using libssh.

Or better, use a better backup tool which handles incremental, versioned, backups, through an encrypted channel.

Plain FTP should have died in 1999.  If you need more reasons search this phrase "stop using plain ftp"

---

