---
title: "Can not join Ubuntu desktop into a Windows 2003 Active Directory"
date: 2011-05-03
forum: Server Platforms
---

### Post by wijendra on 2011-05-03
Hi,

I tired to join ubuntu Desktop  into windows active directory, but couldn't join.

Please help me regarding.

Regards,

Wijendra.


**My setup:**
[B]
[COLOR=Black]I have used Ubuntu desktop 10.10 and windows 2003 domain controller.[/COLOR][/B]

**I have Done following:**
1.sudo apt-get install likewise-open 
2**.** sudo apt-get install likewise-open-gui
2. Set Static IP address for Ubuntu Desktop 
3. Add active directory dns server into resolve.conf
4.set the  /etc/nsswitch.conf as hosts:          files dns [NOTFOUND=return]
5. Issued the command as root user "domainjoin-cli join my-company.com Administrator password
6. can ping to the AD domain name


**The error message.**

" domainjoin-cli join ecomoffice.lk Administrator
Joining to AD Domain:   ecomoffice.lk
With Computer DNS Name: testone.ecomoffice.lk

[EMAIL="Administrator@ECOMOFFICE.LK"]Administrator@ECOMOFFICE.LK[/EMAIL]'s password:

Error: Lsass Error [code 0x00080047]

31 (0x1F) ERROR_GEN_FAILURE - Unknown error

---

