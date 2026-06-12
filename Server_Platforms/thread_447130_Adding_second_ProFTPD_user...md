---
title: "Adding second ProFTPD user.."
date: 2007-05-17
forum: Server Platforms
---

### Post by Naatan on 2007-05-17
Hi, I just added a second FTP user but I cant manage to login with it. Even though settings are identical to the first one (apart from some minor changes)

I have a ProFTPD server running without anonymous access, I am trying to configure every user manually so that I can assign their home directories for when they connect.

I have a user added that works perfectly like so:

```

<Anonymous /www/domain-name.org>
	User username
	Group groupname
	AnonRequirePassword on
	MaxClients 5 "The server is full, hosting %m users"
	DisplayLogin welcome.msg
	DisplayFirstChdir .msg
	<Limit LOGIN>
		Allow from all
		Deny from all
	</Limit>
	AllowOverwrite on
	<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE_CHMOD  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
		 AllowAll
	</Limit>
	<Limit SITE  SITE_CHGRP >
		 DenyAll
	</Limit>
</Anonymous>

```

Like I said, this works perfect..

now I tried adding another user, I added the user in the terminal with the same settings as the other user, basically the only difference is the username, group, homedir and password.

I copied the piece of code above and changed the home directory, username and group name.

I did a chown on the home directory for the new user and restarted proftpd, but it won't work, in the log for proftpd it says the following:

```

May 17 22:18:46 hostname.tld proftpd[24224] hostname.tld (d22C0E2DD.access.isp.com[::ffff:10.10.10.10]): FTP session closed.
May 17 22:18:47 hostname.tld proftpd[28171] hostname.tld (d22C0E2DD.access.isp.com[::ffff:10.10.10.10]): error setting IPV6_V6ONLY: Protocol not available
May 17 22:18:47 hostname.tld proftpd[28171] hostname.tld (d22C0E2DD.access.isp.com[::ffff:10.10.10.10]): FTP session opened.
May 17 22:18:47 hostname.tld proftpd[28171] hostname.tld (d22C0E2DD.access.isp.com[::ffff:10.10.10.10]): mod_delay/0.5: delaying for 77 usecs
May 17 22:18:47 hostname.tld proftpd[28171] hostname.tld (d22C0E2DD.access.isp.com[::ffff:10.10.10.10]): USER username (Login failed): Limit access denies login
May 17 22:18:47 hostname.tld proftpd[28171] hostname.tld (d22C0E2DD.access.isp.com[::ffff:10.10.10.10]): mod_delay/0.5: delaying for 6724 usecs
May 17 22:18:47 hostname.tld proftpd[28171] hostname.tld (d22C0E2DD.access.isp.com[::ffff:10.10.10.10]): FTP session closed.

```

I have no idea what is causing this, there's nothing in syslog either so it has to be in the proftpd config file..

this is my config:

```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName			"Debian"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                    49152 65534

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			6

# Set the user and group that the server normally runs at.
User				proftpd
Group				proftpd

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off

# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile			off

ExtendedLog /var/log/proftpd/xtended.log
TransferLog /var/log/proftpd/xferlog.log
SystemLog /var/log/proftpd/proftpd.log


<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    5
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      10
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

<Global>
RootLogin off
SyslogLevel debug
</Global>

<Limit LOGIN>
DenyAll 
</Limit>

<Anonymous /www/domain-name1.org>
	User username1
	Group groupname1
	AnonRequirePassword on
	MaxClients 5 "The server is full, hosting %m users"
	DisplayLogin welcome.msg
	DisplayFirstChdir .msg
	<Limit LOGIN>
		Allow from all
		Deny from all
	</Limit>
	AllowOverwrite on
	<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE_CHMOD  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
		 AllowAll
	</Limit>
	<Limit SITE  SITE_CHGRP >
		 DenyAll
	</Limit>
</Anonymous>

<Anonymous /www/domain-name2.com>
	User username2
	Group groupname2
	AnonRequirePassword on
	MaxClients 5 "The server is full, hosting %m users"
	DisplayLogin welcome.msg
	DisplayFirstChdir .msg
	<Limit LOGIN>
		Allow from all
		Deny from all
	</Limit>
	AllowOverwrite on
	<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE_CHMOD  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
		 AllowAll
	</Limit>
	<Limit SITE  SITE_CHGRP >
		 DenyAll
	</Limit>
</Anonymous>

```

I seriously dont know why its doing this.. any advice would be greatly appreciated

---

### Post by Naatan on 2007-05-18
bump.. come on.. no one?

---

### Post by Naatan on 2007-05-18
nvm, I managed to add virtual users with pureftpd.

Finally an ftp server that does what it has to do without having to read a 500 page book.

---

