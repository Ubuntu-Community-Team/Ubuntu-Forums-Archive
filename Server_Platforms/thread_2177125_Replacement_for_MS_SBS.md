---
title: "Replacement for MS SBS ?"
date: 2013-09-27
forum: Server Platforms
---

### Post by qsnap on 2013-09-27
Hi, some information i can get about linux servers, 
Our office is about of 25 peoples and we have old SBS 2003 server with  exchange 2003 running and ubuntu linux server with mysql server running  in domain. 


  	So how things goes with one linux server handling emails (importing  from exchange 2003 database)  and running mysql DB on same machine. Is Linux server handles emails like exchange with same features and which  would be the better linux server system?

  	
As of now trying out clearOS in vmware and also got info about zentyal SBS. zentyal uses ubuntu any ubuntu expert will able to guide me any proper direction here.. 
Thanks..

---

### Post by Peter_Watkins on 2013-09-27
You can use Ubuntu as a replacement for an Active Directory server using Samba 4. However Ubuntu has dropped behind in terms of Samba 4 support in their Long Term Support version -- they're using an alpha version of Samba 4 which is very broken.

If you're going the Ubuntu + Samba 4 route, I would go with 13.04 Raring instead of 12.04 Precise. Raring has a release version of Samba 4.

As far as Exchange goes--I have no experience with that. Hopefully someone else will chime in.

---

### Post by sandyd on 2013-09-28
> **qsnap said:**
> Hi, some information i can get about linux servers, 
Our office is about of 25 peoples and we have old SBS 2003 server with  exchange 2003 running and ubuntu linux server with mysql server running  in domain. 


  	So how things goes with one linux server handling emails (importing  from exchange 2003 database)  and running mysql DB on same machine. Is Linux server handles emails like exchange with same features and which  would be the better linux server system?

  	
As of now trying out clearOS in vmware and also got info about zentyal SBS. zentyal uses ubuntu any ubuntu expert will able to guide me any proper direction here.. 
Thanks..
If your going for exchange, check out zimbra - bit heavy, but pretty good exchange clone
If your strapped for ram (zimbra requires 2G+ from experience with all features enabled), check out axigen - you fall under the 100 account free limit

---

