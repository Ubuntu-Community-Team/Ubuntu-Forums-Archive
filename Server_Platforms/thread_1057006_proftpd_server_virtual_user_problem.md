---
title: "proftpd server virtual user problem"
date: 2009-02-01
forum: Server Platforms
---

### Post by cmol on 2009-02-01
Hello

I'm configuring a ubuntu 8.10 server for running www, mail and ftp.
So far the www and mail part are running, however there is a slight problem with the ftp part.

I'm using proftpd v. 1.3.1 with the mysql-mod to manage virtual users. I have the packages proftpd and proftpd-mod-mysql installed.

The ftp is operating just fine when I use unix users as login, but when I try to use mysql, it fails at login with error:

```

cmol@storm-p:~$ ftp localhost
Connected to localhost.
421 Service not available, remote server has closed connection
```

the proftpd log shows:

```

Feb 01 17:33:28 storm-p proftpd[22172] storm-p.fullrate.dk (localhost[127.0.0.1]): ProFTPD terminating (signal 11)
Feb 01 17:33:28 storm-p proftpd[22172] storm-p.fullrate.dk (localhost[127.0.0.1]): FTP session closed.
```

If I try to log in from another pc, result is the same.

My proftpd.conf file is:

```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Includes mysql configuration file
Include /etc/proftpd/mysql.conf
RootLogin off
RequireValidShell off 

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				off
# If set on you can experience a longer connection delay in many cases.
IdentLookups			off

ServerName			"storm-p"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
# DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

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
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd		off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder			*mod_auth_pam.c mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend			mysql
#</IfModule>

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
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
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
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>
<Global>
DefaultChdir /media/lager/
RootLogin off
</Global>

```

and my mysql.conf is:

```
#<IfModule mod_sql.c>

# Force the use of mysql backend
SQLBackend                      mysql

# The passwords in MySQL are using its own PASSWORD function
SQLAuthTypes                    Backend
SQLAuthenticate                 users* groups*

# details to connect to mysql db
# dbname@host dbuser dbpass
SQLConnectInfo                  proftpddb@localhost proftpduser XXPASSWORDXX

# Let proFTPd know the name of the columns in the user table
# Mind that this need to match the name in you table
SQLUserInfo                     ftpuser userid passwd uid gid homedir shell

# Let proFTPd know the name of the columns in the group table
# we want it to interact with. Again the names match with those in the db
SQLGroupInfo                    ftpgroup groupname gid members

# proftpd will dynamicaly create if the homedir does not yet exist
# SQLHomedirOnDemand              on

# update counter when a user logs in
SQLLog                          PASS updatecount
SQLNamedQuery                   updatecount UPDATE "count=count+1, accessed=now() WHERE userid='%u'" ftpuser

# change modified time anytime a user delete a file or upload one
SQLLog                          STOR,DELE modified
SQLNamedQuery                   modified UPDATE "modified=now() WHERE userid='%u'" ftpuser

SQLLogFile			/var/log/proftpd/mysql.log

#</IfModule>

```

Do you have any idea what is coursing the problem?

Thanks.

---

### Post by inphektion on 2009-02-01
and you can successfully login to the database with the proftpduser you have?
did you populate the db?
try following this [http://www.howtoforge.com/proftpd_mysql_virtual_hosting](http://www.howtoforge.com/proftpd_mysql_virtual_hosting)
see if you missed anything.

---

### Post by cmol on 2009-02-01
> **inphektion said:**
> and you can successfully login to the database with the proftpduser you have?
did you populate the db?
try following this [http://www.howtoforge.com/proftpd_mysql_virtual_hosting](http://www.howtoforge.com/proftpd_mysql_virtual_hosting)
see if you missed anything.

Tried to log in to the mysql from bash (with the 'proftpduser' user), and was granted all the access needed. So the problem's not there.

Had a look at the guide, much similar to the one I used at the beginning.
I did not find anything missing besides the "quota thing" which I don't need.

And I have populated the database with a user.

Anything else to test?

---

### Post by inphektion on 2009-02-01
take a look at authorder in proftpd.conf. 
i think you might need a sql module specified there.

---

### Post by cmol on 2009-02-01
> **inphektion said:**
> take a look at authorder in proftpd.conf. 
i think you might need a sql module specified there.

Found my problem.........

I started looking around in my modules.conf and it turned out, that I had only uncommented the mod_sql.c     not the mod_sql_mysql.c

So......

Thanks for helping :)

---

