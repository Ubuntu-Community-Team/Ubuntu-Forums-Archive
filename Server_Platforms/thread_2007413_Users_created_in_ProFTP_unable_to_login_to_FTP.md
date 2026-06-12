---
title: "Users created in ProFTP unable to login to FTP"
date: 2012-06-20
forum: Server Platforms
---

### Post by ihthisham007 on 2012-06-20
Hi There,
I have installed Proftpd/ and Proftpd admin on Ubuntu 11.04.
I can create users and groups fine n proftpd admin.
I checked the MY SQL DB and the data is available on the table.

but when I login to FTP using one of the FTP user password or root or my user id I cant login. 
auth.log-

Jun 20 12:11:09 BMTKAN-VFTP proftpd[1452]: 127.0.1.1 (::ffff:192.168.100.100[::ffff:192.168.100.100]) - USER root: no such user found from ::ffff:192.168.100.100 [::ffff:192.168.100.100] to ::ffff:192.168.100.30:21

Jun 20 12:39:39 BMTKAN-VFTP proftpd[1117]: 127.0.1.1 (::ffff:192.168.100.100[::ffff:192.168.100.100]) - USER anonymous: no such user found from ::ffff:192.168.100.100 [::ffff:192.168.100.100] to ::ffff:192.168.100.30:21

Please Help me fix this issue. 
Thank you

---

### Post by rukiaEnix on 2012-06-20
Could you please post your proFTP configuration file please?

---

### Post by ihthisham007 on 2012-06-20
ServerName			"Server"
ServerType			standalone
ServerIdent			on		"Server"
DeferWelcome			on
DefaultServer			on

DisplayLogin			.welcome	# Textfile to display on login
DisplayConnect			.connect	# Textfile to display on connection
#DisplayFirstChdir               .firstchdir	# Textfile to display on first changedir

UseReverseDNS       		off
IdentLookups        		off

Port				21
Umask				022
MaxInstances                    15
MaxClientsPerHost               3 		"Only %m connections per host allowed"
MaxClients                      10 		"Only %m total simultanious logins allowed"
MaxHostsPerUser                 1
Include                         /etc/proftpd/modules.conf
## Begin Customization
######################
Include /etc/proftpd/sql.conf
RootLogin               off
# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
RequireValidShell       off
# Use this to jail all users in their homes
DefaultRoot             ~
# These two lines help speed up the initial connection to the server
IdentLookups            off
UseReverseDns           off
# Create a user's home directory on demand if it doesn't exist
CreateHome on
## End Customization
####################
User				nobody
Group				nogroup

ScoreboardFile 			/var/log/scoreboard

# Some logging formats
LogFormat            		default 	"%h %l %u %t \"%r\" %s %b"
LogFormat            		auth    	"%v [%P] %h %t \"%r\" %s"
LogFormat            		write   	"%h %l %u %t \"%r\" %s %b"

# Define log-files to use
TransferLog          		/var/log/proftpd.xferlog
ExtendedLog         			/var/log/proftpd.access_log    WRITE,READ write
ExtendedLog          		/var/log/proftpd.auth_log      AUTH auth
ExtendedLog          		/var/log/proftpd.paranoid_log  ALL default
#SQLLogFile				/var/log/proftpd.mysql

# Set up authentication via SQL
# ===========
AuthOrder                       	mod_sql.c
SQLAuthTypes				Backend
SQLConnectInfo       		proftpd_admin@localhost proftpd Pretzel311
SQLUserInfo       			usertable userid passwd uid gid homedir shell 
SQLGroupInfo       			grouptable groupname gid members 
SQLUserWhereClause    		"disabled=0 and (NOW()<=expiration or expiration=-1 or expiration=0)"

# Log the user logging in
SQLLog PASS counter
SQLNamedQuery counter UPDATE "lastlogin=now(), count=count+1 WHERE userid='%u'" usertable

# logout log
SQLLog EXIT time_logout
SQLNamedQuery time_logout UPDATE "lastlogout=now() WHERE userid='%u'" usertable

# display last login time when PASS command is given
SQLNamedQuery login_time SELECT "lastlogin from usertable where userid='%u'"
SQLShowInfo PASS "230" "Last login was: %{login_time}"

# xfer Log in mysql
SQLLog RETR,STOR transfer1
SQLNamedQuery  transfer1 INSERT "'%u', '%f', '%b', '%h', '%a', '%m', '%T', now(), 'c', NULL" xfer_stat
SQLLOG ERR_RETR,ERR_STOR transfer2
SQLNamedQuery  transfer2 INSERT "'%u', '%f', '%b', '%h', '%a', '%m', '%T', now(), 'i', NULL" xfer_stat


AllowStoreRestart 		on
AllowRetrieveRestart		on
RequireValidShell               off
PathDenyFilter                  "\\.ftp)|\\.ht)[a-z]+$"
DefaultRoot 			~
DenyFilter 			\*.*/


#<Directory /ftp/*>
#	AllowOverwrite		off
# 	HideNoAccess		off
#	<Limit READ>
#		AllowAll
#        </Limit>
#
#	<Limit WRITE>
#		DenyGroup	!admins
# 	</Limit>
#</Directory>

#<Directory /ftp/incoming/*>
<Directory /ftp/*>
	AllowOverwrite		on
	HideNoAccess		on

#	<Limit READ>
#     		DenyGroup	!admins
#    	</Limit>

    	<Limit STOR MKD>
      		AllowAll
    	</Limit>
</Directory>

---

### Post by ihthisham007 on 2012-06-20
[ OK ]
root@BMTKAN-VFTP:~# ftp localhost
Connected to localhost.
220 Server
Name (localhost:root): test1
331 Password required for test1
Password:
530 Login incorrect.
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>

---

### Post by rukiaEnix on 2012-06-21
I see your not configuring the FTP users.

Try with this config at the global zone:

```

<Global>
AllowOverwrite on
  <Limit ALL SITE_CHMOD>
    AllowAll
  </Limit>
LoginPasswordPrompt off
RootLogin off
UseFtpUsers on
DefaultRoot ~
PassivePorts 4000 4001
DefaultChdir /home/$USER
</Global>

```

I use that configuration when I want to use the system users.

---

### Post by ihthisham007 on 2012-06-21
I added that part to the Poroftpd.conf file still the same. 

Jun 21 12:29:24 BMTKAN-VFTP proftpd[2208]: 127.0.1.1 (::ffff:192.168.100.100[::ffff:192.168.100.100]) - USER test5 (Login failed): No such user found.

---

### Post by ihthisham007 on 2012-06-21
Can I have a proper/clear instruction on how to setup proftpd/mysql/php with proftpd-admin on ubuntu 10.04 or 11.04 please. 
I am running this on VM. Need a urgent solution on this. any help much appritiated. Thank you

---

### Post by rukiaEnix on 2012-06-21
Is test5 a user in your system?

Try adding this in general settings:

```

UseFtpUsers off
<Limit LOGIN>
AllowUser test5
</Limit>
RootLogin off
DefaultRoot ~
PassivePorts 4000 4001
DefaultChdir /home/$USER

```

---

