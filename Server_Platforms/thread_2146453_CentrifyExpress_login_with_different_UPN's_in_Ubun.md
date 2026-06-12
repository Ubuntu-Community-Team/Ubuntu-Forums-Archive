---
title: "CentrifyExpress login with different UPN's in Ubuntu's LTSP"
date: 2013-05-18
forum: Server Platforms
---

### Post by viniciusferrao on 2013-05-18
Hello dudes,
 
I know that this should be an unsupported scenario but I'm not able to authenticate in a LTSP environment using CentrifyExpress with a different UPN. I just want some help to isolate the problem and report it to the real responsible.
 
CentrifyExpress is an open source service that integrate with Active Directory for authentication purposes.
 
The mais problem is: the authentication process appears to only supports the Pré-Windows 2000 login schema. We can login using the username from the main domain without problems. But when I try to authenticate with the UPN suffix things got wrong.
 
As example, let's imagine an user named john from the CONTOSO domain: CONTOSO\john or [email]john@contoso.com[/email]
 
John can login simply as john, but cannot login as [email]john@contoso.com[/email]; this is fine in this case.
 
But Peter is CONTOSO\something.peter or [email]peter@subdomain.contoso.com[/email] and unfortunattely Peter cannot login as [email]peter@subdomain.contoso.com[/email] but as something.peter the login is accepted.
 
This issue only happens in the graphical user interface login. We can ssh to a machine escaping the @ in the username without problems, in example:
 
peter\@subdomain.contoso.com can log in successfully through ssh.
 
Thanks in advance,
 
PS:
 
/var/log/auth.log authenticating as [email]username@subdomain.contoso.com[/email]
 
May 17 15:46:27 northshire adclient[824]: INFO AUDIT_TRAIL|Centrify Suite|PAM|1.0|100|PAM authentication granted|5|user=subdomain.username(type:ad,subdomain.username@CONTOSO.COM) pid=2565 utc=1368816387581 status=GRANTED service=sshd tty=ssh client=lig1-07.CONTOSO.COM
May 17 15:46:27 northshire adclient[824]: INFO <fd:25 PAMIsUserAllowedAccess2 > audit User 'subdomain.username' is authorized
May 17 15:46:27 northshire sshd[2565]: Accepted password for [email]username@subdomain.CONTOSO.COM[/email] from 146.164.37.217 port 54327 ssh2
May 17 15:46:27 northshire adclient[824]: INFO AUDIT_TRAIL|Centrify Suite|PAM|1.0|300|PAM account management granted|5|user=subdomain.username(type:ad,subdomain.username@CONTOSO.COM) pid=2565 utc=1368816387582 status=GRANTED service=sshd tty=ssh client=lig1-07.CONTOSO.COM
May 17 15:46:28 northshire adclient[824]: INFO AUDIT_TRAIL|Centrify Suite|PAM|1.0|200|PAM set credentials granted|5|user=subdomain.username(type:ad,subdomain.username@CONTOSO.COM) pid=2565 utc=1368816388085 status=GRANTED service=sshd tty=ssh client=lig1-07.CONTOSO.COM
May 17 15:46:28 northshire adclient[824]: INFO AUDIT_TRAIL|Centrify Suite|PAM|1.0|500|PAM open session granted|5|user=subdomain.username(type:ad,subdomain.username@CONTOSO.COM) pid=2565 utc=1368816388086 status=GRANTED service=sshd tty=ssh client=lig1-07.CONTOSO.COM
May 17 15:46:28 northshire sshd[2565]: pam_unix(sshd:session): session opened for user subdomain.username by (uid=0)
May 17 15:46:28 northshire adclient[824]: INFO AUDIT_TRAIL|Centrify Suite|PAM|1.0|200|PAM set credentials granted|5|user=subdomain.username(type:ad,subdomain.username@CONTOSO.COM) pid=2586 utc=1368816388117 status=GRANTED service=sshd tty=ssh client=lig1-07.CONTOSO.COM
May 17 15:46:29 northshire sshd[2565]: pam_unix(sshd:session): session closed for user subdomain.username
May 17 15:46:29 northshire adclient[824]: INFO AUDIT_TRAIL|Centrify Suite|PAM|1.0|600|PAM close session granted|5|user=subdomain.username(type:ad,subdomain.username@CONTOSO.COM) pid=2565 utc=1368816389811 status=GRANTED service=sshd tty=ssh client=lig1-07.CONTOSO.COM

---

