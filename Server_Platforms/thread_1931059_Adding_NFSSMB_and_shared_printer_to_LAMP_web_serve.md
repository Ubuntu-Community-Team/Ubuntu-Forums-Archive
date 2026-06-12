---
title: "Adding NFS/SMB and shared printer to LAMP web server with shorewall"
date: 2012-02-24
forum: Server Platforms
---

### Post by tallicafanatik on 2012-02-24
Greetings, and I apologize for the mouthful of a title...

As a former QA engineer with Palm/webOS, I've worked with Ubuntu for about three years now. But, as far as networking and website hosting goes, I've only been at it for a handful of months.
[B]
Here's what I have working:[/B]
Ubuntu (10.10?) desktop running apache2, mySQL, php, with a website posted live and open to the public.

**Here's what I want to add to the same machine:**
1) A directory that I can share with the other machines on my local network (windows xp, vista, 7, ubuntu) via a shortcut (smb?) or network drive (nfs?)

2) Printer sharing


I've tried both numerous times, been through countless posts, and either don't have the full scope of what's needed, or it could be as simple as bad syntax in my shorewall rules. Any suggestions on where to start?

Thanks!

---

### Post by tallicafanatik on 2012-02-25
I understand that this might be a terrible idea. But, it seems like a waste of an always-on resource to have it just serve a simple website.

Is there some specific config info that I could post to be more helpful?

---

### Post by tallicafanatik on 2012-02-28
Still no luck. Here are my shorewall rules, for reference: 
```

#ACTION         SOURCE          DEST            PROTO   DEST    SOURCE          ORIGINAL        RATE            USER/   MARK
#                                                       PORT    PORT(S)         DEST            LIMIT           GROUP
# Drop Ping from the "bad" net zone.. and prevent your log from being flooded..

Ping(DROP)      net             $FW

# Permit all ICMP traffic FROM the firewall TO the net zone

ACCEPT          $FW             net             icmp
HTTP(ACCEPT)    net             $FW
SSH/ACCEPT      net             $FW
FTP/ACCEPT      net             $FW
ACCEPT          $FW             loc             tcp     80,22,21
ACCEPT          loc             $FW             tcp     631
SMB(ACCEPT)     $FW             loc
SMB(ACCEPT)     loc             $FW
ACCEPT          loc             $FW             tcp     imaps,57667
ACCEPT          loc             $FW             udp     5353,161
ACCEPT          loc             $FW             tcp     139,445
ACCEPT          loc             $FW             udp     137,138

```The last four lines are my attempt at opening SMB and printing ports to the local zone, though shouldn't the two SMB(ACCEPT) lines be doing that?

The error I get from a Vista machine when I enter the server's IP in the address bar is this: "192.168.0.153" is not set up to establish a connection on port "File and printer sharing (SMB)" with this computer.

Seriously, I'm open to any suggestions. I'm not sure what to look for at this point, but I'll keep trying on my own anyhow. And, thanks for any help.

---

