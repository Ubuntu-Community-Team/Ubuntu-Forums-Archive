---
title: "Samba causing LsaSrv 6035 on domain controller"
date: 2013-07-03
forum: Server Platforms
---

### Post by funkymike on 2013-07-03
I have an Ubuntu server configured with samba using powerbroker-open for Active Directory authentication. 

The AD integration itself seems to be fine, I can sign on via SSH as an AD user, all the powerbroker commands can look up info in AD, etc. 

However after a recent set of updates delivered via apt, samba AD authentication appears to be broken. 
It was working fine prior to the apt update and subsequent reboot of the server. 

When you try to authenticate to a samba share, it causes a Warning in the System log on the Windows Server 2008 R2 domain controller. 

Source: LsaSrv
Event ID: 6035

During a logon attempt, the user's security context accumulated too many security IDs. This is a very unusual situation. Remove the user from some global or local groups to reduce the number of security IDs to incorporate into the security context.



....

I have checked all group memberships and all the users are only in one or two groups so it's not a matter of being in too many groups. 

Any ideas on how to fix this?

thank you.

---

