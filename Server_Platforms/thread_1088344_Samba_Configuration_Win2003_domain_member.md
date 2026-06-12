---
title: "Samba Configuration Win2003 domain member"
date: 2009-03-05
forum: Server Platforms
---

### Post by benjicharlton on 2009-03-05
I am having a specific issue with a Ubuntu 8.10 server ed joined to a win2003 domain
specifically when running 
smbclient -k //PDC/C$

I get the following errors
ads_krb5_get_fwd_ticket: krb5_fwd_tgt_creds failed (KDC can't fulfill requested option)
ads_krb5_get_fwd_ticket failed (KDC can't fulfill requested option)
cli_session_setup_kerberos: spnego_gen_negTokenTarg failed: KDC can't fulfill requested option

On the win2003 event log we get
Event Type:    Failure Audit
Event Source:    Security
Event Category:    Account Logon 
Event ID:    673
Date:        6/03/2009
Time:        1:40:37 PM
User:        NT AUTHORITY\SYSTEM
Computer:    DOMAINCONTROLLER
Description:
Service Ticket Request:
     User Name:        [EMAIL="USER@DOMAIN.COM.AU"]USER@DOMAIN.COM.AU[/EMAIL]
     User Domain:        DOMAIN.COM.AU
     Service Name:        krbtgt/DOMAIN.COM.AU
     Service ID:        -
     Ticket Options:        0x20800000
     Ticket Encryption Type:    -
     Client Address:        10.1.3.50
     Failure Code:        0xD
     Logon GUID:        -
     Transited Services:    -
Further info from Microsoft
This problem occurs because the Kerberos client on Windows 2000-based computers and on Windows Server 2003-based computers examines the Key Distribution Center (KDC) at set intervals to verify that the Service-for-User (S4U) Kerberos extension is supported. By default, the Kerberos client examines the KDC every 15 minutes. Because Windows 2000 does not support the S4U Kerberos extension, event ID 677 messages are logged to the security event log of a Windows 2000 domain controller. In Windows Server 2003, event ID 673 messages are logged to the security event log if the S4U Kerberos extension is not configured. To use the S4U Kerberos extension, you must have a Windows Server 2003 native domain, and you must configure the appropriate computer accounts for constrained delegation.

From what I understand Windows Server 2003 domain controllers accept a new type of Kerberos request, where the service requests a ticket from the client to itself, presenting its own credentials instead of the client's. This extension is called Service-for-User-to-Self (S4U2Self).

Am I seeing a samba or windows 2003 problem....given my PDC has been stable and functional hosting win2000 clients and xp clients perfectly I dont really want to go screwing the registry to test the ubuntu machine within the domain...

---

### Post by HermanAB on 2009-03-06
Looks like you need to upgrade Samba.

Cheers,

Herman

---

### Post by benjicharlton on 2009-03-06
Samba is up to date as per the Ubuntu repos - 

did you mean go outside the repos and go native....

---

