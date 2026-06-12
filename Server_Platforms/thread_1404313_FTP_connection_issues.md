---
title: "FTP connection issues"
date: 2010-02-11
forum: Server Platforms
---

### Post by terrapin893 on 2010-02-11
I can not connect to my FTP server at all.  To the best of my knowledge I have done everything right and I have take considerable steps to troubleshoot the issue.  I will provide here all the information that I can.  

I configured the ProFTPD following the method B option from this link.  
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

Every time that I try to connect to FTP I get a Server Ready but incorrect login (530).  This is after double checking the configuration file and manually resetting the password.    I have my router setup with port 7777 open externally forwarding to 21 on my machine.  Port 7777 shows to be open.  

Posted for thoroughness is my proftpd.conf file 
```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
AuthAliasOnly on

#Choose the user alias you want here.
UserAlias terrapin893 userftp

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         on
# If set on you can experience a longer connection delay in many cases.
IdentLookups                    off

ServerName                      "Champion"
ServerType                      standalone
DeferWelcome                    on

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer               600
TimeoutStalled                  100
TimeoutIdle                     2200

DisplayLogin                    welcome.msg
DisplayChdir                    .message true
ListOptions                     "-l"

DenyFilter                      \*.*/

#It's better for debug to create log files ;-)
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

# Use this to jail all users in their homes
# DefaultRoot                   ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell             off

# Port 21 is the standard FTP port.r
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

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
User                            userftp
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
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
#   DisplayChdir                .message
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

"/etc/proftpd/proftpd.conf" 179L, 4964C                                                                                                    1,1           Top

```Ive then checked and changed the username of group 'userftp' 

```
root@champion:/home/paul# passwd userftp
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@champion:/home/paul#
```Then I try to log into FTP and I get 530 Login Incorrect Errors 

Posted, again for thoroughness, my FTP logs
```
localhost UNKNOWN userftp [11/Feb/2010:04:20:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:04:25:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:04:30:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:04:35:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:04:40:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:04:45:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:04:50:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:04:55:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:00:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:05:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:10:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:15:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:20:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:25:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:30:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:35:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:40:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:45:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:50:02 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:05:55:02 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:00:02 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:05:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:10:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:15:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:20:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:25:02 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:30:02 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:35:02 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:40:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:45:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:50:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:06:55:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:07:00:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:07:05:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:07:10:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:07:15:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:07:20:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:07:25:02 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:07:30:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:07:35:01 -0700] "QUIT" 221 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:35:11 -0700] "USER terrapin893" 331 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:35:12 -0700] "PASS (hidden)" 530 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:35:14 -0700] "USER terrapin893" 331 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:35:14 -0700] "PASS (hidden)" 530 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:35:15 -0700] "USER terrapin893" 331 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:35:15 -0700] "PASS (hidden)" 530 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:35:16 -0700] "USER terrapin893" 331 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:35:16 -0700] "PASS (hidden)" 530 -
localhost UNKNOWN userftp [11/Feb/2010:07:40:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:07:45:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:07:50:01 -0700] "QUIT" 221 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:51:42 -0700] "USER terrapin893" 331 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:51:42 -0700] "PASS (hidden)" 530 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:51:44 -0700] "USER terrapin893" 331 -
::ffff:216.207.124.226 UNKNOWN userftp [11/Feb/2010:07:51:44 -0700] "PASS (hidden)" 530 -
localhost UNKNOWN userftp [11/Feb/2010:07:55:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:08:00:01 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:08:05:02 -0700] "QUIT" 221 -
localhost UNKNOWN userftp [11/Feb/2010:08:10:02 -0700] "QUIT" 221 -

                                                                                                                                           1,1           Top

```Another unrelated issue . . . . Im having problems accessing phpmyadmin.  Now I assume that I could do it all via terminal but I kinda like the phpmyadmin interface.  When I try to access any of my domains pointing at my server (via a URL redirect to my DynDNS host name which is setup with my router to update to IP changes) /phpmyadmin it comes up with page not found.  I know the domains are pointing right because it brings up the default apache "It Works" page.  I can also try putting in the server name, champion.ph.cox.net/phpmyadmin but that doesnt come up either.  How can I access phpmyadmin (yes, it is installed too btw.  ;) ) 

Thanks for anyone who has made it this far through all this!!!!!

---

### Post by terrapin893 on 2010-02-11
UPDATE:  I have taken the recommendation of a friend who has helped me with some linux in the past.  He said to make sure that the user that I am trying to log into via FTP has ownership of the FTP home directory.  

So I actually ran the command line to change the user and group of the FTP home directory, /home/FTP-shared and that was successful, yet still I get the same 530 login error. Ive also tried disabling the Alias and using just the username userftp and that does not work either.

---

### Post by terrapin893 on 2010-02-13
SOLVED:  

Well I solved this one myself with a bit more research.  

First off, for the FTP issue I just redid my configuration file without using an alias and that worked just perfectly. 

As for the issue with phpmyadmin . . . . created a symlink to usr/share/phpmyadmin.

All is well, and Im working on a Joomla install right now.

---

### Post by tad1073 on 2010-02-14
maybe you can help me solve my apache problem?

I can access phpmyadmin from localhost but not from a client and the same with apache, both computers are on the same network, I have to ssh -X then do sudo firefox.

---

