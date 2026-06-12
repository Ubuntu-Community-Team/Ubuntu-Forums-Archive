---
title: "Samba pdbedit error"
date: 2013-06-21
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2013-06-21
Samba Version 3.6.3 on Ubuntu 12.04 tdbsam back end.

I discovered a few accounts we created before the Domain was configured did not have the correct domain name. One was an account named "administrator" intended to be the Samba Administrator account. 

In order to change the domain I ran this command:

[INDENT]# pdbedit -I "DOMAINNAME" -U username[/INDENT]

It worked on a number of accounts when I tried it on "administrator" I get this:
[INDENT]
# pdbedit -I "DOMAINNAME" -u administrator
Unable to modify TDB passwd: NT_STATUS_UNSUCCESSFUL!
Unable to modify entry![/INDENT]

Here is the account information:

[INDENT]# pdbedit -v -u administrator gives the following output

Unix username:        administrator
NT username:
Account Flags:        [U          ]
User SID:             S-1-5-21-1504512832-3249319461-1142831928-500
Primary Group SID:    S-1-5-21-1504512832-3249319461-1142831928-513
Full Name:            Samba Administrator,,,
Home Directory:       \\hamlet\administrator
HomeDir Drive:        U
Logon Script:
Profile Path:        deleted for privacy
Domain:               HAMLET
Account desc:
Workstations:
Munged dial:
Logon time:           0
Logoff time:          never
Kickoff time:         never
Password last set:    Fri, 30 Dec 2005 17:29:27 CST
Password can change:  Fri, 30 Dec 2005 17:29:27 CST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF[/INDENT]

I don't see anything here that looks out of place but I don't know what it all means.

I also tried to delete the account using smb password and it failed:
[INDENT]
# smbpasswd -x administrator
Failed to delete entry for user administrator.[/INDENT]

Is there another way to resolve this?

---

### Post by rsteinmetz70112 on 2013-06-28
I think I fixed it. It was necessary to delet the key from passdb.tdb using the tbdtool then add the user again. This is not reccomended and may have other concequences.

---

