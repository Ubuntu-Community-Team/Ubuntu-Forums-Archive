---
title: "Trouble with SYSVOL replication on Ubuntu 16.04, Zentyal 5.07"
date: 2017-03-01
forum: Ubuntu/Debian BASED
---

### Post by keenmouse on 2017-03-01
I have three Zentyal Developer version 5.07 DCs (Ubuntu 16.04, Samba 4.5.4) on a home office network. The PDC is a mini-PC and the other two are currently virtual machines.

DRS replication is working fine, but SYSVOL replication is not happening. I'm aware that Samba does not currently handle SYSVOL replication itself, and that there are suggested methods for handling it [on the Samba wiki.]("https://wiki.samba.org/index.php/SysVol_replication_(DFS-R)")

I'm trying to determine how Zentyal 5 normally handles SYSVOL replication so that I can troubleshoot the problem. I have posted [in the Zentyal forums,]("https://forum.zentyal.org/index.php/topic,30761") but have not received a Zentyal-specific response.

My PDC was originally just an additional DC to which I transferred FSMO roles from a Zentyal 4.2.5 DC, so it's possible that whatever replication method Zentyal uses was never initialized on the current PDC. At any rate, it appears that none of the methods from the Samba wiki are in use because there are no rsync, unison, or osync cron jobs on any of the DCs. The DCs do all have rsync installed. So I suppose it's still possible that the additional DCs run rsync to pull from the PDC by some method other than cron and the rsync daemon on the PDC was never set up.

Anyway, at this point, I'm in over my head. There's a [StackExchange post]("https://unix.stackexchange.com/questions/158879/commands-for-successful-domain-controller-replication-on-ubuntu-samba4-zenty") that talks about using 'sudo net rpc share migrate files sysvol'. I don't know anything about that command or whether Zentyal is using a related method. I don't know what I should be looking for in logs or anything else that might be relevant.

I'm sure I could get the rsync method working, but I'm resistant to doing it that way in case a future Zentyal update screws it up, and I'd also just like to be using whatever the native method is.

I'm happy to provide any other information that would be helpful in figuring this out. Thanks in advance.

---

### Post by howefield on 2017-03-01
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by keenmouse on 2017-03-07
I've seen other people get help with Zentyal issues here and was really  hoping for some help. Is there anyone that can even point me in the  right direction?

---

### Post by drgrieg on 2017-10-03
Keenmouse. Have you found anything yet on the sysvol replication for Zentyal? I’m looking for a good method as you are besides rsync.

---

### Post by keenmouse on 2017-10-04
It turns out that Zentyal currently does not do SYSVOL replication at all. I went with the rsync solution. Below is my procedure, adapted from [here]("https://wiki.samba.org/index.php/Rsync_based_SysVol_replication_workaround"). Not the solution I wanted, but it does the job. Remember, since replication is only one direction, ensure that any Active Directory tool you use is talking to the PDC.

Have you looked into [UCS]("https://www.univention.com/products/ucs/")? It's what I'd like to be using instead of Zentyal, but I can't install it on my Z83-II devices. It has full SYSVOL replication built-in.

**On PDC:**

[LIST]
[*][FONT=Lucida Console]sudoedit /etc/rsyncd.conf[/FONT]
```

[SysVol]
path = /var/lib/samba/sysvol/
comment = Samba Sysvol Share
uid = root
gid = root
read only = yes
auth users = sysvol-replication
secrets file = /var/lib/samba/rsyncd.secret

``` 
[*][FONT=Lucida Console]sudoedit /var/lib/samba/rsyncd.secret[/FONT]
```
sysvol-replication:*[new password]*
``` 
[*][FONT=Lucida Console]sudo chmod o-r /var/lib/samba/rsyncd.secret[/FONT] 
[*][FONT=Lucida Console]sudo systemctl enable rsync[/FONT] 
[*][FONT=Lucida Console]sudo systemctl start rsync[/FONT] 
[*]Zentyal web admin > Firewall > Packet Filter > Configure Rules
[LIST]
[*]Create 'rsync' service, TCP/UDP destination port 873 
[*]Create allow rule for rsync service 
[/LIST]
  
[/LIST]
**On BDC:**

[LIST]
[*][FONT=Lucida Console]sudoedit /var/lib/samba/rsync-sysvol.secret[/FONT]
```
*[password from above]*
``` 
[*][FONT=Lucida Console]sudo chmod o-r /var/lib/samba/rsync-sysvol.secret[/FONT] 
[*][FONT=Lucida Console]sudo crontab -e[/FONT]

Add this:
```

*/5 * * * *     rsync -XAavz --delete-after --password-file=/var/lib/samba/rsync-sysvol.secret rsync://sysvol-replication@*[hostname of PDC]*/SysVol/ /var/lib/samba/sysvol

``` 
[/LIST]

---

