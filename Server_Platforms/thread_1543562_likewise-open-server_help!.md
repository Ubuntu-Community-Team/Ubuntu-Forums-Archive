---
title: "likewise-open-server help!"
date: 2010-08-01
forum: Server Platforms
---

### Post by megamaced on 2010-08-01
I cannot seem to get the likewise-open-server (CIFS server) to work! I have followed the Administrator guides on the likewiseopen website.

These are the steps I have performed

1. Installed Ubuntu 10.04 32BIT
2. Installed all updates, including Backports and Proposed
3. Installed likewise-open-server package
4. Ran sudo domainjoin-cli join DOMAIN USERNAME
5. Restarted
6. Ran sudo lwsm start srvsvc
7. On a Windows 7 domain member, logged in as a user in Domain Admins group, launched Computer Management and attempt to manage the Ubuntu PC
8. Access Denied

Help!

---

### Post by megamaced on 2010-08-01
Ah! Broken Ubuntu packages...

1. I disjoined Ubuntu from the domain
2. Rebooted
3. Uninstalled likewise-open-server
4. Downloaded likewise cifs Ubuntu package directly from Likewise
5. Ran the sh installer
6. Joined to the domain
7. Started srvsvc
8. Bingo, I can connect using Computer Management

---

### Post by Deadpan110 on 2010-08-15
Is this still working for you?
I have attempted installs several times:

1: using the Ubuntu likewise-open and likewise-open-server packages
2: Using the package from Likewise
3: Installing, configuring Ubuntu likewise-open then leaving the domain and removing Ubuntu likewise-open and then using the packages from Likewise.

Performing an nslookup on Ubuntu and the Windows 2008 Server returns the correct results in every scenario.

Using domain-join always succeeds.

Using Computer Manager has varied results every time I try an install (I have done the above methods several times each).

Sometimes I can connect the manager but can not access the shares (permission denied).
Mostly I get the endpoints error.
Mainly I simply cannot connect.

Using a minimal Ubuntu (Lucid) install also requires other dependencies - even for the Likewise package (psmisc for killall).

If anyone has any success or fail stories with any method - please reply to this thread!

REF Likewise-CIFS User Guide:

[http://www.likewise.com/resources/documentation_library/manuals/cifs/likewise-cifs-smb-file-server-guide.html](http://www.likewise.com/resources/documentation_library/manuals/cifs/likewise-cifs-smb-file-server-guide.html)

---

### Post by Deadpan110 on 2010-08-17
UPDATE:
Finally got the Likewise-CIFS (Likewise package) working.

I used a full Ubuntu Lucid Desktop install (I did not have a Lucid Server CD available).

I would still like to find out on what dependencies I must have been missing on a minimal install.

---

