---
title: "proftpd problems"
date: 2006-08-05
forum: Server Platforms
---

### Post by iric on 2006-08-05
Hi all,

I have VHCS2 as control panel which uses proftpd-mysql.
It did work before, but all of a sudden it stopped working, I get a "connection closed by server" in my ftp programs.

Here's the proftpd.conf:

```

#
#	VHCS proftpd config file
#
#

ServerName			"*my server name*"
ServerType			standalone
DeferWelcome			off

ShowSymlinks			on
MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on
AllowOverwrite			on

LogFormat 			traff "%b %u"

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message

#LsDefaultOptions                "-l"

DenyFilter			\*.*/

DefaultRoot			~

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Port 21 is the standard FTP port.

Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)

MaxInstances			30

# Set the user and group that the server normally runs at.

User				nobody
Group				nogroup

# Normally, we want files to be overwriteable.

<Directory /*>
  # Umask 022 is a good standard umask to prevent new files and dirs
  # (second parm) from being group and world writable.
  Umask				022  022

  AllowOverwrite		on
  HideNoAccess on

</Directory>

<Limit ALL>
  IgnoreHidden on
</Limit>

<Global>
	TransferLog                     /var/log/xferlog
	ExtendedLog                     /var/log/ftp_traff.log read,write traff
	PathDenyFilter "\.quota$"
</Global>

<IfModule mod_delay.c>
	DelayEngine off
</IfModule>

#
# VHCS2 Managment;
#

SQLAuthTypes 		Crypt
SQLAuthenticate		on
SQLConnectInfo		*db* *user* *pass*
SQLUserInfo			ftp_users userid passwd uid gid homedir shell
SQLGroupInfo		ftp_group groupname gid members
SQLMinID			2000        

#
# VHCS2 Quota management;
#

QuotaEngine on
QuotaShowQuotas on
QuotaDisplayUnits Mb

SQLNamedQuery get-quota-limit SELECT "name, quota_type, per_session, limit_type, bytes_in_avail, bytes_out_avail, bytes_xfer_avail, files_in_avail, files_out_avail, files_xfer_avail FROM quotalimits WHERE name = '%{0}' AND quota_type = '%{1}'"
SQLNamedQuery get-quota-tally SELECT "name, quota_type, bytes_in_used, bytes_out_used, bytes_xfer_used, files_in_used, files_out_used, files_xfer_used FROM quotatallies WHERE name = '%{0}' AND quota_type = '%{1}'"
SQLNamedQuery update-quota-tally UPDATE "bytes_in_used = bytes_in_used + %{0}, bytes_out_used = bytes_out_used + %{1}, bytes_xfer_used = bytes_xfer_used + %{2}, files_in_used = files_in_used + %{3}, files_out_used = files_out_used + %{4}, files_xfer_used = files_xfer_used + %{5} WHERE name = '%{6}' AND quota_type = '%{7}'" quotatallies
SQLNamedQuery insert-quota-tally INSERT "%{0}, %{1}, %{2}, %{3}, %{4}, %{5}, %{6}, %{7}" quotatallies

QuotaLock /var/run/proftpd/tally.lock
QuotaLimitTable sql:/get-quota-limit
QuotaTallyTable sql:/get-quota-tally/update-quota-tally/insert-quota-tally

```

ofcourse I removed the actual login and servername stuff.

I already removed proftpd-common and proftpd-mysql and reinstalled them but unfortunately it doesn't help at all.

Tried to set Servertype from Standalone tot inetd but when I try to restart proftpd it says:

```

ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.

```

FTP from a computer within the network:

```

FTP Voyager - Version 11.0.0.0
STATUS:>  Connecting to "ftp.xxxxxxxxxx.nl" on port 21.
ERROR:>   Connection closed by the server.
ERROR:>   Unable to login

```

Does anybody have a suggestion?

---

### Post by chrisfay on 2006-08-05
**deleted**

---

### Post by iric on 2006-08-07
> **chrisfay said:**
> **deleted**

Any other solutions than deleted?

---

