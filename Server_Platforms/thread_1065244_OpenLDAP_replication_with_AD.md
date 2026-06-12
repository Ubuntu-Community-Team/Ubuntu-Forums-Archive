---
title: "OpenLDAP replication with AD"
date: 2009-02-09
forum: Server Platforms
---

### Post by om1 on 2009-02-09
I have been searching though google and the forums and haven't found an answer that has been clear.
What I need is to sync OpenLDAP with Active Directory on an SBS 2003 server so if the SBS 2003 Server goes down the OpenLDAP will handle authentication.
Can someone please fill me in on the solution to this problem?
If this works out good this will be the first step to converting this company to Linux. That is my goal.

Edit:
i have already joined the server to the domain and installed OpenLDAP. just need to sync the database of users.

---

### Post by NetworkGuy on 2009-02-09
I think you may be tackling this from the wrong angle.  Look to see if Samba can be used with OpenLDAP as a domain controller.  I know Samba can be made a member server, but I'm not sure about a domain controller.

---

### Post by om1 on 2009-02-09
didn't see any info on using samba as a PDC or BCD in an active directory domain. i know you can use samba and OpenLDAP as a similar solution to an active directory file server. but what I'm trying to set up now is just an backup authentication server for the domain. If I missed the info on setting it up in Samba I would love a link. About the only info I have is an out dated project [http://acctsync.sourceforge.net/](http://acctsync.sourceforge.net/)

---

### Post by HermanAB on 2009-02-09
Samba 3.x can do Win2000 style domain control.  You should consider 'downgrading' to that:
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

Cheers,

Herman

---

