---
title: "BackupPC help! Invalid network name"
date: 2006-09-22
forum: Server Platforms
---

### Post by ahood on 2006-09-22
Please help,

I am at a loss to the message I get when attempting a backup with backuppc of a Windows98 host. Ihave configured backuppc properly I believe.

> 
Backup aborted (tree connect failed: ERRSRV - ERRinvnetname (Invalid network name in tree connect.))


I have found a message at [BackupPC User Maillist]("http://www.mail-archive.com/backuppc-users@lists.sourceforge.net/msg01068.html") saying that the Windows share was not being shared.

I have determined that a possible reason is that the Ubuntu Dapper Server edition (command line only) machine may not be able to see the network share.

I have configured iptables to accept all INBOUND traffic from my LAN  machines (192.168.0.0/24). However, this does not resolve the problem.

How do I get the Ubuntu Dapper Server edition machine able to see the Windows share?

Is there another possible explanation?

Any suggestion will be greatly appreciated.

Dr. Hood

---

### Post by chrisfay on 2006-09-22
Assuming you have Samba configured correctly you might try:

```
sudo smbtree
```

...If you see your Windows share,  verify that it's entered the same in your backup config.

---

### Post by ahood on 2006-09-22
Thank you for replying. The command you gave was indeed helpful and led me to the solution.

The solution was to rename the backuppc host.pl file to the exact name of the netbios name of the host. So, my host (i.e., the computer being backed up) netbios name is drhood and I had created a host.pl file named 'DrHood.pl'. The caps in the DrHood.pl resulted in backuppc not finding the host.pl file for host drhood. Once, I renamed the DrHood.pl to drhood.pl, it works!!!!!

Thanks again.

Al

---

