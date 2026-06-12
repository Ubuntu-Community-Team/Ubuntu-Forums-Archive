---
title: "upload problems with Proftpd"
date: 2009-01-09
forum: Server Platforms
---

### Post by jazzguitarplayer on 2009-01-09
When i try to upload a file on my proftpd server i got a 550 error Permission denied. I got the same message when i modify a file. I use filezilla as a ftp client

The directory of my site i already gave full permissions with the command chmod -R 777 /var/www/html/site/www.mysite.com

This is my configuration file. I changed Umask from 022 022 to 777 777.

By the way i use ubuntu server without GUI



#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         on

ServerName                      "Debian"
ServerType                      inetd
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

DenyFilter                      \*.*/

# Port 21 is the standard FTP port.
Port                            21

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
MaxInstances                    5

# Set the user and group that the server normally runs at.
User                            ftpuser
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           777  777
# Normally, we want files to be overwriteable.
AllowOverwrite                  off

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd              off


# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile                   off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

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
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default.
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

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
#   DisplayFirstChdir           .message
#
#   # Limit WRITE everywhere in the anonymous chroot

#VALID LOGINS
<Limit LOGIN>
AllowUser ftpuser
DenyALL
</Limit>

DefaultRoot /var/www/html/sites/www.xxx.com

<Directory /var/www/html/sites/www.xxx.com>
Umask 777  777

#Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

#<Directory /var/www/html/sites/www.xxx.com>
#Umask 022 022
#AllowOverwrite off
#       <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
#       DenyAll
#       </Limit>
#</Directory>

#<Directory> /var/www/html/sites/www.xxx.com>
#Umask 022 022
#AllowOverwrite on
#       <Limit READ RMD DELE>
#       DenyAll
#       </Limit>
#
#       <Limit STOR CWD MKD>
#       AllowAll
#       </Limit>
#</Directory>

---

### Post by jazzguitarplayer on 2009-01-09
i always restart de service after editing.

I tried so much things but nothing helped. I even made a new user account and changed the path folder

useradd [testuser] -p [password] -d /var/www/html/sites/www.xxx.com -s /bin/false 

I also added the testuser account to the root group in /etc/group:

root:x:0:testuser

All without result
 :(

---

### Post by volkswagner on 2009-01-09
Warning I am no expert, but have struggled with proftp.

My understanding of the following syntax, which is from a default install is....

```
<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>

```

The above is for an _upload only_ folder, so the directives included in the DenyAll are denied, the directives included in the AllowAll are allowed.

It appears you have only DenyAll directives.

---

### Post by jazzguitarplayer on 2009-01-09
hi thanks for your reply. The download and upload folder is de same directory. I comment (#) the DenyAll parameter without result :-(

I'm able to download files but modifying and uploading files is not possible. I'm busy with it the whole with still didn't find a solution.

---

### Post by jazzguitarplayer on 2009-01-09
I also tried with the parameters: AllowOverwrite on. I use it 2 times in the config file. Unfortuatenaly this also does not solve the problem. Anybody out there who could help me please?

---

### Post by bmatthewshea on 2011-08-26
> **jazzguitarplayer said:**
> When i try to upload a file on my proftpd server i got a 550 error Permission denied. I got the same message when i modify a file. I use filezilla as a ftp client

The directory of my site i already gave full permissions with the command chmod -R 777 /var/www/html/site/www.mysite.com

This is my configuration file. I changed Umask from 022 022 to 777 777.

I know this thread is old, but noticed this post trying to figure out my 550 error in proftpd.

You have misunderstood umask parameters. You are doing the opposite of what you intend. 
"umask 000" would equal chmod 777 is setting perm directly.. ("umask 022" should be fine for what you are trying to do. = chmod 755)

So setting 'umask 777' would equal 'chmod 000'


google umask
or
[http://en.wikipedia.org/wiki/Umask](http://en.wikipedia.org/wiki/Umask)

---

