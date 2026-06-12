---
title: "backuppc &quot;tree connect failed: NT_STATUS_BAD_NETWORK_NAME&quot;"
date: 2010-01-09
forum: Server Platforms
---

### Post by metalf8801 on 2010-01-09
I'm trying to use backuppc for the first time and I'm getting this error "tree connect failed: NT_STATUS_BAD_NETWORK_NAME" 

I'm really not sure what the error means and what I need to do to fix it any help you can give me would be great 

Thanks 
Dan

if a network name is an identifier for wireless networks then I'm not sure why I'm getting this error because I'm using a wired connection however is does go threw a wireless router but both the computer I'm trying to back up and the server I'm backing it up to are connected to the router using stranded Ethernet cables so could that be part of the problem?

---

### Post by metalf8801 on 2010-01-09
this is from Last bad XferLOG (errors only) 

Contents of file /var/lib/backuppc/pc/stevexp/XferLOG.bad.z, modified 2010-01-09 18:44:02 (Extracting only Errors)

Running: /usr/bin/smbclient \\\\stevexp\\C\$ -U  -E -d 1 -c tarmode\ full -Tc -
full backup started for share C$
Xfer PIDs are now 4804,4803
Unknown parameter encountered: "hosts equiv"
Ignoring unknown parameter "hosts equiv"
[ skipped 1 lines ]
This backup will fail because: tree connect failed: NT_STATUS_BAD_NETWORK_NAME
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
[ skipped 1 lines ]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
tarExtract: Done: 0 errors, 0 filesExist, 0 sizeExist, 0 sizeExistComp, 0 filesTotal, 0 sizeTotal
Got fatal error during xfer (tree connect failed: NT_STATUS_BAD_NETWORK_NAME)
Backup aborted (tree connect failed: NT_STATUS_BAD_NETWORK_NAME)
Not saving this as a partial backup since it has fewer files than the prior one (got 0 and 0 files versus 0)

---

### Post by hansdown on 2010-01-09
Hi metalf8801.

Are you sure about the IP address?

[http://www.backupcentral.com/phpBB2/two-way-mirrors-of-external-mailing-lists-3/backuppc-21/tree-connect-failed-nt-status-bad-network-name-68895/](http://www.backupcentral.com/phpBB2/two-way-mirrors-of-external-mailing-lists-3/backuppc-21/tree-connect-failed-nt-status-bad-network-name-68895/)

---

### Post by metalf8801 on 2010-01-09
> **hansdown said:**
> Hi metalf8801.

Are you sure about the IP address?

[http://www.backupcentral.com/phpBB2/two-way-mirrors-of-external-mailing-lists-3/backuppc-21/tree-connect-failed-nt-status-bad-network-name-68895/](http://www.backupcentral.com/phpBB2/two-way-mirrors-of-external-mailing-lists-3/backuppc-21/tree-connect-failed-nt-status-bad-network-name-68895/)

I must be doing something wrong the IP address I'm using dhcp and all my computers (I do take my server places from time to time which is why) 

Thank you 
if you can think of anything else that might help me that would be great 

Thanks again 
Dan

---

