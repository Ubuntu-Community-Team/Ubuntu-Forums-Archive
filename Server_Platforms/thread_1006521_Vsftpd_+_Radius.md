---
title: "Vsftpd + Radius"
date: 2008-12-09
forum: Server Platforms
---

### Post by mastertaf on 2008-12-09
Hello all,


I am trying to put in place a FTPs server that will authenticate with Radius.

I have searched all over the web to find a Ubuntu guide for this to no avail. Somehow this seems to be a fairly simple procedure for Red Hat distributions (fedora,CentOS). Here is what i have tried as yet:

installed libpam-radius-auth
modified /etc/pam.d/vsftpd:

> # Standard behaviour for ftpd(8).
auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own.  Do not enable
# pam_ftp.so.

# Standard blurb.
@include common-account
@include common-session
#
@include common-auth
auth    required        pam_shells.so
auth    sufficient     /lib/security/pam_radius_auth.so DEBUG

i configured /etc/pam_radius_auth.conf:

> #  pam_radius_auth configuration file.  Copy to: /etc/raddb/server
#
#  For proper security, this file SHOULD have permissions 0600,
#  that is readable by root, and NO ONE else.  If anyone other than
#  root can read this file, then they can spoof responses from the server!
#
#  There are 3 fields per line in this file.  There may be multiple
#  lines.  Blank lines or lines beginning with '#' are treated as
#  comments, and are ignored.  The fields are:
#
#  server[:port] secret [timeout]
#
#  the port name or number is optional.  The default port name is
#  "radius", and is looked up from /etc/services The timeout field is
#  optional.  The default timeout is 3 seconds.
#
#  If multiple RADIUS server lines exist, they are tried in order.  The
#  first server to return success or failure causes the module to return
#  success or failure.  Only if a server fails to response is it skipped,
#  and the next server in turn is used.
#
#  The timeout field controls how many seconds the module waits before
#  deciding that the server has failed to respond.
#
# server[:port] shared_secret      timeout (s)
#127.0.0.1      secret             1
x.x.x.x         secret             3

#
# having localhost in your radius configuration is a Good Thing.
#
# See the INSTALL file for pam.conf hints.


When i try to log in with our cryptocard solution that uses radius, the connection fails. here is the output of /var/log/auth.log:
> Dec  9 13:23:34 testapache vsftpd: pam_unix(vsftpd:auth): authentication failure; logname= uid=0 euid=0 tty=ftp ruser=testuser rhost=192.168.120.191  user=testuser


the same configurations works great on one of our Fedora 2 systems so i am really stumped.

Thank you for any help you can provide.

---

### Post by mastertaf on 2008-12-11
Well i hope this can help a future admin trying to secure their VSFTPD installation:

To solve the problem, i checked the difference between Fedora and Ubuntu on the /etc/pam.d/vsftpd file.

**Fedora**
> #%PAM-1.0
auth       required	pam_listfile.so item=user sense=deny file=/etc/vsftpd.ftpusers onerr=succeed
auth       sufficient   /lib/security/pam_radius_auth.so
auth       required	pam_stack.so service=system-auth
auth       required	pam_shells.so
account    required	pam_stack.so service=system-auth
session    required	pam_stack.so service=system-auth

**Ubuntu server 8.04**
> # Standard behaviour for ftpd(8).
#auth	required	pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own.  Do not enable
# pam_ftp.so.

# Standard blurb.
@include common-account
@include common-session
#
@include common-auth
auth	required	pam_shells.so
auth    sufficient     /lib/security/pam_radius_auth.so


i verified the common-auth file and noticed this line:

auth	requisite	pam_unix.so nullok_secure

so i changed the /etc/pam.d/vsftpd:
> # Standard behaviour for ftpd(8).
#auth	required	pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own.  Do not enable
# pam_ftp.so.

# Standard blurb.
@include common-account
@include common-session
#
[COLOR="Red"]#@include common-auth[/COLOR]
auth	required	pam_shells.so
[COLOR="Red"]auth    sufficient      pam_unix.so nullok_secure[/COLOR]
auth    sufficient     /lib/security/pam_radius_auth.so 


Everything works now with our Cryptocard servers.

---

