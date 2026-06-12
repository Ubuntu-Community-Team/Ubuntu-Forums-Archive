---
title: "OpenLDAP - Ignores PAM Password Complexity"
date: 2013-09-04
forum: Server Platforms
---

### Post by concord on 2013-09-04
I have an Ubuntu 12.04 LTS Server running OpenLDAP Server for several client servers.  When I expire a password for a user within the directory they are prompted to change their password but the settings I have configured in PAM are ignored.  Complexity is not enforced and passwords are able to be reused.  If I expire a password for a local user on the server all seems fine.  Here are the relevant lines from the /etc/pam.d/common-password file

[SIZE=1]password	requisite			pam_cracklib.so retry=3 minlen=12 difok=4 ucredit=1 lcredit=0 dcredit=1 ocredit=2
password        [success=1 default=ignore]      pam_unix.so obscure remember=4 use_authtok try_first_pass sha512
password	requisite			pam_deny.so
password	required			pam_permit.so[/SIZE]

I've read several of the howtos related to LDAP and I don't see what I'm missing.  Can anyone point me in the right direction?

Thanks in advance,

- Frank

---

### Post by concord on 2013-09-05
I figured it out so I'm posting this here, hopefully to help someone else out.

It turned out that there were a couple of things wrong with the configuration.  What I've ended up with (that actually fixed the issue) is this.

[SIZE=2][FONT=Times New Roman]password	required			pam_cracklib.so retry=3 minlen=12 difok=4 ucredit=1 lcredit=0 dcredit=1 ocredit=2 
password	required			pam_pwhistory.so use_authtok remember=4
password	[success=2 default=ignore]	pam_unix.so obscure remember=4 use_authtok try_first_pass sha512
password	[success=1 user_unknown=ignore default=die]	pam_ldap.so remember=4 use_authtok try_first_pass
password	requisite			pam_deny.so
password	required			pam_permit.so
[/FONT][/SIZE]

I had originally had the control set to 'requisite' which apparently has a different effect than 'required'.  Requisite can fail and pass control back to the application where as Required is what is needed in this case.

Also, even though pam_unix.so has a password history component (this I'm just told) there was a pam_pwhistory.so shared object (DLL) available for just this purpose.  I added it to the configuration along with the argument 'remember=4' to enforce policy.  

Everything is working now.  Hopefully this info will be helpful to someone else.

---

