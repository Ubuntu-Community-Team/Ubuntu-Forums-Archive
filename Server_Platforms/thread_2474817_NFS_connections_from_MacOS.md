---
title: "NFS connections from MacOS"
date: 2022-05-09
forum: Server Platforms
---

### Post by Greg_Frith on 2022-05-09
Hi all,

I'm struggling to mount an NFS share from MacOS with UFW enabled.  Without UFW the share is working fine.

Essentially I have Ubuntu Server 22.04 running on a Raspberry PI.  The server acts as a LAMP server from which I access a couple of NFS shares for development.  My /etc/exports file looks like this:

```
/var/www   192.168.1.0/24(rw,sync,no_root_squash,all_squash,insecure,no_subtree_check,anonuid=1000,anongid=1000)
/workspace 192.168.1.0/24(rw,sync,no_root_squash,all_squash,insecure,no_subtree_check,anonuid=1001,anongid=1000)

```

On MacOS I use the following command to mount:

```
mount -t nfs -o nolocks,resvport,rw,noowners 192.168.1.35:/workspace ~/localNetwork/workspace;
mount -t nfs -o nolocks,resvport,rw,noowners 192.168.1.35:/var/www ~/localNetwork/www-serer;

```

All is fine with UFW disabled, but when enabled the connections are blocked.  UFW status (when enabled is):

```
Status: active


     To                         Action      From
     --                         ------      ----
[ 1] OpenSSH                    ALLOW IN    Anywhere
[ 2] Apache Full                ALLOW IN    Anywhere
[ 3] 2049                       ALLOW IN    Anywhere
[ 4] 111                        ALLOW IN    192.168.1.0/24
[ 5] OpenSSH (v6)               ALLOW IN    Anywhere (v6)
[ 6] Apache Full (v6)           ALLOW IN    Anywhere (v6)
[ 7] 2049 (v6)                  ALLOW IN    Anywhere (v6)

```

When I try to connect from MacOS I get blocks like the following in the UFW logs:

```
May  9 14:48:34 wharfe kernel: [256634.558229] [UFW BLOCK] IN=eth0 OUT= MAC=e4:5f:01:0d:46:ca:3c:a6:f6:79:4c:24:08:00 SRC=192.168.1.219 DST=192.168.1.35 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=868 DPT=57019 WINDOW=65535 RES=0x00 SYN URGP=0
```

Any pointers would be gratefully received.

:wq

---

### Post by TheFu on 2022-05-09
```
sudo ufw allow from <client IP> proto tcp
```

NFS clients shouldn't use DHCP. Their LAN IPs should be static.
BTW, 22.04 can use either iptables or nftables.  The 22.04 release notes have more information.

If you want to be more restrictive to specific ports, then the answer here: [https://serverfault.com/questions/377170/which-ports-do-i-need-to-open-in-the-firewall-to-use-nfs](https://serverfault.com/questions/377170/which-ports-do-i-need-to-open-in-the-firewall-to-use-nfs) lists the different ports, which are dependent on how NFS is setup for locking, etc.

---

### Post by Greg_Frith on 2022-05-09
> **TheFu said:**
> ```
sudo ufw allow from <client IP> proto tcp
```

NFS clients shouldn't use DHCP. Their LAN IPs should be static.
BTW, 22.04 can use either iptables or nftables.  The 22.04 release notes have more information.

If you want to be more restrictive to specific ports, then the answer here: [https://serverfault.com/questions/377170/which-ports-do-i-need-to-open-in-the-firewall-to-use-nfs](https://serverfault.com/questions/377170/which-ports-do-i-need-to-open-in-the-firewall-to-use-nfs) lists the different ports, which are dependent on how NFS is setup for locking, etc.
Thanks @TheFu, so if I'm interpreting your advice correctly, you are suggesting I give my client a static IP and then allow all TCP traffic from that address through the firewall?

:wq

---

### Post by TheFu on 2022-05-09
> **Greg_Frith said:**
> Thanks @TheFu, so if I'm interpreting your advice correctly, you are suggesting I give my client a static IP and then allow all TCP traffic from that address through the firewall?

:wq

All of this comes down to a judgement decision that only you can make based on the expected attackers in the environment.

If the client and server are on the same subnet, yes, I'd allow all TCP between them, since there will be other protocols needed. Lots of people just setup firewall rules to allow the same subnet full access for UDP and TCP between each system. Judgement call.

But you can look through the link provided for the 5+ ports necessary for NFS, if you prefer to only use the exact rules needed.  You can also use more restrictive NFS sharing - don't share for the entire subnet - just share to the exact clients. That's what I do.  Also, I've never used the 'insecure' option. Never needed it.

And if you want lots of security, NFSv4 supports server-to-server Kerberos authentication, not just IP address-based restrictions. [https://help.ubuntu.com/community/NFSv4Howto#NFSv4_with_Kerberos](https://help.ubuntu.com/community/NFSv4Howto#NFSv4_with_Kerberos) Whether OSX supports that or not is a different question, but NFSv4 has been standard over 15 yrs, so it definitely should.

Judgement.

For example, I'd never allow root from a different machine to have control over NFS storage.  That just doesn't enter my mind, but lots of people choose to allow it for different reasons ... sometimes just for convenience.  To me, a quick ssh into the NFS server to do any chown needed is sufficiently convenient.  Everyone has different needs and risks they are willing/unwilling to accept.

---

