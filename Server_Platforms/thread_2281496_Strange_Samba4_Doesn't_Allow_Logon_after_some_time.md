---
title: "Strange Samba4 Doesn't Allow Logon after some time"
date: 2015-06-07
forum: Server Platforms
---

### Post by andrew.coughlin@gmail.com on 2015-06-07
Samba version 4.1.6-Ubuntu

I have a situation where I have a Windows 2008 R2 machine joined to a Samba4 domain and after some time, (5-10 minutes) it no longer allows logins "The user name or password is incorrect".  I have checked the obvious, password is right.  When I try to do a kinit <username that is [EMAIL="failing@MYDOMAIN.LOCAL"]failing@MYDOMAIN.LOCAL[/EMAIL]> I get Warning: Your password will expire in X Days".  I see in the windows host in the security log an audit failure with the following details:

An account failed to log on.

Subject:
    Security ID:  SYSTEM
    Account Name:  <servername>$
    Account Domain:  MYDOMAIN
    Logon ID:  0x3e7

Logon Type:   2

Account For Which Logon Failed:
    Security ID:  NULL SID
    Account Name:  <username>
    Account Domain:  MYDOMAIN

Failure Information:
    Failure Reason:  Unknown user name or bad password.
    Status:   0xc000006d
    Sub Status:  0xc000006a

Process Information:
    Caller Process ID:    0x974
    Caller Process Name:    C:\Windows\System32\winlogon.exe

Network Information:
    Workstation Name:    <servername>
    Source Network Address:    127.0.0.1
    Source Port:  0

Detailed Authentication Information:
    Logon Process:  User32 
    Authentication Package:    Negotiate
    Transited Services:    -
    Package Name (NTLM only):    -
    Key Length:  0

The strange thing is if I reboot my samba4 server everything starts working fine.  I have Samba4 configured as an active directory server.  I have checked to make sure the krb8.conf file has my domain in all capitals.

---

### Post by andrew.coughlin@gmail.com on 2015-06-08
Fixed my issue, for those that have this problem do the following 

Make sure you have logging enabled in the smb.conf like the following:

#Logging
        # Debug logging information
        log level = 3
        log file = /var/log/samba/samba.log.%m
        max log size = 50
        debug timestamp = yes

tail -f samba.log.%m  

you will see something like: 
[2015/06/08 11:48:18.298300,  3] ../source4/auth/kerberos/krb5_init_context.c:80(smb_krb5_debug_wrapper)
  Kerberos: Too large time skew, client time 2015-06-08T11:42:00 is out by 378 > 300 seconds -- <Servername>$@MYDOMAIN.LOCAL
  Kerberos: Too large time skew, client time 2015-06-08T11:42:00 is out by 378 > 300 seconds -- <Servername>$@MYDOMAIN.LOCAL

This would mean the time skew is to far off from the client to the server.  After set the time on the client correctly logins started working.

---

