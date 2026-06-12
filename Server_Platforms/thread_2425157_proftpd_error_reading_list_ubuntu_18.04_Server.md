---
title: "proftpd error reading list ubuntu 18.04 Server"
date: 2019-08-21
forum: Server Platforms
---

### Post by chrispet on 2019-08-21
Hi everyone! I have installed the Ubuntu 18.04 Server version and i want to install and configure the proftpd service. I have installed it but i have a problem. Although i have gave the permissions in a user with this command sudo chown myuser:myuser /var/www/mydomain when i'm trying to access my ftp server i logged in correctly but i can't see the list of my server. What can i do for that? Also i have change the home directory from default to /var/www/mydomain.
Below is my configuration of proftpd server.
```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes, reload proftpd after modifications, if
# it runs in daemon mode. It is not required in inetd/xinetd mode.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6            off
# If set on you can experience a longer connection delay in many cases.
IdentLookups         off

ServerName         "MyServer"
# Set to inetd only if you would run proftpd by inetd/xinetd.
# Read README.Debian for more information on proper configuration.
ServerType           standalone
DeferWelcome         off

MultilineRFC2228      on
DefaultServer         on
ShowSymlinks         on

TimeoutNoTransfer      600
TimeoutStalled         600
TimeoutIdle         1200

DisplayLogin                    welcome.msg
DisplayChdir                  .message true
ListOptions                   "-l"

DenyFilter         \*.*/

# Use this to jail all users in their homes 
DefaultRoot         ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
RequireValidShell      on

# Port 21 is the standard FTP port.
Port            5050

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress      1.2.3.4

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
MaxInstances         30

# Set the user and group that the server normally runs at.
User            proftpd
Group            nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask            022  022
# Normally, we want files to be overwriteable.
AllowOverwrite         on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd      off

# This is required to use both PAM-based authentication and local passwords
AuthOrder         mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile         off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

# Logging onto /var/log/lastlog is enabled but set to off by default
#UseLastlog on

# In order to keep log file dates consistent after chroot, use timezone info
# from /etc/localtime.  If this is not set, and proftpd is configured to
# chroot (e.g. DefaultRoot or <Anonymous>), it will use the non-daylight
# savings timezone regardless of whether DST is in effect.
#SetEnv TZ :/etc/localtime

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://www.securityfocus.com/bid/11430/discuss
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
Include /etc/proftpd/tls.conf

#
# Useful to keep VirtualHost/VirtualRoot directives separated
#
#Include /etc/proftpd/virtuals.conf

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User            ftp
#   Group            nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias         anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser   on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell      off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients         10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin         welcome.msg
#   DisplayChdir      .message
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
#   #   Umask            022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

# Include other custom configuration files
Include /etc/proftpd/conf.d/
```

Thank you very much!

---

### Post by TheFu on 2019-08-21
Any interest in using a secure transfer protocol like sftp, rsync, or scp instead?
Plain FTP should have died in the 1990s.  Google Chrome is removing support for plain FTP.

---

### Post by chrispet on 2019-08-21
Because i'm newbie please could you tell me another way to install a secure ftp server? I also tried with the vsftpd but i have almost the same problem. I have check the error logs but they havent's errors. Also in Vsftpd i can't login because i have this error 
```
500 oops: vsftpd: refusing to run with writable root inside chroot()
```
Unfortunately i can't fix that

---

### Post by slickymaster on 2019-08-21
Thread moved to **Server Platforms** for a better fit

---

### Post by chrispet on 2019-08-21
Could anybody help me please?

---

### Post by TheFu on 2019-08-21
> **chrispet said:**
> Because i'm newbie please could you tell me another way to install a secure ftp server? I also tried with the vsftpd but i have almost the same problem. I have check the error logs but they havent's errors. Also in Vsftpd i can't login because i have this error 
```
500 oops: vsftpd: refusing to run with writable root inside chroot()
```
Unfortunately i can't fix that

I haven't used plain FTP since the early 2000s, so no, I cannot help.  sftp is included in the openssh-server package.  All networked OSes have a great sftp client.

I would (on the remote server):
[LIST=1]
[*]purge any plain FTP server(s) you've attempted to install/setup
[*]**sudo apt install openssh-server fail2ban**  # install the ssh-server and a brute-force blocking tool
[*] if you have a firewall enabled, then you'll want to open port 22/tcp.
[/LIST]
Let's assume this server is on the same LAN, using default port - 22/tcp - with an IP of 192.168.1.59
Access over the internet should use a different port.  Call that a later step for now.

On the client-side, I would:
[LIST]
[*]Install an ssh client: **sudo apt install openssh-client**
[*]Generate ssh keys: **ssh-keygen -t ed25519**  # this will make connections secure enough to use over the internet
[*]Push that new key to the remote server
[*]Push the key to the to the remote server:  **ssh-copy-id thefu@192.168.1.59**    # that will be the last time I type a password to login/sftp/scp to that machine.
[*]Test the ssh and sftp connections:  **ssh thefu@192.168.1.59**   and try **sftp thefu@192.168.1.59**  # no password needed
[/LIST]

Most (all?) Linux file managers support sftp:// in their URLs to make connections.  Use WinSCP or Filezilla on Windows.  Android has ssh and sftp clients.  OSX does too - I haven't any idea what Apple names them.

Unix systems use ssh to communicate.  This is THE standard method used by all Unix systems around the world and has been for decades.  To someone from Windows, it usually has never been learned. MSFT finally added an ssh capability to Win10 about 2 yrs ago.  Finally.  Some other things that the ssh-family of tools can do. [http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html)
I use ssh all day for all sorts of things.  
* login remotely
* transfer files via sftp, scp, rsync
* edit remote files using vim
* connect to a remote desktop using x2go, which uses ssh for encrypting the network channel AND for authentication on the remote system
* as a socks proxy in a browser when I'm at a local cafe, so surf the web safely and appear like I'm at home.
* remotely mount a file system, using sshfs - handy to run a script on remote storage when the script/program isn't installed there.
ssh is amazing.

There are many more things that we can setup to make ssh much more convenient to use.  When was the last time something was both more convenient AND more secure?

---

### Post by LHammonds on 2019-08-21
This is how I setup [vsftpd on Ubuntu 16.04](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=228).  I have not installed it on 18.04 but I would imagine it would be VERY similar in the steps.

LHammonds

---

