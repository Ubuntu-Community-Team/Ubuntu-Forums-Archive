---
title: "Installing FTP server (n00b)"
date: 2007-08-23
forum: Server Platforms
---

### Post by yc2 on 2007-08-23
Hi,

I am completely new with FTP servers. Please help :)  I use Feisty. I am trying to install proftpd.

I have done the following:

```
sudo apt-get install proftpd
```

During install I was given one choice of options: inetd or standalone. I chose inetd activation.

I then downloaded inetd package through synaptic.

If I do:
/etc/init.d/inetd restart
The system replies:
Restarting internet superserver ...        OK

And now the problem :)
I try gFTP from the same machine, setting server to localhost.
I also try, from another (Windows-) machine in my small home-network: ws_ftp_95_le, setting host to 192.168.1.101.
I set <usr> and <pwd> to the data I use as my Ubuntu login.

In both cases (gFTP or ws_ftp_95_le) I get the same behavior:

```
connecting to 192.168.1.101
connected to 192.168.1.101  port 21

connection failed/disconnected
```
(all happens very quickly)

Why does not the connection stay open? Please, what should I do in order to be able to upload/download? Thanks a lot.

proftpd.conf:
```


#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on

ServerName			"Debian"
ServerType			inetd
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

# Use this to jail all users in their homes 
# DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShells		off

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

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off

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



```

---

### Post by A3sthetix on 2007-08-23
I'm kinda noobish too, but try the following:

Turn "UseIPv6" to off

Then restart the server. Also, check you local firewalls (on your computers). I would also try a different port (ie. 12345) and see if you get the same problem. Restart the server after changing your settings file to make them active.

---

### Post by yc2 on 2007-08-23
Thanks for advice, I tried it all:

UseIPv6    off
Shutdown ZoneAlarm on remote computer. As I understand, there is no firewall in my Feisty, see iptables below.

If I change port number in proftpd.conf and try to connect to that port via client at localhost or within LAN then the client will not even connect. Using port 21, as described above **it seems the client connects briefly but then disconnects/is disconnected**.

I restart the server between every change of proftpd.conf, of course.

I am new to this and may have missed something basic.

I just don't seem to make it work. **Further advice appreciated **:)

```
$iptables --list

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by freebeer on 2007-08-23
Have you actually added the username and password to allow access to proftpd?  BTW, I use gprofptd to give me a graphical interface when configuring/checking.  I find it easier in some instances (such as adding users, etc.)

---

### Post by yc2 on 2007-08-23
> **freebeer said:**
> Have you actually added the username and password to allow access to proftpd?  BTW, I use gprofptd to give me a graphical interface when configuring/checking.  I find it easier in some instances (such as adding users, etc.)
Thanks for advice. The following fact supports what you say:
If I try to login with a user that does not exist in my Ubuntu system or use a password that is completely wrong, I still see the same behavior (connected a short second and then disconnected).

I read about gproftpd, but as I understood it is only used with  "standalone" gftpd use. My system rescources are not the most ample and I have therefore been advised to use gftpd in "inet" mode.

I am not  sure how to add users. My impression was that users in my Ubuntu system would automatically be granted ftp access:
([http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ConfigFile.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ConfigFile.html)) saying this:
> By default, the proftpd daemon reads the host's /etc/passwd file for logging in users. This means that to add FTP users, you simply need to create new system accounts for those users in your /etc/passwd file.
So I came under the impression I could just log in with my Ubuntu username and password. I have not added it specifically. If this is to be done, I don't know where to add the new ftp-user.

I have also, without improvement,  played around with parameters in proftpd.conf:
```
RequireValidShells  off
UserAlias <myusername> <mypassword>
DefaultRoot  ~

```

But I am really fumbling in the dark here. Thanks for the help received, but **I haven't got it working yet**.


EDIT #1:
For a second I even doubted the server was running, but I think that is not the problem: If I stop the server by doing
```
/etc/init.d/inetd stop
```
It is not at all possible to connect ("connection refused").
The proftpd.log is empty however.

EDIT #2:
FileZilla is slightly more verbose:¨
```
Status:	Connecting to 192.168.1.101 ...
Status:	Connected with 192.168.1.101. Waiting for welcome message...
Error:	Disconnected from server
Error:	Unable to connect!
Status:	Waiting to retry... (5 retries left)
Status:	Connecting to 192.168.1.101 ...
... <and so on>
```

---

### Post by HermanAB on 2007-08-23
You can debug a TCP connection using telnet:
$ telnet  192.168.1.2  21

That will enable you to see whether the server answers at all.

Cheers,

Herman

---

### Post by soulresin on 2007-08-23
Is it possible that inetd is not configured to listen for FTP requests?

Check /etc/inetd.conf for the ftp stuff (sorry, I don't use inetd, so I'm not entirely sure how it should look).

Also do:

netstat -ntlp | grep :21

to see if inetd is listening on the ftp port.

Hope that helps.

---

### Post by yc2 on 2007-08-24
HermanAB and soulresin
Thanks guys, I did some experimenting before I read your suggestions. I put the result of that here below.

Since I am having problems, maybe I should, at least temporarily, skip the "inetd" way of running proftpd. As seen below, maybe one gets a clearer understanding if one runs proftpd as "standalone". Maybe the clients have only been talking to inetd and proftpd has never run?

I will check your suggestions and be back, thanks.

---- What I just tried ----

I tried running the server in "standalone" mode:
dpkg-reconfigure proftpd

choose standalone

Also tried gproftpd. Managed to add one user (called "y_ftp"). gproftpd completely rewrote /etc/proftpd/proftpd.conf like this:
```

#
# Includes required DSO modules. This is mandatory in proftpd 1.3
#
Include	/etc/proftpd/modules.conf

ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.1.101"
ServerIdent on "My FTPD"
ServerAdmin Admin@this.domain.topdomain
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayFirstChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<Limit LOGIN>
  AllowUser y_ftp
  DenyALL
</Limit>

<Anonymous /var/ftp/y_ftp>
User y_ftp
Group ftp_users
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>

```
However, it is not possible to start the proftp server in standalone mode:
```
$ sudo /etc/init.d/proftpd start
 * Starting ftp server proftpd                                                   
 - IPv4 getaddrinfo 'ubuntu' error: No address associated with hostname
 - warning: unable to determine IP address of 'ubuntu'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]

```
It seems that the proftpd is trying to find the IP-number of "ubuntu". "ubuntu" is the name of my computer. I don't understand from where it gets that name (does not exist in proftpd.conf). Neither do I primarily intend to connect a domain name to the server, only use in LAN.

This entry of proftpd.conf, I have entered myself:
ServerName "192.168.1.101"

So my suspicion is that proftpd has never started properly. If I use the inetd way of running proftpd, clients will first connect to inetd and then be cut off when they cannot be transferred to proftpd???

inetd.conf:
```
#<off># ftp	stream	tcp	nowait	root	/usr/sbin/tcpd /usr/sbin/proftpd

```
Really messy this ;)

---

### Post by yc2 on 2007-08-24
Thank you all for advice. Situation has improved a little. After adding to "etc/hosts":
```
127.0.0.1  ubuntu
```
proftpd starts in standalone mode and seems to work OK. I still don't understand why it looks for "ubuntu", but adding this key to "etc/hosts" made it work.

Thanks to freebeer for advice on gproftpd, seems very useful.
The user created with gproftpd can log in and transfer files over the LAN. (What I had previously read about automatically being able to login for ftp using your Ubuntu user name and pwd does not seem to apply in my case.)

I now have to read up now on directories used for transfer etc.
Sorry for spamming the forum today, thanks for guidance.

---

### Post by NewbieNik on 2007-08-24
Ubuntu is the default hostname provided during installation of Ubuntu. You can change this during the install, but I wouldn recomment changing it once installed as a lot of the services depend on the host name to run (As you have found out)
It is possible, but it is fiddly.....

---

