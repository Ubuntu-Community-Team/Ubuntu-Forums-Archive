---
title: "Can't access ftp after follwed by this guide"
date: 2010-09-04
forum: Server Platforms
---

### Post by xtrmsound on 2010-09-04
Hi

I had followed this **[Guide ]("http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-8.04")**to get proftpd with mysql on a Ubuntu server edition the last one available to download 10.04.1

I did everything. phpmyadmin is working I can access it via the browser and create users and groups.

When I am trying to enter my server using the ip or the domain name I am getting an instant error.

Flash fxp's error log
```
[R] Connecting to 192.168.25.117 -> IP=192.168.25.117 PORT=21 (attempt # 2)
[R] Connected to 192.168.25.117
[R] Connection failed (Connection lost)
```

I followed the guide using Putty to copy paste when ever I needed.
I uncomment the lines
```
/etc/proftpd/modules.conf: LoadModule mod_sql.c
 ...
 LoadModule mod_sql_mysql.c

```
I disabled UFW and even set a rule to the firewall. But still nothing. Restart the server a few times but still I am getting the same error.



Here is my proftpd.conf

```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         off
# If set on you can experience a longer connection delay in many cases.
IdentLookups                    off

ServerName                      "Debian"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayChdir                    .message true
ListOptions                     "-l"

DenyFilter                      \*.*/

# Use this to jail all users in their homes
# DefaultRoot                   ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell             off

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayChdir                    .message true
ListOptions                     "-l"

DenyFilter                      \*.*/

# Use this to jail all users in their homes
# DefaultRoot                   ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell             off

# Port 21 is the standard FTP port.
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
 PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress             1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
 PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress             1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           nogroup



# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
# Umask                         022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           nogroup



# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
# Umask                         022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd              off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder                     mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile                   off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
# AuthOrder                     mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile                   off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default.
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>
#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                                ftp
#   Group                               nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias                   anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser on ftp
#   DirFakeGroup on ftp
#
#   RequireValidShell           off
#
#   # Limit the maximum number of anonymous logins
#   MaxClients                  10
#
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin                        welcome.msg
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
#
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                           022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
#
# </Anonymous>

DefaultRoot ~

SQLBackend              mysql
# The passwords in MySQL are encrypted using CRYPT
SQLAuthTypes            Plaintext Crypt
SQLAuthenticate         users groups


# used to connect to the database
# databasename@host database_user user_password
SQLConnectInfo  ftp@localhost proftpd password


# Here we tell ProFTPd the names of the database columns in the "usertable"
# we want it to interact with. Match the names with those in the db
SQLUserInfo     ftpuser userid passwd uid gid homedir shell

# Here we tell ProFTPd the names of the database columns in the "grouptable"
# we want it to interact with. Again the names match with those in the db
SQLGroupInfo    ftpgroup groupname gid members

# set min UID and GID - otherwise these are 999 each
SQLMinID        500

# create a user's home directory on demand if it doesn't exist
CreateHome on

# Update count every time user logs in
SQLLog PASS updatecount
SQLNamedQuery updatecount UPDATE "count=count+1, accessed=now() WHERE userid='%u'" ftpuser

# Update modified everytime user uploads or deletes a file
SQLLog  STOR,DELE modified
SQLNamedQuery modified UPDATE "modified=now() WHERE userid='%u'" ftpuser

# User quotas
# ===========
QuotaEngine on
QuotaDirectoryTally on
QuotaDisplayUnits Mb
QuotaShowQuotas on

SQLNamedQuery get-quota-limit SELECT "name, quota_type, per_session, limit_type, bytes_in_avail, bytes_out_avail, bytes_xfer_avail, files_in_avail, files_out_avail, files_xfer_avail FROM ftpquotalimits WHERE name = '%{0}' AND quota_type = '%{1}'"

SQLNamedQuery get-quota-tally SELECT "name, quota_type, bytes_in_used, bytes_out_used, bytes_xfer_used, files_in_used, files_out_used, files_xfer_used FROM ftpquotatallies WHERE name = '%{0}' AND quota_type = '%{1}'"

SQLNamedQuery update-quota-tally UPDATE "bytes_in_used = bytes_in_used + %{0}, bytes_out_used = bytes_out_used + %{1}, bytes_xfer_used = bytes_xfer_used + %{2}, files_in_used = files_in_used + %{3}, files_out_used = files_out_used + %{4}, files_xfer_used = files_xfer_used + %{5} WHERE name = '%{6}' AND quota_type = '%{7}'" ftpquotatallies

SQLNamedQuery insert-quota-tally INSERT "%{0}, %{1}, %{2}, %{3}, %{4}, %{5}, %{6}, %{7}" ftpquotatallies

QuotaLimitTable sql:/get-quota-limit
QuotaTallyTable sql:/get-quota-tally/update-quota-tally/insert-quota-tally

RootLogin off
RequireValidShell off

```
If I am removing the sql code I am getting 530 error in flashfxp (wrong user and password) which I should get if it's not connect to a sql database


How do I fix it?

---

### Post by clrg on 2010-09-04
Is the ftp daemon running?

```
ps -ef | grep ftp
```

What error message do you get from the client when connecting manually? Try

```
ftp <my.ser.ver.sip>
```
from the client.

---

### Post by xtrmsound on 2010-09-04
1.

```

root@testing:/home/almog# ps -ef | grep ftp
proftpd    777     1  0 23:48 ?        00:00:00 proftpd: (accepting connections)
root       979   967  0 23:50 pts/0    00:00:00 grep --color=auto ftp

```2. I am getting an instant error from Flashfxp.

```
R] Connecting to 192.168.25.117 -> IP=192.168.25.117 PORT=21 (attempt # 2)
[R] Connected to 192.168.25.117
[R] Connection failed (Connection lost)
[R] Delaying for 120 seconds before reconnect attempt #3

```Thanks

```
root@testing:/home/almog# service proftpd restart
 * Stopping ftp server proftpd                                           [ OK ]
 * Starting ftp server proftpd                                           [ OK ]
root@testing:/home/almog#

```

---

### Post by xtrmsound on 2010-09-04
Downloaded Utuntu 8 server. 

Worked without any error.

Something wrong with guide, Need to rewrite the guide to make it more usable to newer os

---

### Post by de0xyrib0se on 2010-09-04
Well...the guide does say its for 8.04.

---

