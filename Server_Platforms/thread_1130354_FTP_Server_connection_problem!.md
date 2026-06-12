---
title: "FTP Server connection problem!"
date: 2009-04-19
forum: Server Platforms
---

### Post by andrewfashion on 2009-04-19
I have been going at this forever, browsing the forums, every single help doc I could find

I tried VSFTPD and PROFTPD multiple times...

I am on ubuntu server 8.10:

I have mysql, apache, php, ebox, samba, ssh, and a custom dns setup with dyndns.org to host a custom domain pointing to the box, all ports are open on my router so i can access everything just fine.

I made sure port 21 and 20 was open for FTP, but I still can't connect.

It just keeps timing out, I can't even connect with localhost, or connect to ftp on the same box, I keep getting this message...

> fashion@ubuntu2:/home/FTP-shared$ ftp 127.0.0.1
Connected to 127.0.0.1.
421 Service not available, remote server has closed connection

fashion@ubuntu2:/home/FTP-shared$ ftp localhost
Connected to localhost.
421 Service not available, remote server has closed connection


I also cannot connect from my windows computer on the same network. It just times out.

And these are the latest instructions I followed: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

Here is my proftpd.conf file

```

# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         on
# If set on you can experience a longer connection delay in many cases.
IdentLookups                    off

ServerName                      "Debian"
ServerType                      standalone
DeferWelcome                    on

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
DefaultRoot                     /home/FTP-shared

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell             off

# Port 21 is the standard FTP port.
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
PassivePorts                  60000 65535

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
MasqueradeAddress               76.120.117.209

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
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd              off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder                     *mod_auth_pam.c mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile                   off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend                    mysql
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
#   # </Directory>
#
# </Anonymous>

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory>

```

---

### Post by HermanAB on 2009-04-19
FTP is a bit weird, in that the initial conection on the control chanel is established on port 21, but then the protocol turns around: The server becomes a client and the client becomes a server and the original 'server' creates a reverse connection back to the original 'client' over a random numbered high port.  So for it to work through a firewall, you need a FTP connection tracker program.  On Linux machines this should work, but it will not work through some routers.

You can try to debug the connection using telnet:
$ telnet ftp.server.ip.address 21

and you should get a banner from the FTP server.  If not then you have a much bigger problem.  If yes, then the control channel works, but the data channel can still fail.

In general, it is much easier to get SSH Server to work and since it is secure, why not install the ssh-server package?

---

