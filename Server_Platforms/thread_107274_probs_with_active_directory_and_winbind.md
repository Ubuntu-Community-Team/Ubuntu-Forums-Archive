---
title: "probs with active directory and winbind"
date: 2005-12-22
forum: Server Platforms
---

### Post by maphew on 2005-12-22
Hi, I'm having troubles getting winbind and active directory working completely. I've followed the wiki howto [https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto](https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto) . The error in auth.log is:

[INDENT]Dec 22 12:52:08 ubuntu-srv sshd[24922]: Invalid user MYDOMAIN+mwilkie from 123.123.123.123
Dec 22 12:52:17 ubuntu-srv pam_winbind[24924]: request failed: NT_STATUS_NOT_SUPPORTED, PAM error was 4, NT error was NT_STATUS_NOT_SUPPORTED
Dec 22 12:52:17 ubuntu-srv pam_winbind[24924]: internal module error (retval = 4, user = `MYDOMAIN+mwilkie')
Dec 22 12:52:17 ubuntu-srv sshd[24924]: (pam_unix) check pass; user unknown
Dec 22 12:52:17 ubuntu-srv sshd[24924]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=geomatt.mydomain.ca
Dec 22 12:52:19 ubuntu-srv sshd[24922]: error: PAM: Authentication failure for illegal user MYDOMAIN+mwilkie from geomatt.mydomain.ca
Dec 22 12:52:19 ubuntu-srv sshd[24922]: Failed keyboard-interactive/pam for invalid user MYDOMAIN+mwilkie from 123.123.123.123 port 1704 ssh2[/INDENT]

I can retrieve active directory users and groups using 'wbinfo' and 'getent group'. 'getent passwd' returns no errors, but doesn't list any AD users either (because none have logged in yet?).

The 'kinit' test does not work. Though it did 3 months ago when I first started setting this up, with ubuntu 5.04. I dist-upgraded to 5.10. The error from kinit is:

[INDENT]kinit(v5): Cannot resolve network address for KDC in requested realm while getting initial credentials[/INDENT]

your help in troubleshooting this matter would be much appreciated. Thank you.

---

### Post by TeeSeeJay on 2005-12-22
Can you post your krb5.conf file contents?

---

### Post by maphew on 2005-12-23
--------- krb5.conf
[logging]
    default = FILE10000:/var/log/krb5lib.log

[libdefaults]
	ticket_lifetime = 24000
	default_realm = MYDOMAIN.CA
# The following krb5.conf variables are only for MIT Kerberos.
	krb4_config = /etc/krb.conf
	krb4_realms = /etc/krb.realms
	kdc_timesync = 1
	ccache_type = 4
	forwardable = true
	proxiable = true

# The following libdefaults parameters are only for Heimdal Kerberos.
	v4_instance_resolve = false
	v4_name_convert = {
		host = {
			rcmd = host
			ftp = ftp
		}
		plain = {
			something = something-else
		}
	}

[realms]
MYDOMAIN.CA = {
	 kdc = corsair.mydomain.ca:88
	 kdc = aurora
	 kdc = eagle
	admin_server = corsair.mydomain.ca:749
	default_domain = mydomain.ca
}


[domain_realm]
	.mydomain.ca = mydomain.ca
	mydomain.ca = mydomain.ca

[login]
	krb4_convert = true
	krb4_get_tickets = true

---

### Post by maphew on 2005-12-23
the log file, /var/log/krb5lib.log, doesn't exist.

LATER: the kinit test *does* work. I didn't know the domain name was case sensitive and needs to be all uppercase:
[INDENT]kinit [email]mwilkie@MYDOMAIN.CA[/email][/INDENT]

---

