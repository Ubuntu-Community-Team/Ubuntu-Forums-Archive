---
title: "Proftpd-mod-mysql is giving me error 530."
date: 2011-07-18
forum: Server Platforms
---

### Post by jamespuckett on 2011-07-18
I tried to configure ProFTPD with Ubuntu server 10.04 LTS and its throwing up 530 Incorrect login errors when I try to connect. Also, my passwords are crypted, and my user "doonbugie" is in the ftpall group. My setup is as follows, I have proftpd-mod-mysql installed on my remote linux box and the MySQL database is on another box which has its ports allowed so the other server can connect to the DB. I have the permissions for the remote linux box to do anything on the MySQL DB so I don't know what the issue is here.
This error:
Status:    Connecting to 204.12.241.218:21...
Status:    Connection established, waiting for welcome message...
Response:    220 Servers identifying string
Command:    USER doonbugie
Response:    331 Password required for doonbugie
Command:    PASS ******
Response:    530 Login incorrect.
Error:    Critical error
Error:    Could not connect to server

Here is my sql.conf and my proftpd.conf
----PROFTPD.CONF----
ServerName                      "Servername"
ServerType                      standalone
ServerIdent                     on              "Servers identifying string"
DeferWelcome                    on
DefaultServer                   on

DisplayLogin                    .welcome        # Textfile to display on login
DisplayConnect                  .connect        # Textfile to display on connection

UseReverseDNS                   off
IdentLookups                    off

Port                            21
Umask                           022
MaxInstances                    15
MaxClientsPerHost               10              "Only %m connections per host allowed"
MaxClients                      500             "Only %m total simultanious logins allowed"
MaxHostsPerUser                 10

ScoreboardFile                  /var/log/scoreboard

# Some logging formats
LogFormat                       default         "%h %l %u %t \"%r\" %s %b"
LogFormat                       auth            "%v [%P] %h %t \"%r\" %s"
LogFormat                       write           "%h %l %u %t \"%r\" %s %b"

# Define log-files to use
TransferLog                     /var/log/proftpd.xferlog
ExtendedLog                     /var/log/proftpd.access_log    WRITE,READ write
ExtendedLog                     /var/log/proftpd.auth_log      AUTH auth
ExtendedLog                     /var/log/proftpd.paranoid_log  ALL default
# Set up authentication via SQL
# ===========
#
# Log the user logging in
#SQLLog PASS counter
#SQLNamedQuery counter UPDATE "lastlogin=now(), count=count+1 WHERE userid='%u'" usertable

# logout log
#SQLLog EXIT time_logout
#SQLNamedQuery time_logout UPDATE "lastlogout=now() WHERE userid='%u'" usertable

# display last login time when PASS command is given
#SQLNamedQuery login_time SELECT "lastlogin from usertable where userid='%u'"
#SQLShowInfo PASS "230" "Last login was: %{login_time}"

# xfer Log in mysql
#SQLLog RETR,STOR transfer1
#SQLNamedQuery  transfer1 INSERT "'%u', '%f', '%b', '%h', '%a', '%m', '%T', now(), 'c', NULL" xfer_stat
#SQLLOG ERR_RETR,ERR_STOR transfer2
#SQLNamedQuery  transfer2 INSERT "'%u', '%f', '%b', '%h', '%a', '%m', '%T', now(), 'i', NULL" xfer_stat


AllowStoreRestart               on
AllowRetrieveRestart            on
RequireValidShell               off
PathDenyFilter                  "\\.ftp)|\\.ht)[a-z]+$"
DefaultRoot                     ~
DenyFilter                      \*.*/

<Limit LOGIN>
  Order deny,allow
  AllowGroup ftpserver
  AllowGroup ftpall
</Limit>

----SQL.CONF----
#
# Proftpd sample configuration for SQL-based authentication.
#
# (This is not to be used if you prefer a PAM-based SQL authentication)
#

<IfModule mod_sql.c>
#
# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
SQLBackend      mysql
#
SQLEngine on
SQLAuthenticate on
#
# Use both a crypted or plaintext password
#SQLAuthTypes Crypt Plaintext
#
# Use a backend-crypted or a crypted password
SQLAuthTypes Backend
#
# Connection
SQLConnectInfo proftpd@IP root PASSWD
#
# Describes both users/groups tables
#
SQLConnectInfo        proftpd@IP root PASSWD
SQLAuthenticate       users groups
SQLAuthTypes          Crypt Backend
SQLDefaultHomedir     /home/ftp
SQLUserInfo           users userid passwd uid gid homedir shell
SQLGroupInfo          groups groupid gid members

SQLHomedirOnDemand      on
SQLLogFile              /var/log/proftpd.sql_log

# Count number of logins for each user
SQLLog                PASS logincount
SQLNamedQuery         logincount UPDATE "login_count=login_count+1 WHERE userid='%u'" users
# Save last login
SQLLog                PASS lastlogin
SQLNamedQuery         lastlogin UPDATE "last_login=now() WHERE userid='%u'" users
# Count number of bytes/files downloaded and uploaded
SQLLog RETR           dlbytescount
SQLLog RETR           dlcount
SQLNamedQuery         dlcount UPDATE "dl_count=dl_count+1 WHERE userid='%u'" users
SQLLog STOR           ulbytescount
SQLNamedQuery         ulbytescount UPDATE "ul_bytes=ul_bytes+%b WHERE userid='%u'" users
SQLLog STOR           ulcount
SQLNamedQuery         ulcount UPDATE "ul_count=ul_count+1 WHERE userid='%u'" users

# Do not let disabled or expired users to login
SQLUserWhereClause    "disabled!=1 and (NOW()<=expires or expires=-1)"

# Do not require a valid shell, this might be a good thing to turn on for SQL-users
# This might simplify the configuration a little bit
RequireValidShell     off

</IfModule>

---END.CONF FILES--- :popcorn:

---

