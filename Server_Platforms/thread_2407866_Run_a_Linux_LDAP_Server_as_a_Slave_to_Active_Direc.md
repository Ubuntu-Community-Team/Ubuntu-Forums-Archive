---
title: "Run a Linux LDAP Server as a Slave to Active Directory"
date: 2018-12-10
forum: Server Platforms
---

### Post by mglau72 on 2018-12-10
I have a client that is currently using LDAP for user authentication. They run 4 Slave LDAP UBUNTU servers on premise. There are a total of 4 more Slaves running at 2 other offices. The Slaves replicate to a Master UBUNTU LDAP server. The LDAP slaves are being used to provide access to specific services like Apache. There is a Samba server in the mix that serves as the domain controller. Users login to the Samba DC for general domain services. I hope that makes sense. 


They need to change their current environment. Their Goal is as follows; They want to run the 8 UBUNTU servers as Slaves to Active Directory. They want to continue to run LDAP, but want to point at AD and become Read Only Copies of AD. Their goal would then be to remove the Master LDAP server as well as the Samba Server. The Users would login to AD for general Domain Use, but still need the ability to login to the LDAP Servers for Linux Services. 


So- the current situation changes by losing the Master LDAP servers and the Samba server that is used as the DC. Added to this- is the LDAP servers become slaves to Active Directory. 


I've found related information out there, but nothing pointing in this specific direction.

thank you.

---

### Post by wildmanne39 on 2018-12-10
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by LHammonds on 2018-12-10
That sounds like an odd setup.  I would think that the Linux servers would need to "join" the AD domain and the services need to be reconfigured to utilize AD authentication.

I have not done anything like this but there used to be a company that provided such an interface called [Likewise Open](https://help.ubuntu.com/community/LikewiseOpen).

Good luck with your project.  I am interested to know how you eventually solve it.

LHammonds

---

### Post by mglau72 on 2018-12-11
Thank you for the reply- I was starting to wonder if anyone would.  I agree- this is indeed an odd setup.  The background of this is a merger of companies.  One- Ubuntu based, the other Windows.  Thank you for the link.  I am reading it right now.  I have a white board in my cube and I have the Linux Slaves sectioned 4 times.   1) AD Auth via a read only 'copy' of AD..., which will happen when the user initially logs in,2) Common Domain Services messaging between companies.  3) LDAP Authentication for services 4) Linux Services like Apache or Nagios, etc.  

The way I understand it - is, the AD Auth is automatic.  The LDAP Auth is requested.  Therefore- it'd be a regular Windows login to the Domain & likely a putty login to Linux.  The initial thought for me is - run the Linux servers separate.  I think the reason to have a copy of AD on the linux servers has more to do with the merger or the company and simple logistics, as in - the AD isn't onsite (which doesn't really matter).  Ok- I'll go back to reading the info on the link you provided... as I'm starting to get a headache already... too early in the day for that.

---

### Post by mglau72 on 2018-12-28
Ok- My understanding of the situation was WAY off.  The current setup is 2 Master Ubuntu servers  running SLAPD.  Slaved to these are 8 Ubuntu servers running SLAPD.  They recently went through a merger and the other company has a windows environment.  What they want to be able to do is Remove the 2 Master Ubuntu SLAPD Servers and then have the 8 Ubuntu Servers be slaved to Windows Active Directory.  I know that linux can be integrated into a windows AD environment, but cannot find anything out there about how to slave a SLAPD server to AD.     Any thoughts?

thank you

---

